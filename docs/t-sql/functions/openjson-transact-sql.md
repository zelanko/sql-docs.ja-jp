---
title: "OPENJSON (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENJSON
- OPENJSON_TSQL
helpviewer_keywords:
- OPENJSON rowset function
- JSON, importing
- JSON, converting from
ms.assetid: 233d0877-046b-4dcc-b5da-adeb22f78531
caps.latest.revision: "32"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: fe464bedc22fa5ebc47fc7f783e75b994d0cff49
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="openjson-transact-sql"></a>OPENJSON (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

**OPENJSON** JSON テキストを解析して行および列として JSON 入力からのオブジェクトおよびプロパティを返すテーブル値関数です。 つまり、 **OPENJSON** JSON ドキュメントに対する行セット ビューを提供します。 行セットと列の作成に使用する JSON プロパティのパスで列を明示的に指定することができます。 **OPENJSON**使用できる行のセットを返します、 **OPENJSON**で、`FROM`の句、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントと同じように、その他のテーブル、ビュー、またはテーブル値関数を使用することができます。  
  
使用して**OPENJSON** JSON データをインポートする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、JSON データをアプリケーションのリレーショナル形式に変換またはをサービスを提供することはできません使用する JSON 直接またはします。  
  
> [!NOTE]  
>  **OPENJSON**関数は、以降の互換性レベル 130 でのみ利用できます。 データベースの互換性レベルが 130 よりも低い場合、SQL Server は **OPENJSON** 関数を見つけて実行することができません。 他の JSON 関数は、すべての互換性レベルで使用できます。
> 
> `sys.databases` ビューまたはデータベース プロパティで互換性レベルを確認できます。 次のコマンドを使用してデータベースの互換性レベルを変更することができます。  
> 
> `ALTER DATABASE DatabaseName SET COMPATIBILITY_LEVEL = 130`
>   
> 互換性レベル 120 には、新しい Azure SQL データベースであっても既定可能性があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン")[TRANSACT-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
OPENJSON( jsonExpression [ , path ] )  [ <with_clause> ]

<with_clause> ::= WITH ( { colName type [ column_path ] [ AS JSON ] } [ ,...n ] )
```  

**OPENJSON**テーブル値関数を解析し、 *jsonExpression*最初の引数として提供されており、式内の JSON オブジェクトからデータを含む 1 つまたは複数の行を返します。 *jsonExpression*入れ子になったサブオブジェクトを含めることができます。 内から下位のオブジェクトを解析する場合は、 *jsonExpression*を指定することができます、**パス**JSON サブオブジェクトのパラメーターです。

### <a name="openjson"></a>openjson

![OPENJSON tvf 構文](../../relational-databases/json/media/openjson-syntax.png "OPENJSON 構文")  

既定では、 **OPENJSON**テーブル値関数は、キー名、値が含まれている 3 つの列を返し、{キー: 値} の各ペアの型がで見つかった*jsonExpression*です。 代わりに、明示的に指定できます、結果のスキーマを設定する**OPENJSON**により返します*with_clause*です。
  
### <a name="withclause"></a>with_clause
  
![OPENJSON TVF の句での構文](../../relational-databases/json/media/openjson-shema-syntax.png "WITH OPENJSON 構文")

*with_clause*それらの種類を持つ列の一覧を含む**OPENJSON**を返します。 既定では、 **OPENJSON**内のキーと一致する*jsonExpression*で列名を持つ*with_clause* (この場合、一致するキーはことを意味、大文字小文字を区別)。 列名でキー名が一致しない場合は、使用できる、省略可能な*column_path*、これは、 [JSON パス式](../../relational-databases/json/json-path-expressions-sql-server.md)内のキーを参照する、 *jsonExpression*です。 

## <a name="arguments"></a>引数  
### <a name="jsonexpression"></a>*jsonExpression*  
JSON テキストを含む Unicode 文字式です。  
  
OPENJSON では、配列の要素または JSON 式内のオブジェクトのプロパティを反復処理し、要素またはプロパティごとに 1 つの行を返します。 次の例として提供されたオブジェクトの各プロパティを返します*jsonExpression*:  
  
```sql  
DECLARE @json NVARCHAR(4000) = N'{  
   "StringValue":"John",  
   "IntValue":45,  
   "TrueValue":true,  
   "FalseValue":false,  
   "NullValue":null,  
   "ArrayValue":["a","r","r","a","y"],  
   "ObjectValue":{"obj":"ect"}  
}'

