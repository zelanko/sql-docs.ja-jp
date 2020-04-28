---
title: Connect プロパティ (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Connect property [ADO]
ms.assetid: dbad5e77-b213-4eb8-aecf-d60f203fdb59
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ba8b5aa1f59fbb161da878f5930f83d2f6ff0bdd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67964564"
---
# <a name="connect-property-rds"></a>Connect プロパティ (RDS)
クエリおよび更新操作の実行元のデータベース名を示します。  
  
 RDS では、デザイン時に**Connect**プロパティを設定でき[ます。DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトのオブジェクトタグ、またはスクリプトコード (VBScript など) の実行時。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
Design time: <PARAM NAME="Connect" VALUE="ConnectionString">  
Run time: DataControl.Connect = "ConnectionString"  
```  
  
#### <a name="parameters"></a>パラメーター  
 *文字列*  
 有効な接続文字列です。 接続文字列の一般的な情報については、「 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティ」またはプロバイダーのドキュメントを参照してください。  
  
> [!NOTE]
>  MS Remote を RDS のプロバイダーとして指定し**ます。DataControl**は、4層のシナリオを作成します。 3層を超えるシナリオはテストされていないため、必要ありません。  
  
 *DataControl*  
 RDS を表すオブジェクト変数です **。DataControl**オブジェクト。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [Connect プロパティの例 (VBScript)](../../../ado/reference/rds-api/connect-property-example-vbscript.md)   
 [Query メソッド (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Refresh メソッド (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [SubmitChanges メソッド (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


