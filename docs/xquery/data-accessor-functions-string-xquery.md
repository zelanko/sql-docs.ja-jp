---
title: string 関数 (XQuery) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.service: ''
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- string function
- fn:string function
ms.assetid: 7baa2959-9340-429b-ad53-3df03d8e13fc
caps.latest.revision: 27
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c4942413480f2d00f2d3a247fe8367c9e0a79341
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="data-accessor-functions---string-xquery"></a>データ アクセサー関数の文字列 (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  値を返します *$arg*を文字列として表されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:string() as xs:string  
fn:string($arg as item()?) as xs:string  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 ノードまたはアトミック値です。  
  
## <a name="remarks"></a>解説  
  
-   場合 *$arg*空のシーケンスでは、長さゼロの文字列が返されます。  
  
-   場合 *$arg*ノードの場合、string-value アクセサーを使用して取得したノードの文字列値を返します。 これは、W3C XQuery 1.0 and XPath 2.0 Data Model 仕様で定義されています。  
  
-   場合 *$arg*は、アトミック値としてキャスト式によって返されるのと同じ文字列を返します**xs:string**、 *$arg*、以外の場合に特に記載します。  
  
-   場合の種類 *$arg*は**xs:anyURI**、特殊文字をエスケープせず、URI を文字列に変換します。  
  
-   この実装で**fn:string()** せず、引数は、コンテキストに依存する述語のコンテキストでのみ使用できます。 具体的には、角かっこ ([ ]) 内でしか使用できません。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例は、 **xml** AdventureWorks データベース内の列を入力します。  
  
### <a name="a-using-the-string-function"></a>A. string 関数の使用  
 次のクエリは、<`ProductDescription`> 要素の <`Features`> 子要素ノードを取得します。  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
 /PD:ProductDescription/PD:Features  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 結果の一部を次に示します。  
  
```  
<PD:Features xmlns:PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
   These are the product highlights.   
   <p1:Warranty xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p1:WarrantyPeriod>3 years</p1:WarrantyPeriod>  
    <p1:Description>parts and labor</p1:Description>  
   </p1:Warranty>  
       ...  
</PD:Features>  
```  
  
 指定した場合、 **string()** 関数の場合、指定したノードの文字列値を表示します。  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
 string(/PD:ProductDescription[1]/PD:Features[1])  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 次に結果の一部を示します。  
  
```  
These are the product highlights.   
3 yearsparts and labor...    
```  
  
### <a name="b-using-the-string-function-on-various-nodes"></a>B. 異なるノードに対する string 関数の使用  
 次の例では、XML インスタンスが xml 型の変数に割り当てられています。 クエリが適用した結果を示すために指定された**string()** さまざまなノードにします。  
  
```  
declare @x xml  
set @x = '<?xml version="1.0" encoding="UTF-8" ?>  
<!--  This is a comment -->  
<root>  
  <a>10</a>  
just text  
  <b attr="x">20</b>  
</root>  
'  
```  
  
 次のクエリは、ドキュメント ノードの文字列値を取得します。 この値は、このノードの子孫にあたるすべてのテキスト ノードの文字列値を連結して生成されます。  
  
```  
select @x.query('string(/)')  
```  
  
 結果を次に示します。  
  
```  
This is a comment 10  
just text  
 20  
```  
  
 次のクエリは、processing-instruction ノードの文字列値を取得します。 ただし、このノードにはテキスト ノードが含まれていないため、空のシーケンスが結果として返されます。  
  
```  
select @x.query('string(/processing-instruction()[1])')  
```  
  
 次のクエリは、comment ノードの文字列値を取得し、そのテキスト ノードを返します。  
  
```  
select @x.query('string(/comment()[1])')  
```  
  
 結果を次に示します。  
  
```  
This is a comment   
```  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
