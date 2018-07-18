---
title: New 要素 (XMLA) |Microsoft Docs
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
- New Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#New
- microsoft.xml.analysis.new
- urn:schemas-microsoft-com:xml-analysis#New
helpviewer_keywords:
- New element
ms.assetid: 1321adcb-67f7-40f0-8f20-b17c1d3e3f17
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f93da2c5c9dab8b8d7542db68e70df67a87afbe8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37203982"
---
# <a name="new-element-xmla"></a>New 要素 (XMLA)
  によって使用される新しいファイル システム ストレージ場所が含まれています、[フォルダー](folder-element-xmla.md)要素。  
  
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
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[フォルダー](folder-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `New` 要素は、`Original` または `Folder` コマンドの実行時に復元または同期されるすべてのオブジェクトに関して、親要素 `Restore` に含まれる `Synchronize` 要素の値に代わる置換後の UNC パスを含みます。 `Original` 要素の値は、各キューブ、メジャー グループ、パーティションの `StorageLocation` 要素の値と比較され、一致が検出された場合には、復元または同期の実行中にオブジェクトの `StorageLocation` を更新するために、この要素の値が使用されます。  
  
 バックアップと復元のオブジェクトの詳細については、次を参照してください。[をバックアップおよび復元するオブジェクト (XMLA)](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
## <a name="see-also"></a>参照  
 [元の要素&#40;XMLA&#41;](original-element-xmla.md)   
 [Restore 要素&#40;XMLA&#41;](../xml-elements-commands/restore-element-xmla.md)   
 [StorageLocation 要素&#40;ASSL&#41;](../../scripting/properties/storagelocation-element-assl.md)   
 [Synchronize 要素&#40;XMLA&#41;](../xml-elements-commands/synchronize-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
