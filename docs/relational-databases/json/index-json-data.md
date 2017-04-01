---
title: "JSON データへのインデックスの追加 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JSON, JSON データのインデックスの追加"
  - "JSON データのインデックスの追加"
ms.assetid: ced241e1-ff09-4d6e-9f04-a594a9d2f25e
caps.latest.revision: 9
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# JSON データへのインデックスの追加
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  データベース インデックスでは、フィルターおよび並べ替え操作のパフォーマンスを向上させることができます。 インデックスがない場合、SQL Server は、データのクエリを実行するたびに、テーブルを完全にスキャンしなければなりません。  
  
 JSON のデータ型は、SQL Server 2016 には組み込まれてはおらず、SQL Server 2016 には、カスタム JSON インデックスはありません。 ただし、標準的なインデックスを使用して、JSON ドキュメント用にクエリを最適化できます。  
  
## 計算列を使用した JSON のプロパティへのインデックスの追加  
 SQL Server に JSON データを格納する際、通常は JSON ドキュメントのプロパティを使用してクエリの結果をフィルターやソートしたいでしょう。  
  
 この例の AdventureWorks の SalesOrderHeader テーブルには、顧客、販売員、配送/請求先住所など、販売注文に関するさまざまな情報を含む "Info" 列があります。 顧客の販売注文をフィルター処理するために、Info 列の値を使用したいとします。 インデックスを使用して最適化するクエリを次に示します。  
  
```tsql  
SELECT SalesOrderNumber, OrderDate,  
 JSON_VALUE(Info, '$.Customer.Name') AS CustomerName  
 FROM Sales.SalesOrderHeader   
 WHERE JSON_VALUE(Info, '$.Customer.Name') = N'Aaron Campbell'  
```  
  
 JSON ドキュメントのプロパティでフィルターまたは ORDER BY 句を高速化する場合は、他の列で使用しているのと同じインデックスを使用します。 ただし、JSON ドキュメントのプロパティを直接参照することはできません。 最初にフィルター処理に使用する値を返す "仮想列" を作成する必要があります。 それからその仮想列にインデックスを作成します。  
  
 次の例では、インデックスに使用できる計算列を作成し、その後にその列にインデックスを作成します。 この例では、JSON ドキュメントの $.Customer.Name パスに格納されている顧客名を公開する列を作成します。  
  
```tsql  
ALTER TABLE Sales.SalesOrderHeader  
 ADD vCustomerName AS JSON_VALUE(Info, '$.Customer.Name')  
  
 CREATE INDEX idx_soh_json_CustomerName  
 ON Sales.SalesOrderHeader(vCustomerName)  
  
```  
  
 計算列は保存されません。 これでは、テーブルのその他の領域を占有しません。 インデックスを再構築する必要がある場合にのみ計算されます。  
  
 計算列は、クエリで使用するのと同じ式を使用して作成することが重要です。この例では、`JSON_VALUE(Info, '$.Customer.Name')` です。  
  
 クエリは書き直す必要はありません。 JSON_VALUE 関数で式を使用する場合、SQL Server は同じ式を使用する同等な計算列が存在することを確認し、可能であればインデックスを適用します。 ここに、この例のクエリの実行計画を示します。  
  
 ![Execution plan](../../relational-databases/json/media/jsonindexblog1.png "Execution plan")  
  
 SQL Server では、テーブルを完全にスキャンするのではなく、非クラスター化インデックスに index seek を使用し、指定した条件に一致する行を探します。 次いで、SalesOrderHeader テーブルのキー参照を使用し、クエリで参照される、この例では SalesOrderNumber と OrderDate のその他の列をフェッチします。  
  
 JSON インデックスに必要な列を追加すれば、テーブルでこの追加の参照を回避できます。 これらの列は、次の例のとおり標準の付加列として追加できます。  
  
```tsql  
CREATE INDEX idx_soh_json_CustomerName  
 ON Sales.SalesOrderHeader(vCustomerName)  
 INCLUDE (SalesOrderNumber, OrderDate)  
```  
  
 この場合、SQL Server には、JSON の非クラスター化インデックスに必要なすべてのものが含まれているため SalesOrderHeader テーブルから追加のデータを読み取りません。 これは、JSON と列データをクエリに結合し、ワークロードに最適なインデックスを作成するよい方法です。  
  
