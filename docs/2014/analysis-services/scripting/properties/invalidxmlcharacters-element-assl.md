---
title: InvalidXmlCharacters 要素 (ASSL) |Microsoft ドキュメント
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
- InvalidXmlCharacters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- InvalidXmlCharacters
helpviewer_keywords:
- InvalidXmlCharacters element
ms.assetid: 92b1210c-1075-4f2f-a2c4-dfdc6d7e5c05
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 19367018c772e4d512082a45a7a1b6e13e497f1d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173333"
---
# <a name="invalidxmlcharacters-element-assl"></a>InvalidXmlCharacters 要素 (ASSL)
  ソース データの有効でない XML 文字の処理方法を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataItem>  
   ...  
   <InvalidXmlCharacters>...</InvalidXmlCharacters>  
   ...  
</DataItem  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*保持します。*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*保持します。*|無効な XML 文字は保存されます。|  
|*削除*|無効な XML 文字は削除されます。|  
|*[置換]*|無効な XML 文字は疑問符 (?) に置き換えられます。|  
  
 許可される値に対応する列挙`InvalidXmlCharacters`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.InvalidXmlCharacters>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  