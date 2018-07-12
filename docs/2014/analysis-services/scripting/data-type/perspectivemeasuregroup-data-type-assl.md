---
title: PerspectiveMeasureGroup データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- PerspectiveMeasureGroup Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PerspectiveMeasureGroup
helpviewer_keywords:
- PerspectiveMeasureGroup data type
ms.assetid: 5927120d-f30e-4f87-8523-6d17012817d7
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: da4817ba23f7e4be50eb11aa97a3163e48536425
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37154953"
---
# <a name="perspectivemeasuregroup-data-type-assl"></a>PerspectiveMeasureGroup データ型 (ASSL)
  内のメジャー グループに関する情報を表すプリミティブ データ型を定義、[パースペクティブ](../objects/perspective-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<PerspectiveMeasureGroup>  
   <MeasureGroupID>...</MeasureGroupID>  
   <Measures>...</Measures>  
   <Annotations>...</Annotations>  
</PerspectiveMeasureGroup>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../collections/annotations-element-assl.md)、 [MeasureGroupID](../properties/id-element-assl.md)、[メジャー](../collections/measures-element-assl.md)|  
|派生要素|[MeasureGroup](../objects/group-element-assl.md) ([MeasureGroups](../collections/groups-element-assl.md)のコレクション[パースペクティブ](../objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>コメント  
 パースペクティブのメジャー グループは、基になるキューブのメジャー グループと同じ構造です。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
