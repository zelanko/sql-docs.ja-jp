---
title: "Refresh メソッド (RDS) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Refresh
- RDS.DataControl::Refresh
- DataControl::Refresh
helpviewer_keywords: Refresh method [RDS]
ms.assetid: c90a8050-0ff4-4c83-9925-261f2f2ccfe9
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bd8ba42c4e1822e5ef1fafd6ec4f3b53c2a9a363
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="refresh-method-rds"></a>Refresh メソッド (RDS)
指定されたデータ ソースを再クエリ、[接続](../../../ado/reference/rds-api/connect-property-rds.md)プロパティと、クエリの結果を更新します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.Refresh  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 オブジェクト変数を表す、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
## <a name="remarks"></a>解説  
 設定する必要があります、[接続](../../../ado/reference/rds-api/connect-property-rds.md)、[サーバー](../../../ado/reference/rds-api/server-property-rds.md)、および[SQL](../../../ado/reference/rds-api/sql-property.md)プロパティを使用する前に、**更新**メソッドです。 関連付けられているフォーム上のすべてのデータ バインド コントロール、 **.rds ですDataControl**オブジェクトが新しいレコードのセットに反映されます。 既存の[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトが解放され、未保存の変更は破棄されます。 **更新**メソッドに自動的には、最初のレコード、現在のレコードです。  
  
 呼び出すことをお勧め、**更新**メソッド定期的に操作する際にデータを使用します。 データを取得し、しばらくの間、クライアント コンピューターに残す、古くなっている可能性があります。 加えた変更が失敗する、他のユーザー レコードに変更された可能性し、する前に変更を送信してためことができます。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [メソッドの例 (VB) の更新します。](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [メソッドの例 (VBScript) の更新します。](../../../ado/reference/rds-api/refresh-method-example-vbscript.md)   
 [アドレス帳コマンド ボタン](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [ただしメソッド (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Refresh メソッド (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)   
 [SubmitChanges メソッド (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


