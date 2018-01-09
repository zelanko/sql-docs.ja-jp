---
title: "CacheMode 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: CacheMode Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: CacheMode element
ms.assetid: bfb8f7bb-ccd3-4dfe-a36a-1cea15edfe40
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 81eecc814c5c891e26ed3db80deb0b3163db7e05
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="cachemode-element-assl"></a>CacheMode 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]マイニング構造の処理中に取得されたトレーニング データを使用するキャッシュ メカニズムを決定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningStructure>  
   ...  
   <CacheMode>...</CacheMode>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*KeepTrainingCases*|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*KeepTrainingCases*|トレーニング ケースは処理中および処理後にキャッシュされます。|  
|*ClearAfterProcessing*|トレーニング ケースは処理中にキャッシュされますが、処理後に削除されます。|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**CacheMode**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MiningStructure>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
