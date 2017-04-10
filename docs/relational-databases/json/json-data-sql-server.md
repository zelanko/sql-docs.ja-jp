---
title: "JSON データ (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/31/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "JSON"
  - "JSON, 組み込みサポート"
ms.assetid: c9a4e145-33c3-42b2-a510-79813e67806a
caps.latest.revision: 47
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 44
---
# JSON データ (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  JSON は、最新の Web アプリケーションとモバイル アプリケーションでデータを交換するために使用される、一般的なテキスト形式のデータ形式です。 また、JSON はログ ファイル内の非構造化データや Microsoft Azure DocumentDB のような NoSQL データベースを格納するためも使用されます。 REST Web サービスの多くは結果を JSON テキスト形式で返し、データを JSON 形式で受け取ります。 Azure Search、Azure Storage、Azure DocumentDb などの Azure のほとんどのサービスには、JSON を返すか使用する REST エンドポイントがあります。 JSON は、AJAX 呼び出しを使用して Web ページおよび Web サーバー間でデータをやり取りするための主な形式でもあります。  
  
 JSON テキストの例の 1 つを次に示します。  
  
```json  
[   
   { "name": "John", "skills":["SQL","C#","Azure"] },  
   { "name": "Jane", "surname": "Doe" }  
]  
```  
  
 SQL Server は、次の操作を実行するための組み込みの関数および演算子を提供します。  
  
-   JSON テキストを解析し、値を読み取るか、変更する。  
  
-   JSON オブジェクトの配列を表形式に変換する。  
  
-   変換された JSON オブジェクトに対して任意の Transact-SQL クエリを使用する。  
  
-   Transact-SQL クエリの結果を JSON 形式で書式設定する。  
  
 ![Overview of built-in JSON support](../../relational-databases/json/media/jsonslides1overview.png "Overview of built-in JSON support")  
  
 SQL Server が提供する主な機能を次に示します。  
  
 **JSON テキストから値を抽出し、クエリで使用します。** データベース テーブルに格納されている JSON テキストがある場合は、組み込み関数を使用して JSON テキスト内の値を読み取るか、変更することができます。  
  
-   **JSON_VALUE** 関数を使用して、JSON 文字列からスカラー値を抽出します。  
  
-   **JSON_QUERY** を使用して、オブジェクトまたは配列を抽出します。  
  
-   **ISJSON** 関数を使用して、文字列に有効な JSON が含まれているかどうかをテストします。  
  
 次の例のクエリでは、テーブルからリレーショナル データと (jsonCol 列に格納された) JSON データの両方を使用しています。  
  