## 照合順序対応のインデックスである JSON インデックス  
 JSON のインデックスの重要な機能は、それが照合順序に対応しているということです。 JSON_VALUE 関数の結果は、入力式からその照合順序を継承するテキスト値です。 そのため、インデックス内の値は、ソース列で定義されている照合順序規則を使用して並べ替えられています。  
  
 これを示すために、次の例では、主キーと JSON コンテンツを使用して単純なコレクション テーブルを作成します。  
  
```tsql  
CREATE TABLE JsonCollection  
 ( id int identity constraint PK_JSON_ID primary key,  
 json nvarchar(max) COLLATE Serbian_Cyrillic_100_CI_AI  
 CONSTRAINT [Content should be formatted as JSON]  
 CHECK (ISJSON(json)>0)  
 )  
```  
  
 上記のコマンドでは、JSON 列でのセルビア語 (キリル) の照合順序を指定しています。 次の例では、テーブルに入力し、name プロパティにインデックスを作成します。  
  
```tsql  
INSERT INTO JsonCollection  
 VALUES (N'{"name":"Иво","surname":"Андрић"}'),  
 (N'{"name":"Андрија","surname":"Герић"}'),  
 (N'{"name":"Владе","surname":"Дивац"}'),  
 (N'{"name":"Новак","surname":"Ђоковић"}'),  
 (N'{"name":"Предраг","surname":"Стојаковић"}'),  
 (N'{"name":"Михајло","surname":"Пупин"}'),  
 (N'{"name":"Борислав","surname":"Станковић"}'),  
 (N'{"name":"Владимир","surname":"Грбић"}'),  
 (N'{"name":"Жарко","surname":"Паспаљ"}'),  
 (N'{"name":"Дејан","surname":"Бодирога"}'),  
 (N'{"name":"Ђорђе","surname":"Вајферт"}'),  
 (N'{"name":"Горан","surname":"Бреговић"}'),  
 (N'{"name":"Милутин","surname":"Миланковић"}'),  
 (N'{"name":"Никола","surname":"Тесла"}')  
  
 GO  
 ALTER TABLE JsonCollection  
 ADD vName AS JSON_VALUE(json, '$.name')  
  
 CREATE INDEX idx_name  
 ON JsonCollection(vName)  
  
```  
  
 上記のコマンドは、JSON $.name プロパティから値を表す、計算列 vName に標準的なインデックスを作成します。 セルビア語 (キリル) のコードページでは、文字の順序は、'А'、'Б'、'В'、'Г'、'Д'、'Ђ'、'Е' などです。JSON_VALUE 関数の結果は、ソース列からの照合順序を継承するため、インデックスの項目の順序はセルビア語 (キリル) の規則に準拠しています。 次の例では、このコレクションにクエリを実行し、結果を名前で並べ替えます。  
  
```tsql  
SELECT JSON_VALUE(json, '$.name'), * FROM JsonCollection  
 ORDER BY JSON_VALUE(json, '$.name')  
  
```  
  
 実際の実行計画を見ると、非クラスター化インデックスからの並べ替えられた値を使用していることがわかります。  
  
 ![Execution plan](../../relational-databases/json/media/jsonindexblog2.png "Execution plan")  
  
 クエリには ORDER BY 句がありますが、実行計画では、Sort 演算子は使用しません。 JSON インデックスは既にセルビア語 (キリル) の規則に従って並んでいます。 したがって、結果が既に並べ替えられている場合、SQL Server は非クラスター化インデックスを使用できます。  
  
 ただし、JSON_VALUE 関数の後に `COLLATE French_100_CI_AS_SC` を配置するなど、照合順序を式で変更した場合、得られるクエリ実行計画は異なります。  
  
 ![Execution plan](../../relational-databases/json/media/jsonindexblog3.png "Execution plan")  
  
 インデックス内の値の順序はフランス語の照合順序の規則を準拠していないために、SQL Server では、結果の順序付けにそのインデックスを使用できません。 したがって、フランス語の照合順序の規則を使用して結果を並べ替える Sort 演算子が追加されます。  
  
  