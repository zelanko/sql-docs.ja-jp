---
title: EventReasonEnum | Microsoft Docs
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- EventReasonEnum
helpviewer_keywords:
- EventReasonEnum enumeration [ADO]
ms.assetid: 7d4a5496-ec2d-4936-b36a-7049a82be4b4
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a49c3aac3b2f37421df9a68ae01b16770c696993
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="eventreasonenum"></a>EventReasonEnum
イベントを発生の原因となった理由を指定します。  
  
|定数|[値]|Description|  
|--------------|-----------|-----------------|  
|**adRsnAddNew**|1|操作は、新しいレコードを追加します。|  
|**adRsnClose**|9|操作の終了、 **Recordset**です。|  
|**adRsnDelete**|2|操作は、レコードを削除します。|  
|**adRsnFirstChange**|11|操作では、最初の変更を行い、レコードにします。|  
|**adRsnMove**|10|操作内でレコード ポインターを移動する、 **Recordset**です。|  
|**adRsnMoveFirst**|12|操作の最初のレコードをレコード ポインターを移動する、 **Recordset**です。|  
|**adRsnMoveLast**|15|操作の最後のレコードをレコード ポインターを移動する、 **Recordset**です。|  
|**adRsnMoveNext**|13|操作は、次のレコードにレコード ポインターを移動、 **Recordset**です。|  
|**adRsnMovePrevious**|14|操作の前のレコードをレコード ポインターを移動する、 **Recordset**です。|  
|**adRsnRequery**|7|クエリ操作、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。|  
|**adRsnResynch**|8|操作を再同期、 **Recordset**データベースとします。|  
|**adRsnUndoAddNew**|5|新しいレコードの追加が取り消されました。|  
|**adRsnUndoDelete**|6|レコードの削除が取り消されました。|  
|**adRsnUndoUpdate**|4|レコードの更新が取り消されました。|  
|**adRsnUpdate**|3|操作は、既存のレコードを更新します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
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
