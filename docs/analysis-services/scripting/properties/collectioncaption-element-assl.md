---
title: "CollectionCaption 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 33929373-11df-4f89-8d2e-d63923c44f53
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f241e60e8861974245c0f8b23ac6c291f29d8b3c
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="collectioncaption-element-assl"></a>CollectionCaption 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
親要素の複数形の名前を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<RelationshipEndTranslation>  
   <CollectionCaption>...</CollectionCaption>  
</RelationshipEndTranslation>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1: 省略可能な要素で、出現する場合は 1 回だけ出現します。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[RelationshipEndTranslation](../../../analysis-services/scripting/data-type/relationshipendtranslation-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**CollectionCaption**分析管理オブジェクト (AMO) オブジェクト モデルは t:microsoft.analysisservices.relationshipendtranslation です。  
  
  
