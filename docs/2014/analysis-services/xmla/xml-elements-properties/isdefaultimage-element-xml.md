---
title: IsDefaultImage 要素 (XML) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: e29cd137-af82-4753-a681-0d3e705513f3
caps.latest.revision: 6
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: c4d15ea9048c83b1579b688f6848e48deb1dffe4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075351"
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
  
  