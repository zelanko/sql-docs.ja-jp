---
title: "JSON データへのインデックスの追加 | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JSON, indexing JSON data
- indexing JSON data
ms.assetid: ced241e1-ff09-4d6e-9f04-a594a9d2f25e
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 2d618b486f61f2e25a221517eb0efdaed70f582d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/31/2017

---
# <a name="index-json-data"></a>JSON データへのインデックスの追加
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

SQL Server 2016 では、JSON のデータ型は組み込まれておらず、SQL Server には、カスタム JSON インデックスはありません。 ただし、標準的なインデックスを使用して、JSON ドキュメント用にクエリを最適化できます。 

データベース インデックスでは、フィルターおよび並べ替え操作のパフォーマンスを向上させることができます。 インデックスがない場合、SQL Server は、データのクエリを実行するたびに、テーブルを完全にスキャンしなければなりません。  
  
## <a name="index-json-properties-by-using-computed-columns"></a>計算列を使用した JSON のプロパティへのインデックスの追加  
SQL Server に JSON データを格納するときは通常、JSON ドキュメントの 1 つまたは複数の "*プロパティ*" でクエリ結果をフィルターしたり並べ替えたりします。  

### <a name="example"></a>例 
この例では、AdventureWorks の `SalesOrderHeader` テーブルに、注文に関するさまざまな情報を JSON 形式で格納している `Info` 列があるものとします。 たとえば、顧客、営業担当者、出荷および請求先住所などの情報が含まれます。 顧客の販売注文をフィルター処理するために、`Info` 列の値を使用したいとします。

### <a name="query-to-optimize"></a>最適化するためのクエリ
インデックスを使用して最適化するクエリの種類の例を次に示します。  
  
```sql  
SELECT SalesOrderNumber,
    OrderDate,
    JSON_VALUE(Info, '$.Customer.Name') AS CustomerName
FROM Sales.SalesOrderHeader
WHERE JSON_VALUE(Info, '$.Customer.Name') = N'Aaron Campbell' 
```  

### <a name="example-index"></a>インデックスの例
JSON ドキュメントのプロパティでフィルターまたは `ORDER BY` 句を高速化する場合は、他の列で既に使用しているのと同じインデックスを使用します。 ただし、JSON ドキュメントのプロパティを "*直接*" 参照することはできません。
    
1.  最初に、フィルター処理に使用する値を返す "仮想列" を作成する必要があります。
2.  それからその仮想列にインデックスを作成します。  
  
次の例では、インデックスに使用できる計算列を作成します。 その後で、新しい計算列にインデックスを作成します。 この例では、JSON データの `$.Customer.Name` パスに格納されている顧客名を公開する列を作成します。 
  
```sql  
ALTER TABLE Sales.SalesOrderHeader
ADD vCustomerName AS JSON_VALUE(Info,'$.Customer.Name')

CREATE INDEX idx_soh_json_CustomerName
ON Sales.SalesOrderHeader(vCustomerName)  
```  
### <a name="more-info-about-the-computed-column"></a>計算列に関するその他の情報 
計算列は保存されません。 インデックスを再構築する必要がある場合にのみ計算されます。 これでは、テーブルのその他の領域を占有しません。   
  
計算列は、クエリで使用するのと同じ式を使用して作成することが重要です。この例では、式は `JSON_VALUE(Info, '$.Customer.Name')` です。  
  
クエリは書き直す必要はありません。 `JSON_VALUE` 関数を含む式を使用する場合、上の例のクエリのように、SQL Server は同じ式を使用する同等な計算列が存在することを確認し、可能であればインデックスを適用します。

### <a name="execution-plan-for-this-example"></a>この例の実行プラン
この例のクエリの実行プランを次に示します。  
  
![実行計画](../../relational-databases/json/media/jsonindexblog1.png "実行計画")  
  
SQL Server では、テーブルを完全にスキャンするのではなく、非クラスター化インデックスに index seek を使用し、指定した条件に一致する行を探します。 次に、`SalesOrderHeader` テーブルでキー参照を使って、クエリで参照される他の列 (この例では `SalesOrderNumber` と `OrderDate`) をフェッチします。  
 
