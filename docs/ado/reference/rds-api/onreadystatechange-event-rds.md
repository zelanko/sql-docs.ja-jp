---
title: onReadyStateChange イベント (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- onReadyStateChange event [ADO]
ms.assetid: bf2ae3ac-bfe4-4709-b50a-ea7c282c3164
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3558fc1fecd343fff480cca3b45c468860a801f8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67963838"
---
# <a name="onreadystatechange-event-rds"></a>onReadyStateChange イベント (RDS)
**OnReadyStateChange**イベントは、 [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md)プロパティの値が変更されるたびに呼び出されます。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
onReadyStateChange  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし。  
  
## <a name="remarks"></a>Remarks  
 **ReadyState**プロパティは、RDS の進行状況を反映し[ます。DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトは、データ[セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトにデータを非同期的に取得します。 **OnReadyStateChange**イベントは、 **ReadyState**プロパティが発生するたびに、その変更を監視するために使用します。 これは、プロパティの値を定期的にチェックするよりも効率的です。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [ADO Events モデルの例 (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)


