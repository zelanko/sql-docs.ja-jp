---
title: URL アクセスと SOAP | を選択するMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], vs. URL access
- Report Server Web service, application integration
- URL access [Reporting Services], vs. SOAP
- Web service [Reporting Services], application integration
ms.assetid: bccdc243-4366-4ce5-8e63-3dd6c463fa52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 59e44b53baff0cd55c6a8016408fd2af685bbc26
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78173959"
---
# <a name="choosing-between-url-access-and-soap"></a>URL アクセスまたは SOAP の選択
  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をカスタム アプリケーションへ統合するのは、必ずしも容易な作業ではありません。 ただし、その原因はプログラミング モデルや API が複雑なためではなく、統合方法が多数存在することです。 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] はもともと開発者向けプラットフォームとして設計されているので、プログラミングを柔軟に行えるようになっています。 柔軟性を得るには、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のレポート ナビゲーション機能と管理機能を既存ビジネス アプリケーションに統合することに関して重要な意思決定を行う必要があります。

 ![Reporting Services のプログラミングシナリオ](../../../2014/reporting-services/media/bk-ext-04.gif "Reporting Services のプログラミング シナリオ")Reporting Services プログラミングでは、幅広いシナリオをサポートしています。

 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をカスタム アプリケーションに統合するには、URL アクセスと Reporting Services SOAP API という 2 つの方法があります。 どちらの方法を使用するかは、いくつかの要因によって異なります。 状況によっては、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をカスタム ビジネス アプリケーションに統合する場合に URL アクセスと SOAP の両方が必要です。 決定に際して、次の事項を考慮する必要があります。

-   自分自身、またはエンド ユーザーにとって、どのようなエンタープライズ レポート機能が必要か。 レポートの起動や操作はできるだけ簡単な方がよいのか、あるいは、カスタム ビジネス ソリューションの高度なレポート サーバー管理機能を使用する必要があるのか。

-   一般的なユーザーの操作環境はどのようなものか。 ビジネス アプリケーションとして、Web アプリケーションを使用するのか、Windows アプリケーションを使用するのか。 エンド ユーザーは、Win32 環境から Web 環境へ簡単に切り替えることができるか。 レポートを実行および管理するうえで、どのような機能が必要か。

 これらの事項を考慮したうえで、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を IT インフラストラクチャに統合する方法を決定してください。 通常、個別のレポートを表示およびナビゲートする場合は URL アクセスが適しています。 URL アクセスでは、Web サービスのオーバーヘッドなしにレポートを自由にすばやくナビゲートできます。 また、レポートのナビゲーションにレポートのツール バーを含む完全な HTML ビューアーを使用するプログラム技法は、現在のところ URL アクセスのみです。 URL アクセスでは、パフォーマンスも SOAP より向上します。サーバーからやり取りされる SOAP 要求のマーシャリングをバイパスするためです。 組み込まれたツールを使用してレポートを表示およびナビゲーションするために、すばやくかつ簡単なアクセスが必要な統合シナリオには、URL アクセスが適しています。

> [!NOTE]
>  レポート サーバー URL アクセスは、HTML ビューアーとレポート ツール バーの拡張された機能をサポートします。 SOAP API は、この種の表示レポートをサポートしません。 SOAP を使用してレポートを表示する場合は、独自のレポート ツール バーを設計および開発する必要があります。

 レポート ツール バーの詳細については、「[HTML Viewer and the Report Toolbar](../html-viewer-and-the-report-toolbar.md)」(HTML ビューアーとレポート ツール バー) を参照してください。

 URL アクセスの詳細については、「 [Url アクセス &#40;SSRS&#41;](../url-access-ssrs.md)」を参照してください。

 URL アクセスはレポートの表示に便利ですが、エンタープライズ レポート機能に不可欠なレポートと名前空間の管理機能はありません。 このような場合は、Reporting Services SOAP API の幅広く豊富な機能をお勧めします。 SOAP API を使用すると、レポートの管理と配置、スケジュールの作成、サーバーのプロパティの構成、レポート サーバー名前空間の管理、サブスクリプションの作成などが可能です。 SOAP API は、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の管理機能の完全なセットを提供します。 SOAP API では、API の <xref:ReportExecution2005.ReportExecutionService.Render%2A> メソッドを通してレポートを表示およびナビゲートすることもできます。 ただし、SOAP API を通してレポートを表示する場合は、レポート ツール バーの組み込み表示機能を使用できず、URL アクセスのようなレポート対話機能も自動的に処理されません。

 Reporting Services SOAP API の詳細については、「[Report Server Web Service](../report-server-web-service/report-server-web-service.md)」(Report Server Web サービス) を参照してください。

 ほとんどの場合、レポート機能のニーズを満たすために URL アクセスと SOAP 呼び出しの両方が必要です。 SOAP を使用するのは、レポート サーバー データベースに最初に接続するときと、ユーザー インターフェイスに使用可能なレポートの一覧を表示するときです。URL アクセスを使用するのは、実際に個別のレポートにアクセスし、ナビゲートするときです。

 URL アクセスと Web サービスを組み合わせて統合レポート機能を実現する例については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」(SQL Server Reporting Services 製品サンプル) を参照してください。

## <a name="see-also"></a>参照
 [SOAP を使用](../application-integration/integrating-reporting-services-using-soap.md)した[アプリケーションへの Reporting Services](../../../2014/reporting-services/application-integration/integrating-reporting-services-into-applications.md)の統合[Reporting Services URL アクセスを](../application-integration/integrating-reporting-services-using-url-access.md)使用した Reporting Services の統合に[関するテクニカルリファレンス &#40;SSRS&#41;](../../../2014/reporting-services/technical-reference-ssrs.md)


