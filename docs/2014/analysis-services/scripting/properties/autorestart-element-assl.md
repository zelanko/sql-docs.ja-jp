---
title: AutoRestart 要素 (ASSL) |Microsoft Docs
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
- AutoRestart Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AutoRestart
helpviewer_keywords:
- AutoRestart element
ms.assetid: 4c6a0e40-8e13-4d63-bf98-9470ffe95d02
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ecb6893c7c3e87c9e96890a917bbe8aad540433d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159103"
---
# <a name="autorestart-element-assl"></a>AutoRestart 要素 (ASSL)
  決定かどうかを[トレース](../objects/trace-element-assl.md)する場合、要素を自動的に再開する、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]サービスが停止して再起動します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Trace>  
   ...  
   <AutoRestart>...</AutoRestart>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|`False`|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[トレース](../objects/trace-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`AutoRestart`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Trace>します。  
  
## <a name="see-also"></a>参照  
 [要素をトレース&#40;ASSL&#41;](../collections/traces-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
