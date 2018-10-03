---
title: KpiGoal 要素 (CSDLBI) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: fd8afbe7-b57d-4b47-862d-eb7b2489c327
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ceee819fb887e2a45b3f366b261fba00df4776a6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191382"
---
# <a name="kpigoal-element-csdlbi"></a>KpiGoal 要素 (CSDLBI)
  KpiGoal 要素は、主要業績評価指標 (KPI) の目標値を定義するために使用されている列への参照を提供します。  
  
 CSDLBI では、KPI はメジャーに基づき、Measure 要素には数式 (ある場合) が含まれていますが、KPI と関連付けられている他のメタデータは [KPI 要素 &#40;CSDLBI&#41;](kpi-element-csdlbi.md) の一部として定義されています。  Kpigoal 要素は Kpi 要素のサブタイプです。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、KpiGoal 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|説明|  
|----------|-----------------|-----------------|  
|PropertyRef|はい|KPI の目標値を含む列への参照。<br /><br /> Kpigoal 要素はただ 1 つの PropertyRef 要素を持つ必要があります。<br /><br /> 「[PropertyRef 要素 &#40;CSDLBI&#41;](propertyref-element-csdlbi.md)」を参照してください。|  
  
## <a name="example"></a>例  
 **テーブル**  
  
 CSDLBI Version 1.1 における次の例では、AdventureWorks サンプル モデルからの KPI を示します。  
  
```  
  
<Property Name="InternetCurrentSalesPerformance" Type="Double">  
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
  
 CSDLBI Version 1.1 における次の例では、Contoso Operations キューブからの KPI を示します。  
  
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
 [KPI 要素&#40;CSDLBI&#41;](kpi-element-csdlbi.md)  
  
  
