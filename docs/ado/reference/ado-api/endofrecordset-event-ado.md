---
title: "EndOfRecordset イベント (ADO) |Microsoft ドキュメント"
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
- EndOfRecordset
- Recordset::EndOfRecordset
helpviewer_keywords:
- EndOfRecordset event [ADO]
ms.assetid: 475de5e2-f634-4954-9edf-0027a6ba38d6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4cf00efb278f6ea9937bd0fa87f929d45b8294cb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="endofrecordset-event-ado"></a>EndOfRecordset イベント (ADO)
**EndOfRecordset**イベントは、行の末尾に移動しようとしたときに呼び出されますが、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
EndOfRecordset fMoreData, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>パラメーター  
 *fMoreData*  
 A **VARIANT_BOOL**値 VARIANT_TRUE に設定、複数の行に追加されたことを示します、 **Recordset**です。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)状態値。  
  
 ときに**EndOfRecordset**が呼び出されると、このパラメーターに設定されている**adStatusOK**イベントの原因となった操作が成功した場合。 設定されている**adStatusCantDeny**場合、このイベントは、このイベントの原因となった操作のキャンセルを要求できません。  
  
 前に**EndOfRecordset**戻り値は、このパラメーターに設定する**adStatusUnwantedEvent**を後続の通知を防ぐためにします。  
  
 *pRecordset*  
 A **Recordset**オブジェクト。 **Recordset**のこのイベントが発生しました。  
  
## <a name="remarks"></a>解説  
 **EndOfRecordset**場合に、イベントが発生する可能性があります、 [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)操作は失敗します。  
  
 このイベント ハンドラーが呼び出されますの末尾を越えた移動しようとしましたが、**レコード セット**呼び出しの結果などのオブジェクト**MoveNext**です。 ただし、このイベントの中でしたより多くのレコードをデータベースから取得し、それらの末尾に追加、 **Recordset**です。 その場合は、設定*fMoreData* VARIANT_TRUE とからの戻り値に**EndOfRecordset**です。 呼び出す**MoveNext**新しく取得されたレコードにアクセスするには、もう一度です。  
  
## <a name="see-also"></a>参照  
 [ADO イベント モデルの例 (vc++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)
