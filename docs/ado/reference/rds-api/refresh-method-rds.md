---
description: Refresh メソッド (RDS)
title: Refresh メソッド (RDS) |Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
f1_keywords:
- Refresh
- RDS.DataControl::Refresh
- DataControl::Refresh
helpviewer_keywords:
- Refresh method [RDS]
ms.assetid: c90a8050-0ff4-4c83-9925-261f2f2ccfe9
author: rothja
ms.author: jroth
ms.openlocfilehash: 372d4a2506f5ea7d14905ffed0842ca5cf2ce6ee
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438714"
---
# <a name="refresh-method-rds"></a>Refresh メソッド (RDS)
[接続](../../../ado/reference/rds-api/connect-property-rds.md)プロパティで指定されたデータソースを再クエリし、クエリ結果を更新します。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および [Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416) 」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.Refresh  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 RDS を表すオブジェクト変数です [。DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) オブジェクト。  
  
## <a name="remarks"></a>解説  
 **Refresh**メソッドを使用する前に、 [Connect](../../../ado/reference/rds-api/connect-property-rds.md)、 [Server](../../../ado/reference/rds-api/server-property-rds.md)、および[SQL](../../../ado/reference/rds-api/sql-property.md)の各プロパティを設定する必要があります。 RDS に関連付けられているフォーム上のすべてのデータバインドコントロール。 **DataControl** オブジェクトには、新しいレコードのセットが反映されます。 既存の [レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md) オブジェクトがすべて解放され、保存されていない変更はすべて破棄されます。 **Refresh**メソッドでは、最初のレコードが自動的に現在のレコードになります。  
  
 データを操作するときは、 **Refresh** メソッドを定期的に呼び出すことをお勧めします。 データを取得し、しばらくの間クライアントコンピューターに残しておくと、最新の状態にならない可能性があります。 他のユーザーがレコードを変更して変更を送信した可能性があるため、変更が失敗する可能性があります。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [Refresh メソッドの例 (VB)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Refresh メソッドの例 (VBScript)](../../../ado/reference/rds-api/refresh-method-example-vbscript.md)   
 [アドレス帳のコマンドボタン](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [CancelUpdate メソッド (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Refresh メソッド (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)   
 [SubmitChanges メソッド (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


