---
title: Locations 要素 (XMLA) |Microsoft Docs
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
- Locations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Locations
- urn:schemas-microsoft-com:xml-analysis#Locations
- microsoft.xml.analysis.locations
helpviewer_keywords:
- Locations element
ms.assetid: 630929cb-f0dc-472a-86bc-28b67e907c3d
caps.latest.revision: 10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 901c2d1cccacef54462d5f8cf9df4a4c59907a11
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263318"
---
# <a name="locations-element-xmla"></a>Locations 要素 (XMLA)
  コレクションを含む[場所](query-element-xmla.md)親によって使用される要素[バックアップ](../xml-elements-commands/backup-element-xmla.md)、[復元](../xml-elements-commands/restore-element-xmla.md)、または[同期](../xml-elements-commands/synchronize-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
< Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Locations>  
      <Location>...</Location>  
   </Locations>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[バックアップ](../xml-elements-commands/backup-element-xmla.md)、[復元](../xml-elements-commands/restore-element-xmla.md)、または[同期](../xml-elements-commands/synchronize-element-xmla.md)|  
|子要素|[[場所]](location-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