SELECT *
FROM OPENJSON(@json)
```  
  
**[結果]**  
  
|キー (key)|value|型|  
|---------|-----------|----------|  
|文字列値|John|1|  
|IntValue|45|2|  
|trueValue|true|3|  
|falseValue|オプション|3|  
|nullValue|NULL|0|  
|ArrayValue|["a"、"r"、"r"、"「,」y"]|4|  
|ObjectValue|{"obj":"ect"}|5|  

### <a name="path"></a>*パス*  
オブジェクトまたは配列内で参照される省略可能な JSON パス式は、 *jsonExpression*です。 **OPENJSON**シークを指定した位置にある JSON テキストに、参照先のフラグメントのみを解析します。 詳細については、次を参照してください。 [JSON パス式 &#40;です。SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md).

[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]し、 [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)]、変数の値として使用できる*パス*です。
  
次の例では、入れ子になったオブジェクトを返しますを指定して、*パス*:  

```sql  
DECLARE @json NVARCHAR(4000) = N'{  
      "path": {  
            "to":{  
                 "sub-object":["en-GB", "en-UK","de-AT","es-AR","sr-Cyrl"]  
                 }  
              }  
 }';

SELECT [key], value
FROM OPENJSON(@json,'$.path.to."sub-object"')
```  
  
 **[結果]**  
  
|[キー]|値|  
|---------|-----------|  
|0|en-GB|  
|1|en 英国|  
|2|de AT|  
|3|es AR|  
|4|sr という|  
 
ときに**OPENJSON**解析関数を JSON 配列要素のインデックスの JSON テキストとして返しますキー。

JSON 式のプロパティを持つパス ステップの照合に使用する比較では、大文字と小文字および照合順序に対応していない (つまり、BIN2 の比較)。 

### <a name="withclause"></a>*with_clause*
出力スキーマを明示的に定義、 **OPENJSON**関数を返します。 省略可能な*with_clause*次の要素を含めることができます。

*colName*出力列の名前を指定します。  
  
既定では、 **OPENJSON** JSON テキストのプロパティと一致する列の名前を使用します。 たとえば、列を指定する*名前*スキーマでは、OPENJSON は JSON テキストに"name"プロパティを使用してこの列を作成しようとします。 使用して、この既定のマッピングをオーバーライドすることができます、 *column_path*引数。  
  
*型*  
出力列のデータ型です。  

> [!NOTE]
> 使用する場合は、 **AS JSON**オプション、列*型*する必要があります`NVARCHAR(MAX)`です。
  
*column_path*  
指定された列で返されるプロパティを指定する JSON のパスです。 詳細については、の説明を参照して、*パス*このトピックの前のパラメーターです。  
  
使用して*column_path*出力列の名前は、プロパティの名前と一致しない場合、既定のマッピング ルールを上書きします。  
  
JSON の式のプロパティを持つパスの手順を照合に使用する比較では、大文字と小文字および照合順序に関係なく (つまり、BIN2 の比較)。  
  
パスの詳細については、次を参照してください。 [JSON パス式 &#40;です。SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
*JSON として*  
使用して、 **AS JSON**列定義のオプションは、参照されたプロパティには、内部の JSON オブジェクトまたは配列が含まれているを指定します。 指定した場合、 **AS JSON**オプション、列の型は nvarchar (max) である必要があります。

-   指定しない場合は**AS JSON**列、関数は、スカラー値を返す (たとえば、int、文字列、true、false)、指定された JSON プロパティから指定したパスにします。 オブジェクトまたは配列では、パスを表し、プロパティが指定したパスに見つかりません場合は、関数は lax モードでは null を返します。 または、厳格モードではエラーを返します。 この動作の動作と同様に、 **JSON_VALUE**関数。  
  
-   指定した場合**AS JSON**列の場合、関数を返しますは JSON フラグメント指定の JSON プロパティから指定したパスにします。 パスは、スカラー値を表し、プロパティが指定したパスに見つかりません場合、関数は lax モードでは null を返します。 または、厳格モードではエラーを返します。 この動作の動作と同様に、 **JSON_QUERY**関数。  
  
> [!NOTE]  
> JSON プロパティから入れ子になった JSON フラグメントを返す場合は、提供する必要がある、 **AS JSON**フラグ。 このオプションを使用せず OPENJSON には、参照先の JSON オブジェクトまたは配列の代わりに NULL 値が返されます。 プロパティが見つからない場合または strict モードで実行時エラーが返されます。  
  
たとえば、次のクエリを返し、配列の要素を書式設定。  
  
```sql  
DECLARE @json NVARCHAR(MAX) = N'[  
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
   
