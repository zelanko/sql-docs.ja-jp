---
title: Write 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Write Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Write element
ms.assetid: d8f7a367-d7bf-4b40-acb4-19c8bc8c6c20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dd39e3354ee68a2e716e4cfbf50e41e371bf5303
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104252"
---
# <a name="write-element-assl"></a>Write 要素 (ASSL)
  データまたはメタデータを書き込みが可能かどうかを判断します、指定された[CubeDimensionPermission](../data-type/permission-data-type-assl.md)または[権限](../data-type/permission-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeDimensionPermission> <!-- or Permission -->  
   ...  
   <Write>...</Write>  
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
|*許可されています。*|親オブジェクトのデータおよびメタデータへの書き込みアクセスが許可されています。|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`Write`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.CubeDimensionPermission>と<xref:Microsoft.AnalysisServices.Permission>します。  
  
## <a name="see-also"></a>参照  
 [キューブ要素&#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [ディメンション要素&#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
