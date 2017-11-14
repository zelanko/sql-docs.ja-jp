---
title: "KpiStatus 要素 (CSDLBI) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 6fee5b82-caa8-46a1-ad68-bbce3e11e01e
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 574cb8e39b224bcaa5f73be784c0c6aff4d39dde
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="kpistatus-element-csdlbi"></a>KpiStatus 要素 (CSDLBI)
  KpiStatus 要素は、主要業績評価指標 (KPI) で状態インジケーターとして使用される値を含む列への参照を定義します。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、KpiStatus 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|Description|  
|----------|-----------------|-----------------|  
|PropertyRef|可|KPI で状態インジケーターとして使用される値を含む列への参照です。<br /><br /> この要素は、TPropertyRefcomplex 型で定義されるように、ただ 1 つの列参照を含む必要があります。|  
  
## <a name="example"></a>例  
 **テーブル**  
  
 CSDLBI Version 1.1 における次の例は、AdventureWorks のテーブル モデル サンプルからの KPI を示します。 KpiStatus 要素が、値を含む列 (PropertyRef として表されます) を参照します。  
  
```  
  
<Property Name="InternetCurrSalesPerf" Type="Double">  
   <bi:Measure>  
     <bi:Kpi StatusGraphic="Three Stars Colored">  
       <bi:KpiGoal>  
         <bi:PropertyRef Name="v_InternetCurrSalesPerf_Goal" />  
       </bi:KpiGoal>  
       <bi:KpiStatus>  
         <bi:PropertyRef Name="v_InternetCurrSalesPerf_Status" />  
       </bi:KpiStatus>  
     </bi:Kpi>  
   </bi:Measure>  
</Property>  
  
```  
  
## <a name="example"></a>例  
 **多次元**  
  
 CSDLBI Version 1.1 における次の例では、Contoso Operations キューブからの KPI を示します。 KpiStatus 要素が、KPI の状態の値を計算するメジャーを参照します。  
  
```  
<bi:Measure   
       Caption="Sum of SalesAmount"   
       ReferenceName="Sum of SalesAmount"   
       FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
  
    <bi:Kpi   
       StatusGraphic="Three Circles Colored">  
  
      <bi:KpiGoal>  
         <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Goal" />  
       </bi:KpiGoal>  
  
       <bi:KpiStatus>  
          <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Status" />  
        </bi:KpiStatus>  
  
       </bi:Kpi>  
</bi:Measure>  
  
```  
  
## <a name="see-also"></a>参照  
 [KPI 要素 & #40 です。CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/kpi-element-csdlbi.md)  
  
  

