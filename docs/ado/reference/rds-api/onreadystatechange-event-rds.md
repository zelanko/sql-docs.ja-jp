---
title: "onReadyStateChange イベント (RDS) |Microsoft ドキュメント"
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
helpviewer_keywords:
- onReadyStateChange event [ADO]
ms.assetid: bf2ae3ac-bfe4-4709-b50a-ea7c282c3164
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cbc9538b623fdbd9182c98456a3a3b742fc878fe
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="onreadystatechange-event-rds"></a>onReadyStateChange イベント (RDS)
**OnReadyStateChange**イベントが呼び出されたときの値、 [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md)プロパティが変更されました。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
onReadyStateChange  
```  
  
#### <a name="parameters"></a>パラメーター  
 [なし] :  
  
## <a name="remarks"></a>解説  
 **ReadyState**プロパティに反映の進行状況、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトへのデータを非同期的に取得されて、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。 使用して、 **onReadyStateChange**変更を監視するイベント、 **ReadyState**プロパティが発生したときにします。 これは、プロパティの値を定期的に確認するよりも効率的です。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [ADO イベント モデルの例 (vc++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)



