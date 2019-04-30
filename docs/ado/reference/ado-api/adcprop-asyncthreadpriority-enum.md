---
title: ADCPROP_ASYNCTHREADPRIORITY_ENUM | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM
helpviewer_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM [ADO]
ms.assetid: f0965617-17d8-41e0-98d0-f824274735a6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0b9d4e0e6f844ef2dda18e95aadfcf3b910995d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63065307"
---
# <a name="adcpropasyncthreadpriorityenum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
RDS の[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト、データを取得する非同期のスレッドの実行の優先順位を指定します。  
  
 これらの定数を使用して、**レコード セット**"**バック グラウンド スレッド優先順位**"動的プロパティを ADO、OLE DB の動的プロパティのインデックスで参照されていると記載されて、 [OLE DB 用の Microsoft カーソル サービス](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)ドキュメント。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adPriorityAboveNormal**|4|通常と最高の優先順位を設定します。|  
|**adPriorityBelowNormal**|2|最も低いと通常の優先順位を設定します。|  
|**adPriorityHighest**|5|指定できる最大の優先順位を設定します。|  
|**AdPriorityLowest**|1|最下位の優先順位を設定します。|  
|**adPriorityNormal**|3|優先度を normal に設定します。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.AdcPropAsyncThreadPriority.ABOVENORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.BELOWNORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.HIGHEST|  
|AdoEnums.AdcPropAsyncThreadPriority.LOWEST|  
|AdoEnums.AdcPropAsyncThreadPriority.NORMAL|
