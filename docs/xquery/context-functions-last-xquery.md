---
title: last 関数 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- last function [XQuery]
- fn:last function
ms.assetid: dc92086e-3b01-4b0b-9f54-3bbf306cf7ae
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7220b0fe10f88ec9ba78d31a8507d12eba7aafff
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51674071"
---
# <a name="context-functions---last-xquery"></a>コンテキスト関数 - last (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  現在処理中のシーケンス内のアイテム数を返します。 具体的には、シーケンス内の最後のアイテムの整数インデックスを返します。 シーケンス内の最初のアイテムのインデックス値が 1 になります。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:last() as xs:integer  
```  
  
## <a name="remarks"></a>コメント  
 SQL Server で**fn:last()** をコンテキストに依存する述語のコンテキストでのみ使用できます。 具体的には、角かっこ (`[ ]`) 内でしか使用できません。  
  
## <a name="examples"></a>使用例  
 このトピックではさまざまなに格納されている XML インスタンスに対して XQuery の例について**xml**型の列には、AdventureWorks データベース。  
  
### <a name="a-using-the-last-xquery-function-to-retrieve-the-last-two-manufacturing-steps"></a>A. last() XQuery 関数を使用して、最後の 2 つの製造ステップを取得する  
 次のクエリでは、特定の製品モデルの最後の 2 つの製造ステップを取得します。 値、によって返される、製造手順の数、 **last()** 最後の 2 つの製造ステップを取得する、このクエリで使用される関数。  
  
```  
SELECT ProductModelID, Instructions.query('   
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  <LastTwoManuSteps>  
   <Last-1Step>   
     { (/AWMI:root/AWMI:Location)[1]/AWMI:step[(last()-1)]/text() }  
   </Last-1Step>  
   <LastStep>   
     { (/AWMI:root/AWMI:Location)[1]/AWMI:step[last()]/text() }  
   </LastStep>  
  </LastTwoManuSteps>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 上記のクエリで、 **last()** 関数/`/AWMI:root//AWMI:Location)[1]/AWMI:step[last()]`の製造手順の数を返します。 この値は、ワーク センター拠点で最後の製造ステップを取得するために使用されます。  
  
 結果を次に示します。  
  
```  
ProductModelID Result    
-------------- -------------------------------------  
7      <LastTwoManuSteps>  
         <Last-1Step>  
            When finished, inspect the forms for defects per   
            Inspection Specification .  
         </Last-1Step>  
         <LastStep>Remove the frames from the tool and place them   
            in the Completed or Rejected bin as appropriate.  
         </LastStep>  
       </LastTwoManuSteps>  
```  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
