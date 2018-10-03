---
title: 開発者&#39;ガイド (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 16c0f4451b66b0aa0c004476a4dc332acf973a1c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116012"
---
# <a name="developer39s-guide-reporting-services"></a>開発者&#39;ガイド (Reporting Services)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] には、独自のアプリケーションで活用できるいくつかのプログラミング インターフェイスが用意されています。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の既存機能を使用して、カスタム レポート ツールと管理ツールを Web サイトや Windows アプリケーションに組み込むことができます。また、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のプラットフォームを拡張することもできます。  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] プラットフォームの拡張には、データへのアクセス、レポート配信などに使用できる新しいコンポーネントとリソースの作成もあります。 これらのコンポーネントとリソースは、組織内で [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] を使用している企業に販売できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [アプリケーションへの Reporting Services の統合](application-integration/integrating-reporting-services-into-applications.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] を使用してレポート機能をカスタム アプリーションに統合する方法の概要です。 レポート サーバーにアクセスするにあたり、どのような場合に直接的な URL アクセスを使用し、どのような場合に Web サービスを使用するかを説明します。  
  
 [レポート サーバー web サービス](report-server-web-service/report-server-web-service.md)  
 レポート サーバー Web サービスでは、レポート サーバーのすべての機能にアクセスできます。 Web サービスは、HTTP に対して SOAP を使用し、クライアント プログラムとレポート サーバー間の通信インターフェイスとして動作するように設計されています。 Web サービスとそのメソッドは、レポート サーバーの機能を提供するため、管理から実行までのレポートのライフ サイクルのあらゆる部分にカスタム ツールを作成できます。  
  
 [URL アクセス &#40;SSRS&#41;](url-access-ssrs.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、レポートのナビゲーションおよび表示を行うためにすばやくかつ簡単なアクセス ポイントとして使用できる URL ベースの完全な要求セットをサポートします。 このテクノロジをレポート サーバー Web サービスと組み合わせることにより、完全なレポート ソリューションをカスタム ビジネス アプリケーションに統合できます。 Web ポータルの一部としてレポートを統合するとき、または Web ブラウザーからレポートを表示するときに、URL アクセスが特に役立ちます。  
  
 [Reporting Services の拡張機能](extensions/reporting-services-extensions.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のモジュール式アーキテクチャは、拡張性を考慮して設計されています。 マネージド コード API を使用して、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の多くのコンポーネントで使用される拡張機能を容易に開発、インストール、および管理できます。 発展するビジネス ニーズに対応するために、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] を使用してアセンブリを作成し、新しい [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の表示、セキュリティ、配信、およびデータ処理機能を追加できます。  
  
 [カスタム レポート アイテム](custom-report-items/custom-report-items.md)  
 カスタム レポート アイテムを作成して RDL に機能を追加する方法、または既存のコントロールの機能を拡張する方法について説明します。  
  
 [レポートでのカスタム アセンブリの使用](custom-assemblies/using-custom-assemblies-with-reports.md)  
 レポート定義内にコード参照を含めることによって、カスタム アセンブリとレポートを併用する方法について説明します。  
  
 [Reporting Services WMI プロバイダーへのアクセス](tools/access-the-reporting-services-wmi-provider.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] WMI プロバイダーを使用して、レポート サーバーの配置を管理する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [レポート定義言語 &#40;SSRS&#41;](reports/report-definition-language-ssrs.md)   
 [テクニカル リファレンス (SSRS)](technical-reference-ssrs.md)   
 [セキュリティで保護された開発 &#40;Reporting Services&#41;](extensions/secure-development/secure-development-reporting-services.md)  
  
  
