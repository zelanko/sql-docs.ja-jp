---
title: 名前空間 uri 関数 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:namespace-uri function
- namespace-uri function
ms.assetid: 9b48d216-26c8-431d-9ab4-20ab187917f4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 046017ed9e7a9f99f2fde48426888045b4a02890
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51667172"
---
# <a name="functions-on-nodes---namespace-uri"></a>ノードの関数 - namespace-uri
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  名前空間で指定された QName の URI を返します *$arg* xs:string にキャストします。  
  
## <a name="syntax"></a>構文  
  
```  
fn:namespace-uri() as xs:string  
fn:namespace-uri($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 名前空間 URI 部分が取得されるノードの名前。  
  
## <a name="remarks"></a>コメント  
  
-   引数が省略された場合、既定値はコンテキスト ノードです。  
  
-   SQL Server で**fn:namespace-uri()** せず、引数は、コンテキストに依存する述語のコンテキストでのみ使用できます。 具体的には、角かっこ ([ ]) 内でしか使用できません。  
  
-   場合 *$arg*空のシーケンスでは、長さ 0 の文字列が返されます。  
  
-   場合 *$arg*要素または属性ノードが持つ Expanded-qname が、名前空間の関数では長さ 0 の文字列を返します  
  
## <a name="examples"></a>使用例  
 このトピックではさまざまなに格納されている XML インスタンスに対して XQuery の例について**xml**型の列には、AdventureWorks データベース。  
  
### <a name="a-retrieve-namespace-uri-of-a-specific-node"></a>A. 特定のノードの名前空間 URI を取得する  
 次のクエリは、型指定されていない XML インスタンスに対して指定されています。 クエリ式 `namespace-uri(/ROOT[1])` によって、指定されたのノードの名前空間 URI 部分が取得されます。  
  
```  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('namespace-uri(/ROOT[1])')  
```  
  
 指定された QName には名前空間 URI 部分がなく、ローカル名部分しかないため、結果は長さゼロの文字列となります。  
  
 次のクエリは型指定された手順に対して指定**xml**列。 式 `namespace-uri(/AWMI:root[1]/AWMI:Location[1])` によって、<`root`> 要素の最初の <`Location`> 子要素の名前空間 URI が返されます。  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     namespace-uri(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 結果を次に示します。  
  
```  
https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions  
```  
  
### <a name="b-using-namespace-uri-without-argument-in-a-predicate"></a>B. 述語で引数を指定せずに namespace-uri() を使用する  
 次のクエリは、CatalogDescription 型が指定された xml 列に対して指定されています。 この式によって、名前空間 URI が `https://www.adventure-works.com/schemas/OtherFeatures` であるすべての要素ノードが返されます。 名前空間 -**uri()** 関数で、引数なしで指定された、コンテキスト ノードを使用します。  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
   /p1:ProductDescription//*[namespace-uri() = "https://www.adventure-works.com/schemas/OtherFeatures"]  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 これは、結果の一部です。  
  
```  
<p1:wheel xmlns:p1="https://www.adventure-works.com/schemas/OtherFeatures">High performance wheels.</p1:wheel>  
<p2:saddle xmlns:p2="https://www.adventure-works.com/schemas/OtherFeatures">  
  <p3:i xmlns:p3="https://www.w3.org/1999/xhtml">Anatomic design</p3:i> and made from durable leather for a full-day of riding in comfort.</p2:saddle>  
…  
```  
  
 上のクエリの名前空間 URI は `https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain` に変更できます。 その場合、展開された QName の URI 名前空間部分が `https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain` である <`ProductDescription`> 要素のすべての子要素ノードが取得されます。  
  
### <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Namespace-uri()** 関数は、xs:anyURI ではなく xs:string 型のインスタンスを返します。  
  
## <a name="see-also"></a>参照  
 [ノードの関数](https://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [local-name 関数&#40;XQuery&#41;](../xquery/functions-on-nodes-local-name.md)  
  
  
