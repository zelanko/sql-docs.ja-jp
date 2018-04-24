---
title: BeginTrans、CommitTrans RollbackTrans イベント (ADO) |Microsoft ドキュメント
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
- CommitTransComplete
- Connection::BeginTransComplete
- Connection::RollbackTransComplete
- Connection::CommitTransComplete
- RollbackTransComplete
- BeginTransComplete
helpviewer_keywords:
- CommitTransComplete event [ADO]
- RollbackTransComplete event [ADO]
- BeginTransComplete event [ADO]
ms.assetid: ec4e4b38-e9c6-4757-b2ef-4e468ae5f1d8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 05a5809043ca348d78c1d73cb362c8b2f99efc7c
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado"></a>BeginTransComplete、CommitTransComplete、および RollbackTransComplete イベント (ADO)
これらのイベントが関連付けられている操作の後に呼び出される、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの実行が終了します。  
  
-   **BeginTransComplete**後に呼び出されます、 [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)操作します。  
  
-   **CommitTransComplete**後に呼び出されます、 [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)操作します。  
  
-   **RollbackTransComplete**後に呼び出されます、 [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)操作します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BeginTransComplete TransactionLevel, pError, adStatus, pConnection  
CommitTransComplete pError, adStatus, pConnection  
RollbackTransComplete pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>パラメーター  
 *TransactionLevel*  
 A**長い**新しいトランザクションのレベルを表す値、 **BeginTrans**このイベントの原因となった。  
  
 *pError*  
 [エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。 EventStatusEnum の値がある場合に発生したエラーを説明**adStatusErrorsOccurred**です。 それ以外の場合、設定されていません。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)状態値。 このパラメーターに設定されているこれらのイベントのいずれかが呼び出されると**adStatusOK**イベントの原因となった操作が成功した場合または**adStatusErrorsOccurred**操作が失敗した場合。  
  
 これらのイベントは、後続の通知を防ぐためこのパラメーターを設定して**adStatusUnwantedEvent**イベントが返される前にします。  
  
 *pConnection*  
 **接続**オブジェクトに対してこのイベントが発生しました。  
  
## <a name="remarks"></a>解説  
 Visual c で複数**接続**同じイベント処理メソッドを共有できます。 メソッドを使用して、返された**接続**を決定するオブジェクトがイベントを発生させたオブジェクト。  
  
 場合、[属性](../../../ado/reference/ado-api/attributes-property-ado.md)プロパティに設定されている**adXactCommitRetaining**または**adXactAbortRetaining**、新しいトランザクションがコミットまたはロールバック、トランザクション後に開始します。 使用して、 **BeginTransComplete**を無視するすべてのイベントが最初のトランザクションの開始イベント。  
  
## <a name="see-also"></a>参照  
 [ADO イベント モデルの例 (vc++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [BeginTrans、CommitTrans、および RollbackTrans メソッドの例 (VB)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [BeginTrans、CommitTrans、および RollbackTrans メソッド (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)
