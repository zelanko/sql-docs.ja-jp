---
title: "KPI 要素 (CSDLBI) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 203ee6e8-eef2-4476-b09f-bd95e492ddaa
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bc60e58643df0a47c0f31b93278e95bd1b64a804
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="kpi-element-csdlbi"></a>KPI 要素 (CSDLBI)
  Kpi 要素は、主要業績評価指標 (KPI) として使用できる計算を定義します。 ビジネス インテリジェンス データ モデルでは KPI はメジャーが基になっているので、KPI の定義には、メジャーと関連付けられているすべてのメタデータと共に、既定のグラフィックなどの KPI 値のプレゼンテーションに必要な情報が含まれます。  
  
 Kpi 要素は、メジャー定義に含まれる式を指定するのではなく、KPI として使用されるメジャーと関連付けられた追加メタデータを指定します。 いったん KPI として指定したメジャーは、他のコンテキストでメジャーとして使用できません。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、Kpi 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|Description|  
|----------|-----------------|-----------------|  
|ドキュメント|いいえ|KPI の説明。|  
|KpiGoal|可|目標値として使用できる値を含む列への参照。<br /><br /> 「[PropertyRef 要素 &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/propertyref-element-csdlbi.md)」を参照してください。|  
|KpiStatus|可|KPI の現在の状態を表す値を含む列への参照。|  
|StatusGraphic|可|KPI で定義されているターゲットに対するマイナス、0、またはプラスの進行状況を示すイメージの参照。|  
  
## <a name="remarks"></a>解説  
 モデルを設計するときは、メジャーを作成してから KPI として使用するようにメジャーを割り当てることで、KPI を作成できます。 次に、傾向の表示で使用されるグラフィックなど、KPI に固有の情報を追加します。  
  
## <a name="example"></a>例  
 **テーブル**  
  
 CSDLBI Version 1.1 における次の例では、AdventureWorks のテーブル モデル サンプルから売上を測定する KPI を示します。  
  
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
  
 CSDLBI Version 1.1 における次の例では、Contoso Operations キューブからの KPI を示します。  
  
```  
<Property Name="Sum_of_SalesAmount" Type="Decimal" Precision="19" Scale="4">  
   <Documentation>  
     <Summary>KPI Description</Summary>  
   </Documentation>  
     <bi:Measure   
         Caption="Sum of SalesAmount"   
         ReferenceName="Sum of SalesAmount"   
         FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
     <bi:Kpi   
           StatusGraphic="Three Circles Colored">  
         <bi:KpiGoal>  
            <bi:PropertyRef Name="v_Sum_of_SalesAmount_Goal" />  
          </bi:KpiGoal>  
          <bi:KpiStatus>  
              <bi:PropertyRef Name="v_Sum_of_SalesAmount_Status" />  
          </bi:KpiStatus>  
     </bi:Kpi>  
     </bi:Measure>  
</Property>  
```  
  
## <a name="see-also"></a>参照  
 [CSDL への BI 注釈のテクニカル リファレンス](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  

