---
title: WillChangeRecordset および RecordsetChangeComplete イベント (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset::RecordsetChangeComplete
- RecordsetChangeComplete
- Recordset::WillChangeRecordset
- WillChangeRecordset
helpviewer_keywords:
- RecordsetChangeComplete event [ADO]
- WillChangeRecordset event [ADO]
ms.assetid: d5d44659-e0d9-46d9-a297-99c43555082f
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9cacdf90f02fed37f15b5c76cfef9feb9275f5ff
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="willchangerecordset-and-recordsetchangecomplete-events-ado"></a>WillChangeRecordset および RecordsetChangeComplete イベント (ADO)
**WillChangeRecordset**イベントが保留中の操作を変更する前に呼び出されます、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。 **RecordsetChangeComplete**イベントが呼び出された後、**レコード セット**が変更されました。  
  
## <a name="syntax"></a>構文  
  
```  
  
WillChangeRecordset adReason, adStatus, pRecordset  
RecordsetChangeComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>パラメーター  
 *adReason*  
 [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md)このイベントの理由を指定する値。 その値を指定できます**adRsnRequery**、 **adRsnResynch**、 **adRsnClose**、 **adRsnOpen**です。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)状態値。  
  
 ときに**WillChangeRecordset**が呼び出されると、このパラメーターに設定されている**adStatusOK**イベントの原因となった操作が成功した場合。 設定されている**adStatusCantDeny**場合、このイベントは、保留中の操作の取り消しを要求できません。  
  
 ときに**RecordsetChangeComplete**が呼び出されると、このパラメーターに設定されている**adStatusOK**イベントの原因となった操作が成功した場合**adStatusErrorsOccurred**場合操作は失敗、または**adStatusCancel**操作は、承認済みに関連付けられている場合**WillChangeRecordset**イベントが取り消されました。  
  
 前に**WillChangeRecordset**戻り値は、このパラメーターに設定する**adStatusCancel**保留中の操作のキャンセルを要求またはそれ以降を防ぐために adStatusUnwantedEvent にこのパラメーターを設定通知です。  
  
 前に**WillChangeRecordset**または**RecordsetChangeComplete**戻り値は、このパラメーターに設定する**adStatusUnwantedEvent**を後続の通知を防ぐためにします。  
  
 *pError*  
 [エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。 場合に発生したエラーを説明の値*adStatus*は**adStatusErrorsOccurred**です。 それ以外の場合、設定されていません。  
  
 *pRecordset*  
 A **Recordset**オブジェクト。 **Recordset**のこのイベントが発生しました。  
  
## <a name="remarks"></a>解説  
 A **WillChangeRecordset**または**RecordsetChangeComplete**ので、イベントが発生する、 **Recordset** [Requery](../../../ado/reference/ado-api/requery-method.md)または[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドです。  
  
 プロバイダーは、ブックマークをサポートしていない場合、 **RecordsetChange**イベント通知がプロバイダーから新しい行が取得されるたびに発生します。 このイベントの頻度によって異なります、 **RecordsetCacheSize**プロパティです。  
  
 設定する必要があります、 **adStatus**パラメーターを**adStatusUnwantedEvent**可能性のある各の**adReason**値を含む任意のイベントのイベント通知を完全に停止するには**adReason**パラメーター。  
  
## <a name="see-also"></a>参照  
 [ADO イベント モデルの例 (vc++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)
