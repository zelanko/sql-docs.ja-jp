---
title: "Cancel メソッド (RDS) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: Cancel method [RDS]
ms.assetid: 560b5b3d-fba9-4275-8920-9c3e186134f7
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bae65aa8c95d5dc6b0d21cbe66f3174462d69290
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="cancel-method-rds"></a>Cancel メソッド (RDS)
実行をキャンセルする保留中、非同期メソッドの呼び出しです。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
RDS.DataControl.Cancel  
```  
  
## <a name="remarks"></a>解説  
 呼び出すと**キャンセル**、 [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md)に自動的に設定されている**adcReadyStateLoaded**、および[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)は空になります。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [キャンセル メソッドの例 (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Cancel メソッド (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [CancelBatch メソッド (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [ただしメソッド (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [ただしメソッド (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [ExecuteOptions プロパティ (RDS)](../../../ado/reference/rds-api/executeoptions-property-rds.md)


