---
title: "exist() メソッド (xml データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- exist() method
- exist method
ms.assetid: a55b75e0-0a17-4787-a525-9b095410f7af
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 74fc65730d0c46858c282b9625c86d1ab651ec49
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="exist-method-xml-data-type"></a>exist() メソッド (xml データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  返します、**ビット**を表す、次の条件のいずれか。  
  
-   1 (True)。クエリ内の XQuery 式により、空以外の結果が返されたことを示します。 つまり、少なくとも 1 つの XML ノードが返されます。  
  
-   0 (False)。クエリ内の XQuery 式により、空の結果が返されたことを示します。  
  
-   NULL の場合、 **xml**クエリの実行対象となるデータ型のインスタンスには、NULL が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
  
exist (XQuery)   
```  
  
## <a name="arguments"></a>引数  
 XQuery  
 文字列リテラルの XQuery 式です。  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]  
>  **Exist()**メソッドは、空でない結果を返す XQuery 式に対して 1 を返します。 指定する場合、 **true()**または**false()**の内部機能、 **exist()**メソッド、 **exist()**メソッドは 1、ため、関数**true()**と**false()**それぞれブール値 True および False を返します。 (つまり、空でない結果が返されます)。 したがって、 **exist()**は次の例で示すように 1 (True) を返します。  
  
```  
declare @x xml;  
set @x='';  
select @x.exist('true()');   
```  
  
## <a name="examples"></a>使用例  
 次の例を指定する方法を示して、 **exist()**メソッドです。  
  
### <a name="example-specifying-the-exist-method-against-an-xml-type-variable"></a>例 : xml 型の変数に対する exist() メソッドの指定  
 次の例では、@xは、 **xml**型の変数 (型指定されていない xml) と@fによって返される値を格納する整数型の変数は、 **exist()**メソッドです。 **Exist()**メソッドは、XML インスタンスに格納されている日付の値がある場合に True (1) を返します`2002-01-01`です。  
  
```  
declare @x xml;  
declare @f bit;  
set @x = '<root Somedate = "2002-01-01Z"/>';  
set @f = @x.exist('/root[(@Somedate cast as xs:date?) eq xs:date("2002-01-01Z")]');  
select @f;  
```  
  
 日付を比較する、 **exist()**メソッドを次に注意してください。  
  
-   コード`cast as xs:date?`に値をキャストするために使用**xs:date**比較の目的の型。  
  
-   値、  **@Somedate** 属性に型指定されていません。 この値を比較する場合は暗黙的にキャスト、比較の右側にある型に、 **xs:date**型です。  
  
-   代わりに**as xs:date() キャスト**、使用することができます、 **xs:date()**コンス トラクター関数。 詳細については、次を参照してください。[コンス トラクター関数 &#40;です。XQuery と #41 です。](../../xquery/constructor-functions-xquery.md).  
  
 次の例は似ていますが、1 つ前に、<`Somedate`> 要素。  
  
```  
DECLARE @x xml;  
DECLARE @f bit;  
SET @x = '<Somedate>2002-01-01Z</Somedate>';  
SET @f = @x.exist('/Somedate[(text()[1] cast as xs:date ?) = xs:date("2002-01-01Z") ]')  
SELECT @f;  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   **Text()**メソッドを型指定されていない値を含むテキスト ノードを返します`2002-01-01`です。 (XQuery 型が**xdt:untypedAtomic**)。この型指定された値を明示的にキャストする必要があります**x**に**xsd:date**暗黙のキャストがここではサポートされていないため、します。  
  
### <a name="example-specifying-the-exist-method-against-a-typed-xml-variable"></a>例 : 型指定された xml 型の変数に対する exist() メソッドの指定  
 次の例では、使用、 **exist()**メソッドに対して、 **xml**型の変数です。 この例で使用する変数は、スキーマ名前空間コレクション名 `ManuInstructionsSchemaCollection` を指定しているため、型指定された XML 変数です。  
  
 ドキュメントがこの変数に割り当てられた最初の製造手順の例でし、 **exist()**メソッドは、ドキュメントを含むかどうかを検索するため、<`Location`> 要素が**LocationID**属性値は 50 です。  
  
 **Exist()**に対して指定されたメソッド、@x変数は 1 を返します (True)、製造手順ドキュメントが含まれています、<`Location`> を持つ要素`LocationID=50`です。 それ以外の場合は 0 (False) を返します。  
  
```  
DECLARE @x xml (Production.ManuInstructionsSchemaCollection);  
SELECT @x=Instructions  
FROM Production.ProductModel  
WHERE ProductModelID=67;  
--SELECT @x  
DECLARE @f int;  
SET @f = @x.exist(' declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
    /AWMI:root/AWMI:Location[@LocationID=50]  
');  
SELECT @f;  
```  
  
### <a name="example-specifying-the-exist-method-against-an-xml-type-column"></a>例 : xml 型の列に対する exist() メソッドの指定  
 次のクエリは、製品モデル カタログの説明には、仕様を含めないでください Id を取得 <`Specifications`> 要素。  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
declare namespace pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
    declare namespace  pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     /pd:ProductDescription[not(pd:Specifications)]'  
    ) = 1;  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   WHERE 句の行だけを選択する、 **ProductDescription**に対して指定された条件を満たすテーブル、 **CatalogDescription xml**型の列です。  
  
-   **Exist()**いずれかの XML が含まれない場合、WHERE 句を 1 (True) を返すメソッド <`Specifications`> 要素。 使用に注意してください、 [not() 関数 (XQuery)](../../xquery/functions-on-boolean-values-not-function.md)です。  
  
-   [Sql:column() 関数 (XQuery)](../../xquery/xquery-extension-functions-sql-column.md)関数を使用して、XML 以外の列から値を取り込みます。  
  
-   このクエリでは、空の行セットが返されます。  
  
 クエリで指定**query()**と**exist()** xml データ型のメソッドとこれら両方の方法は、クエリ プロローグ内で同じ名前空間を宣言します。 この場合、WITH XMLNAMESPACES を使用してプレフィックスを宣言し、そのプレフィックスをこのクエリに使用できます。  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
     /pd:ProductDescription[not(pd:Specifications)]'  
    ) = 1;  
```  
  
## <a name="see-also"></a>参照  
 [WITH XMLNAMESPACES を使用したクエリへの名前空間の追加](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [型指定された XML と型指定されていない XML の比較](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML データのインスタンスの作成](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml データ型メソッド](../../t-sql/xml/xml-data-type-methods.md)   
 [XML データ変更言語 &#40;です。XML DML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
