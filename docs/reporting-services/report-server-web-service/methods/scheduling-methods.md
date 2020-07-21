---
title: メソッドのスケジュール設定 | Microsoft Docs
description: レポート サービスでは、これらのメソッドにより、レポートの実行と配信のための共有スケジュールと、レポート サーバーで使用されるキャッシュ更新計画を作成および管理します。
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- schedules [Reporting Services], methods
- reports [Reporting Services], scheduling
- shared schedules [Reporting Services], methods
- methods [Reporting Services], scheduling
ms.assetid: 68ae13f9-d91e-4572-a82a-8fa42001569e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 087e2111987de00b347c400ce7255cb7f9eee97e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "79198339"
---
# <a name="scheduling-methods"></a>メソッドのスケジュール設定
  これらのメソッドを使用して、レポート サーバーが利用する、レポートの実行と配信のための共有スケジュールとキャッシュ更新計画を作成および管理できます。  
  
|方法|アクション|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateCacheRefreshPlan%2A>|アイテムのキャッシュ更新プランを作成します。|  
|<xref:ReportService2010.ReportingService2010.CreateSchedule%2A>|新しい共有スケジュールを作成します。|  
|<xref:ReportService2010.ReportingService2010.DeleteCacheRefreshPlan%2A>|キャッシュ更新プランを削除します。|  
|<xref:ReportService2010.ReportingService2010.DeleteSchedule%2A>|特定のスケジュール ID に基づいて共有スケジュールを削除します。|  
|<xref:ReportService2010.ReportingService2010.GetCacheRefreshPlanProperties%2A>|指定したキャッシュ更新プランのプロパティを返します。|  
|<xref:ReportService2010.ReportingService2010.GetScheduleProperties%2A>|共有スケジュールのプロパティ値を返します。|  
|<xref:ReportService2010.ReportingService2010.ListCacheRefreshPlans%2A>|カタログ アイテムに関連付けられたキャッシュ更新プランの一覧を返します。|  
|<xref:ReportService2010.ReportingService2010.ListScheduledItems%2A>|共有スケジュールに関連付けられたアイテムの一覧を返します。|  
|<xref:ReportService2010.ReportingService2010.ListSchedules%2A>|レポート サーバーまたは SharePoint サイトにおけるすべての共有スケジュールの一覧を返します。|  
|<xref:ReportService2010.ReportingService2010.ListScheduleStates%2A>|サポートされているスケジュールの状態の一覧を返します。|  
|<xref:ReportService2010.ReportingService2010.PauseSchedule%2A>|指定したスケジュールの実行を一時停止します。|  
|<xref:ReportService2010.ReportingService2010.ResumeSchedule%2A>|一時停止している共有スケジュールを再開します。|  
|<xref:ReportService2010.ReportingService2010.SetCacheRefreshPlanProperties%2A>|キャッシュ更新計画のプロパティを設定します。|  
|<xref:ReportService2010.ReportingService2010.SetScheduleProperties%2A>|共有スケジュールのプロパティ値を設定します。|  
  
## <a name="see-also"></a>参照  
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [レポート サーバー Web サービス メソッド](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [テクニカル リファレンス (SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
