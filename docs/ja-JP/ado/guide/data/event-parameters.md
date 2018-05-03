---
title: イベント パラメーター |Microsoft ドキュメント
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
helpviewer_keywords:
- Error parameter [ADO]
- Object parameter [ADO]
- Status parameter [ADO]
- events [ADO], parameters
- Reason parameter [ADO]
- event parameters [ADO]
ms.assetid: bd5c5afa-d301-4899-acda-40f98a6afa4d
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5351c36af4082c40be10b451122ca04101cf4b3d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="event-parameters"></a>イベントのパラメーター
すべてのイベント ハンドラーには、イベント ハンドラーを制御する状態パラメーターがあります。 完全なイベントは、このパラメーターは、イベントを生成する操作の成否を示すためにも使用します。 最も包括的なイベントには、発生したエラーと、操作を実行するために使用する ADO オブジェクトを参照する 1 つまたは複数のオブジェクトのパラメーターに関する情報を提供するエラー パラメーターもがあります。 たとえば、 [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)イベントにはオブジェクトのパラメーターが含まれています、**コマンド**、 **Recordset**、および**接続**オブジェクトイベントに関連付けられています。 Microsoft® Visual Basic® の次の例では、pCommand、pRecordset、およびを表す pConnection オブジェクトを参照できます、**コマンド**、 **Recordset**、および**接続**オブジェクトによって使用されている、 **Execute**メソッドです。  
  
```  
Private Sub connEvent_ExecuteComplete(ByVal RecordsAffected As Long, _  
     ByVal pError As ADODB.Error, _  
     adStatus As ADODB.EventStatusEnum, _  
     ByVal pCommand As ADODB.Command, _  
     ByVal pRecordset As ADODB.Recordset, _  
     ByVal pConnection As ADODB.Connection)  
```  
  
 を除き、**エラー**オブジェクト、同じパラメーターはイベントに渡されます。 これにより各保留中の操作で使用され、操作が完了できるかどうかを判断するオブジェクトを確認します。  
  
 一部のイベント ハンドラーが、*理由*パラメーターで、イベントが発生した理由に関する追加情報を提供します。 たとえば、 **WillMove**と**MoveComplete**ナビゲーション方法のいずれかのためのイベントが発生する可能性が (**MoveNext**、 **MovePrevious**など) が呼び出された、または再クエリの結果として。  
  
## <a name="status-parameter"></a>状態パラメーター  
 イベント ハンドラー ルーチンを呼び出したときに、*ステータス*パラメーターは、次の値のいずれかに設定します。  
  
|値|Description|  
|-----------|-----------------|  
|**adStatusOK**|完了イベントの両方に渡されます。 この値は、正常に完了したイベントの原因となった操作を意味します。|  
|**adStatusErrorsOccurred**|完全なイベントのみに渡されます。 この値は、イベントの原因となった操作が成功すると、できなかったかはイベントには、操作が取り消されましたことを示します。 チェック、*エラー*詳細パラメーター。|  
|**adStatusCantDeny**|イベントのみに渡されます。 この値はイベントによって、操作をキャンセルすることはできないことを意味します。 実行する必要があります。|  
  
 操作を続行する必要がありますはイベントで判断した場合のままにして、*ステータス*パラメーター。 状態の入力方向のパラメーター設定されていない限り、 **adStatusCantDeny**、ただし、変更することによって保留中の操作を取り消すことができます*ステータス*に**adStatusCancel**です。 操作に関連付けられている完全なイベントには、これを行うときにその*ステータス*パラメーターに設定**adStatusErrorsOccurred**です。 **エラー**完了イベントに渡されるオブジェクトの値を含む**adErrOperationCancelled**です。  
  
 不要になったイベントを処理する場合は、設定*ステータス*に**adStatusUnwantedEvent**アプリケーションでは、そのイベントの通知を受け取る不要になったとします。 ただし、理由の 1 つ以上のいくつかのイベントが発生することに注意してください。 その場合は、指定する必要があります**adStatusUnwantedEvent**の考えられる各理由。 たとえば、保留中の通知の受信を停止する**RecordChange**設定する必要があります、イベント、*ステータス*パラメーターを**adStatusUnwantedEvent**の**adRsnAddNew**、 **adRsnDelete**、 **adRsnUpdate**、 **adRsnUndoUpdate**、 **adRsnUndoAddNew**、**adRsnUndoDelete**、および**adRsnFirstChange**発生するとします。  
  
|値|Description|  
|-----------|-----------------|  
|**adStatusUnwantedEvent**|このイベント ハンドラーにさらに通知が発生しないことを要求します。|  
|**adStatusCancel**|実行する操作のキャンセルを要求します。|  
  
## <a name="error-parameter"></a>エラー パラメーター  
 *エラー*パラメーターは、ADO への参照を[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。 ときに、*ステータス*にパラメーターが設定されている**adStatusErrorsOccurred**、**エラー**オブジェクトには、操作が失敗した理由に関する詳細情報が含まれています。 完了イベントに関連付けられている Will イベントが設定して、操作をキャンセルされた場合、*ステータス*パラメーターを**adStatusCancel**、エラー オブジェクトは、常に設定**adErrOperationCancelled**です。  
  
## <a name="object-parameter"></a>オブジェクトのパラメーター  
 各イベントは、操作に関係しているオブジェクトを表す 1 つまたは複数のオブジェクトを受け取ります。 たとえば、 **ExecuteComplete**イベントを受け取る、**コマンド**オブジェクト、**レコード セット**オブジェクト、および**接続**オブジェクト。  
  
## <a name="reason-parameter"></a>Reason パラメータ  
 *理由*パラメーター、 *adReason*イベントが発生した理由に関する追加情報を提供します。 イベントを*adReason*パラメーターは、別の理由たびに、同じ操作に対してもを複数回呼び出すことができます。 たとえば、 **WillChangeRecord**操作または挿入、削除、またはレコードの変更を元に戻すしようとする操作のイベント ハンドラーが呼び出されます。 使用することが何らかの理由で発生したときにのみイベントを処理する場合、 *adReason*をフィルターで除外する必要がない、出現回数のパラメーターです。 たとえば、レコードが追加された理由で発生した場合にのみ、レコードの変更イベントを処理したい場合は、次のようなを使用できます。  
  
```  
' BeginEventExampleVB01  
Private Sub rsTest_WillChangeRecord(ByVal adReason As ADODB.EventReasonEnum, ByVal cRecords As Long, adStatus As ADODB.EventStatusEnum, ByVal pRecordset As ADODB.Recordset)  
   If adReason = adRsnAddNew Then  
       ' Process event  
       '...  
   Else  
       ' Cancel event notification for all  
       ' other possible adReason values.  
       adStatus = adStatusUnwantedEvent  
   End If  
End Sub  
' EndEventExampleVB01  
```  
  
 この場合、通知可能性のあるその他の理由の列ごと発生します。 ただしには 1 回だけの各理由。 通知が各理由の 1 回発生した後に、新しいレコードの追加にのみ通知を受け取ります。  
  
 設定する必要がこれに対し、 *adStatus*に**adStatusUnwantedEvent** 1 回だけを要求できることがなく、イベント ハンドラー、 **adReason**パラメーター停止受信イベント通知です。  
  
## <a name="see-also"></a>参照  
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [言語によって、ADO イベントのインスタンス化](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [イベント ハンドラーがどのように連携](../../../ado/guide/data/how-event-handlers-work-together.md)   
 [イベントの種類](../../../ado/guide/data/types-of-events.md)
