---
title: オブジェクトのプログラミング モデルを RDS |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS programming model [ADO]
- RDS objects [ADO]
ms.assetid: 07ce0ef0-72f1-48f4-823d-1b65d28c0926
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32cd0b412e06f591eee69581e1e7ea8f871cab7f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="rds-programming-model-with-objects"></a>オブジェクトと RDS プログラミング モデル
RDS の目的にアクセスし、IIS などの中間層経由でデータ ソースの更新です。 プログラミング モデルでは、この目標を達成するために必要な活動のシーケンスを指定します。 オブジェクト モデルでは、あるメソッドとプロパティに影響を与える、プログラミング モデルのオブジェクトを指定します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 RDS は、次の一連の操作を実行する手段を提供します。  
  
-   サーバーで、呼び出されるプログラムを指定し、クライアントから参照する方法 (プロキシ) を取得 ([.rds ですDataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md))。  
  
-   サーバーのプログラムを起動します。 データ ソースおよび発行するコマンドを識別するサーバーのプログラムにパラメーターを渡す (プロキシまたは[.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md))。  
  
-   サーバーのプログラムを取得、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) ADO を使用して、通常、データ ソースからのオブジェクト。 必要に応じて、 **Recordset**オブジェクトは、サーバーで処理される ([RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md))。  
  
-   サーバーを返します、最終的な**レコード セット**をクライアント アプリケーション (プロキシ) オブジェクト。  
  
-   クライアントで、 **Recordset**オブジェクトがビジュアル コントロールで簡単に使用できるフォームに配置 (ビジュアル コントロールと **.rds ですDataControl**)。  
  
-   変更、 **Recordset**オブジェクトがサーバーに送信され、データ ソースを更新するために使用 (**.rds ですDataControl**または**RDSServer.DataFactory**)。  
  
## <a name="see-also"></a>参照  
 [RDS オブジェクト モデルの概要](../../../ado/guide/remote-data-service/rds-object-model-summary.md)   
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [DataSpace オブジェクト (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)   
 [RDS のシナリオ](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [RDS チュートリアル](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [RDS の使用方法とセキュリティ](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


