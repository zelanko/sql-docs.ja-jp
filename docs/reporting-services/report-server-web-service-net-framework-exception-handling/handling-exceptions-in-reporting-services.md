---
title: "Reporting Services の例外の処理 |Microsoft ドキュメント"
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
- SOAP [Reporting Services], exceptions
- .NET Framework [Reporting Services]
- exceptions [Reporting Services], about exception handling
- SoapException object
ms.assetid: 1a443432-2db5-48c5-bc29-433b4688082f
caps.latest.revision: 31
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 7e1472c11575ba8bed99992ec9630e408c347291
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="handling-exceptions-in-reporting-services"></a>Reporting Services の例外の処理
  Reporting Services SOAP API クライアント要求を完了できない場合は、レポート サーバーが予期した呼び出しの結果ではなくエラーを返します。 呼び出しを完了できない場合、レポート サーバー Web サービスのエラーが SOAP として返されます。**フォールト**XML 要素です。 エラーのキーのわかりやすい要素は、**詳細**要素は、すべてのレポート サーバーだけでなく、追加の Web サービス エラー情報によって提供されるエラー情報が含まれています。 キー情報、**詳細**要素は、レポート サーバーのエラー コード。 メッセージとエラー コードから、アプリケーションで次にとるべき適切な処理を判断することができます。 SOAP エラーの詳細については、W3C (World Wide Web Consortium) の Web サイト (http://www.w3.org/TR/SOAP) を参照してください。  
  
## <a name="soap-faults-and-the-net-framework"></a>SOAP のエラーと .NET Framework  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]、レポート サーバーの通信エラーをスローすることによって、Web サービスを呼び出すクライアント コードを Web サービスへのクライアント要求で、エラーが発生した場合、 **SoapException**オブジェクト。 **SoapException** SOAP エラーに含まれる情報をラップします。 **詳細**のプロパティ、 **SoapException**にマップ、**詳細**SOAP エラー内の要素。 アプリケーションをキャッチする必要があります、 **SoapException** try ブロックと catch ブロックでオブジェクトを使用して、**詳細**のプロパティ、 **SoapException**適切な操作を実行します。 詳細については、 **SoapException**クラスおよび**詳細**プロパティ[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を参照してください[Reporting Services SoapException クラス](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)です。 詳細については、 **SoapException**クラスを参照してください、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK のドキュメントです。  
  
## <a name="see-also"></a>参照  
 [Detail プロパティ](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)   
 [Reporting Services での例外処理の概要](../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException クラス](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
