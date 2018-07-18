---
title: Algorithm 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Algorithm Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Algorithm
helpviewer_keywords:
- Algorithm element
ms.assetid: 188bf7ce-c5c9-406a-af75-5a026c92a569
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 38ca7406538a81768e8cab8d0c24142c8105c963
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218492"
---
# <a name="algorithm-element-assl"></a>Algorithm 要素 (ASSL)
  使用されるアルゴリズムを定義、 [MiningModel](../objects/miningmodel-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningModel>  
      ...  
   <Algorithm>...</Algorithm>  
      ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningModel](../objects/miningmodel-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Algorithm` 要素の値は、アルゴリズムを識別する文字列です。 たとえば、文字列になります*Microsoft_Naive_Bayes*、 *Microsoft_Decision_Trees*、または*Microsoft_Clustering します。* 文字列によって指定されたアルゴリズムを識別する[!INCLUDE[msCoName](../../../includes/msconame-md.md)]と、ユーザーが指定したカスタム アルゴリズム。 使用可能な値の`Algorithm`の SERVICE_NAME 列から要素を取得できる、 [DMSCHEMA_MINING_SERVICES](../../schema-rowsets/data-mining/dmschema-mining-services-rowset.md)スキーマ行セット。  
  
 親に対応する要素`Algorithm`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningModel>します。 AMO オブジェクト モデルの中で、関連性の高い要素は <xref:Microsoft.AnalysisServices.MiningModelAlgorithms> です。  
  
## <a name="see-also"></a>参照  
 [AlgorithmParameter 要素&#40;ASSL&#41;](../objects/algorithmparameter-element-assl.md)   
 [AlgorithmParameters 要素&#40;ASSL&#41;](../collections/algorithmparameters-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
