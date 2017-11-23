---
title: "Folders 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Folders Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.folders
- http://schemas.microsoft.com/analysisservices/2003/engine#Folders
- urn:schemas-microsoft-com:xml-analysis#Folders
helpviewer_keywords: Folders element
ms.assetid: fefb0469-22ea-4804-8dc3-9c49825b32f1
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 83571bacbbd3779909d79d3f327c4088b9222bb6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="folders-element-xmla"></a>Folders 要素 (XMLA)
  [Restore](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) または [Synchronize](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) コマンドの実行中に親要素 [Location](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) によって使用される [Folder](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) 要素のコレクションを含みます。  
  
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
|親要素|[場所](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|子要素|[フォルダー](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [要素 &#40; を復元します。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [要素 &#40; を同期します。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
