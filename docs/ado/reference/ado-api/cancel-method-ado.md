---
title: Cancel メソッド (ADO) |Microsoft ドキュメント
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
- Recordset20::Cancel
- _Record::Cancel
- _Connection::Cancel
- Command25::Cancel
- _Stream::Cancel
helpviewer_keywords:
- Cancel method [ADO]
ms.assetid: e0db4e15-6787-41e2-8f13-9e9b524d620a
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dfa05c071a40189478c361c1d5f4e3b34813daf1
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="cancel-method-ado"></a>Cancel メソッド (ADO)
保留中の非同期メソッド呼び出しの実行をキャンセルします。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.Cancel  
```  
  
## <a name="remarks"></a>解説  
 使用して、**キャンセル**非同期メソッド呼び出しの実行を終了する方法: には、メソッドが呼び出された、 **adAsyncConnect**、 **adAsyncExecute**、または**adAsyncFetch**オプション。  
  
 次の表を使用するときにどのようなタスクが終了した、**キャンセル**オブジェクトの特定の型のメソッドです。  
  
|場合*オブジェクト*は、|このメソッドの最後の非同期呼び出しが終了しました|  
|----------------------|-------------------------------------------------------------|  
|[Command](../../../ado/reference/ado-api/command-object-ado.md)|[Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[接続](../../../ado/reference/ado-api/connection-object-ado.md)|[実行](../../../ado/reference/ado-api/execute-method-ado-connection.md)または[開く](../../../ado/reference/ado-api/open-method-ado-connection.md)|  
|[レコード](../../../ado/reference/ado-api/record-object-ado.md)|[つまり](../../../ado/reference/ado-api/copyrecord-method-ado.md)、[関係する](../../../ado/reference/ado-api/deleterecord-method-ado.md)、[後続](../../../ado/reference/ado-api/moverecord-method-ado.md)、または[開く](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)|[[ファイル]](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)|[[ファイル]](../../../ado/reference/ado-api/open-method-ado-stream.md)|  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>参照  
 [キャンセル メソッドの例 (VB)](../../../ado/reference/ado-api/cancel-method-example-vb.md)   
 [キャンセル メソッドの例 (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [キャンセル メソッドの例 (vc++)](../../../ado/reference/ado-api/cancel-method-example-vc.md)   
 [Cancel メソッド (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelBatch メソッド (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [ただしメソッド (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [ただしメソッド (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Execute メソッド (ADO コマンド)](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [Execute メソッド (ADO 接続)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Open メソッド (ADO 接続)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open メソッド (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)
