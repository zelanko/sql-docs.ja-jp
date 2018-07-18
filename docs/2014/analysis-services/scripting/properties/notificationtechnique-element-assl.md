---
title: NotificationTechnique 要素 (ASSL) |Microsoft Docs
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
- NotificationTechnique Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- NotificationTechnique element
ms.assetid: 80c43de3-f147-4bf5-bb85-da9d182ce415
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e661b47c5344b0094daef53102aada68a6b6aad9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213912"
---
# <a name="notificationtechnique-element-assl"></a>NotificationTechnique 要素 (ASSL)
  指定するかどうか[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]または外部クライアント アプリケーションは、通知を処理します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ProactiveCachingBinding>  
   <NotificationTechnique>...</NotificationTechnique>  
</ProactiveCachingBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*クライアント*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ProactiveCachingBinding](../data-type/binding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*クライアント*|外部クライアント アプリケーションによって通知を処理します。|  
|*[サーバー]*|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって通知を処理します。|  
  
 親に対応する要素`NotificationTechnique`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ProactiveCachingBinding>します。  
  
 許容された値に対応する列挙体`NotificationTechnique`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.NotificationTechnique>します。  
  
## <a name="see-also"></a>参照  
 [ProactiveCachingBinding データ型&#40;ASSL&#41;](../data-type/binding-data-type-assl.md)  
  
  
