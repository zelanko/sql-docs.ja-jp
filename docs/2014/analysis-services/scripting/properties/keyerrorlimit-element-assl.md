---
title: KeyErrorLimit 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- KeyErrorLimit Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyErrorLimit
helpviewer_keywords:
- KeyErrorLimit element
ms.assetid: c91d3bd8-2ad7-416f-a860-2599e4a4dbee
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 42c796878560bdc905b40e61e18d67ec075810da
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48225982"
---
# <a name="keyerrorlimit-element-assl"></a>KeyErrorLimit 要素 (ASSL)
  処理時に許容可能なエラーの数を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyErrorLimit>...</KeyErrorLimit>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Long|  
|既定値|`0`|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`KeyErrorLimit`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ErrorConfiguration>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
