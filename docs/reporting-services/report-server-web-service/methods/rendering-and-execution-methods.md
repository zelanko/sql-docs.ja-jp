---
title: "レンダリング メソッドと Execution メソッド |Microsoft ドキュメント"
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
helpviewer_keywords:
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
caps.latest.revision: 36
author: sabotta
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c56c8b0a0fc4e2cb6f6bc78710e6fd4ed8e77cff
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

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
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [レポート サーバー Web サービス メソッド](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [テクニカル リファレンス & #40 です。SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
