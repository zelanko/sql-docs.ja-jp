---
title: EventReasonEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EventReasonEnum
helpviewer_keywords:
- EventReasonEnum enumeration [ADO]
ms.assetid: 7d4a5496-ec2d-4936-b36a-7049a82be4b4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 743e36e379760cb2c148c5484bb7b49b08d1d27e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644645"
---
# <a name="eventreasonenum"></a>EventReasonEnum
イベントの発生の原因となった理由を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adRsnAddNew**|1|操作は、新しいレコードを追加します。|  
|**adRsnClose**|9|操作の終了、 **Recordset**します。|  
|**adRsnDelete**|2|操作は、レコードを削除します。|  
|**adRsnFirstChange**|11|操作は、レコードに、最初の変更を加えた。|  
|**adRsnMove**|10|操作内のレコード ポインターを移動する、 **Recordset**します。|  
|**adRsnMoveFirst**|12|操作の最初のレコードをレコード ポインターを移動する、 **Recordset**します。|  
|**adRsnMoveLast**|15|操作は、最後のレコードをレコード ポインターを移動、 **Recordset**します。|  
|**adRsnMoveNext**|13|操作は次のレコードをレコード ポインターを移動、 **Recordset**します。|  
|**adRsnMovePrevious**|14|操作の前のレコードをレコード ポインターを移動する、 **Recordset**します。|  
|**adRsnRequery**|7|クエリを再実行する操作、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)します。|  
|**adRsnResynch**|8|操作が再同期、 **Recordset**データベースとします。|  
|**adRsnUndoAddNew**|5|新しいレコードの追加が取り消されました。|  
|**adRsnUndoDelete**|6|レコードの削除が取り消されました。|  
|**adRsnUndoUpdate**|4|レコードの更新が取り消されました。|  
|**adRsnUpdate**|3|操作は、既存のレコードを更新します。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.EventReason.ADDNEW|  
|AdoEnums.EventReason.CLOSE|  
|AdoEnums.EventReason.DELETE|  
|AdoEnums.EventReason.FIRSTCHANGE|  
|AdoEnums.EventReason.MOVE|  
|AdoEnums.EventReason.MOVEFIRST|  
|AdoEnums.EventReason.MOVELAST|  
|AdoEnums.EventReason.MOVENEXT|  
|AdoEnums.EventReason.MOVEPREVIOUS|  
|AdoEnums.EventReason.REQUERY|  
|AdoEnums.EventReason.RESYNCH|  
|AdoEnums.EventReason.UNDOADDNEW|  
|AdoEnums.EventReason.UNDODELETE|  
|AdoEnums.EventReason.UNDOUPDATE|  
|AdoEnums.EventReason.UPDATE|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[WillChangeRecord および RecordChangeComplete イベント (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|[WillChangeRecordset および RecordsetChangeComplete イベント (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|  
|[WillMove および MoveComplete イベント (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)||
