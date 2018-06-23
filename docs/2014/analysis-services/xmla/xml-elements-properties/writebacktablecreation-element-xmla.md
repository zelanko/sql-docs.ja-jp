---
title: WritebackTableCreation 要素 (XMLA) |Microsoft ドキュメント
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
- WritebackTableCreation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#WritebackTableCreation
- microsoft.xml.analysis.writebacktablecreation
- http://schemas.microsoft.com/analysisservices/2003/engine#WritebackTableCreation
helpviewer_keywords:
- WritebackTableCreation element
ms.assetid: e9579d63-e28c-4d4e-9f4a-21c5da24c276
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 95b9639b34002aa69366f87cac48427624f7d0dd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164356"
---
# <a name="writebacktablecreation-element-xmla"></a>WritebackTableCreation 要素 (XMLA)
  中に、書き戻しテーブルを作成するかどうかを決定、[プロセス](../xml-elements-commands/process-element-xmla.md)操作します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Process>  
...  
   <WritebackTableCreation>...</WritebackTableCreation>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[処理]](../xml-elements-commands/process-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 Analysis Services インスタンス上のオブジェクトで使用できる処理オプションの詳細については、次を参照してください。[多次元モデル オブジェクトの処理](../../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)です。  
  
 `WritebackTableCreation` 要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*作成*|既存の書き戻しテーブルが存在しない場合、新しい書き戻しテーブルを作成します。 書き戻しテーブルが既に存在する場合、エラーが発生します。|  
|*[Createalways]*|既存の書き戻しテーブルを上書きして、新しい書き戻しテーブルを作成します。|  
|*UseExisting*|既に存在する場合は、既存の書き戻しテーブルを使用します。 存在しない場合は、エラーが発生します。|  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  