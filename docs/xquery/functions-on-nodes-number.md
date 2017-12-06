---
title: "number 関数 (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- number function
- fn:number function
ms.assetid: dff6d19b-765c-4df9-afff-9a0e7be9b91b
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 72371138871bce0dc775112f56015abaef53a225
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="functions-on-nodes---number"></a>ノードの数の関数
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  示されているノードの数値を返します*$arg*です。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:number() as xs:double?   
fn:number($arg as node()?) as xs:double?  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 数値として値が返されるノード。  
  
## <a name="remarks"></a>解説  
 場合*$arg*が指定されていない、double 型に変換と、コンテキスト ノードの数値の値が返されます。 SQL Server で**fn:number()**せず、引数は、コンテキストに依存する述語のコンテキストでのみ使用できます。 具体的には、角かっこ ([ ]) 内でしか使用できません。 たとえば、次の式では <`ROOT`> 要素が返されます。  
  
```  
declare @x xml  
set @x='<ROOT>111</ROOT>'  
select @x.query('/ROOT[number()=111]')  
```  
  
 ノードの値がない場合、数値の単純型の有効な字句表現で定義されている**XML Schema Part 2: datatypes」、W3C Recommendation**、空のシーケンスを返します。 NaN はサポートされません。  
  
## <a name="examples"></a>使用例  
 このトピックでは、さまざまなに格納されている XML インスタンスに対して XQuery の例**xml** AdventureWorks データベース内の列を入力します。  
  
### <a name="a-using-the-number-xquery-function-to-retrieve-the-numeric-value-of-an-attribute"></a>A. number() XQuery 関数を使用して属性の数値を取得する  
 次のクエリでは、製造モデル 7 の製造プロセスに含まれる最初のワーク センター拠点から、ロット サイズ属性の数値が取得されます。  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     for $i in (//AWMI:root//AWMI:Location)[1]  
     return   
       <Location LocationID="{ ($i/@LocationID) }"   
                   LotSizeA="{  $i/@LotSize }"  
                   LotSizeB="{  number($i/@LotSize) }"  
                   LotSizeC="{ number($i/@LotSize) + 1 }" >  
  
       </Location>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   **Number()**のクエリで示すように関数が必要でない、 **LotSizeA**属性。 これは XPath 1.0 関数で、主に旧バージョンとの互換性上の理由で含まれています。  
  
-   XQuery **LotSizeB** number 関数を指定し、冗長です。  
  
-   クエリ**LotSizeD**算術演算の番号の値の使用方法について説明します。  
  
 結果を次に示します。  
  
```  
ProductModelID   Result  
----------------------------------------------  
7              <Location LocationID="10"   
                         LotSizeA="100"   
                         LotSizeB="100"   
                         LotSizeC="101" />  
```  
  
### <a name="implementation-limitations"></a>実装の制限事項  
 制限事項を次に示します。  
  
-   **Number()**関数はノードのみを受け入れます。 アトミック値を受け取ることはできません。  
  
-   値は、数値として返されることはできません、 **number()**関数が NaN ではなく、空のシーケンスを返します。  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
