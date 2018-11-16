---
title: local-name 関数 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:local-name function
- local-name function
ms.assetid: c901ef5d-89c5-482a-bf64-3eefbcf3098d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 93f289ed165742ae8fdf8d49732186161a4a8b5d
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51666991"
---
# <a name="functions-on-nodes---local-name"></a>ノードの関数 - local-name
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  名前のローカル部分を返します *$arg* xs:string される長さ 0 の文字列になりますか、または形式の名前、xs:NCName する必要があります。 引数を指定しない場合の既定値はコンテキスト ノードです。  
  
## <a name="syntax"></a>構文  
  
```  
fn:local-name() as xs:string  
fn:local-name($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 ローカル名部分を取得するノード名。  
  
## <a name="remarks"></a>コメント  
  
-   SQL Server で**fn:local-name()** せず、引数は、コンテキストに依存する述語のコンテキストでのみ使用できます。 具体的には、角かっこ (`[ ]`) 内でしか使用できません。  
  
-   引数に空のシーケンスを指定すると、関数は長さゼロの文字列を返します。  
  
-   対象ノードに名前がない場合、そのノードはドキュメント ノード、コメント、またはテキスト ノードなので、関数は長さゼロの文字列を返します。  
  
## <a name="examples"></a>使用例  
 このトピックではさまざまなに格納されている XML インスタンスに対して XQuery の例について**xml**型の列には、AdventureWorks データベース。  
  
### <a name="a-retrieve-local-name-of-a-specific-node"></a>A. 特定のノードのローカル名を取得する  
 次のクエリは、型指定されていない XML インスタンスに対して指定されています。 クエリ式 `local-name(/ROOT[1])` は、指定されたノードのローカル名部分を取得します。  
  
```  
declare @x xml  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('local-name(/ROOT[1])')  
-- result = ROOT  
```  
  
 次のクエリは、ProductModel テーブルの型指定された xml 型の列である Instructions 列に対して指定されています。 式 `local-name(/AWMI:root[1]/AWMI:Location[1])` は、指定されたノードのローカル名 `Location` を返します。  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     local-name(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
-- result = Location  
```  
  
### <a name="b-using-local-name-without-argument-in-a-predicate"></a>B. 述語で引数を指定せずに local-name を使用する  
 次のクエリは型指定された、Instructions 列に対して指定**xml** ProductModel テーブルの列。 式は、QName のローカル名部分が "Location" である <`root`> 要素のすべての子要素を返します。 **Local-name()** 関数は、述語で指定し、コンテキスト ノードが、関数で使用される引数を持ちません。  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
  /AWMI:root//*[local-name() = "Location"]') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 このクエリは、<`root`> 要素の <`Location`> 子要素を返します。  
  
## <a name="see-also"></a>参照  
 [ノードの関数](https://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [名前空間 uri 関数&#40;XQuery&#41;](../xquery/functions-on-nodes-namespace-uri.md)  
  
  
