---
title: "IsDefaultImage 要素 (XML) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: e29cd137-af82-4753-a681-0d3e705513f3
caps.latest.revision: 6
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ed09bbccf5bb5aa399fbab0c9e6a58c7f58c7ecd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

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
|既定値|オプション|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[RelationshipEndVisualizationProperties](../../../analysis-services/scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **RelationshipEndVisualizationProperties** 、要素、 **IsDefaultImage**要素は、このエンティティの既定のイメージをこのもう一方の端に移動することによって取得できることを示しますリレーションシップです。 既定値の**false**取得される既定のイメージがないことを示します。  
  
  
