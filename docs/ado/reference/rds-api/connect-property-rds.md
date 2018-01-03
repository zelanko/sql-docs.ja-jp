---
title: "接続プロパティ (RDS) |Microsoft ドキュメント"
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
helpviewer_keywords: Connect property [ADO]
ms.assetid: dbad5e77-b213-4eb8-aecf-d60f203fdb59
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fd828ee21628a5c0b00566c47b9b7dedcb5b0b65
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="connect-property-rds"></a>プロパティ (RDS) 接続します。
クエリおよび更新操作の実行起点となるデータベース名を示します。  
  
 設定することができます、**接続**でデザイン時にプロパティ、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトのオブジェクトのタグ、またはコード (たとえば、VBScript) スクリプトの実行時にします。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Design time: <PARAM NAME="Connect" VALUE="ConnectionString">  
Run time: DataControl.Connect = "ConnectionString"  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ConnectionString*  
 有効な接続文字列。 一般的な接続文字列については、次を参照してください。、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティや、プロバイダーのドキュメントです。  
  
> [!NOTE]
>  プロバイダーとして MS Remote の指定、 **.rds ですDataControl** 4 層のシナリオを作成します。 3 つのレベルよりも大きいシナリオでは、テストされていないと、必要はありません。  
  
 *DataControl*  
 オブジェクト変数を表す、 **.rds ですDataControl**オブジェクト。  
  
## <a name="applies-to"></a>適用対象  
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>参照  
 [プロパティの例 (VBScript) の接続します。](../../../ado/reference/rds-api/connect-property-example-vbscript.md)   
 [クエリ メソッド (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Refresh メソッド (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [SubmitChanges メソッド (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


