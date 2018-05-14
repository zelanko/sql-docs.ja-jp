---
title: 新しい要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: acb0043613c784b5677f3446beef22b6ecc12321
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="new-element-xmla"></a>New 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  新しいファイル システム ストレージの場所で使用が含まれています、[フォルダー](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Folder>  
   ...  
   <New>...</New>  
   ...  
</Folder>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[フォルダー](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **新規**要素が値の置換される UNC パスを含む、**元**親に含まれる要素**フォルダー**復元または同期されている、すべてのオブジェクトの要素中に、それぞれ、**復元**または**同期**コマンド。 値、**元**要素の値と比較されます、 **StorageLocation**各キューブ、メジャー グループ、またはパーティションの要素と、更新するこの要素の値が使用される、一致が見つかった場合、**StorageLocation**復元または同期中にオブジェクトの。  
  
 バックアップと復元のオブジェクトの詳細については、次を参照してください。[をバックアップおよび復元するオブジェクト (XMLA)](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)です。  
  
## <a name="see-also"></a>参照  
 [元の要素 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/original-element-xmla.md)   
 [要素 & #40; を復元します。XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [StorageLocation 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)   
 [要素 & #40; を同期します。XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
