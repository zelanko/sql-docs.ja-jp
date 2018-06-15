---
title: WillMove および MoveComplete イベント (ADO) |Microsoft ドキュメント
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
- Recordset::MoveComplete
- WillMove
- MoveComplete
- Recordset::WillMove
helpviewer_keywords:
- MoveComplete event [ADO]
- WillMove event [ADO]
ms.assetid: 1a3d1042-4f30-4526-a0c7-853c242496db
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30394da01328ad1f533834081cd33f6620c54dd4
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282891"
---
# <a name="willmove-and-movecomplete-events-ado"></a>WillMove および MoveComplete イベント (ADO)
**WillMove**イベントが保留中の操作が現在の位置を変更する前に呼び出されます、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。 **MoveComplete**イベントは、現在の位置の後に呼び出されます、 **Recordset**変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
WillMove adReason, adStatus, pRecordset  
MoveComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>パラメーター  
 *adReason*  
 [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md)このイベントの理由を指定する値。 その値を指定できます**adRsnMoveFirst**、 **adRsnMoveLast**、 **adRsnMoveNext**、 **adRsnMovePrevious**、 **adRsnMove**、または**adRsnRequery**です。  
  
 *pError*  
 [エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。 場合に発生したエラーを説明の値*adStatus*は**adStatusErrorsOccurred**です。 それ以外の場合、パラメーターが設定されていません。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)状態値。  
  
 ときに**WillMove**が呼び出されると、このパラメーターに設定されている**adStatusOK**イベントの原因となった操作が成功した場合。 設定されている**adStatusCantDeny**場合、このイベントは、保留中の操作の取り消しを要求できません。  
  
 ときに**MoveComplete**が呼び出されると、このパラメーターに設定されている**adStatusOK**イベントの原因となった操作が成功した場合または**adStatusErrorsOccurred**場合、操作に失敗しました。  
  
 前に**WillMove**戻り値は、このパラメーターに設定する**adStatusCancel**保留中の操作の取り消しを要求するか、このパラメーターに設定する**adStatusUnwantedEvent**その後の通知を防ぐ。  
  
 前に**MoveComplete**戻り値は、このパラメーターに設定する**adStatusUnwantedEvent**を後続の通知を防ぐためにします。  
  
 *pRecordset*  
 A [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。 **Recordset**のこのイベントが発生しました。  
  
## <a name="remarks"></a>コメント  
 A **WillMove**または**MoveComplete**イベントは、以下の理由により発生する可能性があります**Recordset**操作:[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)、 [を移動](../../../ado/reference/ado-api/move-method-ado.md)、 [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)、 [MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)、 [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)、 [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)、 [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)、および[Requery](../../../ado/reference/ado-api/requery-method.md)です。 次のプロパティによりこれらのイベントが発生する:[フィルター](../../../ado/reference/ado-api/filter-property.md)、[インデックス](../../../ado/reference/ado-api/index-property.md)、[ブックマーク](../../../ado/reference/ado-api/bookmark-property-ado.md)、[と、AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)、および[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)です。 これらのイベントは、子の場合にも発生する**Recordset**が**レコード セット**接続されているイベントと、親**レコード セット**が移動します。  
  
 設定する必要があります、 *adStatus*パラメーターを**adStatusUnwantedEvent**可能性のある各の*adReason*の任意のイベントのイベント通知を完全に停止するのには値を含まれています、 *adReason*パラメーター。  
  
## <a name="see-also"></a>参照  
 [ADO イベント モデルの例 (vc++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
