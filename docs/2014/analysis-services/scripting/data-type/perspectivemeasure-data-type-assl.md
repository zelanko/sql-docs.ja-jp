---
title: PerspectiveMeasure データ型 (ASSL) |Microsoft Docs
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
- PerspectiveMeasure Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PerspectiveMeasure
helpviewer_keywords:
- PerspectiveMeasure data type
ms.assetid: 8622ad67-3dcf-48e2-ad4a-c5f0a086eec3
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 47d8578d2d41d5362b43a514dcb6d20df0999828
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37210012"
---
# <a name="perspectivemeasure-data-type-assl"></a>PerspectiveMeasure データ型 (ASSL)
  メジャーに関する情報を表すプリミティブ データ型を定義、 [PerspectiveMeasureGroup](perspectivemeasuregroup-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<PerspectiveMeasure>  
   <MeasureID>...</MeasureID>  
   <Annotations>...</Annotations>  
</PerspectiveMeasure>  
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
|子要素|[注釈](../collections/annotations-element-assl.md)、 [MeasureID](../properties/id-element-assl.md)|  
|派生要素|[メジャー](../objects/measure-element-assl.md) ([メジャー](../collections/measures-element-assl.md)のコレクション[PerspectiveMeasureGroup](perspectivemeasuregroup-data-type-assl.md))|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.PerspectiveMeasure>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
