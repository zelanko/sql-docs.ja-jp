---
title: Original 要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Original Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.original
- http://schemas.microsoft.com/analysisservices/2003/engine#Original
- urn:schemas-microsoft-com:xml-analysis#Original
helpviewer_keywords:
- Original element
ms.assetid: c98a3700-ac19-4341-85d9-5afedf662601
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d93423cb5913af488152bb7b2914b4075db70b12
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="original-element-xmla"></a>Original 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]によって使用される元のファイル システム ストレージ場所を含む、[フォルダー](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Folder>  
   ...  
   <Original>...</Original>  
   ...  
</Folder>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|基数|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[フォルダー](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **元**要素には値に置き換えられますへの UNC パスが含まれています、[新規](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md)親に含まれる要素**フォルダー**復元のすべてのオブジェクトの要素または同期中にはそれぞれ、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)または[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)コマンド。 この要素の値がの値と比較して、 [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)各キューブ、メジャー グループ、またはパーティションの要素と一致するものが見つかった場合の値、**新規**要素を使用して、を更新**StorageLocation**復元または同期中にオブジェクトの。  
  
 バックアップと復元のオブジェクトの詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期 (&) #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
