---
title: Folders 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 803ec660944663c7f40f1b7c9dddc118b8b6b76c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050560"
---
# <a name="folders-element-xmla"></a>Folders 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[場所]](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|子要素|[フォルダー](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照
 [Restore 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Synchronize 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
