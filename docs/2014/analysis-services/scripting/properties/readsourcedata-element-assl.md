---
title: ReadSourceData 要素 (ASSL) |Microsoft Docs
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
- ReadSourceData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ReadSourceData element
ms.assetid: 7da4665a-fba3-4aae-8dee-678dc14d3b05
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 38e24d324a6f29b55cfb8bf0b55289e2139bfb85
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194192"
---
# <a name="readsourcedata-element-assl"></a>ReadSourceData 要素 (ASSL)
  一意の名前が決定内に含まれる階層に対して生成される、 [CubePermission](../objects/cubepermission-element-assl.md)します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubePermission>  
   ...  
   <ReadSourceData>...</ReadSourceData>  
   ...  
</CubePermission>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*なし*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubePermission](../objects/cubepermission-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*なし*|計算パス 0 で使用可能なデータへのアクセスは許可されていません。|  
|*許可されています。*|計算パス 0 で使用可能なデータへのアクセスは許可されています。|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`ReadSourceData`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.CubePermission>します。  
  
## <a name="see-also"></a>参照  
 [キューブ要素&#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [ディメンション要素&#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
