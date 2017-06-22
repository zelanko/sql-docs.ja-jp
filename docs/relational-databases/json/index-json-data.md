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
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 3ed7a51b28d2b17b3239f971d0f4f684bec145cd
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="index-json-data"></a>JSON データへのインデックスの追加
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

SQL Server 2016 で JSON は、組み込みのデータ型ではありませんし、SQL Server には、カスタム JSON インデックスはありません。 最適化できますクエリ JSON ドキュメントでは、ただし、標準的なインデックスを使用しています。 

データベースのインデックスには、フィルターおよび並べ替え操作のパフォーマンスが向上します。 インデックスがない場合、SQL Server は、データのクエリを実行するたびに、テーブルを完全にスキャンしなければなりません。  
  
## <a name="index-json-properties-by-using-computed-columns"></a>計算列を使用した JSON のプロパティへのインデックスの追加  
SQL Server に JSON データを格納するときに通常するフィルターやソート クエリの結果を 1 つまたは複数*プロパティ*は JSON ドキュメントのです。  

### <a name="example"></a>例 
この例であると想定 AdventureWorks`SalesOrderHeader`テーブルには、`Info`販売注文に関する JSON 形式でさまざまな情報を含む列。 たとえば、顧客、販売員、および請求先住所、およびなどに関する情報が含まれています。 値を使用する場合、`Info`顧客の販売注文をフィルターする列。

### <a name="query-to-optimize"></a>クエリを最適化するには
インデックスを使用して最適化するクエリの種類の例を次に示します。  
  
```sql  
SELECT SalesOrderNumber,
    OrderDate,
    JSON_VALUE(Info, '$.Customer.Name') AS CustomerName
FROM Sales.SalesOrderHeader
WHERE JSON_VALUE(Info, '$.Customer.Name') = N'Aaron Campbell' 
```  

### <a name="example-index"></a>例のインデックス
フィルターを高速化する場合または`ORDER BY`プロパティを JSON ドキュメントで句は、他の列で既に使用していると同じインデックスを使用することができます。 ことはできませんただし、*直接*JSON ドキュメントのプロパティを参照します。
    
1.  「仮想列」を作成する必要が最初に、フィルター処理に使用する値を返します。
2.  それからその仮想列にインデックスを作成します。  
  
次の例では、インデックス作成のために使用できる計算列を作成します。 新しい計算列にインデックスを作成します。 この例に格納されている顧客名を公開する列を作成、 `$.Customer.Name` JSON データのパス。 
  
```sql  
ALTER TABLE Sales.SalesOrderHeader
ADD vCustomerName AS JSON_VALUE(Info,'$.Customer.Name')

CREATE INDEX idx_soh_json_CustomerName
ON Sales.SalesOrderHeader(vCustomerName)  
```  
### <a name="more-info-about-the-computed-column"></a>詳細については、計算列 
計算列は保存されません。 インデックスを再構築する必要がある場合にのみ計算されます。 これでは、テーブルのその他の領域を占有しません。   
  
この例では、クエリで使用しようとすると同じ式に、計算列を作成して、式がされる重要`JSON_VALUE(Info, '$.Customer.Name')`です。  
  
クエリは書き直す必要はありません。 含む式を使用する場合、`JSON_VALUE`関数、上記のクエリの例に示すように SQL Server 存在することは、同じ式を使用する同等な計算列と表示可能であればインデックスを適用します。

### <a name="execution-plan-for-this-example"></a>この例の実行プラン
この例では、クエリの実行プランを次に示します。  
  
![実行計画](../../relational-databases/json/media/jsonindexblog1.png "実行計画")  
  
SQL Server では、テーブルを完全にスキャンするのではなく、非クラスター化インデックスに index seek を使用し、指定した条件に一致する行を探します。 キーの参照を使用し、`SalesOrderHeader`この例では、クエリで参照されているその他の列をフェッチするテーブル`SalesOrderNumber`と`OrderDate`です。  
 
### <a name="optimize-the-index-further-with-included-columns"></a>付加列を含むインデックスはさらに最適化します。
インデックスに必要な列を追加する場合は、テーブルでこの追加の参照を回避できます。 拡張し、次の例で示すように、標準の付加列としてこれらの列を追加することができます、`CREATE INDEX`上に示した例です。  
  
```sql  
CREATE INDEX idx_soh_json_CustomerName
ON Sales.SalesOrderHeader(vCustomerName)
INCLUDE(SalesOrderNumber,OrderDate)
```  
  
ここでは SQL Server はありませんから追加のデータを読み取る、`SalesOrderHeader`テーブルの JSON の非クラスター化インデックスに含まれる必要があるためです。 これは、クエリで JSON と列のデータを結合して、ワークロードに最適なインデックスを作成することをお勧めします。  
  
## <a name="json-indexes-are-collation-aware-indexes"></a>照合順序対応のインデックスである JSON インデックス  
JSON データに対してインデックスの重要な機能は、インデックスが照合順序に対応することです。 結果、`JSON_VALUE`計算列を作成するときに使用する関数は、入力式からその照合順序を継承するテキスト値。 そのため、インデックス内の値は、ソース列で定義されている照合順序の規則を使用する並べ替え。  
  
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
  
上記のコマンドでは、標準的なインデックスを作成、計算列で`vName`、JSON から値を表す`$.name`プロパティです。 セルビア語 (キリル) のコードページでは、文字の順序は、'А'、'Б'、'В'、'Г'、'Д'、'Ђ'、'Е' などです。インデックス内のアイテムの順序はセルビア語 (キリル) の規則に準拠しているため、結果の`JSON_VALUE`関数は、ソース列からその照合順序を継承します。 次の例では、このコレクションにクエリを実行し、結果を名前で並べ替えます。  
  
```sql  
SELECT JSON_VALUE(json,'$.name'),*
FROM JsonCollection
ORDER BY JSON_VALUE(json,'$.name')
```  
  
 実際の実行計画を見ると、非クラスター化インデックスからの並べ替えられた値を使用していることがわかります。  
  
 ![実行計画](../../relational-databases/json/media/jsonindexblog2.png "実行計画")  
  
 クエリには、`ORDER BY`句、実行プランは、Sort 演算子を使用しません。 JSON インデックスは既にセルビア語 (キリル) の規則に従って並んでいます。 したがって、結果が既に並べ替えられている場合、SQL Server は非クラスター化インデックスを使用できます。  
  
 ただしの照合順序を変更する場合、`ORDER BY`式の例では、配置した場合の`COLLATE French_100_CI_AS_SC`後、`JSON_VALUE`関数 - 別のクエリ実行プランが得です。  
  
 ![実行計画](../../relational-databases/json/media/jsonindexblog3.png "実行計画")  
  
 インデックス内の値の順序はフランス語の照合順序の規則を準拠していないために、SQL Server では、結果の順序付けにそのインデックスを使用できません。 したがって、フランス語の照合順序の規則を使用して結果を並べ替える Sort 演算子が追加されます。  
 
## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>詳細については、組み込みの JSON が SQL Server のサポート  
特定のソリューションの多くは、ケース、および推奨事項を使用して、参照してください、[組み込みの JSON サポートに関するブログの投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)SQL Server および Microsoft のプログラム マネージャー Jovan Popovic による Azure SQL データベースでします。

