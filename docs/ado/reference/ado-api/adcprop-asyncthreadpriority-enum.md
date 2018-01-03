---
title: "ADCPROP_ASYNCTHREADPRIORITY_ENUM |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: ADCPROP_ASYNCTHREADPRIORITY_ENUM
helpviewer_keywords: ADCPROP_ASYNCTHREADPRIORITY_ENUM [ADO]
ms.assetid: f0965617-17d8-41e0-98d0-f824274735a6
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8a03809de8f86cf4ece91be598a71cd24b3ad9d7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="adcpropasyncthreadpriorityenum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
RDS の[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト、データを取得する非同期スレッドの実行の優先順位を指定します。  
  
 これらの定数を使用して、 **Recordset** "**バック グラウンド スレッドの優先順位**"動的なプロパティを ADO、OLE DB プロパティの動的インデックス内で参照されに記載されていますが、 [OLE DB 用の Microsoft カーソル サービス](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)ドキュメント。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adPriorityAboveNormal**|4|標準と最高の優先順位を設定します。|  
|**adPriorityBelowNormal**|2|最下位と通常の優先順位を設定します。|  
|**adPriorityHighest**|5|可能な最高レベルを優先順位を設定します。|  
|**AdPriorityLowest**|@shouldalert|最下位に優先順位を設定します。|  
|**adPriorityNormal**|3|優先度を normal に設定します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.AdcPropAsyncThreadPriority.ABOVENORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.BELOWNORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.HIGHEST|  
|AdoEnums.AdcPropAsyncThreadPriority.LOWEST|  
|AdoEnums.AdcPropAsyncThreadPriority.NORMAL|
