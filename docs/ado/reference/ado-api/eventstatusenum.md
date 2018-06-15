---
title: EventStatusEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EventStatusEnum
helpviewer_keywords:
- EventStatusEnum enumeration [ADO]
ms.assetid: ebfd4cda-4017-4873-9d28-38b1c7db12a8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 20a5582eb8c8744e5d8a065c5fa8ce29c0d4b793
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278061"
---
# <a name="eventstatusenum"></a>EventStatusEnum
イベントの実行の現在の状態を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adStatusCancel**|4|イベントが発生する原因となった操作の取り消しを要求します。|  
|**adStatusCantDeny**|3|操作が保留中の操作の取り消しを要求できないことを示します。|  
|**adStatusErrorsOccurred**|2|エラーまたはエラーのため、イベントの原因となった操作が失敗したことを示します。|  
|**adStatusOK**|1|イベントの原因となった操作が成功したことを示します。|  
|**adStatusUnwantedEvent**|5|イベント メソッドの実行が完了する前に、後続の通知をできないようにします。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.EventStatus.CANCEL|  
|AdoEnums.EventStatus.CANTDENY|  
|AdoEnums.EventStatus.ERRORSOCCURRED|  
|AdoEnums.EventStatus.OK|  
|AdoEnums.EventStatus.UNWANTEDEVENT|  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[BeginTransComplete、CommitTransComplete、および RollbackTransComplete イベント (ADO)](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|[ConnectComplete および Disconnect イベント (ADO)](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|[EndOfRecordset イベント (ADO)](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|  
|[ExecuteComplete イベント (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)|[FetchComplete イベント (ADO)](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|[InfoMessage イベント (ADO)](../../../ado/reference/ado-api/infomessage-event-ado.md)|  
|[WillChangeField および FieldChangeComplete イベント (ADO)](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|[WillChangeRecord および RecordChangeComplete イベント (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[WillChangeRecordset および RecordsetChangeComplete イベント (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[WillConnect イベント (ADO)](../../../ado/reference/ado-api/willconnect-event-ado.md)|[WillExecute イベント (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|[WillMove および MoveComplete イベント (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|
