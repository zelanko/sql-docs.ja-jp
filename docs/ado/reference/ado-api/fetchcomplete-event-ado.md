---
title: "FetchComplete イベント (ADO) |Microsoft ドキュメント"
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
- Recordset::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- FetchComplete event [ADO]
ms.assetid: a28d3858-566c-468d-b070-d1de4339fbea
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a8332a6332f27a8e2022975a80814be9c28cf4da
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="fetchcomplete-event-ado"></a>FetchComplete イベント (ADO)
**FetchComplete**に長い非同期操作のすべてのレコードを取得した後、イベントが呼び出された、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
FetchComplete pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pError*  
 [エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。 場合に発生したエラーを説明の値**adStatus**は**adStatusErrorsOccurred**です。 それ以外の場合、設定されていません。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)状態値。 このイベントが呼び出されると、このパラメーターに設定されている**adStatusOK**イベントの原因となった操作が成功した場合または**adStatusErrorsOccurred**場合は、操作に失敗しました。  
  
 このイベントが返される前に、このパラメーターを設定**adStatusUnwantedEvent**を後続の通知を防ぐためにします。  
  
 *pRecordset*  
 A **Recordset**オブジェクト。 レコードを取得したオブジェクト。  
  
## <a name="remarks"></a>解説  
 使用する**FetchComplete** with Microsoft Visual Basic、Visual Basic 6.0 またはそれ以降が必要です。  
  
## <a name="see-also"></a>参照  
 [ADO イベント モデルの例 (vc++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)
