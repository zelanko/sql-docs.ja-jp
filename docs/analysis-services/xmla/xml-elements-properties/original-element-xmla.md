---
title: "Original 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
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
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 75a0345459be5e065a7a737b8036e505f799d549
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="original-element-xmla"></a>Original 要素 (XMLA)
  によって使用される元のファイル システム ストレージ場所を含む、[フォルダー](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)要素。  
  
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
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[フォルダー](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **元**要素には値に置き換えられますへの UNC パスが含まれています、[新規](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md)親に含まれる要素**フォルダー**復元のすべてのオブジェクトの要素または同期中にはそれぞれ、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)または[同期](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)コマンド。 この要素の値がの値と比較して、 [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md)各キューブ、メジャー グループ、またはパーティションの要素と一致するものが見つかった場合の値、**新規**要素を使用して、を更新**StorageLocation**復元または同期中にオブジェクトの。  
  
 バックアップと復元のオブジェクトの詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期 (&) #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

