---
title: Reporting Services での例外を処理 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: report-server-web-service-net-framework-exception-handling
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SOAP [Reporting Services], exceptions
- .NET Framework [Reporting Services]
- exceptions [Reporting Services], about exception handling
- SoapException object
ms.assetid: 1a443432-2db5-48c5-bc29-433b4688082f
caps.latest.revision: 31
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 75bc7d7f057c9207a0f70525acf61072b82f3469
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="handling-exceptions-in-reporting-services"></a>Reporting Services の例外の処理
  Reporting Services SOAP API クライアント要求を完了できない場合は、レポート サーバーが予期した呼び出しの結果ではなくエラーを返します。 呼び出しを完了できない場合は、レポート サーバー Web サービスのエラーが SOAP **Fault** XML 要素として返されます。 エラー解消の鍵となる要素は **detail** 要素です。この要素には、レポート サーバーが提供するすべてのエラー情報に加えて、Web サービス エラー情報も含まれています。 **detail** 要素の中の最重要情報は、レポート サーバー エラー コードです。 メッセージとエラー コードから、アプリケーションで次にとるべき適切な処理を判断することができます。 SOAP エラーの詳細については、W3C (World Wide Web Consortium) の Web サイト (http://www.w3.org/TR/SOAP) を参照してください。  
  
## <a name="soap-faults-and-the-net-framework"></a>SOAP のエラーと .NET Framework  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] では、Web サービスへのクライアント要求にエラーが発生した場合に、レポート サーバーが **SoapException** オブジェクトをスローすることによって Web サービスを呼び出すクライアント コードにエラーを通知します。 **SoapException** は SOAP エラーに含まれる情報をラップします。 **SoapException** の **Detail** プロパティは、SOAP エラーの **detail** 要素にマップされます。 アプリケーションは **SoapException** オブジェクトを try ブロックまたは catch ブロックと共にキャッチし、**SoapException** の **Detail** プロパティを使用して適切な処理を行う必要があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の **SoapException** クラスと **Detail** プロパティの詳細については、「[Reporting Services SoapException クラス](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)」を参照してください。 **SoapException** クラスの詳細については、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK ドキュメントを参照してください。  
  
## <a name="see-also"></a>参照  
 [Detail プロパティ](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)   
 [Reporting Services における例外処理の概要](../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException クラス](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
