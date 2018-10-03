---
title: Cancel メソッド (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Cancel method [RDS]
ms.assetid: 560b5b3d-fba9-4275-8920-9c3e186134f7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: be5ff99397e73f1098f4c11b57a636b08bfa5921
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747320"
---
# <a name="cancel-method-rds"></a>Cancel メソッド (RDS)
実行をキャンセルする保留中、非同期メソッド呼び出し。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RDS.DataControl.Cancel  
```  
  
## <a name="remarks"></a>コメント  
 呼び出すと**キャンセル**、 [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md)に自動的に設定されている**adcReadyStateLoaded**、および[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)は空になります。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [Cancel メソッドの例 (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Cancel メソッド (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [CancelBatch メソッド (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate メソッド (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [CancelUpdate メソッド (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [ExecuteOptions プロパティ (RDS)](../../../ado/reference/rds-api/executeoptions-property-rds.md)


