---
title: "レポート サーバー Web サービスのメソッド | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: report-server-web-service
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- XML Web service [Reporting Services], features
- Web service [Reporting Services], features
- Report Server Web service, features
- XML Web service [Reporting Services], methods
ms.assetid: ce5afa27-e90c-44a7-b204-098a065b3665
caps.latest.revision: "49"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: c577245ad46a2989d7e3c7fbc33a1f9e8cfc19e7
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="report-server-web-service-methods"></a>レポート サーバー Web サービスのメソッド
  レポート サーバー Web サービスには、コンポーネントの機能に基づいた、複数のカテゴリのメソッドが含まれています。 これらのメソッドは、Web サービスのいくつかのエンドポイントを介して (レポート管理用に 3 つ、レポート実行用に 1 つ)、<xref:ReportService2010.ReportingService2010> クラスおよび <xref:ReportExecution2005.ReportExecutionService> クラスのメンバーとして提供されます。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK に含まれる wsdl.exe などのプロキシ クラス ツールを使用して、これらのクラスを生成できます。 Report Server Web サービスと [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] の詳細については、「[Web サービスと、.NET Framework を使用してのアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)」を参照してください。  
  
## <a name="endpoints-and-methods"></a>エンドポイントおよびメソッド  
 次の表に、レポート サーバー Web サービスのエンドポイントと、<xref:ReportService2010.ReportingService2010> エンドポイントにより提供されるメソッドのカテゴリを示します。 他のエンドポイントで利用可能なメソッドの詳細については、「[テクニカル リファレンス (SSRS)](../../../reporting-services/technical-reference-ssrs.md)」を参照してください。  
  
|トピック|Description|  
|-----------|-----------------|  
|[レポート サーバー Web サービス, エンドポイント](../../../reporting-services/report-server-web-service/methods/report-server-web-service-endpoints.md)|レポート サーバー Web サービスの管理用エンドポイントと実行用エンドポイントについて説明します。|  
|[レポート サーバー名前空間管理メソッド](../../../reporting-services/report-server-web-service/methods/report-server-namespace-management-methods.md)|レポート サーバー データベースの管理に使用できるメソッドについて説明します。 フォルダーとリソースの管理、アイテム プロパティの設定を行えます。|  
|[Authorization メソッド](../../../reporting-services/report-server-web-service/methods/authorization-methods.md)|タスク、ロール、およびポリシーの管理に使用できるメソッドについて説明します。|  
|[データ ソースと接続のメソッド](../../../reporting-services/report-server-web-service/methods/data-sources-and-connection-methods.md)|レポートのデータ ソース接続や資格情報の設定および管理に使用できるメソッドについて説明します。|  
|[レポート パラメーターのメソッド](../../../reporting-services/report-server-web-service/methods/report-parameters-methods.md)|レポートのパラメーターを設定および取得するためのメソッドについて説明します。|  
|[モデル メソッド - レポート サーバー Web サービス メソッド](../../../reporting-services/report-server-web-service/methods/model-methods-report-server-web-service.md)|モデルの管理に使用できるメソッドについて説明します。|  
|[Rendering メソッドと Execution メソッド](../../../reporting-services/report-server-web-service/methods/rendering-and-execution-methods.md)|レポートの実行、表示、およびキャッシュを管理するためのメソッドについて説明します。|  
|[レポート履歴メソッド](../../../reporting-services/report-server-web-service/methods/report-history-methods.md)|レポート履歴スナップショットを作成および管理するためのメソッドについて説明します。|  
|[メソッドのスケジュール設定](../../../reporting-services/report-server-web-service/methods/scheduling-methods.md)|レポート サーバーが使用する共有スケジュールとキャッシュ更新計画を作成および管理するためのメソッドについて説明します。|  
|[サブスクリプション メソッドおよび配信メソッド](../../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md)|サブスクリプションとレポート配信を作成および管理するためのメソッドについて説明します。|  
|[リンク レポートのメソッド](../../../reporting-services/report-server-web-service/methods/linked-reports-methods.md)|リンク レポートを作成および管理するためのメソッドについて説明します。|  
  
## <a name="see-also"></a>参照  
 [SOAP API へのアクセス](../../../reporting-services/report-server-web-service/accessing-the-soap-api.md)   
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [テクニカル リファレンス (SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
