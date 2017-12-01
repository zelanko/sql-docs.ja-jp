---
title: "モデル メソッド - レポート サーバー Web サービス | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: d3e658c9-bb22-480b-a3d5-bcde8f537ab2
caps.latest.revision: "4"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: c9730c12ed92d1035238b6836016b0f62e03bba0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="model-methods---report-server-web-service"></a>モデル メソッド - レポート サーバー Web サービス
  これらのメソッドを使用して、モデルを管理できます。  
  
|方法|操作|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GenerateModel%2A>|共有データ ソース上に既定のモデルを生成します。|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPermissions%2A>|モデル アイテムに関連付けられたユーザー アクセス許可を取得します。|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPolicies%2A>|モデル アイテムに関連付けられたポリシーを取得します。|  
|<xref:ReportService2010.ReportingService2010.GetUserModel%2A>|現在のユーザーのモデルのセマンティック部分を返します。|  
|<xref:ReportService2010.ReportingService2010.InheritModelItemParentSecurity%2A>|モデル アイテムに関連付けられたポリシーを削除します。これにより、モデル アイテムは親からポリシーを継承します。|  
|<xref:ReportService2010.ReportingService2010.ListModelDrillthroughReports%2A>|モデル内のエンティティに関連付けられた詳細レポートの一覧を示します。|  
|<xref:ReportService2010.ReportingService2010.ListModelItemChildren%2A>|モデル アイテムの子要素の配列を返します。|  
|<xref:ReportService2010.ReportingService2010.ListModelItemTypes%2A>|サポートされているモデル アイテムの種類の一覧を返します。|  
|<xref:ReportService2010.ReportingService2010.ListModelPerspectives%2A>|ユーザーが利用できるモデルとパースペクティブの一覧を示します。|  
|<xref:ReportService2010.ReportingService2010.RegenerateModel%2A>|データ ソース スキーマの変更に基づいて既存のモデルを更新します。|  
|<xref:ReportService2010.ReportingService2010.RemoveAllModelItemPolicies%2A>|指定したモデル内のモデル アイテムに関連付けられたすべてのポリシーを削除します。|  
|<xref:ReportService2010.ReportingService2010.SetModelDrillthroughReports%2A>|一連の詳細レポートをモデルに関連付けます。|  
|<xref:ReportService2010.ReportingService2010.SetModelItemPolicies%2A>|モデル アイテムにセキュリティ ポリシーを設定します。|  
  
## <a name="see-also"></a>参照  
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [レポート サーバー Web サービス メソッド](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [テクニカル リファレンス (SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
