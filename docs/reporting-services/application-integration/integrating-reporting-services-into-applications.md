---
title: "アプリケーションにサービス レポートの統合 |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/19/2017
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
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 26e1da5a720aab965d014cada16f85086e0f70a0
ms.contentlocale: ja-jp
ms.lasthandoff: 10/20/2017

---
# <a name="integrating-reporting-services-into-applications"></a>アプリケーションへの Reporting Services の統合

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、拡張性のあるオープンなレポート プラットフォームであり、ソリューションを開発するための API の包括的なセットを開発者に提供するように設計されています。

> [!NOTE]
> SQL Server 2017 Reporting Services から始めて、REST API アクセスがあるソリューションを開発するためです。 SOAP API のアクセスは廃止されました。 詳細については、次を参照してください。 [Reporting Services の REST Api を使用した開発](../developer/rest-api.md)です。
  
 統合するための 3 つのオプションがある[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]カスタム アプリケーションに: レポート サーバー Web サービスとも呼ばれる、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API での ReportViewer コントロール[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、および URL アクセス。 アプリケーションに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を統合する方法は、オプションごとに異なります。
  
## <a name="report-server-web-service"></a>レポート サーバー Web サービス

 レポート サーバー Web サービスは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に対して開発を行うための主要なインターフェイスです。 レポート カタログを管理するためのコードを開発する場合でも、サポートされている形式でレポートを表示するためのコードを開発する場合でも、Web サービスでは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアプリケーションに統合するために必要なすべての方法が公開されています。 このような 1 つのアプリケーションの例は、レポート マネージャーに含まれている[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]; をレポート サーバー データベースを管理する Web サービスを使用します。  
  
## <a name="reportviewer-controls-for-visual-studio"></a>Visual Studio の ReportViewer コントロール

 ReportViewer コントロールの使用可能な[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]をアプリケーションに表示するレポートを統合するために使用されます。 コントロールには、Windows フォームベースのアプリケーション用と Web フォームのアプリケーション用の 2 つがあります。 どちらのコントロールにも、レポート サーバーに配置されたレポートを表示する機能と、レポート サーバーがインストールされていない環境にあるレポートを表示する機能があります。  
  
## <a name="url-access"></a>URL アクセス  
 URL アクセスは、ReportViewer コントロールがオプションでない場合にレポート表示機能をアプリケーションに統合するためのもう 1 つのオプションです。 さらに、電子メールを介してユーザーにレポートへのリンクを送信するためにも使用できます。  
  
## <a name="in-this-section"></a>このセクションの内容

 [SOAP を使用した Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-soap.md)  
 レポート サーバー Web サービスを使用して、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のレポート ナビゲーションおよび管理を既存のビジネス アプリケーションに統合する方法について説明します。  
  
 [ReportViewer コントロールを使用して Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 ReportViewer コントロールを使用して、レポート表示機能を既存のアプリケーションに統合する方法について説明します。  
  
 [URL アクセスを使用した Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)  
 URL アクセスを使用して、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のレポート ナビゲーションを既存のビジネス アプリケーションに統合する方法について説明します。  
  
## <a name="next-steps"></a>次の手順

URL アクセスまたは SOAP Api を使用して決定する、次を参照してください。 [URL アクセスと SOAP in Reporting Services の間で選択](choosing-between-url-access-and-soap.md)です。

SQL Server 2017 Reporting Services REST API については、次を参照してください。 [Reporting Services の REST Api を使用した開発](../developer/rest-api.md)です。

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
