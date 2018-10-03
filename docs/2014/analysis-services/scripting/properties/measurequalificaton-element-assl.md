---
title: MeasureQualificaton 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MeasureQualificaton Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MeasureQualification element
ms.assetid: 754a037c-f20b-4717-a6e8-12f495e8e3b4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aff36cad69d59b7effa51ac9ab3e32490931f779
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48123332"
---
# <a name="measurequalificaton-element-assl"></a>MeasureQualificaton 要素 (ASSL)
  内のメジャーにプレフィックスが適用されるかどうかを決定する、 [MeasureGroup](../objects/group-element-assl.md)します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureGroup>  
   ...  
   <MeasureQualification>...</MeasureQualification>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*なし*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メジャー グループ](../objects/group-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*なし*|このメジャー グループ内のメジャーにプレフィックスは適用されません。|  
|*PrefixMeasureGroup*|このメジャーグループの各メジャーの一意の名前およびキャプションに、プレフィックスとしてメジャー グループの名前と 1 つのスペースが付加されます。|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`MeasureQualification`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MeasureGroup>します。  
  
## <a name="see-also"></a>参照  
 [キューブ要素&#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [ディメンション要素&#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [MeasureGroup 要素&#40;ASSL&#41;](../objects/group-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
