---
title: "Reporting Services における例外処理の概要 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: report-server-web-service-net-framework-exception-handling
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Web service [Reporting Services], exception handling
- errors [Reporting Services]
- exceptions [Reporting Services]
- Report Server Web service, exception handling
- XML Web service [Reporting Services], exception handling
ms.assetid: 54381870-ce67-482b-aa83-6a838cdbf9b9
caps.latest.revision: "29"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9d8b566100b09c485df3a713191e90a180b05746
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="introducing-exception-handling-in-reporting-services"></a>Reporting Services における例外処理の概要
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーションが要求をレポート サーバー Web サービスに送信し、サービスが要求を処理できない場合、サービスは SOAP 例外をクライアントに返します。 レポート サーバー Web サービスによってスローされた例外の処理は、開発するアプリケーションの重要な部分です。エラーが発生した場合にユーザーに有益な情報を返すことができるからです。  
  
 ここでは、例外の処理、無効なユーザー入力の回避、およびユーザーへの有意義なエラー情報の送信について説明します。 例外処理の一般的な情報については、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK ドキュメントの「例外の処理とスロー」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[Reporting Services での例外を処理](../../reporting-services/report-server-web-service-net-framework-exception-handling/handling-exceptions-in-reporting-services.md)|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] における例外および Web サービスからエラーを返すときの SOAP の役割について説明します。|  
|[Reporting Services 例外処理のベスト プラクティス](../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/best-practices-for-reporting-services-exception-handling.md)|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] での例外処理に関する推奨事項が記載されています。|  
|[Reporting Services SoapException クラス](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の **SoapException** クラスについて説明します。|  
  
## <a name="see-also"></a>参照  
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
