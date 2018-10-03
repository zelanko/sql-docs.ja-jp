---
title: number 関数 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- number function
- fn:number function
ms.assetid: dff6d19b-765c-4df9-afff-9a0e7be9b91b
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: dbe1476f9b05d6ebaf3e919244fb759137cb2402
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47650940"
---
# <a name="functions-on-nodes---number"></a>ノードの関数 - number
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  によって示されるノードの数値の値を返します *$arg*します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:number() as xs:double?   
fn:number($arg as node()?) as xs:double?  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 数値として値が返されるノード。  
  
## <a name="remarks"></a>コメント  
 場合 *$arg*が指定されていない、double 型に変換された、コンテキスト ノードの数値の値が返されます。 SQL Server で**fn:number()** せず、引数は、コンテキストに依存する述語のコンテキストでのみ使用できます。 具体的には、角かっこ ([ ]) 内でしか使用できません。 たとえば、次の式では <`ROOT`> 要素が返されます。  
  
```  
declare @x xml  
set @x='<ROOT>111</ROOT>'  
select @x.query('/ROOT[number()=111]')  
```  
  
 ノードの値でない場合、数値の単純型の有効な字句表現で定義されている**XML Schema Part 2: datatypes,、W3C 勧告**関数は空のシーケンスを返します。 NaN はサポートされません。  
  
## <a name="examples"></a>使用例  
 このトピックではさまざまなに格納されている XML インスタンスに対して XQuery の例について**xml**型の列には、AdventureWorks データベース。  
  
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
  
-   **Number()** 関数のためのクエリで示すように必須ではありません、 **LotSizeA**属性。 これは XPath 1.0 関数で、主に旧バージョンとの互換性上の理由で含まれています。  
  
-   XQuery では**LotSizeB** number 関数を指定し、冗長です。  
  
-   クエリを**LotSizeD**算術演算の番号の値の使用方法を示します。  
  
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
  
-   **Number()** 関数ノードのみを受け取ります。 アトミック値を受け取ることはできません。  
  
-   値は、数値として返すことができないときに、 **number()** 関数が NaN ではなく空のシーケンスを返します。  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