SELECT *
FROM OPENJSON ( @json )  
WITH (   
              Number   varchar(200)   '$.Order.Number',  
              Date     datetime       '$.Order.Date',  
              Customer varchar(200)   '$.AccountNumber',  
              Quantity int            '$.Item.Quantity',  
              [Order]  nvarchar(MAX)  AS JSON  
 )
```  
  
**[結果]**  
  
|数値|日付|Customer|Quantity|書|  
|------------|----------|--------------|--------------|-----------|  
|SO43659|2011-05-により、|AW29825|1|{"Number":"SO43659"、「日付」:"2011-05-により、"}|  
|として SO43661|2011-06-01T00:00:00|AW73565|3|{"Number":"として SO43661"、「日付」:"2011-06-01T00:00:00"}|  
  

## <a name="return-value"></a>戻り値  
OPENJSON 関数によって返される列は、WITH オプションによって異なります。  
  
1. -既定のスキーマで OPENJSON を呼び出すときに、- WITH 句で明示的なスキーマを指定しない場合、関数のテーブルを返します、次の列。  
    1.  **キー**です。 指定した配列内の要素のインデックスまたは指定したプロパティの名前を含む、nvarchar (4000) 値です。 キーの列では、BIN2 照合順序を持っています。  
    2.  **値**。 プロパティの値を含む、nvarchar (max) 値です。 [値] 列の照合順序を継承する*jsonExpression*です。
    3.  **型**です。 値の型を含む整数値。 **型**既定のスキーマで OPENJSON を使用する場合にのみ列が返されます。 型の列は、次の値のいずれか。  
  
        |型の列の値|JSON データ型|  
        |------------------------------|--------------------|  
        |0|null|  
        |1|string|  
        |2|int|  
        |3|true または false|  
        |4|array|  
        |5|オブジェクト (object)|  
  
     最初のレベル プロパティのみが返されます。 JSON のテキストが正しくフォーマットされていない場合、ステートメントが失敗します。  

2. OPENJSON を呼び出す、WITH 句で明示的なスキーマを指定すると、関数は、WITH 句で定義されているスキーマを持つテーブルを返します。  

## <a name="remarks"></a>解説  

*json_path*の 2 番目の引数で使用される**OPENJSON**または*with_clause*からでも開始できます、 **lax**または**strict**キーワードです。

-   **Lax**モード、 **OPENJSON**オブジェクトまたは指定したパスの値が見つからない場合、エラーが発生しません。 パスが見つからない場合**OPENJSON**空の結果セットまたは NULL 値を返します。
-   **Strict**、モード**OPENJSON**パスが見つからない場合はエラーを返します。

このページの例のいくつかは、path モード、lax または strict を明示的に指定します。 Path モードではオプションです。 厳密でないモードは、明示的に path モードを指定しない場合は、既定になります。 Path モードとパス式についての詳細については、次を参照してください。 [JSON パス式 &#40;です。SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md).    

列名が*with_clause* JSON テキスト内のキーと照合されます。 列名を指定する場合`[Address.Country]`、キーと対応している`Address.Country`です。 入れ子になったキーを参照する場合は、`Country`オブジェクト内で`Address`、パスを指定する必要が`$.Address.Country`列のパスにします。

*json_path*文字の英数字を使用してキーを含めることがあります。 キー名をエスケープ*json_path*キーに特殊文字がある場合、二重引用符を含むです。 たとえば、`$."my key $1".regularKey."key with . dot"`と一致する値の 1 次の JSON テキストに。

```json
{
  "my key $1": {
    "regularKey":{
      "key with . dot": 1
    }
  }
}
```  

## <a name="examples"></a>使用例  
  
### <a name="example-1---convert-a-json-array-to-a-temporary-table"></a>例 1: 一時テーブルを JSON 配列に変換します。  
次の例では、数値の JSON 配列として識別子の一覧を提供します。 クエリでは、識別子のテーブルを JSON 配列に変換し、指定の id を持つすべての製品をフィルターします。  
  
```sql  
DECLARE @pSearchOptions NVARCHAR(4000) = N'[1,2,3,4]'

SELECT *
FROM products
INNER JOIN OPENJSON(@pSearchOptions) AS productTypes
 ON product.productTypeID = productTypes.value
```  
  
このクエリは、次の例と同じです。 ただし、次の例では、数値をパラメーターとして渡すことではなく、クエリに埋め込む必要があります。  
  
```sql  
SELECT *
FROM products
WHERE product.productTypeID IN (1,2,3,4)
```  
  
### <a name="example-2---merge-properties-from-two-json-objects"></a>例 2: 2 つの JSON オブジェクトからのマージ プロパティ  
次の例では、2 つの JSON オブジェクトのすべてのプロパティの和集合を選択します。 2 つのオブジェクトがある重複*名前*プロパティです。 例では、キーの値を使用して、重複する行を結果から除外します。  
  
```sql  
DECLARE @json1 NVARCHAR(MAX),@json2 NVARCHAR(MAX)

