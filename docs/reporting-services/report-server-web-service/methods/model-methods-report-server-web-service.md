---
title: "レポート サーバー Web サービス メソッドをモデル化 |Microsoft ドキュメント"
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
applies_to:
- SQL Server 2016 Preview
ms.assetid: d3e658c9-bb22-480b-a3d5-bcde8f537ab2
caps.latest.revision: 4
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 6f95a5e6d379d9f0a998cb58cbf32c00be980884
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="model-methods---report-server-web-service"></a>モデルのメソッドのレポート サーバー Web サービス
  これらのメソッドを使用して、モデルを管理できます。  
  
|方法|操作|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GenerateModel%2A>|共有データ ソース上に既定のモデルを生成します。|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPermissions%2A>|モデル アイテムに関連付けられているユーザーのアクセス許可を取得します。|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPolicies%2A>|モデル アイテムに関連付けられたポリシーを取得します。|  
|<xref:ReportService2010.ReportingService2010.GetUserModel%2A>|現在のユーザーのモデルのセマンティック部分を返します。|  
|<xref:ReportService2010.ReportingService2010.InheritModelItemParentSecurity%2A>|モデル アイテムに関連付けられているポリシーを削除し、モデル アイテムは親からポリシーを継承します。|  
|<xref:ReportService2010.ReportingService2010.ListModelDrillthroughReports%2A>|モデル内のエンティティに関連付けられている詳細レポートを一覧表示します。|  
|<xref:ReportService2010.ReportingService2010.ListModelItemChildren%2A>|モデル アイテムの子要素の配列を返します。|  
|<xref:ReportService2010.ReportingService2010.ListModelItemTypes%2A>|サポートされているモデル アイテムの種類の一覧を返します。|  
|<xref:ReportService2010.ReportingService2010.ListModelPerspectives%2A>|モデルと、ユーザーが利用できるパースペクティブを一覧表示します。|  
|<xref:ReportService2010.ReportingService2010.RegenerateModel%2A>|データ ソース スキーマの変更に基づいて既存のモデルを更新します。|  
|<xref:ReportService2010.ReportingService2010.RemoveAllModelItemPolicies%2A>|指定されたモデル内のモデル アイテムに関連付けられているすべてのポリシーを削除します。|  
|<xref:ReportService2010.ReportingService2010.SetModelDrillthroughReports%2A>|ドリルスルー レポート、モデルとのセットに関連付けます。|  
|<xref:ReportService2010.ReportingService2010.SetModelItemPolicies%2A>|モデル アイテムにセキュリティ ポリシーを設定します。|  
  
## <a name="see-also"></a>参照  
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [レポート サーバー Web サービス メソッド](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [テクニカル リファレンス & #40 です。SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
