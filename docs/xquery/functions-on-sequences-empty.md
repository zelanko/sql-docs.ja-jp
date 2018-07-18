---
title: 空の関数 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
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
- empty function
- fn:empty function
ms.assetid: 46da89a8-0cd9-4913-8521-4087589a04ba
caps.latest.revision: 27
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f312276737406070eb07f371d5fb1c807b8e24b2
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38040500"
---
# <a name="functions-on-sequences---empty"></a>空のシーケンスの関数-
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  True の場合の値 *$arg*は空のシーケンスです。 それ以外の場合は False を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:empty($arg as item()*) as xs:boolean  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 アイテムのシーケンス。 シーケンスが空の場合、関数は True を返します。 それ以外の場合は False を返します。  
  
## <a name="remarks"></a>コメント  
 **Fn:exists()** 関数がサポートされていません。 別の方法として、 **not()** 関数を使用できます。  
  
## <a name="examples"></a>使用例  
 このトピックではさまざまなに格納されている XML インスタンスに対して XQuery の例について**xml**型の列には、AdventureWorks データベース。  
  
### <a name="a-using-the-empty-xquery-function-to-determine-if-an-attribute-is-present"></a>A. empty() XQuery 関数を使用した属性の有無の判断  
 製品モデル 7 の製造プロセスをこのクエリがないすべてのワーク センター拠点が返されます、 **MachineHours**属性。  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     for $i in /AWMI:root/AWMI:Location[empty(@MachineHours)]  
     return  
       <Location  
            LocationID="{ ($i/@LocationID) }"  
            LaborHrs="{ ($i/@LaborHours) }" >  
            {   
              $i/@MachineHours  
            }    
       </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 結果を次に示します。  
  
```  
ProductModelID      Result          
-------------- ------------------------------------------  
7              <Location LocationID="30" LaborHrs="1"/>  
               <Location LocationID="50" LaborHrs="3"/>  
               <Location LocationID="60" LaborHrs="4"/>  
```  
  
 以下、少し変更のクエリが場合、"NotFound"を返します、 **MachineHour**属性が存在しません。  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace p14="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     for $i in /p14:root/p14:Location  
     return  
       <Location  
            LocationID="{ ($i/@LocationID) }"  
            LaborHrs="{ ($i/@LaborHours) }" >  
            {   
                 if (empty($i/@MachineHours)) then  
                    attribute MachineHours { "NotFound" }  
                 else  
                    attribute MachineHours { data($i/@MachineHours) }  
            }    
       </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 結果を次に示します。  
  
```  
ProductModelID Result                         
-------------- -----------------------------------  
7                
  <Location LocationID="10" LaborHrs="2.5" MachineHours="3"/>  
  <Location LocationID="20" LaborHrs="1.75" MachineHours="2"/>  
  <Location LocationID="30" LaborHrs="1" MachineHours="NotFound"/>  
  <Location LocationID="45" LaborHrs="0.5" MachineHours="0.65"/>  
  <Location LocationID="50" LaborHrs="3" MachineHours="NotFound"/>  
  <Location LocationID="60" LaborHrs="4" MachineHours="NotFound"/>  
```  
  
## <a name="see-also"></a>参照  
 [Xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)   
 [exist&#40;&#41; メソッド &#40;xml データ型&#41;](../t-sql/xml/exist-method-xml-data-type.md)  
  
  
