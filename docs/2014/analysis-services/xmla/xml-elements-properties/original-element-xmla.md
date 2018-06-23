---
title: Original 要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 63ee76cd3b476b3a8dbf45a50ad0f9d22a55e0fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176023"
---
# <a name="original-element-xmla"></a>Original 要素 (XMLA)
  によって使用される元のファイル システム ストレージ場所を含む、[フォルダー](folder-element-xmla.md)要素。  
  
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
 `Original`要素には値に置き換えられますへの UNC パスが含まれています、[新規](new-element-xmla.md)親に含まれる要素`Folder`復元または同期中に、それぞれ、オブジェクトのすべての要素、[復元](../xml-elements-commands/restore-element-xmla.md)または[同期](../xml-elements-commands/synchronize-element-xmla.md)コマンド。 この要素の値がの値と比較して、 [StorageLocation](../../scripting/properties/storagelocation-element-assl.md)各キューブ、メジャー グループ、またはパーティションの要素と一致するものが見つかった場合の値、`New`要素は、更新に使用される、`StorageLocation`の復元または同期中にオブジェクト。  
  
 バックアップと復元のオブジェクトの詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  