---
title: ローカル名関数 (XQuery) |Microsoft Docs
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
ms.openlocfilehash: 382bbc9aeedacf37c7fe38abd592bcee7e154f5a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68038872"
---
# <a name="functions-on-nodes---local-name"></a>ノードの関数 - local-name
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  *$Arg*の名前のローカル部分を xs: string として返します。この文字列は、長さが0の文字列であるか、または Xs: NCName という構文形式になります。 引数が指定されていない場合、既定値はコンテキストノードです。  
  
## <a name="syntax"></a>構文  
  
```  
fn:local-name() as xs:string  
fn:local-name($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 ローカル名の部分を取得するノードの名前。  
  
## <a name="remarks"></a>Remarks  
  
-   SQL Server では、引数が指定されていない**fn: ローカル名 ()** は、コンテキストに依存する述語のコンテキストでのみ使用できます。 具体的には、角かっこ (`[ ]`) 内でのみ使用できます。  
  
-   引数を指定し、空のシーケンスの場合、関数は長さ0の文字列を返します。  
  
-   ターゲットノードがドキュメントノード、コメント、またはテキストノードであるために名前がない場合、関数は長さ0の文字列を返します。  
  
## <a name="examples"></a>使用例  
 このトピックでは、AdventureWorks データベースのさまざまな**xml**型の列に格納されている xml インスタンスに対して XQuery の例を示します。  
  
### <a name="a-retrieve-local-name-of-a-specific-node"></a>A. 特定のノードのローカル名を取得する  
 次のクエリは、型指定されていない XML インスタンスに対して指定されています。 クエリ式`local-name(/ROOT[1])`は、指定されたノードのローカル名部分を取得します。  
  
```  
declare @x xml  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('local-name(/ROOT[1])')  
-- result = ROOT  
```  
  
 次のクエリは、ProductModel テーブルの型指定された xml 列である命令列に対して指定されています。 式`local-name(/AWMI:root[1]/AWMI:Location[1])`は、指定されたノードの`Location`ローカル名を返します。  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     local-name(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
-- result = Location  
```  
  
### <a name="b-using-local-name-without-argument-in-a-predicate"></a>B. 述語で引数を指定せずに local-name を使用する  
 次のクエリは、ProductModel テーブルの型指定された**xml**列である命令列に対して指定されています。 この式は、QName のローカル名部分が`root` "Location" である <> 要素のすべての子要素を返します。 **ローカル名 ()** 関数は、述語で指定され、引数がありません。この関数では、コンテキストノードが使用されます。  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
  /AWMI:root//*[local-name() = "Location"]') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 このクエリでは、<`Location` `root`> 要素のすべての <> 子要素が返されます。  
  
## <a name="see-also"></a>参照  
 [ノードの関数](https://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [名前空間 uri 関数 &#40;XQuery&#41;](../xquery/functions-on-nodes-namespace-uri.md)  
  
  
