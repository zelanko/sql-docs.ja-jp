---
title: 新しい要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- New Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#New
- microsoft.xml.analysis.new
- urn:schemas-microsoft-com:xml-analysis#New
helpviewer_keywords:
- New element
ms.assetid: 1321adcb-67f7-40f0-8f20-b17c1d3e3f17
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 975ee0144b0733500efa7d3008e21ff7d020bb8a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
  
  
