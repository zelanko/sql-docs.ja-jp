---
title: "SOAP を使用してサービス レポートの統合 |Microsoft ドキュメント"
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
- Report Server Web service, application integration
- SOAP [Reporting Services]
- SOAP [Reporting Services], about report integration
- integrating reports [Reporting Services]
- Web service [Reporting Services], application integration
ms.assetid: 6bc17af5-883c-4bfa-87d9-48cd7056d145
caps.latest.revision: 45
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: f993204ae0c9140a5fba51c125ce1d57d0e3a125
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="integrating-reporting-services-using-soap"></a>SOAP を使用した Reporting Services の統合
  [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API は、カスタム レポート ソリューション開発のいくつかの Web サービス エンドポイントを提供します。 現在、このエンドポイントは、管理と実行という 2 つのカテゴリに分類されます。 管理機能は、<xref:ReportService2005> エンドポイント、<xref:ReportService2006> エンドポイント、および <xref:ReportService2010> エンドポイントを介して公開されます。 <xref:ReportService2005> エンドポイントは、ネイティブ モードで構成されたレポート サーバーを管理するために使用され、<xref:ReportService2006> エンドポイントは、SharePoint 統合モード用に構成されたレポート サーバーを管理するために使用されます。 <xref:ReportService2010> は、<xref:ReportService2005> と <xref:ReportService2006> の機能をまとめたものであり、ネイティブ モード用または SharePoint 統合モード用に構成されているレポート サーバーを管理できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] では、<xref:ReportService2005> エンドポイントと <xref:ReportService2006> エンドポイントは非推奨です。 <xref:ReportService2010> エンドポイントには、両方のエンドポイントの機能と追加の管理機能が含まれています。  
  
 実行機能は <xref:ReportExecution2005> エンドポイントを介して公開され、レポート サーバーがネイティブ モードまたは SharePoint 統合モードで構成されているときに使用されます。 次の各トピックでは、これらのエンドポイントを使用して [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows、SharePoint、および Web アプリケーションでどのようにレポート ソリューションを開発するかについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Windows アプリケーションで SOAP API の使用](../../reporting-services/application-integration/integrating-reporting-services-using-soap-windows-application.md)  
 SOAP API を使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を Windows 環境に統合する方法について説明します。  
  
 [Web アプリケーションで SOAP API の使用](../../reporting-services/application-integration/integrating-reporting-services-using-soap-web-application.md)  
 SOAP API を使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を Web 環境に統合する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [アプリケーションへの Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [レポート サーバー Web サービス](../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
