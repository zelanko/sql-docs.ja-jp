---
title: "アクティビ ティー イベント (ADO) |Microsoft ドキュメント"
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
- WillExecute
- Connection::WillExecute
helpviewer_keywords:
- WillExecute event [ADO]
ms.assetid: dd755e46-f589-48a3-93a9-51ff998d44b5
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 63062a2b16cc423c1188aef4302f5b0f8b1e0677
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="willexecute-event-ado"></a>アクティビ ティー イベント (ADO)
**アクティビ ティー**イベントは、接続で保留中のコマンドを実行する前に呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
WillExecute Source, CursorType, LockType, Options, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ソース*  
 A**文字列**SQL コマンドまたはストアド プロシージャの名前を格納しています。  
  
 *カーソル。*  
 A [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md)のカーソルの種類を格納している、 **Recordset**は開かれます。 このパラメーターを使用中に任意の型にカーソルを変更することができます、 **Recordset**[Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)操作します。 *カーソル。*他の操作は無視されます。  
  
 *ロック。*  
 A [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md)のロックの種類を格納している、 **Recordset**は開かれます。 このパラメーターを使用中に任意の型にロックを変更することができます、 **RecordsetOpen**操作します。 *LockType*他の操作は無視されます。  
  
 *および*  
 A**長い**コマンドを実行したり、開いたりに使用できるオプションを示す値、 **Recordset**です。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)可能性のある状態値**adStatusCantDeny**または**adStatusOK**このイベントが呼び出されたとき。 場合は**adStatusCantDeny**、このイベントは、保留中の操作の取り消しを要求しない場合があります。  
  
 *pCommand*  
 [コマンド オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトに対してこのイベント通知が適用されます。  
  
 *pRecordset*  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトに対してこのイベント通知が適用されます。  
  
 *pConnection*  
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトに対してこのイベント通知が適用されます。  
  
## <a name="remarks"></a>解説  
 A**アクティビ ティー**接続によるイベントが発生します。  [Execute メソッド (ADO 接続)](../../../ado/reference/ado-api/execute-method-ado-connection.md)、[メソッドの実行 (ADO コマンド)](../../../ado/reference/ado-api/execute-method-ado-command.md)、または[Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッド、 *pConnection*パラメーターにする必要があります常に有効な参照が含まれて、**接続**オブジェクト。 場合は、イベントの原因**Connection.Execute**、 *pRecordset*と*pCommand*パラメーターに設定されて**Nothing**です。 場合は、イベントの原因**Recordset.Open**、 *pRecordset*パラメーターで参照、 **Recordset**オブジェクトおよび*pCommand*パラメーターに設定されている**Nothing**です。 場合は、イベントの原因**Command.Execute**、 *pCommand*パラメーターは参照、**コマンド**オブジェクトおよび*pRecordset*パラメーターに設定されている**Nothing**です。  
  
 **アクティビ ティー**を確認し、保留中の実行のパラメーターを変更することができます。 このイベントは、保留中のコマンドをキャンセルする要求を返す可能性があります。  
  
> [!NOTE]
>  元のソースの場合、**コマンド**で指定されたストリーム、 [CommandStream プロパティ (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)プロパティ、新しい文字列を割り当てる、**アクティビ ティー** *ソース*パラメーターのソースの変更、**コマンド**です。 **CommandStream**プロパティはクリアされ、 [CommandText プロパティ (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)プロパティは、新しいソースで更新されます。 指定された元のストリーム**CommandStream**がリリースされ、アクセスできません。  
  
 新しいソース文字列の言語が、元の設定と異なるかどうか、 [Dialect プロパティ](../../../ado/reference/ado-api/dialect-property.md)プロパティ (に対応しますが、 **CommandStream**)、正しい言語を設定して指定する必要があります**Dialect**によって参照されるコマンド オブジェクトのプロパティ*pCommand*です。  
  
## <a name="see-also"></a>参照  
 [ADO イベント モデルの例 (vc++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)

