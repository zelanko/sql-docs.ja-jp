---
title: "名前空間 uri 関数 (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:namespace-uri function
- namespace-uri function
ms.assetid: 9b48d216-26c8-431d-9ab4-20ab187917f4
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 89c8cf916143a1041c340aeea48642c87c1d17cd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="functions-on-nodes---namespace-uri"></a>ノードの名前空間 uri の関数
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  名前空間で指定された QName の URI を返します*$arg* xs:string にキャストします。  
  
## <a name="syntax"></a>構文  
  
```  
fn:namespace-uri() as xs:string  
fn:namespace-uri($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 名前空間 URI 部分が取得されるノードの名前。  
  
## <a name="remarks"></a>解説  
  
-   引数が省略された場合、既定値はコンテキスト ノードです。  
  
-   SQL Server で**fn:namespace-uri()**せず、引数は、コンテキストに依存する述語のコンテキストでのみ使用できます。 具体的には、角かっこ ([ ]) 内でしか使用できません。  
  
-   場合*$arg*空のシーケンスでは、長さゼロの文字列が返されます。  
  
-   場合*$arg*要素または属性ノードが持つ Expanded-qname が名前空間、関数は長さゼロの文字列を返します  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例**xml** AdventureWorks データベース内の列を入力します。  
  
### <a name="a-retrieve-namespace-uri-of-a-specific-node"></a>A. 特定のノードの名前空間 URI を取得する  
 次のクエリは、型指定されていない XML インスタンスに対して指定されています。 クエリ式 `namespace-uri(/ROOT[1])` によって、指定されたのノードの名前空間 URI 部分が取得されます。  
  
```  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('namespace-uri(/ROOT[1])')  
```  
  
 指定された QName には名前空間 URI 部分がなく、ローカル名部分しかないため、結果は長さゼロの文字列となります。  
  
 次のクエリは型指定された手順に対して指定**xml**列です。 式 `namespace-uri(/AWMI:root[1]/AWMI:Location[1])` によって、<`root`> 要素の最初の <`Location`> 子要素の名前空間 URI が返されます。  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     namespace-uri(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 結果を次に示します。  
  
```  
http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions  
```  
  
### <a name="b-using-namespace-uri-without-argument-in-a-predicate"></a>B. 述語で引数を指定せずに namespace-uri() を使用する  
 次のクエリは、CatalogDescription 型が指定された xml 列に対して指定されています。 式は名前空間 URI のすべての要素ノードを返しますが`http://www.adventure-works.com/schemas/OtherFeatures`です。 名前空間 -**uri()**関数で、引数なしで指定された、コンテキスト ノードを使用します。  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
   /p1:ProductDescription//*[namespace-uri() = "http://www.adventure-works.com/schemas/OtherFeatures"]  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 これは、結果の一部です。  
  
```  
<p1:wheel xmlns:p1="http://www.adventure-works.com/schemas/OtherFeatures">High performance wheels.</p1:wheel>  
<p2:saddle xmlns:p2="http://www.adventure-works.com/schemas/OtherFeatures">  
  <p3:i xmlns:p3="http://www.w3.org/1999/xhtml">Anatomic design</p3:i> and made from durable leather for a full-day of riding in comfort.</p2:saddle>  
…  
```  
  
 上のクエリの名前空間 URI は `http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain` に変更できます。 その場合、展開された QName の URI 名前空間部分が `http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain` である <`ProductDescription`> 要素のすべての子要素ノードが取得されます。  
  
### <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Namespace-uri()**関数 xs:anyURI ではなく xs:string 型のインスタンスを返します。  
  
## <a name="see-also"></a>参照  
 [ノードの関数](http://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [ローカル名関数と #40 です。XQuery と #41 です。](../xquery/functions-on-nodes-local-name.md)  
  
  

