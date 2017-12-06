---
title: "Rendering メソッドと Execution メソッド | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: report-server-web-service
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
caps.latest.revision: "36"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3adff3b8401c0693174c4ad4739352cabd135e2d
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="rendering-and-execution-methods"></a>Rendering メソッドと Execution メソッド
  これらのメソッドを使用して、アイテムの実行とキャッシュ、およびレポートの表示を管理します。  
  
|方法|操作|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.FlushCache%2A>|アイテムのキャッシュを無効にします。|  
|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|アイテムのキャッシュ構成と、キャッシュされたコピーの有効期限がいつ切れるかを表す設定を返します。|  
|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|個々のアイテムの実行オプションおよび関連付けられている設定を返します。|  
|<xref:ReportService2010.ReportingService2010.ListExecutionSettings%2A>|サポートされている実行設定の一覧を返します。|  
|<xref:ReportExecution2005.ReportExecutionService.Render%2A>|指定されたレポートを処理し、指定された書式でレポートを表示します。|  
|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|アイテムをキャッシュ用に構成し、キャッシュ内のアイテムの有効期限を示す設定を提供します。|  
|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|指定したアイテムの実行オプションおよび関連付けられた実行プロパティを設定します。|  
|<xref:ReportService2010.ReportingService2010.UpdateItemExecutionSnapshot%2A>|指定したアイテムのアイテム実行スナップショットを生成します。|  
  
## <a name="see-also"></a>参照  
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [レポート サーバー Web サービス メソッド](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [テクニカル リファレンス (SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
