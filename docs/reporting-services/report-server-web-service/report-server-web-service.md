---
title: "レポート サーバー Web サービス |Microsoft ドキュメント"
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
- SSIS, Web service
- Web service [Reporting Services]
- Reporting Services, extending
- SQL Server Reporting Services, Web service
- Reporting Services, Web service
- XML Web service [Reporting Services]
- Report Server Web service
ms.assetid: 16c21dec-6b46-4497-9a0c-1b0f2b6ab8fc
caps.latest.revision: 47
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 5fd4d415e452549e80aa12b9eb1397bf83ce6557
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="report-server-web-service"></a>レポート サーバー Web サービス
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]レポート サーバー Web サービスを通じて、レポート サーバーのすべての機能へのアクセスを提供します。 レポート サーバー Web サービスは、SOAP API を使用した XML Web サービスです。 SOAP over HTTP を使用し、クライアント プログラムとレポート サーバー間の通信インターフェイスとして機能します。 Web サービスは 2 つのエンドポイントを提供します。1 つはレポートを実行するためのもので、もう 1 つはレポートを管理するためのものです。加えて、レポート サーバーの機能を公開するメソッドが用意されています。このメソッドにより、レポートのライフ サイクルの任意の時点に対するカスタム ツールを作成できます。  
  
 3 つの主な方法を開発する[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Web サービスに基づくアプリケーションです。 可能な代替手段としては以下の方法があります。  
  
-   使用してアプリケーションを開発[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]と[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK。 使用しての詳細については、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Web サービス アプリケーションを構築するを参照してください。 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)です。  
  
-   使用してアプリケーションを開発、 **rs**ユーティリティ (RS.exe)、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]スクリプト環境です。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]と[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]スクリプトを実行してレポート サーバー Web サービス操作。 スクリプトの詳細については[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を参照してください[ユーティリティと Web サービスは、スクリプト、rs.exe と](../../reporting-services/tools/script-with-the-rs-exe-utility-and-the-web-service.md)です。  
  
-   SOAP 対応の開発ツールを使用してアプリケーションを開発する。 詳細については、次を参照してください。 [The Role of SOAP in Reporting Services](../../reporting-services/report-server-web-service/the-role-of-soap-in-reporting-services.md)です。  
  
## <a name="programming-diagram"></a>プログラミング図  
 ![レポート サーバー Web サービス開発オプション](../../reporting-services/report-server-web-service/media/reportserviceswebserviceprog-01.gif "Report Server Web service development options")  
Reporting Services で利用可能な Web サービス開発オプション  
  
## <a name="in-this-section"></a>このセクションの内容  
 [レポート サーバー Web サービス メソッド](../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)  
 各レポート サーバー Web サービスの機能とメソッドについて説明します。  
  
 [Reporting Services における SOAP の役割](../../reporting-services/report-server-web-service/the-role-of-soap-in-reporting-services.md)  
 SOAP の概要およびレポート サーバー Web サービスでの使用方法について説明します。  
  
 [SOAP API にアクセスします。](../../reporting-services/report-server-web-service/accessing-the-soap-api.md)  
 Web サービス記述言語 (WSDL) について説明し、Reporting Services WSDL ファイルにアクセスするための URL を記載します。  
  
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
 Reporting Services SOAP API を呼び出すアプリケーションと Web サービスの開発について説明します。  
  
 [Rs.exe ユーティリティと Web サービスのスクリプト](../../reporting-services/tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] スクリプト環境の概要を説明します。  
  
 [テクニカル リファレンス (SSRS)](../../reporting-services/technical-reference-ssrs.md)  
 レポート サーバー Web サービスのメソッドおよび対応する複合型のリファレンス情報です。  
  
## <a name="user-requirements-for-web-service-development"></a>Web サービスを開発するためのユーザーの必要条件  
 レポート サーバー Web サービスを使用してアプリケーションを開発するには、次の必要条件を満たす必要があります。  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)]Internet Explorer 5.5 以降がインターネットに接続して、レポート サーバーへのアクセスがあるコンピューターにインストールされています。  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]または[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]開発および配置する場合は、コンピューターにインストールされている SDK[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を使用するアプリケーション、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]です。  
  
-   詳細に検討する[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]機能と機能します。  
  
-   SOAP および [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)] に関する十分な知識があること。  
  
-   開発エクスペリエンス、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-など、互換性のある言語[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[csprcs](../../includes/csprcs-md.md)]または[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]を使用する場合、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]開発プラットフォームとして。  
  
## <a name="see-also"></a>参照  
 [レポート サーバー Web サービス](../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  

