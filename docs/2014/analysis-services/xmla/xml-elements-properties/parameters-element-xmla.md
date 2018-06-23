---
title: Parameters 要素 (XMLA) |Microsoft ドキュメント
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
- Parameters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Parameters
- urn:schemas-microsoft-com:xml-analysis#Parameters
- microsoft.xml.analysis.parameters
helpviewer_keywords:
- Parameters element
ms.assetid: d46454a1-a1d1-4aa8-95ea-54be22a53e83
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 63d50c1b57691a9b4cdb76adb9edaa202388d15e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085954"
---
# <a name="parameters-element-xmla"></a>Parameters 要素 (XMLA)
  コレクションを格納[パラメーター](parameter-element-xmla.md)によって使用される要素、 [Execute](../xml-elements-methods-execute.md)メソッドです。  
  
 **Namespace:** `urn:schemas-microsoft-com:xml-analysis`  
  
## <a name="syntax"></a>構文  
  
```  
  
<Execute>  
...  
   <Parameters>  
      <Parameter>...</Parameter>  
   </Parameters>  
...  
</Execute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[実行](../xml-elements-methods-execute.md)|  
|子要素|[パラメーター](parameter-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 などのいくつかの XML for Analysis (XMLA) コマンド、[プロセス](../xml-elements-commands/process-element-xmla.md)コマンド、追加情報が必要になることができます。 `Parameters` 要素は、XMLA コマンドで使用するための追加情報 (チャンクされた情報を含む) を提供するメカニズムとなります。  
  
 XMLA コマンドが `Parameters` 要素を使用しない場合、`Execute` メソッド呼び出し時にこの要素を省略できます。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  