---
title: IsDefaultMeasure 要素 (XML) |Microsoft ドキュメント
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
ms.assetid: 523cf3d7-9df0-4f9d-8486-9109de8d3cca
caps.latest.revision: 6
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: a4229507c856d511b805a249b162516d8b11feb6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074254"
---
# <a name="isdefaultmeasure-element-xml"></a>IsDefaultMeasure 要素 (XML)
  このリレーションシップを他のテーブルまでナビゲートし、属性 DefaultMeasure を持っているメンバーをフェッチすることにより、このエンティティの既定のメジャーを取得できることを示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <IsDefaultMeasure>...</IsDefaultMeasure>  
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
 `RelationshipEndVisualizationProperties` 要素の場合、`IsDefaultMeasure` 要素は、このリレーションシップの他の端までナビゲートすることにより、このエンティティの既定のメジャーを取得できることを示します。 既定値 `false` は、取得できる既定のメジャーがないことを示します。  
  
  