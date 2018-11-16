---
title: RDS オブジェクト モデルの概要 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS objects [ADO], object model summary
- RDS object model [ADO]
ms.assetid: 909f9af7-31db-4eec-ad52-650ce74dac2f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b19a138e9e4d479e7fb9cb3f8b4e140838b43e8a
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558409"
---
# <a name="rds-object-model-summary"></a>RDS オブジェクト モデルの概要
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
|オブジェクト|説明|  
|------------|-----------------|  
|[RDS.DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)|このオブジェクトには、サーバーのプロキシを取得するメソッドが含まれています。 プロキシは、既定またはカスタムのサーバー プログラム (ビジネス オブジェクト) にあります。 サーバーのプログラムは、インターネット、イントラネット、ローカル エリア ネットワークで呼び出すことがでもローカル ダイナミック リンク ライブラリです。<br /><br /> **DataSpace**オブジェクトがスクリプトを実行します。|  
|[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|このオブジェクトは、既定のサーバー プログラムを表します。 既定の RDS のデータの取得と更新動作を実行します。<br /><br /> **DataFactory**オブジェクトは、スクリプトを実行することはありません。|  
|[RDS.DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)|このオブジェクトは自動的に呼び出すことができます、 **rds.DataSpace**と**RDSServer.DataFactory**オブジェクト。<br /><br /> このオブジェクトを使用して、既定の RDS のデータの取得や更新プログラムの動作を呼び出します。<br /><br /> このオブジェクトは、ビジュアル コントロールへのアクセス、返されたにするための手段も用意されています。 **Recordset**オブジェクト。<br /><br /> **DataControl**オブジェクトがスクリプトを実行します。|  
  
## <a name="see-also"></a>参照  
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [RDS のシナリオ](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [RDS チュートリアル](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [RDS の使用方法とセキュリティ](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


