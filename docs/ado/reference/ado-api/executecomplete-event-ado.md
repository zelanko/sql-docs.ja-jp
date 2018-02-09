---
title: "ExecuteComplete イベント (ADO) |Microsoft ドキュメント"
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
- Connection::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- ExecuteComplete event [ADO]
ms.assetid: 62470d42-e511-494c-bec4-ad4591734b7b
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bda38ed41e57c84d629ff6f301575e963d893f5e
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="executecomplete-event-ado"></a>ExecuteComplete イベント (ADO)
**ExecuteComplete**コマンドの実行が完了した後にイベントが呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
ExecuteComplete RecordsAffected, pError, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>パラメーター  
 *RecordsAffected*  
 A**長い**コマンドによって影響を受けたレコードの数を示す値。  
  
 *pError*  
 [エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。 場合に発生したエラーを説明の値**adStatus**は**adStatusErrorsOccurred**です。 それ以外の場合、設定されていません。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)状態値。 このイベントが呼び出されると、このパラメーターに設定されている**adStatusOK**イベントの原因となった操作が成功した場合または**adStatusErrorsOccurred**場合は、操作に失敗しました。  
  
 このイベントが返される前に、このパラメーターを設定**adStatusUnwantedEvent**を後続の通知を防ぐためにします。  
  
 *pCommand*  
 [コマンド](../../../ado/reference/ado-api/command-object-ado.md)が実行されたオブジェクト。 含まれています、**コマンド**オブジェクトを呼び出すときにも**Connection.Execute**または**Recordset.Open**明示的に作成することがなく、**コマンド**、どのような場合、**コマンド**オブジェクトは ADO によって内部的に作成します。  
  
 *pRecordset*  
 A [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)実行されるコマンドの結果であるオブジェクト。 これは、 **Recordset**空にすることがあります。 このイベント ハンドラー内から、このレコード セット オブジェクトは破棄しないでください。 これを行う場合は、ADO が存在しなくなったオブジェクトにアクセスしようとするときに、アクセス違反を恐れはします。  
  
 *pConnection*  
 A[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。 操作の実行対象で接続します。  
  
## <a name="remarks"></a>解説  
 **ExecuteComplete**ためにイベントが発生する、**接続**。[実行](../../../ado/reference/ado-api/execute-method-ado-connection.md)、**コマンド**。[実行](../../../ado/reference/ado-api/execute-method-ado-command.md)、**レコード セット**。[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)、**レコード セット**。[Requery](../../../ado/reference/ado-api/requery-method.md)、または**レコード セット**。[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)メソッドです。  
  
## <a name="see-also"></a>参照  
 [ADO イベント モデルの例 (vc++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)