SET @json1=N'{"name": "John", "surname":"Doe"}'

SET @json2=N'{"name": "John", "age":45}'

SELECT *
FROM OPENJSON(@json1)
UNION ALL
SELECT *
FROM OPENJSON(@json2)
WHERE [key] NOT IN (SELECT [key] FROM OPENJSON(@json1))
```  
  
### <a name="example-3---join-rows-with-json-data-stored-in-table-cells-using-cross-apply"></a>例 3 - CROSS APPLY を使用してテーブルのセルに格納されている JSON データを含む結合行  
次の例で、`SalesOrderHeader`テーブルには、`SalesReason`の配列を含むテキスト列`SalesOrderReasons`JSON 形式でします。 `SalesOrderReasons`オブジェクトと同様にプロパティが含ま*品質*と*製造元*です。 例では、販売注文のすべての行を関連する販売理由に結合するレポートを作成します。 OPENJSON 演算子は、理由は、1 つの子テーブルに格納されていたかのように、販売理由の JSON 配列を展開します。 そして、CROSS APPLY 演算子は、OPENJSON テーブル値関数によって返される行に各販売注文の行を結合します。  
  
```sql  
SELECT SalesOrderID,OrderDate,value AS Reason
FROM Sales.SalesOrderHeader
CROSS APPLY OPENJSON(SalesReasons)
```  
  
> [!TIP] 
> 通常使用順に展開するときに、JSON 配列が個々 のフィールドに格納されているし、その親の行に結合して、 [!INCLUDE[tsql](../../includes/tsql-md.md)] CROSS APPLY 演算子。 詳細については、CROSS APPLY を参照してください。 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md).  
  
使用して、同じクエリを書き直すことができます`OPENJSON`で明示的に定義されたスキーマを返す行の。  
  
```sql  
SELECT SalesOrderID, OrderDate, value AS Reason  
FROM Sales.SalesOrderHeader  
     CROSS APPLY OPENJSON (SalesReasons) WITH (value nvarchar(100) '$')
```  
  
この例では、`$`パスは、配列内の各要素を参照します。 返される値を明示的にキャストする場合は、この種類のクエリを使用することができます。  
  
### <a name="example-4---combine-relational-rows-and-json-elements-with-cross-apply"></a>例 4 - CROSS APPLY とリレーショナル行と JSON 要素を結合します。  
次のクエリは、次の表に示すように結果をリレーショナル行と JSON 要素を結合します。  
  
```sql  
SELECT store.title, location.street, location.lat, location.long  
FROM store  
CROSS APPLY OPENJSON(store.jsonCol, 'lax $.location')   
     WITH (street varchar(500) ,  postcode  varchar(500) '$.postcode' ,  
     lon int '$.geo.longitude', lat int '$.geo.latitude')  
     AS location
```  
  
**[結果]**  
  
|title|street|郵便番号|lon|lat|  
|-----------|------------|--------------|---------|---------|  
|全体の食品市場|17991 Redmond の方法|WA 98052|47.666124|-122.10155|  
|Sears|148th Ave NE|WA 98052|47.63024|-122.141246,17|  
  
### <a name="example-5---import-json-data-into-sql-server"></a>例 5 - インポートを SQL Server に JSON データ  
次の例では、全体の JSON オブジェクトを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルです。  
  
```sql  
DECLARE @json NVARCHAR(max)  = N'{  
  "id" : 2,  
  "firstName": "John",  
  "lastName": "Smith",  
  "isAlive": true,  
  "age": 25,  
  "dateOfBirth": "2015-03-25T12:00:00",  
  "spouse": null  
  }';  
   
  INSERT INTO Person  
  SELECT *   
  FROM OPENJSON(@json)  
  WITH (id int,  
        firstName nvarchar(50), lastName nvarchar(50),   
        isAlive bit, age int,  
        dateOfBirth datetime2, spouse nvarchar(50)
```  
  
## <a name="see-also"></a>参照  
 [JSON パス式 &#40;です。SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [行と OPENJSON &#40; を持つ列に JSON データを変換します。SQL Server &#41;](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md)   
 [既定のスキーマ &#40; を OPENJSON を使用します。SQL Server &#41;](../../relational-databases/json/use-openjson-with-the-default-schema-sql-server.md)   
 [OPENJSON、明示的なスキーマ &#40; を使用します。SQL Server &#41;](../../relational-databases/json/use-openjson-with-an-explicit-schema-sql-server.md)  
  
  
