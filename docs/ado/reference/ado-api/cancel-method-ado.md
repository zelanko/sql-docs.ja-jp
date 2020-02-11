---
title: Cancel メソッド (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: db369b32737c0e2dae4603a4a5a6c26cdd3a7142
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920239"
---
# <a name="cancel-method-ado"></a>Cancel メソッド (ADO)
保留中の非同期メソッド呼び出しの実行を取り消します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.Cancel  
```  
  
## <a name="remarks"></a>解説  
 **Cancel**メソッドを使用して、非同期メソッド呼び出しの実行を終了します。つまり、 **adasyncconnect**、 **adasyncconnect**、または**adasyncconnect**オプションを使用して呼び出されたメソッドです。  
  
 次の表は、特定の種類のオブジェクトに対して**Cancel**メソッドを使用した場合に終了するタスクを示しています。  
  
|*オブジェクト*がである場合|このメソッドへの最後の非同期呼び出しが終了しました|  
|----------------------|-------------------------------------------------------------|  
|[command](../../../ado/reference/ado-api/command-object-ado.md)|[おい](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[接続](../../../ado/reference/ado-api/connection-object-ado.md)|[実行](../../../ado/reference/ado-api/execute-method-ado-connection.md)または[開く](../../../ado/reference/ado-api/open-method-ado-connection.md)|  
|[Record](../../../ado/reference/ado-api/record-object-ado.md)|[Copyrecord](../../../ado/reference/ado-api/copyrecord-method-ado.md)、 [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md)、 [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md)、または[Open](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)|[開き](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)|[開き](../../../ado/reference/ado-api/open-method-ado-stream.md)|  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>参照  
 [Cancel メソッドの例 (VB)](../../../ado/reference/ado-api/cancel-method-example-vb.md)   
 [Cancel メソッドの例 (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Cancel メソッドの例 (VC + +)](../../../ado/reference/ado-api/cancel-method-example-vc.md)   
 [Cancel メソッド (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelBatch メソッド (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate メソッド (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [CancelUpdate メソッド (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Execute メソッド (ADO コマンド)](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [Execute メソッド (ADO Connection)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Open メソッド (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open メソッド (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)
