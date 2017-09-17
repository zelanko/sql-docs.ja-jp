---
title: "ConnectComplete し、切断イベント (ADO) |Microsoft ドキュメント"
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
- Disconnect
- Connection::ConnectComplete
- ConnectComplete
- Connection::Disconnect
helpviewer_keywords:
- Disconnect event [ADO]
- ConnectComplete event [ADO]
ms.assetid: 568f5252-d069-4d99-a01b-2ada87ad1304
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ebd4363f166a67a6e48fee41c2585b68de93bc98
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="connectcomplete-and-disconnect-events-ado"></a>ConnectComplete し、切断イベント (ADO)
**ConnectComplete**イベントは、接続の開始後に呼び出されます。 **切断**接続が終了した後にイベントが呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
ConnectComplete pError, adStatus, pConnection  
Disconnect adStatus, pConnection  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pError*  
 [エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。 場合に発生したエラーを説明の値*adStatus*は**adStatusErrorsOccurred**です。 それ以外の場合、設定されていません。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)値を常に返します**adStatusOK**です。  
  
 ときに**ConnectComplete**が呼び出されると、このパラメーターに設定されている**adStatusCancel**場合、 **WillConnect**イベントが保留中の接続のキャンセルを要求します。  
  
 どちらのイベントが返される前に、このパラメーターを設定**adStatusUnwantedEvent**を後続の通知を防ぐためにします。 ただし、終了および再開、[接続](../../../ado/reference/ado-api/connection-object-ado.md)これらのイベントを再度発生させます。  
  
 *pConnection*  
 **接続**オブジェクトに対してこのイベントが適用されます。  
  
## <a name="see-also"></a>参照  
 [ADO イベント モデルの例 (vc++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)
