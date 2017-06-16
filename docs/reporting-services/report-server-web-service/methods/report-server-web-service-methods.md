---
title: "レポート サーバー Web サービスのメソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- XML Web service [Reporting Services], features
- Web service [Reporting Services], features
- Report Server Web service, features
- XML Web service [Reporting Services], methods
ms.assetid: ce5afa27-e90c-44a7-b204-098a065b3665
caps.latest.revision: 49
author: sabotta
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: ec79e5169ff32294cc68f5bee24c3df677d8b38b
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="report-server-web-service-methods"></a>レポート サーバー Web サービスのメソッド
  レポート サーバー Web サービスには、コンポーネントの機能に基づいた、複数のカテゴリのメソッドが含まれています。 これらのメソッドは、Web サービスのいくつかのエンドポイントを介して (レポート管理用に 3 つ、レポート実行用に 1 つ)、<xref:ReportService2010.ReportingService2010> クラスおよび <xref:ReportExecution2005.ReportExecutionService> クラスのメンバーとして提供されます。 含まれる wsdl.exe など、プロキシ クラス ツールを使ってこれらのクラスを生成することができます、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK。 レポート サーバー Web サービスの詳細については、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]を参照してください[Web サービスと、.NET Framework を使用してアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)です。  
  
## <a name="endpoints-and-methods"></a>エンドポイントおよびメソッド  
 次の表に、レポート サーバー Web サービスのエンドポイントと、<xref:ReportService2010.ReportingService2010> エンドポイントにより提供されるメソッドのカテゴリを示します。 他のエンドポイントで使用できる方法については、次を参照してください。[テクニカル リファレンス & #40 です。SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md).  
  
|トピック|Description|  
|-----------|-----------------|  
|[レポート サーバー Web サービス エンドポイント](../../../reporting-services/report-server-web-service/methods/report-server-web-service-endpoints.md)|レポート サーバー Web サービスの管理用エンドポイントと実行用エンドポイントについて説明します。|  
|[レポート サーバーの Namespace 管理メソッド](../../../reporting-services/report-server-web-service/methods/report-server-namespace-management-methods.md)|レポート サーバー データベースの管理に使用できるメソッドについて説明します。 フォルダーとリソースの管理、アイテム プロパティの設定を行えます。|  
|[Authorization メソッド](../../../reporting-services/report-server-web-service/methods/authorization-methods.md)|タスク、ロール、およびポリシーの管理に使用できるメソッドについて説明します。|  
|[データ ソースとの接続方法](../../../reporting-services/report-server-web-service/methods/data-sources-and-connection-methods.md)|レポートのデータ ソース接続や資格情報の設定および管理に使用できるメソッドについて説明します。|  
|[レポート パラメーターのメソッド](../../../reporting-services/report-server-web-service/methods/report-parameters-methods.md)|レポートのパラメーターを設定および取得するためのメソッドについて説明します。|  
|[モデルのメソッドのレポート サーバー Web サービス](../../../reporting-services/report-server-web-service/methods/model-methods-report-server-web-service.md)|モデルの管理に使用できるメソッドについて説明します。|  
|[レンダリング メソッドと Execution メソッド](../../../reporting-services/report-server-web-service/methods/rendering-and-execution-methods.md)|レポートの実行、表示、およびキャッシュを管理するためのメソッドについて説明します。|  
|[レポート履歴メソッド](../../../reporting-services/report-server-web-service/methods/report-history-methods.md)|レポート履歴スナップショットを作成および管理するためのメソッドについて説明します。|  
|[メソッドのスケジュール設定](../../../reporting-services/report-server-web-service/methods/scheduling-methods.md)|レポート サーバーが使用する共有スケジュールとキャッシュ更新計画を作成および管理するためのメソッドについて説明します。|  
|[サブスクリプションおよび配信メソッド](../../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md)|サブスクリプションとレポート配信を作成および管理するためのメソッドについて説明します。|  
|[リンク レポートのメソッド](../../../reporting-services/report-server-web-service/methods/linked-reports-methods.md)|リンク レポートを作成および管理するためのメソッドについて説明します。|  
  
## <a name="see-also"></a>参照  
 [SOAP API にアクセスします。](../../../reporting-services/report-server-web-service/accessing-the-soap-api.md)   
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [テクニカル リファレンス & #40 です。SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
