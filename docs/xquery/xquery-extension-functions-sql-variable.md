---
title: 関数 (XQuery) |マイクロソフトドキュメント
description: XQuery 拡張関数 sql:variable() を使用して、XQuery 式内の SQL リレーショナル値を含む変数を公開する方法について説明します。
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sql:variable() function
- sql:variable function
ms.assetid: 6e2e5063-c1cf-4b5a-b642-234921e3f4f7
author: rothja
ms.author: jroth
ms.openlocfilehash: 8241e15643eb4aa25912451ddfed94699954797f
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388606"
---
# <a name="xquery-extension-functions---sqlvariable"></a>XQuery Extension Functions - sql:variable()
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  SQL リレーショナル値を含む変数を XQuery 式内部に公開します。  
  
## <a name="syntax"></a>構文  
  
```  
  
sql:variable("variableName") as xdt:anyAtomicType?  
```  
  
## <a name="remarks"></a>解説  
 トピック[「XML 内のリレーショナル データのバインド](../t-sql/xml/binding-relational-data-inside-xml-data.md)」で説明されているように[、Xml データ型のメソッド](../t-sql/xml/xml-data-type-methods.md)を使用して XQuery 内のリレーショナル値を公開するときに、この関数を使用できます。  
  
 たとえば[、query() メソッド](../t-sql/xml/query-method-xml-data-type.md)を使用して **、xml**データ型の変数または列に格納されている XML インスタンスに対するクエリを指定します。 また、場合によっては、リレーショナル データと XML データを一緒にするために、[!INCLUDE[tsql](../includes/tsql-md.md)] 変数の値 (パラメーター) をクエリで使用することもできます。 これを行うには **、sql:変数**関数を使用します。  
  
 SQL 値は対応する XQuery 値にマップされ、その型は対応する SQL 型と同等の XQuery 基本型になります。  
  
 **XML-DML**挿入ステートメントのソース式のコンテキストでのみ、xml インスタンスを参照できます。それ以外の場合は **、xml**型または共通言語ランタイム (CLR) のユーザー定義型の値を参照できません。  
  
## <a name="examples"></a>例  
  
### <a name="a-using-the-sqlvariable-function-to-bring-a-transact-sql-variable-value-into-xml"></a>A. SQL:変数() 関数を使用して、XML に Transact-SQL 変数値を取り込む  
 次の例では、次の要素から構成される XML インスタンスを作成します。  
  
-   XML 以外の列の値 (`ProductID`)。 [sql:column() 関数](../xquery/xquery-extension-functions-sql-column.md)は、XML でこの値をバインドするために使用されます。  
  
-   他のテーブルの XML 以外の列の値 (`ListPrice`)。 この場合`sql:column()`も、この値を XML にバインドするために使用されます。  
  
-   [!INCLUDE[tsql](../includes/tsql-md.md)] 変数の値 (`DiscountPrice`)。 この`sql:variable()`メソッドは、この値を XML にバインドするために使用されます。  
  
-   クエリをより興味深`ProductModelName`いものにするために **、xml**型の列の値 ( ) を返します。  
  
 クエリは次のとおりです。  
  
```sql
DECLARE @price money  
  
SET @price=2500.00  
SELECT ProductID, Production.ProductModel.ProductModelID,CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  
       <Product   
           ProductID="{ sql:column("Production.Product.ProductID") }"  
           ProductModelID= "{ sql:column("Production.Product.ProductModelID") }"  
           ProductModelName="{/pd:ProductDescription[1]/@ProductModelName }"  
           ListPrice="{ sql:column("Production.Product.ListPrice") }"  
           DiscountPrice="{ sql:variable("@price") }"  
        />')   
FROM Production.Product   
JOIN Production.ProductModel  
ON Production.Product.ProductModelID = Production.ProductModel.ProductModelID  
WHERE ProductID=771  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   メソッド内の XQuery は`query()`XML を構築します。  
  
-   キーワード`namespace`は[、XQuery Prolog](../xquery/modules-and-prologs-xquery-prolog.md)で名前空間プレフィックスを定義するために使用されます。 これは、`ProductModelName`属性値が`CatalogDescription xml`、スキーマが関連付けられている型列から取得されるためです。  
  
 結果を次に示します。  
  
```xml
<Product ProductID="771" ProductModelID="19"   
         ProductModelName="Mountain 100"   
         ListPrice="3399.99" DiscountPrice="2500" />  
```  
  
## <a name="see-also"></a>参照  
 [XQuery 拡張関数](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)   
 [型指定された XML と型指定されていない XML を比較する](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML データ &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XML データのインスタンスの作成](../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml データ型メソッド](../t-sql/xml/xml-data-type-methods.md)   
 [XML データ変更言語 &#40;XML DML&#41;](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
