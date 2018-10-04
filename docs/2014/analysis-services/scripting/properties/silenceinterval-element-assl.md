---
title: SilenceInterval 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- SilenceInterval Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SilenceInterval
helpviewer_keywords:
- SilenceInterval element
ms.assetid: c22060a9-99ca-4b81-9df3-89b020b4d1d4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0a0bf34efb06c60358acacaef501e5dafef2095a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201462"
---
# <a name="silenceinterval-element-assl"></a>SilenceInterval 要素 (ASSL)
  インスタンスの最短時間を定義します[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]多次元 OLAP (MOLAP) イメージ作成プロセスを開始する前に一時停止します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ProactiveCaching>  
   ...  
   <SilenceInterval>...</SilenceInterval>  
   ...  
</ProactiveCaching>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|duration|  
|既定値|P0s|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`SilenceInterval`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ProactiveCaching>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
