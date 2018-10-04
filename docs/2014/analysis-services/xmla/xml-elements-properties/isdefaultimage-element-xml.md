---
title: IsDefaultImage 要素 (XML) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: e29cd137-af82-4753-a681-0d3e705513f3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0821c2dfaa25f3d9a557663046db0405aca0cb24
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201372"
---
# <a name="isdefaultimage-element-xml"></a>IsDefaultImage 要素 (XML)
  このリレーションシップを他のテーブルまでナビゲートし、属性 IsDefaultImage を持っているメンバーをフェッチすることにより、このエンティティの既定の画像を取得できることを示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <IsDefaultImage>...</IsDefaultImage>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|false|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[RelationshipEndVisualizationProperties](../../scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `RelationshipEndVisualizationProperties` 要素の場合、`IsDefaultImage` 要素は、このリレーションシップの他の端までナビゲートすることにより、このエンティティの既定の画像を取得できることを示します。 既定値 `false` は、取得できる既定の画像がないことを示します。  
  
  
