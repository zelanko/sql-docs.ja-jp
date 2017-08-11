---
title: "アプリケーションにサービス レポートの統合 |Microsoft ドキュメント"
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
- integrating reports [Reporting Services]
- custom applications [SSRS]
- Reporting Services, application integration
- application integration [Reporting Services]
- reports [Reporting Services], integrating
ms.assetid: 49eb539c-d89b-4291-839a-0ec1a65cd270
caps.latest.revision: 57
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8a1cabc088c7c0ec6c69c8290549e035a4cec7bb
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="integrating-reporting-services-into-applications"></a>アプリケーションへの Reporting Services の統合
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、拡張性のあるオープンなレポート プラットフォームであり、ソリューションを開発するための API の包括的なセットを開発者に提供するように設計されています。  
  
 統合するための 3 つのオプションがある[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]カスタム アプリケーションに: レポート サーバー Web サービスとも呼ばれる、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API での ReportViewer コントロール[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]、および URL アクセス。 アプリケーションに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を統合する方法は、オプションごとに異なります。  
  
## <a name="report-server-web-service"></a>レポート サーバー Web サービス  
 レポート サーバー Web サービスは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に対して開発を行うための主要なインターフェイスです。 レポート カタログを管理するためのコードを開発する場合でも、サポートされている形式でレポートを表示するためのコードを開発する場合でも、Web サービスでは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアプリケーションに統合するために必要なすべての方法が公開されています。 このような 1 つのアプリケーションの例は、レポート マネージャーに含まれている[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]; をレポート サーバー データベースを管理する Web サービスを使用します。  
  
## <a name="reportviewer-controls-for-visual-studio"></a>Visual Studio の ReportViewer コントロール  
 [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] に付属の ReportViewer コントロールは、レポート表示機能をアプリケーションに統合するために使用されます。 コントロールには、Windows フォームベースのアプリケーション用と Web フォームのアプリケーション用の 2 つがあります。 どちらのコントロールにも、レポート サーバーに配置されたレポートを表示する機能と、レポート サーバーがインストールされていない環境にあるレポートを表示する機能があります。  
  
## <a name="url-access"></a>URL アクセス  
 URL アクセスは、ReportViewer コントロールがオプションでない場合にレポート表示機能をアプリケーションに統合するためのもう 1 つのオプションです。 さらに、電子メールを介してユーザーにレポートへのリンクを送信するためにも使用できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SOAP を使用した Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-soap.md)  
 レポート サーバー Web サービスを使用して、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のレポート ナビゲーションおよび管理を既存のビジネス アプリケーションに統合する方法について説明します。  
  
 [ReportViewer コントロールを使用して Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 ReportViewer コントロールを使用して、レポート表示機能を既存のアプリケーションに統合する方法について説明します。  
  
 [URL アクセスを使用した Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)  
 URL アクセスを使用して、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のレポート ナビゲーションを既存のビジネス アプリケーションに統合する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [レポート マネージャーと &#40; です。SSRS ネイティブ モードと &#41; です。](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [URL アクセスと SOAP の選択](../../reporting-services/application-integration/choosing-between-url-access-and-soap.md)   
 [テクニカル リファレンス & #40 です。SSRS &#41;](../../reporting-services/technical-reference-ssrs.md)   
 [レポート サーバー Web サービス](../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
