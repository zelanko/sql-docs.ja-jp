---
title: アトミック化 (XQuery) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/01/2016
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
dev_langs:
- XML
helpviewer_keywords:
- XQuery, atomization
- atomization [XQuery]
ms.assetid: e3d7cf2f-c6fb-43c2-8538-4470a6375af5
caps.latest.revision: 16
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a670727f677f17eb8ecab859dd1593bdae855a97
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="atomization-xquery"></a>アトミック化 (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  アトミック化とは、アイテムの型指定された値を抽出するプロセスです。 このプロセスは、特定の環境では暗黙的に実行されます。 算術演算子や比較演算子などの一部の XQuery 演算子は、このプロセスに依存します。 たとえば、ノードに直接算術演算子を適用する場合、ノードの型指定された値が最初に取得暗黙的に呼び出すことによって、[データ関数](../xquery/data-accessor-functions-data-xquery.md)です。 これにより、アトミック値がオペランドとして算術演算子に渡されます。  
  
 たとえば、次のクエリは LaborHours 属性の合計を返します。 この場合、 **data()** が属性ノードに暗黙的に適用します。  
  
```  
declare @x xml  
set @x='<ROOT><Location LID="1" SetupTime="1.1" LaborHours="3.3" />  
<Location LID="2" SetupTime="1.0" LaborHours="5" />  
<Location LID="3" SetupTime="2.1" LaborHours="4" />  
</ROOT>'  
-- data() implicitly applied to the attribute node sequence.  
SELECT @x.query('sum(/ROOT/Location/@LaborHours)')  
```  
  
 明示的に指定できますは必要ありませんが、 **data()** 関数。  
  
```  
SELECT @x.query('sum(data(ROOT/Location/@LaborHours))')  
```  
  
 暗黙のアトミック化の別の例として、算術演算子を使用するケースがあります。 **+** 演算子はアトミック値を必要と**data()** LaborHours 属性のアトミック値を取得するが暗黙的に適用します。 クエリがの Instructions 列に対して指定された、 **xml** ProductModel テーブルを入力します。 次のクエリでは、LaborHours 属性を 3 回返します。 このクエリでは、次の点に注意してください。  
  
-   OrignialLaborHours 属性の構築では、(`$WC/@LaborHours`) によって返される単一シーケンスにアトミック化が暗黙的に適用されます。 LaborHours 属性の型指定された値が、OrignialLaborHours に代入されます。  
  
-   UpdatedLaborHoursV1 属性の構築では、算術演算子がアトミック値を必要とします。 したがって、 **data()** によって返される LaborHours 属性に暗黙的に適用されます (`$WC/@LaborHours`)。 次に、アトミック値 1 が加算されます。 UpdatedLaborHoursV2 属性の構築の明示的な適用を示しています。 **data()**、は必要ありませんが、します。  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $WC in /AWMI:root/AWMI:Location[1]  
        return  
            <WC OriginalLaborHours = "{ $WC/@LaborHours }"  
                UpdatedLaborHoursV1 = "{ $WC/@LaborHours + 1 }"   
                UpdatedLaborHoursV2 = "{ data($WC/@LaborHours) + 1 }" >  
            </WC>') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 結果を次に示します。  
  
```  
<WC OriginalLaborHours="2.5"   
    UpdatedLaborHoursV1="3.5"   
    UpdatedLaborHoursV2="3.5" />  
```  
  
 アトミック化を行うと、結果は単純な型のインスタンス、空のセット、または静的な型エラーになります。  
  
 アトミック化は、関数、関数によって返される値に渡される比較式のパラメーターにも発生**cast()** 式、および by 句の順序で渡される順序式です。  
  
## <a name="see-also"></a>参照  
 [XQuery の基礎](../xquery/xquery-basics.md)   
 [比較式&#40;XQuery&#41;](../xquery/comparison-expressions-xquery.md)   
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
