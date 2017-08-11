---
title: "URL アクセスと SOAP の選択 |Microsoft ドキュメント"
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
- SOAP [Reporting Services], vs. URL access
- Report Server Web service, application integration
- URL access [Reporting Services], vs. SOAP
- Web service [Reporting Services], application integration
ms.assetid: bccdc243-4366-4ce5-8e63-3dd6c463fa52
caps.latest.revision: 40
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: d53edb542a9666f4d5636f362e6689f33dbf9dcc
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="choosing-between-url-access-and-soap"></a>URL アクセスまたは SOAP の選択
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をカスタム アプリケーションへ統合するのは、必ずしも容易な作業ではありません。 ただし、その原因はプログラミング モデルや API が複雑なためではなく、統合方法が多数存在することです。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] はもともと開発者向けプラットフォームとして設計されているので、プログラミングを柔軟に行えるようになっています。 柔軟性を得るには、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のレポート ナビゲーション機能と管理機能を既存ビジネス アプリケーションに統合することに関して重要な意思決定を行う必要があります。  
  
 ![Reporting Services のプログラミング シナリオ](../../reporting-services/application-integration/media/bk-ext-04.gif "Reporting Services のプログラミング シナリオ")  
Reporting Services のプログラミングは、幅広いシナリオをサポートします。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をカスタム アプリケーションに統合するには、URL アクセスと Reporting Services SOAP API という 2 つの方法があります。 どちらの方法を使用するかは、いくつかの要因によって異なります。 状況によっては、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をカスタム ビジネス アプリケーションに統合する場合に URL アクセスと SOAP の両方が必要です。 決定に際して、次の事項を考慮する必要があります。  
  
-   自分自身、またはエンド ユーザーにとって、どのようなエンタープライズ レポート機能が必要か。 レポートの起動や操作はできるだけ簡単な方がよいのか、あるいは、カスタム ビジネス ソリューションの高度なレポート サーバー管理機能を使用する必要があるのか。  
  
-   一般的なユーザーの操作環境はどのようなものか。 ビジネス アプリケーションとして、Web アプリケーションを使用するのか、Windows アプリケーションを使用するのか。 エンド ユーザーは、Win32 環境から Web 環境へ簡単に切り替えることができるか。 レポートを実行および管理するうえで、どのような機能が必要か。  
  
 これらの事項を考慮したうえで、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を IT インフラストラクチャに統合する方法を決定してください。 通常、個別のレポートを表示およびナビゲートする場合は URL アクセスが適しています。 URL アクセスでは、Web サービスのオーバーヘッドなしにレポートを自由にすばやくナビゲートできます。 また、レポートのナビゲーションにレポートのツール バーを含む完全な HTML ビューアーを使用するプログラム技法は、現在のところ URL アクセスのみです。 URL アクセスでは、パフォーマンスも SOAP より向上します。サーバーからやり取りされる SOAP 要求のマーシャリングをバイパスするためです。 組み込まれたツールを使用してレポートを表示およびナビゲーションするために、すばやくかつ簡単なアクセスが必要な統合シナリオには、URL アクセスが適しています。  
  
> [!NOTE]  
>  レポート サーバー URL アクセスは、HTML ビューアーとレポート ツール バーの拡張された機能をサポートします。 SOAP API は、この種の表示レポートをサポートしません。 SOAP を使用してレポートを表示する場合は、独自のレポート ツール バーを設計および開発する必要があります。  
  
 レポート ツールバーの詳細については、次を参照してください。 [HTML ビューアーとレポート ツールバー](../../reporting-services/html-viewer-and-the-report-toolbar.md)です。  
  
 URL アクセスの詳細については、次を参照してください。 [URL アクセスと #40 です。SSRS &#41;](../../reporting-services/url-access-ssrs.md).  
  
 URL アクセスはレポートの表示に便利ですが、エンタープライズ レポート機能に不可欠なレポートと名前空間の管理機能はありません。 このような場合は、Reporting Services SOAP API の幅広く豊富な機能をお勧めします。 SOAP API を使用すると、レポートの管理と配置、スケジュールの作成、サーバーのプロパティの構成、レポート サーバー名前空間の管理、サブスクリプションの作成などが可能です。 SOAP API は、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の管理機能の完全なセットを提供します。 SOAP API では、API の <xref:ReportExecution2005.ReportExecutionService.Render%2A> メソッドを通してレポートを表示およびナビゲートすることもできます。 ただし、SOAP API を通してレポートを表示する場合は、レポート ツール バーの組み込み表示機能を使用できず、URL アクセスのようなレポート対話機能も自動的に処理されません。  
  
 Reporting Services SOAP API の詳細については、次を参照してください。[レポート サーバー Web サービス](../../reporting-services/report-server-web-service/report-server-web-service.md)です。  
  
 ほとんどの場合、レポート機能のニーズを満たすために URL アクセスと SOAP 呼び出しの両方が必要です。 SOAP を使用するのは、レポート サーバー データベースに最初に接続するときと、ユーザー インターフェイスに使用可能なレポートの一覧を表示するときです。URL アクセスを使用するのは、実際に個別のレポートにアクセスし、ナビゲートするときです。  
  
 URL アクセスと統合されたレポートを提供する Web サービスの組み合わせの例は、次を参照してください。 [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)です。  
  
## <a name="see-also"></a>参照  
 [アプリケーションへの Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [SOAP を使用して Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-soap.md)   
 [URL アクセスを使用して Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)   
 [テクニカル リファレンス & #40 です。SSRS &#41;](../../reporting-services/technical-reference-ssrs.md)  
  
  
