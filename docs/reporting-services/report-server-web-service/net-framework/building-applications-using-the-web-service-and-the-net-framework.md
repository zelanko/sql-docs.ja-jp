---
title: "Web サービスと、.NET Framework を使用してアプリケーションを構築 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
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
- Report Server Web service, application building
- .NET Framework [Reporting Services]
- XML Web service [Reporting Services], client creation
- reports [Reporting Services], building
- Web service [Reporting Services], application building
- Report Server Web service, client creation
- client configuration [Reporting Services]
- XML Web service [Reporting Services], application building
- Web service [Reporting Services], client creation
ms.assetid: 92a9678c-bc4f-4d7a-ba44-85989bfe27ca
caps.latest.revision: 38
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 58588838e0e74b545290df5ff0e77dc68ad5e918
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="building-applications-using-the-web-service-and-the-net-framework"></a>Building Applications Using the Web Service and the .NET Framework
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]メソッド、プリミティブ型などの使い慣れたプログラミング構造を使用することができます、およびユーザー定義の複合が Web サービスを使用する型します。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] により、W3C (World Wide Web Consortium) の標準に準拠した任意の Web サービスを呼び出すことができる、Web サービス クライアントを作成するためのインフラストラクチャとツールが提供されます。  
  
 レポート サーバー Web サービス クライアントとは、Simple Object Access Protocol (SOAP) メッセージを使用して、レポート サーバーと通信をする任意のコンポーネントまたはアプリケーションのことです。  
  
 **.NET Framework を使用してレポート サーバー Web サービス クライアントを作成するには、次の基本的な手順を実行します。**  
  
1.  Web サービスのプロキシ クラスを作成します。  
  
     そのためには、プロキシ クラスまたは Web 参照を開発プロジェクトに追加し、クライアント コードでそのプロキシ クラスを参照します。次に、そのプロキシのインスタンスを生成します。 詳細については、次を参照してください。 [Web サービス プロキシを作成する](../../../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md)です。  
  
2.  レポート サーバーで Web サービス クライアントを認証します。  
  
     そのためには、サービス オブジェクトの <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> プロパティを、レポート サーバーで認証されるユーザーの資格情報と同じに設定します。 詳細については、次を参照してください。 [Web サービス認証](../../../reporting-services/report-server-web-service/net-framework/web-service-authentication.md)です。  
  
3.  呼び出す Web サービス操作に対応したプロキシ クラスのメソッドを呼び出します。  
  
     そのためには、Web サービス メソッドを呼び出し、必要な引数を指定します。 Web サービス メソッドの詳細については、次を参照してください。[レポート サーバー Web サービス メソッド](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)です。 呼び出し元の詳細については、次を参照してください。 [Web サービス メソッドを呼び出して](../../../reporting-services/report-server-web-service/net-framework/calling-web-service-methods.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[Web サービス プロキシの作成](../../../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md)|プロキシ クラスを使用して、プロジェクトに追加する方法について説明[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]です。|  
|[Web サービスの認証](../../../reporting-services/report-server-web-service/net-framework/web-service-authentication.md)|レポート サーバー Web サービスに対する呼び出しの認証方法について説明します。|  
|[Web サービス メソッドの呼び出し](../../../reporting-services/report-server-web-service/net-framework/calling-web-service-methods.md)|Web サービス メソッドを呼び出すには SOAP API を使用する方法について説明[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]です。|  
|[Web サービスの Url プロパティを設定](../../../reporting-services/report-server-web-service/net-framework/setting-the-url-property-of-the-web-service.md)|Web 参照の作成後に新しいサーバーの URL を Web サービス プロキシに知らせるためのプログラミング方法について説明します。|  
|[Web サービス メソッドの引数を指定します。](../../../reporting-services/report-server-web-service/net-framework/supplying-web-service-method-arguments.md)|Web サービス メソッドを呼び出す方法およびメソッドの引数の指定方法を説明します。|  
|[省略可能な Web サービス オブジェクトの値を省略](../../../reporting-services/report-server-web-service/net-framework/omitting-values-for-optional-web-service-objects.md)|省略可能な Web サービス オブジェクトの値の省略方法を説明します。|  
|[セキュリティで保護された Web サービス メソッドを使用します。](../../../reporting-services/report-server-web-service/net-framework/using-secure-web-service-methods.md)|について説明します、 **SecureConnectionLevel**設定と Reporting Services SOAP API の使用に影響する方法です。|  
|[表示拡張機能にデバイス情報設定を渡す](../../../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)|異なる形式でレポートを表示するための、デバイス情報の設定について説明します。|  
|[Reporting Services 配信拡張機能の設定](../../../reporting-services/report-server-web-service/net-framework/reporting-services-delivery-extension-settings.md)|レポート サーバーの電子メールを使用してレポートを配信するための設定について説明します。|  
|[SOAP ヘッダーをサービス レポートを使用します。](../../../reporting-services/report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の SOAP ヘッダーの使用について説明します。|  
|[Reporting Services での例外処理の概要](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のエラー処理方法に関する情報を提供します。|  
  
## <a name="see-also"></a>参照  
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [テクニカル リファレンス & #40 です。SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
