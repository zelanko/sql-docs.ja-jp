---
title: "MergePartitions 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MergePartitions Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#MergePartitions
- microsoft.xml.analysis.mergepartitions
- urn:schemas-microsoft-com:xml-analysis#MergePartitions
helpviewer_keywords:
- MergePartitions command
ms.assetid: cf538189-0629-49b3-8e01-32afba7b020d
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 11ce0aefda9de795ce3338be71e5314659786403
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="mergepartitions-element-xmla"></a>MergePartitions 要素 (XMLA)
  先パーティションに 1 つまたは複数のソース パーティションのデータをマージし、元のパーティションを削除します。  
  
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
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[ソース](../../../analysis-services/xmla/xml-elements-properties/sources-element-xmla.md)、[ターゲット](../../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 すべてのオブジェクトの参照、**ソース**と**ターゲット**要素は、同じメジャー グループ内の別個のパーティションを指す必要があります。 そうでない場合、エラーが発生します。  
  
## <a name="see-also"></a>参照  
 [コマンドと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