```tsql  
  
SELECT Name, Surname,     
    JSON_VALUE(jsonCol, '$.info.address.PostCode') as PostCode,  
    JSON_VALUE(jsonCol, '$.info.address."Address Line 1"') +  ' ' + JSON_VALUE(jsonCol, '$.info.address."Address Line 2"') AS Address,  
    JSON_QUERY(jsonCol, '$.info.skills') as Skills  
FROM PeopleCollection  
WHERE ISJSON(jsonCol) > 0   
  AND JSON_VALUE(jsonCol, '$.info.address.town') = 'Belgrade'  
  AND Status = 'Active'  
ORDER BY JSON_VALUE(@jsonInfo, '$.info.address.PostCode')  
  
```  
  
 アプリケーションやツールでは、スカラー テーブル列から取得した値であるか、JSON 列から取得した値であるかの見分けは付きません。 JSON テキストからの値は、Transact-SQL クエリのすべての部分で使用できます (例: WHERE 句、ORDER BY 句、GROUP BY 句、ウィンドウの集計など)。 JSON 関数は、JavaScript のような構文を使用して JSON テキスト内の値を参照します。 詳細については、「[組み込み関数を使用した JSON データの検証、クエリ、変更 &#40;SQL Server&#41;](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md)」、「[JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)」、「[JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)」をご覧ください。  
  
 **JSON 値を変更します。** JSON テキストの一部を修正する必要がある場合は、**JSON_MODIFY** 関数を使用して JSON 文字列のプロパティの値を更新し、更新された JSON 文字列を返します。 次の例では、JSON を格納する変数のプロパティの値を更新します。  
  
```tsql  
SET @jsonInfo = JSON_MODIFY(@jsonInfo, '$.info.address[0].town', 'London')  
```  
  
 **JSON コレクションを行セットに変換します。** SQL Server で JSON のクエリを実行するのにカスタム クエリ言語は不要です。 JSON データのクエリを実行するには、標準の T-SQL を使用することができます。 JSON データのクエリまたはレポートを作成する必要がある場合は、**OPENJSON** 行セット関数を呼び出して JSON データを簡単に行と列に変換できます。 **OPENJSON** 関数を使用すると、JSON データが SQL Server にインポート、または JSON データが行と列に変換されます。 詳細については、「[OPENJSON を使用して JSON データを行と列に変換する &#40;SQL Server&#41;](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md)」をご覧ください。  
  
 次の例では、 **OPENJSON** を呼び出し、 **@json** 変数に格納されたオブジェクトの配列を、標準の SQL SELECT ステートメントを使用してクエリを実行できる行セットに変換します。  
  
```tsql  
SET @json =  
N'[  
      { "id" : 2,"info": { "name": "John", "surname": "Smith" }, "age": 25 },  
      { "id" : 5,"info": { "name": "Jane", "surname": "Smith" }, "dob": "2005-11-04T12:00:00" }  
]'  
  
SELECT *  
FROM OPENJSON(@json)  
 WITH (id int 'strict $.id',  
       firstName nvarchar(50) '$.info.name', lastName nvarchar(50) '$.info.surname',  
       age int, dateOfBirth datetime2 '$.dob')  
  
```  
  
 **結果**  
  
|id|firstName|lastName|age|dateOfBirth|  
|--------|---------------|--------------|---------|-----------------|  
|2|John|Smith|25||  
|5|Jane|Smith||2005-11-04T12:00:00|  
  
 **OPENJSON** では、JSON オブジェクトの配列がテーブルに変換され、各オブジェクトが 1 つの行として表わされ、キーと値のペアがセルとして返されます。 **OPENJSON** が JSON 値を指定の型に変換します。 **OPENJSON** は、フラットなキーと値のペアと、入れ子になった階層構造のオブジェクトの両方を処理できます。 JSON テキストに含まれるすべてのフィールドを返す必要はありません。 JSON 値が存在しない場合、**OPENJSON** は NULL 値を返します。 オプションで型指定の後にパスを指定して、入れ子にされたプロパティを参照するか、異なる名前のプロパティを参照できます。 パス内の省略可能な **strict** プレフィックスでは、指定されたプロパティの値が JSON テキストに存在していなければならないことを指定します。 詳細については、「[OPENJSON を使用して JSON データを行と列に変換する &#40;SQL Server&#41;](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md)」および「[OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)」をご覧ください。  
  
 **SQL Server のデータを JSON に変換または JSON をエクスポートします。** **FOR JSON** 句を **SELECT** ステートメントに追加して、SQL Server データまたは SQL クエリの結果を JSON として書式設定します。 FOR JSON を使用して、JSON 出力の形式設定をクライアント アプリケーションから SQL Server に委任します。 詳細については、「[FOR JSON を使用してクエリ結果を JSON として書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)｣をご覧ください。  
  
 次の例では、PATH モードを FOR JSON 句とともに使用しています。  
  
```tsql  
SELECT id, firstName AS "info.name", lastName AS "info.surname", age, dateOfBirth as dob  
FROM People  
FOR JSON PATH  
```  
  
 [曜日]   
    **FOR JSON** 句は SQL 結果を JSON テキスト形式に設定し、JSON を理解するすべてのアプリケーションで使用できます。 PATH オプションでは、SELECT 句にドット区切りのエイリアスを使用して、クエリ結果内のオブジェクトを入れ子にします。  
  
 **[結果]**  
  
```json  
[  
      { "id" : 2,"info": { "name": "John", "surname": "Smith" }, "age": 25 },  
      { "id" : 5,"info": { "name": "Jane", "surname": "Smith" }, "dob": "2005-11-04T12:00:00" }  
]  
```  
  
 詳細については、「[FOR JSON を使用してクエリ結果を JSON として書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)」および「[FOR 句 &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)」をご覧ください。  
  
## ユース ケース  
 SQL Server は、標準の Transact-SQL 言語を使用してリレーショナル データと JSON データの両方を格納および処理するハイブリッド モデルを提供します。 これにより、JSON ドキュメントのコレクションをテーブル別に整理し、それらの間のリレーションシップを確立、テーブルに格納された厳密に型指定されたスカラー列を JSON 列に格納された柔軟なキーと値のペアに結合し、完全な Transact-SQL を使用して 1 つまたは複数のテーブルのスカラー値と JSON 値の両方についてクエリを実行します。 JSON テキストは通常、varchar 列または nvarchar 列に格納されており、プレーン テキストとしてインデックスが作成されます。 テキストをサポートするすべての SQL Server の機能またはコンポーネントは JSON をサポートします。そのため、JSON とその他の SQL Server 機能間の対話には、ほとんど制約がありません。 JSON はメモリ内テーブルやテンポラル テーブルに格納できるほか、行レベルのセキュリティの述語を JSON テキストに適用することなどができます。 純粋な JSON ワークロードがあり、JSON ドキュメントの処理のためにカスタマイズされたクエリ言語を使用する場合は、Microsoft Azure [DocumentDB](https://azure.microsoft.com/services/documentdb/) の使用をお勧めします。  
  
 ここでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で組み込みの JSON サポートの使用方法を示すユース ケースを紹介します。  
  
## JSON として書式設定された SQL Server テーブルからデータを返す  
 データベース層からデータを取得し、それを JSON 形式で返す Web サービス、または JSON 形式に設定されたデータを受け取る JavaScript フレームワークまたはライブラリがある場合、結果の形式を SQL クエリで直接設定できます。 コードを記述するかライブラリを追加して、タブ形式のクエリ結果を変換し、それからオブジェクトを JSON 形式にシリアライズする代わりに、FOR JSON を使用して JSON 形式への設定を SQL Server に委任できます。  
  
 たとえば、OData の仕様に準拠した JSON 出力を生成するとします。 Web サービスは、次の形式の要求と応答を求めています。  
  
-   要求: `/Northwind/Northwind.svc/Products(1)?$select=ProductID,ProductName`  
  
-   応答: `{"@odata.context":"http://services.odata.org/V4/Northwind/Northwind.svc/$metadata#Products(ProductID,ProductName)/$entity","ProductID":1,"ProductName":"Chai"}`  
  
 この OData URL は、ID が 1 のプロダクトの Product ID 列と ProductName 列に対する要求を表します。 FOR JSON を使用して、出力を SQL Server で求められている形式に設定できます。  
  
```tsql  
SELECT 'http://services.odata.org/V4/Northwind/Northwind.svc/$metadata#Products(ProductID,ProductName)/$entity' AS '@odata.context',   
ProductID, Name as ProductName   
FROM Production.Product  
WHERE ProductID = 1  
FOR JSON AUTO  
  
```  
  
 このクエリの結果は、OData 仕様に完全に準拠した JSON テキストになります。 形式設定とエスケープは、SQL Server によって処理されます。 SQL Server はクエリ結果を OData JSON や GeoJSON など、任意の形式に設定できます。「[空間データを GeoJSON 形式で返す](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/returning-spatial-data-in-geojson-format-part-1)」をご覧ください。  
  
## SQL クエリで JSON データを分析する  
 レポート作成のために JSON データをフィルター処理または集計する必要がある場合は、OPENJSON を使用して JSON をリレーショナル形式に変換できます。 その後、標準の [!INCLUDE[tsql](../../includes/tsql-md.md)] と組み込み関数を使用してレポートを用意します。  
  
```tsql  
SELECT Tab.Id, SalesOrderJsonData.Customer, SalesOrderJsonData.Date  
FROM   SalesOrderRecord AS Tab  
         CROSS APPLY  
    OPENJSON (Tab.json, N'$.Orders.OrdersArray')  
          WITH (  
             Number   varchar(200) N'$.Order.Number',   
             Date     datetime     N'$.Order.Date',  
             Customer varchar(200) N'$.AccountNumber',   
             Quantity int          N'$.Item.Quantity'  
          )  
 AS SalesOrderJsonData  
WHERE JSON_VALUE(Tab.json, '$.Status') = N'Closed'  
ORDER BY JSON_VALUE(Tab.json, '$.Group'), Tab.DateModified  
  
```  
  
 同じクエリに標準テーブルの列と JSON テキストからの値の両方を使用できます。 JSON_VALUE(Tab.json, '$.Status') 式にインデックスを追加して、クエリのパフォーマンスを向上させることができます。  
  
## SQL Server に JSON データをインポートする  
 JSON データを外部サービスから SQL Server に読み込む必要がある場合は、アプリケーション レイヤー内でデータを解析する代わりに、OPENJSON を使用してデータを SQL Server にインポートできます。  
  
```tsql  
INSERT INTO SalesReport  
SELECT SalesOrderJsonData.*  
FROM OPENJSON (@jsonVariable, N'$.Orders.OrdersArray')  
          WITH (  
             Number   varchar(200) N'$.Order.Number',   
             Date     datetime     N'$.Order.Date',  
             Customer varchar(200) N'$.AccountNumber',   
             Quantity int          N'$.Item.Quantity'  
          )  
 AS SalesOrderJsonData;  
  
```  
  
 JSON 変数の内容は、何らかの外部 REST サービスによって提供されたり、何らかのクライアント側 JavaScript フレームワークからのパラメーターとして送信されたり、外部ファイルから読み込まれたりします。 結果は、JSON テキストから SQL Server テーブルに簡単に挿入、更新、マージできます。 このシナリオの詳細については、 [JSON データを SQL Server にインポートする方法に関するブログ](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/09/22/openjson-the-easiest-way-to-import-json-text-into-table/)、「 [Upsert JSON documents in SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/03/upsert-json-documents-in-sql-server-2016)」 (SQL Server 2016 で JSON ドキュメントの UPSERT を実行する)、「 [Loading GeoJSON data into SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/loading-geojson-data-into-sql-server/)」 (GeoJSON データを SQL Server に読み込む) を参照してください。  
  
## SQL Server に JSON ファイルを読み込む  
 ファイルに格納された情報は、標準の JSON または行区切りの JSON 形式に書式設定できます。 SQL Server は JSON ファイルのコンテンツをインポートし、OPENJSON または JSON_VALUE 関数を使用してそれを解析してテーブルに読み込むことができます。  
  
 JSON ファイルが SQL Server がアクセスできる ローカル ファイル、共有ネットワーク ドライブ、Azure File Storage の場所に格納されている場合は、一括インポートを使用して SQL Server に JSON データを読み込むことができます。 このシナリオの詳細については、「[OPENROWSET (BULK) を使用して SQL Server に JSON ファイルをインポートする](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2015/10/07/importing-json-files-into-sql-server-using-openrowset-bulk.aspx)」を参照してください。  
  
 行区切りの JSON ファイルが Azure Blob Storage または Hadoop ファイル システムに格納されている場合、Polybase を使用して JSON テキストを読み込み、Transact-SQL コードでそれを解析してテーブルに読み込むことができます。  
  
## 組み込みの JSON サポートを試用する  
 **AdventureWorks サンプル データベースを使用して、組み込みの JSON サポートを試用できます。** AdventureWorks サンプル データベースを入手するには、[こちら](https://www.microsoft.com/en-us/download/details.aspx?id=49502)から最小限のデータベース ファイルとサンプルおよびスクリプト ファイルをダウンロードしてください。 SQL Server 2016 のインスタンスにサンプル データベースを復元したら、サンプル ファイルを解凍し、JSON フォルダーから "JSON Sample Queries procedures views and indexes.sql" ファイルを開きます。 このファイルのスクリプトを実行して JSON データとして既存のデータの一部の形式を再度設定し、JSON データに対してサンプル クエリとレポートを実行してから、JSON データにインデックスを付けて JSON をインポートおよびエクスポートします。  
  
 ファイルに含まれているスクリプトでは、次のことを実行できます。  
  
1.  既存のスキーマを非正規化して JSON データの列を作成する。  
  
    1.  SalesReasons、SalesOrderDetails、SalesPerson、Customer、およびその他の販売注文に関する情報を含むテーブルからの情報を、SalesOrder_json テーブルの JSON 列に格納します。  
  
    2.  EmailAddresses/PersonPhone テーブルからの情報を、Person_json に JSON オブジェクトの配列として格納します。  
  
2.  JSON データに対してクエリを実行するプロシージャとビューを作成する。  
  
3.  JSON データにインデックスを追加する - JSON のプロパティとフルテキスト インデックスにインデックスを作成します。  
  
4.  JSON をインポートおよびエクスポートする - Person テーブルと SalesOrder テーブルのコンテンツを JSON の結果としてエクスポートする、および JSON 入力をインポートして Person テーブルと SalesOrder テーブルを更新するプロシージャを作成して実行します。  
  
5.  サンプル クエリを実行する – 手順 2 と 4 で作成したストアド プロシージャとビューを呼び出すいくつかのクエリを実行します。  
  
6.  スクリプトをクリーンアップする - 手順 2 と 4 で作成したストアド プロシージャとビューを保持する場合は、この部分を実行しないでください。  
  
## 組み込みの JSON サポートの詳細情報  
  
### このセクションのトピック  
 [FOR JSON を使用してクエリ結果を JSON として書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
 FOR JSON 句を使用して、JSON 出力の形式設定をクライアント アプリケーションから SQL Server に委任します。  
  
 [OPENJSON を使用して JSON データを行と列に変換する &#40;SQL Server&#41;](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md)  
 OPENJSON を使用して、JSON データを SQL Server にインポートする、または現状 JSON を直接処理できないアプリケーションやサービス (SQL Server Integration Services など) 用に、JSON データをリレーショナル形式に変換します。  
  
 [組み込み関数を使用した JSON データの検証、クエリ、変更 &#40;SQL Server&#41;](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md)  
 これらの組み込み関数を使用して JSON テキストを検証し、スカラー値、オブジェクト、配列を抽出します。  
  
 [JSON パス式 &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)  
 パス式を使用して、使用する JSON テキストを指定します。  
  
 [JSON データへのインデックスの追加](../../relational-databases/json/index-json-data.md)  
 計算列を使用して、JSON ドキュメントのプロパティに対して照合順序に対応したインデックスを作成します。  
  
 [SQL Server での JSON に関してよく寄せられる質問](../Topic/Frequently%20Asked%20Questions%20about%20JSON%20in%20SQL%20Server.md)  
 SQL Server での組み込み JSON サポートに関する一般的な質問に対する回答を見つけることができます。  
  
### マイクロソフトのブログ記事  
  
-   [マイクロソフトのプログラム マネージャー Jovan Popovic によるブログ記事](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
### 参照トピック  
  
-   [FOR 句 &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md) (FOR JSON)  
  
-   [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
-   [JSON 関数 &#40;Transact-SQL&#41;](../../t-sql/functions/json-functions-transact-sql.md)  
  
    -   [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)  
  
    -   [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)  
  
    -   [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)  
  
    -   [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)  
  
  