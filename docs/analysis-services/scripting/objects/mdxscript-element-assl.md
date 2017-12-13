---
title: "MdxScript 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MdxScript Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: MdxScript
helpviewer_keywords: MdxScript element
ms.assetid: 0c59a550-dc95-4d50-948a-bb99348bdd86
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 42c2a65b308359584788694f5f526a8069d3201a
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="mdxscript-element-assl"></a>MdxScript 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]関連付けられている多次元式 (MDX) スクリプトに関する情報が含まれています、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MdxScripts>  
   <MdxScript>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Annotations>...</Annotations>  
      <Commands>...</Commands>  
      <DefaultScript>...</DefaultScript>  
      <CalculationProperties>...</CalculationProperties>  
   </MdxScript>  
</MdxScripts>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MdxScripts](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [CalculationProperties](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)、[コマンド](../../../analysis-services/scripting/collections/commands-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、 [DefaultScript](../../../analysis-services/scripting/properties/defaultscript-element-assl.md)、 [説明](../../../analysis-services/scripting/properties/description-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、[名](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 スクリプトの**DefaultScript**要素に設定されている**True**既定です。 設定**DefaultScript**に**True**特定のスクリプト設定の**DefaultScript**に**False**他のすべてのスクリプト。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.MdxScript>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
