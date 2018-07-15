---
title: メソッドのスケジュール設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- schedules [Reporting Services], methods
- reports [Reporting Services], scheduling
- shared schedules [Reporting Services], methods
- methods [Reporting Services], scheduling
ms.assetid: 68ae13f9-d91e-4572-a82a-8fa42001569e
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: f4e9adafb6fa7311ca246e2ce4233ed03e073df1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282628"
---
# <a name="scheduling-methods"></a>メソッドのスケジュール設定
  これらのメソッドを使用して、レポート サーバーが利用する、レポートの実行と配信のための共有スケジュールとキャッシュ更新計画を作成および管理できます。  
  
|方法|操作|  
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
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../report-server-web-service.md)   
 [レポート サーバー Web サービス メソッド](report-server-web-service-methods.md)   
 [テクニカル リファレンス (SSRS)](../../technical-reference-ssrs.md)  
  
  
