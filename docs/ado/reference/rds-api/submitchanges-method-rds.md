---
title: "SubmitChanges メソッド (RDS) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: SubmitChanges method [ADO]
ms.assetid: 250062a4-13c4-4bed-807d-8b9ad81536d4
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2d7015e1a668697a12c373904c0bd71e22108449
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="submitchanges-method-rds"></a>SubmitChanges メソッド (RDS)
保留中のローカル キャッシュと更新の変更を送信する[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)で指定されたデータ ソースに、[接続](../../../ado/reference/rds-api/connect-property-rds.md)プロパティまたは[URL](../../../ado/reference/rds-api/url-property-rds.md)プロパティです。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.SubmitChanges DataFactory.SubmitChanges Connection, Recordset  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 オブジェクト変数を表す、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
 *DataFactory*  
 オブジェクト変数を表す、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)オブジェクト。  
  
 *接続*  
 A**文字列**で作成された接続を表す値、 **.rds ですDataControl**オブジェクトの[接続](../../../ado/reference/rds-api/connect-property-rds.md)プロパティです。  
  
 *レコード セット*  
 オブジェクト変数を表す、 **Recordset**オブジェクト。  
  
## <a name="remarks"></a>解説  
 [接続](../../../ado/reference/rds-api/connect-property-rds.md)、[サーバー](../../../ado/reference/rds-api/server-property-rds.md)、および[SQL](../../../ado/reference/rds-api/sql-property.md)を使用するには、プロパティを設定する必要があります、 **SubmitChanges**メソッドを**RDS.DataControl**オブジェクト。  
  
 呼び出す場合は、[ただし](../../../ado/reference/rds-api/cancelupdate-method-rds.md)メソッドを呼び出した後**SubmitChanges**同じ**Recordset**オブジェクト、**ただし**変更がコミット済みの呼び出しは失敗します。  
  
 成功または失敗するすべての変更、変更、および変更のすべての変更されたレコードだけが送信されます。  
  
 使用することができます**SubmitChanges**既定値でのみ**RDSServer.DataFactory**オブジェクト。 カスタム ビジネス オブジェクトには、このメソッドを使用できません。  
  
 場合、 **URL**プロパティが設定されている、 **SubmitChanges** URL で指定された場所への変更を送信します。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>参照  
 [SubmitChanges メソッドの例 (VBScript)](../../../ado/reference/rds-api/submitchanges-method-example-vbscript.md)   
 [アドレス帳コマンド ボタン](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [ただしメソッド (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Refresh メソッド (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)



