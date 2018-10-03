---
title: MergePartitions 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MergePartitions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#MergePartitions
- microsoft.xml.analysis.mergepartitions
- urn:schemas-microsoft-com:xml-analysis#MergePartitions
helpviewer_keywords:
- MergePartitions command
ms.assetid: cf538189-0629-49b3-8e01-32afba7b020d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fbae4ca1baa8908f172e385d3bb44e7b6b2b3281
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48156459"
---
# <a name="mergepartitions-element-xmla"></a>MergePartitions 要素 (XMLA)
  対象パーティションに 1 つまたは複数のソース パーティションのデータをマージし、し、基になるパーティションを削除します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <MergePartitions>  
      <Sources>...</Sources>  
      <Target>...</Target>  
   </MergePartitions>  
</Command>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../xml-elements-properties/command-element-xmla.md)|  
|子要素|[ソース](../xml-elements-properties/sources-element-xmla.md)、[ターゲット](../xml-elements-properties/target-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Sources` および `Target` 要素内のすべてのオブジェクト参照は、同じメジャー グループ内の別個のパーティションを指している必要があります。 そうでない場合、エラーが発生します。  
  
## <a name="see-also"></a>参照  
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
