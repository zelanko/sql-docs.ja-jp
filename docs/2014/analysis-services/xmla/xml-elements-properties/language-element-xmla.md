---
title: Language 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Language Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Language
- microsoft.xml.analysis.language
- http://schemas.microsoft.com/analysisservices/2003/engine#Language
helpviewer_keywords:
- Language element
ms.assetid: cd998202-e43f-4c6c-8727-a15a76a520ea
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d247e81c19c3394ac46274ba775c1695741e00ff
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37205852"
---
# <a name="language-element-xmla"></a>Language 要素 (XMLA)
  親のロケール識別子 (LCID) を含む[翻訳](translation-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Translation>  
   ...  
   <Language>...</Language>  
   ...  
</Translation>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Integer|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[翻訳](translation-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Language` 要素は、親要素 `Translation` によって使用される LCID を指定します。これを使用して、`Name` または `Translation` コマンドの実行中に、指定された言語について親要素 `Insert` の `Update` 要素を属性メンバーに割り当てます。  
  
## <a name="see-also"></a>参照  
 [要素を挿入&#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [要素名を指定&#40;XMLA&#41;](name-element-xmla.md)   
 [Update 要素&#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
