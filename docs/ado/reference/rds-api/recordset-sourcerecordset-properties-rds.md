---
title: "レコード セット、SourceRecordset プロパティ (RDS) |Microsoft ドキュメント"
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: Recordset property [ADO]
ms.assetid: a29e3fb9-306d-497a-9a59-1856a914e5e9
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dbe0667cd71609f092e3008bf65d7a5cca2faf37
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="recordset-sourcerecordset-properties-rds"></a>レコード セット、SourceRecordset プロパティ (RDS)
示します、 **Recordset**カスタム ビジネス オブジェクトから返されたオブジェクト。  
  
 **適用対象:** [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
DataControl.SourceRecordset = Recordset  
Recordset = DataControl.Recordset   
```  
  
#### <a name="parameters"></a>パラメーター  
 *DataControl*  
 オブジェクト変数を表す、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
 *レコード セット*  
 オブジェクト変数を表す、 **Recordset**オブジェクト。  
  
## <a name="remarks"></a>解説  
 設定することができます、 **SourceRecordset**プロパティを[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)カスタム ビジネス オブジェクトから返されます。  
  
 これらのプロパティでは、アプリケーションがカスタム プロセスを使用して、バインディング プロセスを処理できるようにします。 ラップ、行セットを受信する、 **Recordset**と直接やり取りできるように、 **Recordset**プロパティの設定などの操作の実行、または反復処理に使用、**レコード セット**.  
  
 設定することができます、 **SourceRecordset**プロパティまたは読み取り、 **Recordset**スクリプト コードの実行時にプロパティです。  
  
 **SourceRecordset**は書き込み専用プロパティでは、対照的、 **Recordset**プロパティで、読み取り専用プロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [レコード セットと SourceRecordset プロパティの例 (VBScript)](../../../ado/reference/rds-api/recordset-and-sourcerecordset-properties-example-vbscript.md)   
 [CreateRecordset メソッド (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)   
 [クエリ メソッド (RDS)](../../../ado/reference/rds-api/query-method-rds.md)


