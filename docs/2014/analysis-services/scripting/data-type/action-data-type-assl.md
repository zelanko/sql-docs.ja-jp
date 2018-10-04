---
title: Action データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Action Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Action data type
ms.assetid: 8c4d2ff7-17e1-4e74-bec7-637e0b191acf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 21c13562fa53c0ba396a4c3826889e8d275f7d9a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197492"
---
# <a name="action-data-type-assl"></a>Action データ型 (ASSL)
  内のアクションを表す抽象プリミティブ データ型を定義、[キューブ](../objects/cube-element-assl.md)要素または[パースペクティブ](../objects/perspective-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Action>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Caption>...</Caption>  
      <CaptionIsMdx>...</CaptionIsMdx>  
      <Translations>...</Translations>  
   <TargetType>...</TargetType>  
   <Target>...</Target>  
   <Condition>...</Condition>  
   <Type>...</Type>  
   <Invocation>...</Invocation>  
   <Application>...</Application>  
      <Description>...</Description>  
      <Annotations>...</Annotations>  
</Action>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|[DrillThroughAction](action-data-type-assl.md)、 [ReportAction](reportaction-data-type-assl.md)、 [StandardAction](standardaction-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アクション](../collections/actions-element-assl.md)|  
|子要素|[注釈](../collections/annotations-element-assl.md)、[アプリケーション](../properties/application-element-assl.md)、[キャプション](../properties/caption-element-assl.md)、 [CaptionIsMdx](../properties/captionismdx-element-assl.md)、[条件](../properties/condition-element-assl.md)、[の説明](../properties/description-element-assl.md)、 [ID](../properties/id-element-assl.md)、[呼び出し](../properties/invocation-element-assl.md)、[名前](../properties/name-element-assl.md)、[ターゲット](../properties/target-element-assl.md)、 [TargetType](../properties/targettype-element-assl.md)、[翻訳](../collections/translations-element-assl.md)、[型](../properties/type-element-action-assl.md)|  
|派生要素|[DrillThroughAction](action-data-type-assl.md)、 [ReportAction](reportaction-data-type-assl.md)、 [StandardAction](standardaction-data-type-assl.md)|  
  
## <a name="remarks"></a>コメント  
 アクションの詳細については、「[アクション &#40;Analysis Services - 多次元データ&#41;](../../multidimensional-models/actions-analysis-services-multidimensional-data.md)」を参照してください。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Action>します。  
  
## <a name="see-also"></a>参照  
 [キューブ要素&#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Perspective 要素&#40;ASSL&#41;](../objects/perspective-element-assl.md)   
 [PerspectiveAction データ型&#40;ASSL&#41;](perspectiveaction-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