### <a name="optimize-the-index-further-with-included-columns"></a>付加列でインデックスをさらに最適化する
インデックスに必要な列を追加すれば、テーブルでこの追加の参照を回避できます。 これらの列は、次の例のとおり標準の付加列として追加できます。これは、前に示した `CREATE INDEX` の例を拡張します。  
  
```sql  
CREATE INDEX idx_soh_json_CustomerName
ON Sales.SalesOrderHeader(vCustomerName)
INCLUDE(SalesOrderNumber,OrderDate)
```  
  
この場合、必要なものがすべて JSON の非クラスター化インデックスに含まれているため、SQL Server は `SalesOrderHeader` テーブルから追加のデータを読み取る必要はありません。 これは、JSON と列データをクエリに結合し、ワークロードに最適なインデックスを作成するよい方法です。  
  
## <a name="json-indexes-are-collation-aware-indexes"></a>照合順序対応のインデックスである JSON インデックス  
JSON データに対するインデックスの重要な機能は、インデックスが照合順序に対応することです。 計算列の作成に使う `JSON_VALUE` 関数の結果は、入力式からその照合順序を継承するテキスト値です。 そのため、インデックス内の値は、ソース列で定義されている照合順序規則を使用して並べ替えられています。  
  
これを示すために、次の例では、主キーと JSON コンテンツを使用して単純なコレクション テーブルを作成します。  
  
```sql  
CREATE TABLE JsonCollection
 (
  id INT IDENTITY CONSTRAINT PK_JSON_ID PRIMARY KEY,
  json NVARCHAR(MAX) COLLATE SERBIAN_CYRILLIC_100_CI_AI
  CONSTRAINT [Content should be formatted as JSON]
  CHECK(ISJSON(json)>0)
 ) 
```  
  
上記のコマンドでは、JSON 列でのセルビア語 (キリル) の照合順序を指定しています。 次の例では、テーブルに入力し、name プロパティにインデックスを作成します。  
  
```sql  
INSERT INTO JsonCollection
VALUES
(N'{"name":"Иво","surname":"Андрић"}'),
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
ADD vName AS JSON_VALUE(json,'$.name')

CREATE INDEX idx_name
ON JsonCollection(vName)
```  
  
上記のコマンドは計算列 `vName` に標準的なインデックスを作成します。これはJSON の `$.name` プロパティからの値を表します。 セルビア語 (キリル) のコードページでは、文字の順序は、'А'、'Б'、'В'、'Г'、'Д'、'Ђ'、'Е' などです。`JSON_VALUE` 関数の結果は、ソース列からの照合順序を継承するため、インデックスの項目の順序はセルビア語 (キリル) の規則に準拠しています。 次の例では、このコレクションにクエリを実行し、結果を名前で並べ替えます。  
  
```sql  
SELECT JSON_VALUE(json,'$.name'),*
FROM JsonCollection
ORDER BY JSON_VALUE(json,'$.name')
```  
  
 実際の実行計画を見ると、非クラスター化インデックスからの並べ替えられた値を使用していることがわかります。  
  
 ![実行計画](../../relational-databases/json/media/jsonindexblog2.png "実行計画")  
  
 クエリには `ORDER BY` 句がありますが、実行プランでは、Sort 演算子は使用しません。 JSON インデックスは既にセルビア語 (キリル) の規則に従って並んでいます。 したがって、結果が既に並べ替えられている場合、SQL Server は非クラスター化インデックスを使用できます。  
  
 ただし、`JSON_VALUE` 関数の後に `COLLATE French_100_CI_AS_SC` を配置するなど、`ORDER BY` 式の照合順序を変更した場合、得られるクエリ実行プランは異なります。  
  
 ![実行計画](../../relational-databases/json/media/jsonindexblog3.png "実行計画")  
  
 インデックス内の値の順序はフランス語の照合順序の規則を準拠していないために、SQL Server では、結果の順序付けにそのインデックスを使用できません。 したがって、フランス語の照合順序の規則を使用して結果を並べ替える Sort 演算子が追加されます。  
 
## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>SQL Server に組み込まれている JSON サポートの詳細情報  
多くの具体的なソリューション、ユース ケース、推奨事項については、Microsoft のプログラム マネージャー Jovan Popovic による SQL Server および Azure SQL Database に[組み込まれている JSON のサポートに関するブログ投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)をご覧ください。

