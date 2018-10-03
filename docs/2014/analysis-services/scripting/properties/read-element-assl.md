---
title: 要素 (ASSL) の読み取り |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Read Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Read element
ms.assetid: 2e2c1173-72ca-4e8a-a6cd-fd348ef96d78
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2f950d35e74a64b75ec239c7d35ba31660ec8f08
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157382"
---
# <a name="read-element-assl"></a>Read 要素 (ASSL)
  データまたはメタデータの読み取りができるかどうかを決定を指定した[CubeDimensionPermission](../data-type/permission-data-type-assl.md)または[権限](../data-type/permission-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeDimensionPermission> <!-- or Permission -->  
   ...  
   <Read>...</Read>  
   ...  
</CubeDimensionPermission>  
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
|親要素|[CubeDimensionPermission](../objects/cubepermission-element-assl.md)、[アクセス許可](../data-type/permission-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*なし*|親オブジェクトのデータまたはメタデータへのアクセスは許可されていません。|  
|*許可されています。*|親オブジェクトのデータおよびメタデータへの読み取りアクセスが許可されています。|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`Read`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.CubeDimensionPermission>と<xref:Microsoft.AnalysisServices.Permission>します。  
  
## <a name="see-also"></a>参照  
 [キューブ要素&#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [ディメンション要素&#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [CubePermission 要素&#40;ASSL&#41;](../objects/cubepermission-element-assl.md)   
 [Permission データ型&#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
