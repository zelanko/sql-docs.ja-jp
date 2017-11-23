---
title: "query() メソッド (xml データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- query method
- query() method
ms.assetid: f48f6f7b-219f-463a-bf36-bc10f21afaeb
caps.latest.revision: "28"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 22770e7338ef7a3dff5a4f4486d0543cdf75d76c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="query-method-xml-data-type"></a>query() メソッド (xml データ型)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンスに対して XQuery を指定、 **xml**データ型。 結果は**xml**型です。 このメソッドでは、型指定されていない XML のインスタンスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
query ('XQuery')  
```  
  
## <a name="arguments"></a>引数  
 XQuery  
 XML インスタンス内の XML ノード (要素や属性など) をクエリする XQuery 式の文字列です。  
  
## <a name="examples"></a>使用例  
 このセクションで説明の query() メソッドの使用例、 **xml**データ型。  
  
### <a name="a-using-the-query-method-against-an-xml-type-variable"></a>A. xml 型変数に対する query() メソッドの使用  
 次の例は、変数を宣言 **@myDoc** の**xml**を入力し、XML インスタンスを代入します。 **Query()**ドキュメントに対して XQuery を指定するメソッドを使用しています。  
  
 次のクエリは、<`ProductDescription`> 要素の <`Features`> 子要素を取得します。  
  
```  
declare @myDoc xml  
set @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>'  
SELECT @myDoc.query('/Root/ProductDescription/Features')  
```  
  
 結果を次に示します。  
  
```  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>        
```  
  
### <a name="b-using-the-query-method-against-an-xml-type-column"></a>B. xml 型列に対する query() メソッドの使用  
 次の例で、 **query()**に対して XQuery を指定するメソッドが使用される、 **CatalogDescription**の列**xml**に入力、 **AdventureWorks**データベース。  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />  
') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   CatalogDescription 列は、型指定された**xml**列です。 つまり、これには関連付けられたスキーマ コレクションがあります。 [XQuery プロローグ](../../xquery/modules-and-prologs-xquery-prolog.md)、**名前空間**キーワードの使用をクエリ本文で後で使用されるプレフィックスを定義します。  
  
-   **Query()**メソッドは XML を構築、<`Product`> を持つ要素を**ProductModelID**されるは、属性、 **ProductModelID**属性の値データベースから取得します。 XML の構築の詳細については、次を参照してください。 [XML の構築と #40 です。XQuery と #41 です。](../../xquery/xml-construction-xquery.md).  
  
-   [Exist() メソッド (XML データ型)](../../t-sql/xml/exist-method-xml-data-type.md)を含む行のみを検索する WHERE 句を使用することで、<`Warranty`> XML 内の要素。 もう一度、**名前空間**キーワードの使用を 2 つの名前空間プレフィックスを定義します。  
  
 結果の一部を次に示します。  
  
```  
<Product ProductModelID="19"/>   
<Product ProductModelID="23"/>   
...  
```  
  
 query() メソッドと exist() メソッドはどちらも PD プレフィックスを宣言していることに注意してください。 このような場合は、WITH XMLNAMESPACES を最初に使用して、プレフィックス定義し、これをクエリで使用することもできます。  
  
```  
WITH XMLNAMESPACES (  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
SELECT CatalogDescription.query('  
<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />  
') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
## <a name="see-also"></a>参照  
 [WITH XMLNAMESPACES を使用したクエリへの名前空間の追加](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [型指定された XML と型指定されていない XML の比較](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML データのインスタンスの作成](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml データ型メソッド](../../t-sql/xml/xml-data-type-methods.md)   
 [XML データ変更言語 &#40;です。XML DML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
