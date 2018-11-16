---
title: 接続プロパティ (RDS) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 2612fdc52bde6b199080bcdd7b67a8e8401e6805
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51604662"
---
# <a name="connect-property-rds"></a>Connect プロパティ (RDS)
クエリと更新操作の実行元となるデータベース名を示します。  
  
 設定することができます、 **Connect**でデザイン時にプロパティ、 [rds.DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトのオブジェクトのタグ、または実行時にスクリプト コード (たとえば、VBScript など)。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Design time: <PARAM NAME="Connect" VALUE="ConnectionString">  
Run time: DataControl.Connect = "ConnectionString"  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ConnectionString*  
 有効な接続文字列。 接続文字列の概要については、次を参照してください。、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティまたはプロバイダーのドキュメント。  
  
> [!NOTE]
>  プロバイダーとして MS Remote の指定、 **rds.DataControl** 4 層のシナリオを作成します。 3 つのレベルよりも大きいシナリオでは、テストされていないと、必要はありません。  
  
 *DataControl*  
 オブジェクト変数を表す、 **rds.DataControl**オブジェクト。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [接続プロパティの例 (VBScript)](../../../ado/reference/rds-api/connect-property-example-vbscript.md)   
 [クエリ メソッド (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Refresh メソッド (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [SubmitChanges メソッド (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


