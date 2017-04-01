---
title: "OPENJSON を使用して JSON データを行と列に変換する (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/31/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OPENJSON"
  - "JSON, インポート"
  - "JSON のインポート"
ms.assetid: 0c139901-01e2-49ef-9d62-57e08e32c68e
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# OPENJSON を使用して JSON データを行と列に変換する (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  **OPENJSON** 行セット関数を利用すると、JSON テキストを行と列のセットに変換できます。 **OPENJSON** を利用し、JSON コレクションに SQL クエリを実行したり、JSON テキストを SQL Server テーブルにインポートしたりできます。  
  
> [!NOTE] **OPENJSON** 関数は、**互換性レベル 130** でのみ使用できます。 データベースの互換性レベルが 130 よりも低い場合、SQL Server は **OPENJSON** 関数を見つけて実行することができません。 他の JSON 関数は、すべての互換性レベルで使用できます。 sys.databases ビューまたはデータベース プロパティで互換性レベルを確認できます。
> 
>   次のコマンドを利用し、データベースの互換性レベルを変更できます。   
>   ALTER DATABASE DatabaseName SET COMPATIBILITY_LEVEL = 130  
  
 **OPENJSON** 関数は、1 つまたは集合の JSON オブジェクトを受け取り、1 つまたは複数の行に変換します。 既定では、**OPENJSON** 関数は JSON オブジェクトの最初のレベルで見つかるキーと値の組み合わせをすべて返すか、JSON 配列のすべての要素とその索引を返します。  
  
 WITH 句を利用すれば、**OPENJSON** 関数で返される行のスキーマを指定できます。 この明示的スキーマにより出力の構造が定義されます。  
  
## 結果スキーマなしで OPENJSON を使用する

これは、既定のスキーマを使って **OPENJSON**  を使用した簡単な例です。この例では JSON オブジェクトのプロパティごとに 1 つの行が返されています。  
 
返される結果のスキーマを指定せずに **OPENJSON** 関数を使用すると (OPENJSON の後に WITH 句を指定しないなど)、3 つの列を持つテーブルが返されます。入力オブジェクトのプロパティの名前 (または、入力配列の要素の索引)、プロパティまたは配列要素の値、型 (文字列、数値、ブール値、配列、オブジェクトなど) です。 JSON オブジェクトのプロパティ (または、配列の要素) は個別行で返されます。  

-   詳細と例については、「[既定のスキーマを使用する OPENJSON の使用 &#40;SQL Server&#41;](../../relational-databases/json/use-openjson-with-the-default-schema-sql-server.md)」を参照してください。
-   構文と使用法については、「[OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)」を参照してください。 

```tsql  
SET @json = '{"name":"John","surname":"Doe","age":45,"skills":["SQL","C#","MVC"]}';  
  
SELECT *  
FROM OPENJSON(@json);  
```  
  
**[結果]**  
  
|キー (key)|value|型|  
|---------|-----------|----------|  
|name|John|1|  
|姓|Doe|1|  
|有効期間|45|2|  
|スキル|["SQL","C#","MVC"]|4|
    
## 明示的なスキーマで OPENJSON を使用する

スキーマを明示的に指定して **OPENJSON** を使用する簡単な例は次のようになります。  
  
**OPENJSON** 関数の WITH 句に返される結果のスキーマを指定すると、WITH 句に定義した列を持つテーブルが返されます。 WITH 句では、設定された出力列、それぞれの型、各出力値の JSON ソース プロパティのパスを定義できます。 **OPENJSON** は JSON オブジェクトの配列を繰り返し処理し、列ごとに指定されたパスで値を読み取り、値を指定の型に変換します。  

-   詳細と例については、「[明示的なスキーマで OPENJSON を使用する &#40;SQL Server&#41;](../../relational-databases/json/use-openjson-with-an-explicit-schema-sql-server.md)」を参照してください。
-   構文と使用法については、「[OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)」を参照してください。
  
```tsql  
SET @json =   
 N'[  
      {  
        "Order": {  
          "Number":"SO43659",  
          "Date":"2011-05-31T00:00:00"  
        },  
        "AccountNumber":"AW29825",  
        "Item": {  
          "Price":2024.9940,  
          "Quantity":1  
        }  
      },  
      {  
        "Order": {  
          "Number":"SO43661",  
          "Date":"2011-06-01T00:00:00"  
        },  
        "AccountNumber":"AW73565",  
        "Item": {  
          "Price":2024.9940,  
          "Quantity":3  
        }  
     }  
]'  
  
SELECT * FROM  
OPENJSON ( @json )  
WITH (   
             Number   varchar(200) '$.Order.Number' ,  
             Date     datetime     '$.Order.Date',  
             Customer varchar(200) '$.AccountNumber',  
             Quantity int          '$.Item.Quantity'  
)  
```  
  
**[結果]**  
  
|数値|日付|Customer|Quantity|  
|------------|----------|--------------|--------------|  
|SO43659|2011-05-により、|AW29825|1|  
|として SO43661|2011-06-01T00:00:00|AW73565|3|  
  
 この関数は JSON 配列の要素を返し、書式設定します。  
  
-   JSON 配列の要素ごとに、**OPENJSON** によって出力テーブルに新しい行が生成されます。 JSON 配列の 2 つの要素が、返されるテーブルで、2 つの行に変換されます。  
  
-   `colName type json_path` 構文の使用で指定された列ごとに、**OPENJSON** 関数は、指定したパスの配列要素で検出された値を変換し、それを指定の型に変換し、出力テーブルのセルに入力します。 この例では、Date 列の値がパス `$.Order.Date` の各オブジェクトから取得され、datetime 値に変換されます。  
  
行セットに JSON コレクションを変換したら、返されたデータで SQL クエリを実行したり、行セットをテーブルに挿入したりできます。  
  
## SQL Server での OPENJSON と組み込みの JSON サポートの詳細情報  
 [Microsoft のプログラム マネージャー Jovan Popovic によるブログ記事](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## 参照  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
  