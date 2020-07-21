---
title: InfoMessage イベント (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::InfoMessage
- InfoMessage
helpviewer_keywords:
- InfoMessage event [ADO]
ms.assetid: 468c87dd-e3bc-4084-9941-94d10743d4e9
author: rothja
ms.author: jroth
ms.openlocfilehash: c5fc0adfec791294bb6c680dab94078b8a63ec07
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758688"
---
# <a name="infomessage-event-ado"></a>InfoMessage イベント (ADO)
**Connectionevent**操作中に警告が発生するたびに、 **infomessage**イベントが呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
InfoMessage pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pError*  
 [エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトです。 このパラメーターには、返されたすべてのエラーが含まれます。 複数のエラーが返された場合は、**エラー**コレクションを列挙して検出します。  
  
 *adStatus*  
 [Eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md)状態の値です。 警告が発生した場合、 *adstatus*は**adstatusok**に設定*され、* エラーメッセージには警告が含まれます。  
  
 このイベントが返される前に、このパラメーターを**adStatusUnwantedEvent**に設定して、後続の通知が行われないようにします。  
  
 *pConnection*  
 [接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトです。 警告が発生した接続。 たとえば、接続オブジェクトを開いたり、**接続**で[コマンド](../../../ado/reference/ado-api/command-object-ado.md)を**実行したり**すると、警告が発生することがあります。  
  
## <a name="see-also"></a>参照  
 [ADO Events モデルの例 (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベントハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
