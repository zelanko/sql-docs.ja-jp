---
title: Usage 要素 (MiningModelColumn) (ASSL) |Microsoft Docs
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
- Usage Element (MiningModelColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Usage
helpviewer_keywords:
- Usage element
ms.assetid: 435a857e-37a9-434e-9de1-354f1ff2993f
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a6767c4c5ac535ac603cc6182cbe645088c8ac05
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265303"
---
# <a name="usage-element-miningmodelcolumn-assl"></a>Usage 要素 (MiningModelColumn) (ASSL)
  について説明しますどの親に関連付けられている列[MiningStructure](../objects/miningstructure-element-assl.md)使用されます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningModelColumn>  
   ...  
   <Usage>...</Usage>  
   ...  
</MiningModelColumn>  
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
|親要素|[MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*[キー]*|列はキー列です。|  
|*入力*|列は入力列です。|  
|*Predict*|列は予測列です。|  
|*PredictOnly*|列は予測列のみです。|  
|*なし*|列はモデルによって使用されません。 **警告:** 使用状況の値が"None"の場合は、Analysis Services は値を送信サーバーに既定ではそのため、使用法 属性を要求/応答に含まれません。|  
  
 許容された値に対応する列挙体`Usage`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningModelColumnUsages>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
