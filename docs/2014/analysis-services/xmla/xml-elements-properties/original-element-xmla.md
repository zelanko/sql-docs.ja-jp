---
title: Original 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Original Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.original
- http://schemas.microsoft.com/analysisservices/2003/engine#Original
- urn:schemas-microsoft-com:xml-analysis#Original
helpviewer_keywords:
- Original element
ms.assetid: c98a3700-ac19-4341-85d9-5afedf662601
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b09f2388c47206b1b879a5c8dc98f10a28675342
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212072"
---
# <a name="original-element-xmla"></a>Original 要素 (XMLA)
  使用される元のファイル システム ストレージ場所が含まれています、[フォルダー](folder-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Folder>  
   ...  
   <Original>...</Original>  
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
 `Original`要素には値に置き換えられますへの UNC パスが含まれています、[新規](new-element-xmla.md)親に含まれる要素`Folder`要素すべてのオブジェクトを復元または同期される、実行時に、[復元](../xml-elements-commands/restore-element-xmla.md)または[同期](../xml-elements-commands/synchronize-element-xmla.md)コマンド。 この要素の値の値と比較されます、 [StorageLocation](../../scripting/properties/storagelocation-element-assl.md)各キューブ、メジャー グループ、またはパーティションの要素と、一致が見つかった場合の値、`New`要素を使用して、更新、`StorageLocation`の復元または同期中にオブジェクト。  
  
 バックアップと復元のオブジェクトの詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
