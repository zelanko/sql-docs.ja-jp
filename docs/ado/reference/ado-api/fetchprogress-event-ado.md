---
title: FetchProgress イベント (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FetchProgress
- Recordset::FetchProgress
helpviewer_keywords:
- FetchProgress event [ADO]
ms.assetid: 301716fd-81fc-40eb-8a04-221ef7ab410e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7fea26975fc162f92527f63123eddb95fade8a8e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="fetchprogress-event-ado"></a>FetchProgress イベント (ADO)
**FetchProgress**イベントが現在までに取得された複数行の数を報告する時間のかかる非同期操作中に定期的と呼ばれる、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
FetchProgress Progress, MaxProgress, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>パラメーター  
 *[進行状況]*  
 A**長い**現在フェッチ操作によって取得されたレコードの数を示す値。  
  
 *MaxProgress*  
 A**長い**レコードの最大数を示す値を取得する予定です。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)状態値。  
  
 *pRecordset*  
 A **Recordset**レコードを取得するオブジェクトです。  
  
## <a name="remarks"></a>解説  
 使用する場合**FetchProgress**子を持つ**レコード セット**、注意してくださいを*進行状況*と*MaxProgress*パラメーターの値は派生基になるから[カーソル サービス](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)行セット。 返される値は、基になる行セット、現在のチャプター内のレコードの数だけでなく内のレコードの合計数を表します。  
  
> [!NOTE]
>  使用する**FetchProgress** with Microsoft Visual Basic、Visual Basic 6.0 またはそれ以降が必要です。  
  
## <a name="see-also"></a>参照  
 [ADO イベント モデルの例 (vc++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)
