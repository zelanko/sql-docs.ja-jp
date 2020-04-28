---
title: FetchProgress イベント (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FetchProgress
- Recordset::FetchProgress
helpviewer_keywords:
- FetchProgress event [ADO]
ms.assetid: 301716fd-81fc-40eb-8a04-221ef7ab410e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ab93d8117a5fb3d2bbc95ea33bbacdc7fba3f151
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932829"
---
# <a name="fetchprogress-event-ado"></a>FetchProgress イベント (ADO)
**Fetchprogress**イベントは、[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)に現在取得されている行の数を報告するために、長い非同期操作中に定期的に呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
FetchProgress Progress, MaxProgress, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>パラメーター  
 *進行状況*  
 フェッチ操作によって現在取得されているレコードの数を示す**Long 型**の値。  
  
 *MaxProgress*  
 取得する必要があるレコードの最大数を示す**Long**値。  
  
 *adStatus*  
 [Eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md)状態の値です。  
  
 *pRecordset*  
 レコードを取得する対象のオブジェクトである**レコードセット**オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 子**レコードセット**で**fetchprogress**を使用する場合は、 *Progress*および*maxprogress*パラメーターの値が基になる[Cursor Service](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)行セットから派生することに注意してください。 返される値は、現在のチャプター内のレコード数だけでなく、基になる行セット内のレコードの合計数を表します。  
  
> [!NOTE]
>  Microsoft Visual Basic で**Fetchprogress**を使用するには Visual Basic 6.0 以降が必要です。  
  
## <a name="see-also"></a>参照  
 [ADO Events モデルの例 (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)
