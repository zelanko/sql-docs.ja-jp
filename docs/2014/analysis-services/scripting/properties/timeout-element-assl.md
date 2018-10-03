---
title: Timeout 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Timeout Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Timeout
helpviewer_keywords:
- Timeout element
ms.assetid: 7694872b-bd05-459f-b5dc-3cfbd92a9664
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 051da6eafdd75cc8c3a041dc6ec9115dd962363d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48058812"
---
# <a name="timeout-element-assl"></a>Timeout 要素 (ASSL)
  データの取得を試みたときにタイムアウトをレポートするまでの時間を指定します (秒単位)。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataSource>  
   ...  
   <Timeout>...</Timeout>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Duration|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataSource](../objects/datasource-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>Remarks  
 親に対応する要素`Timeout`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DataSource>します。  
  
## <a name="see-also"></a>関連項目  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
