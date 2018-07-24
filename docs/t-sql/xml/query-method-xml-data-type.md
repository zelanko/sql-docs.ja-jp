---
title: query() メソッド (xml データ型) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- query method
- query() method
ms.assetid: f48f6f7b-219f-463a-bf36-bc10f21afaeb
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dedb594cbded10d17e93f1ed52dddf858b2fa67f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38051770"
---
# <a name="query-method-xml-data-type"></a>query() メソッド (xml データ型)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **xml** データ型のインスタンスに対する XQuery を指定します。 結果は、**xml** 型の値になります。 このメソッドでは、型指定されていない XML のインスタンスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
query ('XQuery')  
```  
  
## <a name="arguments"></a>引数  
 XQuery  
 XML インスタンス内の XML ノード (要素や属性など) をクエリする XQuery 式の文字列です。  
  
## <a name="examples"></a>使用例  
 このセクションでは、**xml** データ型の query() メソッドの使用例について説明します。  
  
### <a name="a-using-the-query-method-against-an-xml-type-variable"></a>A. xml 型変数に対する query() メソッドの使用  
 次の例では、**xml** 型の変数 **@myDoc** を宣言し、XML インスタンスをこれに代入します。 その後 **query()** メソッドを使用して、ドキュメントに対して XQuery を指定します。  
  
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
 次の例では、**query()** メソッドを使用して、**AdventureWorks** データベースの **xml** 型の列 **CatalogDescription** に対して XQuery を指定します。  
  
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
  
-   CatalogDescription 列は型指定された **xml** 列です。 つまり、これには関連付けられたスキーマ コレクションがあります。 [XQuery プロローグ](../../xquery/modules-and-prologs-xquery-prolog.md)では、**namespace** キーワードを使って、後でクエリ本文で使用するプレフィックスを定義しています。  
  
-   **query()** メソッドは XML を構築します。<`Product`> 要素には **ProductModelID** 属性が指定されます。また、**ProductModelID** 属性値はデータベースから取得されます。 XML 構築の詳細については、「[XML 構築 &#40;XQuery&#41;](../../xquery/xml-construction-xquery.md)」を参照してください。  
  
-   WHERE 句の [exist() メソッド (XML データ型)](../../t-sql/xml/exist-method-xml-data-type.md) は、XML 内で <`Warranty`> 要素を含む行だけを検索することに使用されています。 **namespace** キーワードを使用して名前空間プレフィックスが定義されています。  
  
 結果の一部を次に示します。  
  
```  
<Product ProductModelID="19"/>   
<Product ProductModelID="23"/>   
...  
```  
  
 query() メソッドと exist() メソッドはどちらも PD プレフィックスを宣言していることに注意してください。 このような場合は、WITH XMLNAMESPACES を最初に使用して、プレフィックス定義し、これをクエリで使用することもできます。  
  
```  
WITH XMLNAMESPACES 
(  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS WM
)  
SELECT CatalogDescription.query('<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />')
       AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('/PD:ProductDescription/PD:Features/WM:Warranty ') = 1;

```  
  
## <a name="see-also"></a>参照  
 [WITH XMLNAMESPACES を使用したクエリへの名前空間の追加](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [型指定された XML と型指定されていない XML の比較](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML データのインスタンスの作成](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml データ型メソッド](../../t-sql/xml/xml-data-type-methods.md)   
 [XML データ変更言語 &#40;XML DML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
