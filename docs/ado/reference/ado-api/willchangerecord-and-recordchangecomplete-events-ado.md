---
title: WillChangeRecord および RecordChangeComplete イベント (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- RecordChangeComplete
- Recordset::WillChangeRecord
- WillChangeRecord
- Recordset::RecordChangeComplete
helpviewer_keywords:
- WillChangeRecord event [ADO]
- recordchangecomplete event [ADO]
ms.assetid: cbc369fd-63af-4a7d-96ae-efa91b78ca69
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77d02d1a5b5d643c49fcbbd33057d6c709f1949a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="willchangerecord-and-recordchangecomplete-events-ado"></a>WillChangeRecord および RecordChangeComplete イベント (ADO)
**WillChangeRecord**でイベントが 1 つまたは複数のレコード (行) より前に呼び出される、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)を変更します。 **RecordChangeComplete**いずれかの後にイベントが呼び出されるかより多くのレコードを変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
WillChangeRecord adReason, cRecords, adStatus, pRecordset  
RecordChangeCompleteadReason, cRecords, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>パラメーター  
 *adReason*  
 [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md)このイベントの理由を指定する値。 その値を指定できます**adRsnAddNew**、 **adRsnDelete**、 **adRsnUpdate**、 **adRsnUndoUpdate**、 **adRsnUndoAddNew**、 **adRsnUndoDelete**、または**adRsnFirstChange**です。  
  
 *cRecords*  
 A**長い**(影響) を変更するレコードの数を示す値。  
  
 *pError*  
 [エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。 場合に発生したエラーを説明の値*adStatus*は**adStatusErrorsOccurred**です。 それ以外の場合、設定されていません。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)状態値。  
  
 ときに**WillChangeRecord**が呼び出されると、このパラメーターに設定されている**adStatusOK**イベントの原因となった操作が成功した場合。 設定されている**adStatusCantDeny**場合、このイベントは、保留中の操作の取り消しを要求できません。  
  
 ときに**RecordChangeComplete**が呼び出されると、このパラメーターに設定されている**adStatusOK**イベントの原因となった操作が成功した場合または**adStatusErrorsOccurred**場合操作に失敗しました。  
  
 前に**WillChangeRecord**戻り値は、このパラメーターに設定する**adStatusCancel**このイベントが発生したか、このパラメーターに設定する操作のキャンセルを要求**adStatusUnwantedEvent**を後続の通知を防ぐためにします。  
  
 前に**RecordChangeComplete**戻り値は、このパラメーターに設定する**adStatusUnwantedEvent**を後続の通知を防ぐためにします。  
  
 *pRecordset*  
 A **Recordset**オブジェクト。 **Recordset**のこのイベントが発生しました。  
  
## <a name="remarks"></a>解説  
 A **WillChangeRecord**または**RecordChangeComplete** 、以下の理由により行の最初の変更されたフィールドのイベントが発生する**Recordset**操作: [更新](../../../ado/reference/ado-api/update-method.md)、[削除](../../../ado/reference/ado-api/delete-method-ado-recordset.md)、[ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)、 [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)、および[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)です。 値、 **Recordset** [カーソル。](../../../ado/reference/ado-api/cursortype-property-ado.md)どのような操作が発生するイベントの原因を判断します。  
  
 中に、 **WillChangeRecord**イベント、 **Recordset** [フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティに設定されている**adFilterAffectedRecords**です。 イベントを処理中にこのプロパティを変更することはできません。  
  
 設定する必要があります、 **adStatus**パラメーターを**adStatusUnwantedEvent**可能性のある各の**adReason**値を含む任意のイベントのイベント通知を完全に停止するには**adReason**パラメーター。  
  
## <a name="see-also"></a>参照  
 [ADO イベント モデルの例 (vc++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)
