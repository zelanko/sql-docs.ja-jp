---
title: "Reporting Services の開発者向けドキュメント | Microsoft Docs"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
caps.latest.revision: "21"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 8fdeebfe932d265bed931b2c5bead413def304d1
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="reporting-services-developer-documentation"></a>Reporting Services の開発者向けのドキュメント
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] には、独自のアプリケーションで活用できるいくつかのプログラミング インターフェイスが用意されています。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の既存機能を使用して、カスタム レポート ツールと管理ツールを Web サイトや Windows アプリケーションに組み込むことができます。また、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のプラットフォームを拡張することもできます。  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] プラットフォームの拡張には、データへのアクセス、レポート配信などに使用できる新しいコンポーネントとリソースの作成もあります。 これらのコンポーネントとリソースは、組織内で [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] を使用している企業に販売できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] には、概要の把握に役立つプログラミング サンプルとチュートリアルが用意されています。 詳細については、「[Reporting Services サンプル](https://msdn.microsoft.com/library/ms160954\(v=sql.110\).aspx)」と「[開発者ガイド: チュートリアル (Reporting Services)](https://msdn.microsoft.com/library/aa337423\(v=sql.110\).aspx)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [アプリケーションへの Reporting Services の統合](../reporting-services/application-integration/integrating-reporting-services-into-applications.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] を使用してレポート機能をカスタム アプリーションに統合する方法の概要です。 レポート サーバーにアクセスするにあたり、どのような場合に直接的な URL アクセスを使用し、どのような場合に Web サービスを使用するかを説明します。  
  
 [レポート サーバー web サービス](../reporting-services/report-server-web-service/report-server-web-service.md)  
 レポート サーバー Web サービスでは、レポート サーバーのすべての機能にアクセスできます。 Web サービスは、HTTP に対して SOAP を使用し、クライアント プログラムとレポート サーバー間の通信インターフェイスとして動作するように設計されています。 Web サービスとそのメソッドは、レポート サーバーの機能を提供するため、管理から実行までのレポートのライフ サイクルのあらゆる部分にカスタム ツールを作成できます。  
  
 [URL アクセス (SSRS)](../reporting-services/url-access-ssrs.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、レポートのナビゲーションおよび表示を行うためにすばやくかつ簡単なアクセス ポイントとして使用できる URL ベースの完全な要求セットをサポートします。 このテクノロジをレポート サーバー Web サービスと組み合わせることにより、完全なレポート ソリューションをカスタム ビジネス アプリケーションに統合できます。 Web ポータルの一部としてレポートを統合するとき、または Web ブラウザーからレポートを表示するときに、URL アクセスが特に役立ちます。  
  
 [Reporting Services の拡張機能](../reporting-services/extensions/reporting-services-extensions.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のモジュール式アーキテクチャは、拡張性を考慮して設計されています。 マネージ コード API を使用して、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の多くのコンポーネントで使用される拡張機能を容易に開発、インストール、および管理できます。 発展するビジネス ニーズに対応するために、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] を使用してアセンブリを作成し、新しい [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の表示、セキュリティ、配信、およびデータ処理機能を追加できます。  
  
 [カスタム レポート アイテム](../reporting-services/custom-report-items/custom-report-items.md)  
 カスタム レポート アイテムを作成して RDL に機能を追加する方法、または既存のコントロールの機能を拡張する方法について説明します。  
  
 [レポートでのカスタム アセンブリの使用](../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
 レポート定義内にコード参照を含めることによって、カスタム アセンブリとレポートを併用する方法について説明します。  
  
 [Reporting Services WMI プロバイダーへのアクセス](../reporting-services/tools/access-the-reporting-services-wmi-provider.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] WMI プロバイダーを使用して、レポート サーバーの配置を管理する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services &#40;SSRS&#41;](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [レポート定義言語 &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)   
 [テクニカル リファレンス (SSRS)](../reporting-services/technical-reference-ssrs.md)   
 [セキュリティで保護された開発 &#40;Reporting Services&#41;](../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
  
  
