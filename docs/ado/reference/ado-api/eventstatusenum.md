---
title: "EventStatusEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- EventStatusEnum
helpviewer_keywords:
- EventStatusEnum enumeration [ADO]
ms.assetid: ebfd4cda-4017-4873-9d28-38b1c7db12a8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2e0b963373521b7d981e192dbbfc94d5fe008bf6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="eventstatusenum"></a>EventStatusEnum
イベントの実行の現在の状態を指定します。  
  
|定数|値|Description|  
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
|[BeginTransComplete、CommitTransComplete、および RollbackTransComplete イベント (ADO)](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|[ConnectComplete し、切断イベント (ADO)](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|[EndOfRecordset イベント (ADO)](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|  
|[ExecuteComplete イベント (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)|[FetchComplete イベント (ADO)](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|[InfoMessage イベント (ADO)](../../../ado/reference/ado-api/infomessage-event-ado.md)|  
|[WillChangeField および FieldChangeComplete イベント (ADO)](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|[WillChangeRecord および RecordChangeComplete イベント (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[WillChangeRecordset および RecordsetChangeComplete イベント (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[WillConnect イベント (ADO)](../../../ado/reference/ado-api/willconnect-event-ado.md)|[アクティビ ティー イベント (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|[WillMove および MoveComplete イベント (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|

