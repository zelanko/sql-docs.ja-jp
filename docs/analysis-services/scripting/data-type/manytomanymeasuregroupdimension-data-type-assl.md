---
title: ManyToManyMeasureGroupDimension データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dba37727a3e21c60d17e6d596281820655ddd730
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="manytomanymeasuregroupdimension-data-type-assl"></a>ManyToManyMeasureGroupDimension データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  多対多ディメンションとメジャー グループとの間のリレーションシップを表す派生データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ManyToManyMeasureGroupDimension>  
   <!-- The following elements extend MeasureGroupDimension -->  
   <MeasureGroupID>...</MeasureGroupID>  
   <DefaultMember>...</DefaultMember>  
</ManyToManyMeasureGroupDimension>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[MeasureGroupDimension](../../../analysis-services/scripting/data-type/measuregroupdimension-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[DefaultMember](../../../analysis-services/scripting/properties/defaultmember-element-assl.md)、 [MeasureGroupID](../../../analysis-services/scripting/properties/measuregroupid-element-assl.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ManyToManyMeasureGroupDimension>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
