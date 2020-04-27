---
title: ExecuteComplete イベント (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- ExecuteComplete event [ADO]
ms.assetid: 62470d42-e511-494c-bec4-ad4591734b7b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 62b78b608526ae0d6943a7416a21687fd1e51412
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67918782"
---
# <a name="executecomplete-event-ado"></a>ExecuteComplete イベント (ADO)
**ExecuteComplete**イベントは、コマンドの実行が完了した後に呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
ExecuteComplete RecordsAffected, pError, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>パラメーター  
 *RecordsAffected*  
 コマンドの影響を受けるレコードの数を示す**Long 型**の値。  
  
 *pError*  
 [エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトです。 **Adstatus**の値が**adstatuserrorて**いる場合に発生したエラーについて説明します。それ以外の場合は設定されません。  
  
 *adStatus*  
 [Eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md)状態の値です。 このイベントが呼び出されると、このパラメーターは、イベントの原因となった操作が成功した場合は**Adstatusok**に、操作が失敗した場合は**Adstatuserrorの curred**に設定されます。  
  
 このイベントが返される前に、このパラメーターを**adStatusUnwantedEvent**に設定して、後続の通知が行われないようにします。  
  
 *pCommand*  
 実行された[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。 コマンドオブジェクト**が**含まれてい**ます。** **コマンドを明示**的に**作成せず****に、コマンドオブジェクトが**ADO によって内部で作成されます。  
  
 *pRecordset*  
 実行されたコマンドの結果である[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。 この**レコードセット**は空にすることができます。 このイベントハンドラー内からは、このレコードセットオブジェクトを破棄しないでください。 これを行うと、存在しなくなったオブジェクトに ADO がアクセスしようとしたときにアクセス違反が発生します。  
  
 *pConnection*  
 [接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトです。 操作が実行された接続です。  
  
## <a name="remarks"></a>Remarks  
 接続が原因で**ExecuteComplete**イベントが発生する可能性があり**ます。** コマンドを[実行](../../../ado/reference/ado-api/execute-method-ado-connection.md)**します。**[Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)、 **Recordset。** レコードセットを[開き](../../../ado/reference/ado-api/open-method-ado-recordset.md)**ます。**[Requery](../../../ado/reference/ado-api/requery-method.md)、または**レコードセット。**[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)メソッド。  
  
## <a name="see-also"></a>参照  
 [ADO Events モデルの例 (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)
