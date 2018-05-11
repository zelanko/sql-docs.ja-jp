---
title: DisplayFolder 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6986e1dc728591f9540b533052ef8fd135aca1b0
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="displayfolder-element-assl"></a>DisplayFolder 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  親要素を一覧表示するフォルダーを指定します。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 開発者および管理者向けのアプリケーションでは、複数の要素を視覚的に分類する表示フォルダーの使用をサポート可能性があります。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CalculationProperty> <!-- or Hierarchy, Kpi, Measure, Translation -->  
   ...  
   <DisplayFolder>...</DisplayFolder>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)、[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)、 [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)、[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)、[翻訳](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 比較的大きなキューブには、何百ものメジャーと階層が含まれている場合があります。 **DisplayFolder**プロパティは、クライアントのユーザーの外観を定義します。 値、 **DisplayFolder**プロパティは、次のオプションのいずれかを含めることができます。  
  
-   空にする - メジャーがフォルダーに所属しないことを示します。  
  
-   単一のフォルダー名を含んでいる - 同じ名前のフォルダーに所属するものとしてメジャーを表示する必要があることを示します。  
  
-   円記号で区切られた複数のフォルダー名が含まれます (\\)、埋め込みのフォルダー階層を示すです。  
  
 **DisplayFolder**プロパティに適用されます**CalculationProperty**場合にのみ、要素の値[CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md)に設定されている*メンバー*.  
  
 親に対応する要素**DisplayFolder**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.CalculationProperty>、 <xref:Microsoft.AnalysisServices.Hierarchy>、 <xref:Microsoft.AnalysisServices.Kpi>、 <xref:Microsoft.AnalysisServices.Measure>、および<xref:Microsoft.AnalysisServices.Translation>です。  
  
## <a name="see-also"></a>参照  
 [CalculationProperties 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [MdxScript 要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [MdxScripts 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
