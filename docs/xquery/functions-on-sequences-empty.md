---
title: empty 関数 (XQuery) |Microsoft Docs
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
- empty function
- fn:empty function
ms.assetid: 46da89a8-0cd9-4913-8521-4087589a04ba
author: rothja
ms.author: jroth
ms.openlocfilehash: 888739807a79163a8188f3b2f27b7f7860032bc4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68004675"
---
# <a name="functions-on-sequences---empty"></a>シーケンスの関数 - empty
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  *$Arg*の値が空のシーケンスの場合に True を返します。 それ以外の場合、関数は False を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
fn:empty($arg as item()*) as xs:boolean  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 項目のシーケンス。 シーケンスが空の場合、関数は True を返します。 それ以外の場合、関数は False を返します。  
  
## <a name="remarks"></a>Remarks  
 **Fn: exists ()** 関数はサポートされていません。 代わりに、 **not ()** 関数を使用することもできます。  
  
## <a name="examples"></a>使用例  
 このトピックでは、AdventureWorks データベースのさまざまな**xml**型の列に格納されている xml インスタンスに対して XQuery の例を示します。  
  
### <a name="a-using-the-empty-xquery-function-to-determine-if-an-attribute-is-present"></a>A. Empty () XQuery 関数を使用して、属性が存在するかどうかを判断する  
 製品モデル7の製造プロセスでは、このクエリは**Machinehours**属性を持たないすべてのワークセンターの場所を返します。  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
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
  
 次のように若干変更されたクエリでは、 **Machinehour**属性が存在しない場合に "NotFound" が返されます。  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace p14="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
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
  
  
