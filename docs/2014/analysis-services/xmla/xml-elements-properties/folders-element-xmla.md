---
title: Folders 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Folders Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.folders
- http://schemas.microsoft.com/analysisservices/2003/engine#Folders
- urn:schemas-microsoft-com:xml-analysis#Folders
helpviewer_keywords:
- Folders element
ms.assetid: fefb0469-22ea-4804-8dc3-9c49825b32f1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8e8097a5499f1d8d34d9dd5dd53726bf02a4b098
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48174352"
---
# <a name="folders-element-xmla"></a>Folders 要素 (XMLA)
  [Restore](folder-element-xmla.md) または [Synchronize](location-element-xmla.md) コマンドの実行中に親要素 [Location](../xml-elements-commands/restore-element-xmla.md) によって使用される [Folder](../xml-elements-commands/synchronize-element-xmla.md) 要素のコレクションを含みます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Location>  
   ...  
   <Folders>  
      <Folder>...</Folder>  
   </Folders>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし (コレクション型)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[場所]](location-element-xmla.md)|  
|子要素|[フォルダー](folder-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [Restore 要素&#40;XMLA&#41;](../xml-elements-commands/restore-element-xmla.md)   
 [Synchronize 要素&#40;XMLA&#41;](../xml-elements-commands/synchronize-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
