---
title: "表示拡張機能にデバイス情報設定を渡す |Microsoft ドキュメント"
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
- device information settings [Reporting Services]
- Render method
- Report Server Web service, device information settings
- Web service [Reporting Services], device information settings
- XML Web service [Reporting Services], device information settings
- passing device information [Reporting Services]
- rendering extensions [Reporting Services], device information settings
- rendering [Reporting Services], settings
- device information settings [Reporting Services], about device information settings
- extensions [Reporting Services], device information settings
ms.assetid: fe718939-7efe-4c7f-87cb-5f5b09caeff4
caps.latest.revision: 47
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: da897abf38fb1c6e89178a9314189890b88eab87
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="passing-device-information-settings-to-rendering-extensions"></a>表示拡張機能にデバイス情報設定を渡す
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]では、デバイス情報設定を使用して、表示パラメーターを表示拡張機能に渡します。 レポート サーバー Web サービスの設定は **DeviceInfo** XML 要素として渡し、レポート サーバーで処理されます。 デバイス情報設定には既定値があるため、表示プロセスでは省略可能な引数と見なされます。 しかし、デバイス情報設定を使用して、表示をカスタマイズし、サーバーで提供される既定値を上書きできます。  
  
 デバイス情報設定はさまざまな方法で指定できます。 プログラムでは Render メソッドを使用できます。 URL によりレポートにアクセスする場合、URL パラメーターとしてデバイス情報を指定できます。 また、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 構成ファイルのデバイス情報設定を編集し、表示パラメーターをグローバルに指定することもできます。 表示パラメーターをグローバルに指定の詳細については、次を参照してください。 [RSReportServer.Config で表示拡張機能パラメーターをカスタマイズ](../../../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)です。  
  
## <a name="passing-device-information-using-the-render-method"></a>Render メソッドを使用してデバイス情報を渡す  
 To pass device information settings to a rendering extension, use the **M:Microsoft.WSSUX.ReportingServicesWebService.RSExecutionService2005.ReportExecutionService.Render(System.String,System.String,System.String@,System.String@,System.String@,Microsoft.WSSUX.ReportingServicesWebService.RSExecutionService2005.Warning[]@,System.String[]@)** method. 例を次の XML 文字列を渡すことができます、<xref:ReportExecution2005.ReportExecutionService.Render%2A>メソッドを HTML で表示したときに HTML 断片を作成します。  
  
```  
<DeviceInfo>  
   <HTMLFragment>True</HTMLFragment>  
</DeviceInfo>  
```  
  
 レポートが HTML 断片として表示される場合、レポートの内容は TABLE 要素内に含まれ、HTML または BODY 要素は使用されません。 HTML 断片を使用して、既存の HTML ドキュメントにレポートを組み込むことができます。 HTML 出力のデバイス情報設定の詳細については、次を参照してください。 [HTML Device Information Settings](../../../reporting-services/html-device-information-settings.md)です。  
  
## <a name="passing-device-information-using-url-access"></a>URL アクセスを使用してデバイス情報を渡す  
 URL アクセスを使用してデバイス情報設定を渡すこともできます。 デバイス情報設定は URL パラメーターとして渡されます。 次の URL アクセス文字列をレポート サーバーに渡すと、HTML ビューアー ツール バーなしで表示するレポートを生成できます。  
  
```  
http://<Server Name>/reportserver?/SampleReports/Sales Order Detail&rs:Command=Render&rs:Format=HTML4.0&rc:Toolbar=False  
```  
  
 詳細については、次を参照してください。 [URL でのデバイス情報設定の指定](../../../reporting-services/specify-device-information-settings-in-a-url.md)です。  
  
## <a name="see-also"></a>参照  
 [拡張機能 &#40; を表示するためのデバイス情報設定Reporting Services &#41;](../../../reporting-services/device-information-settings-for-rendering-extensions-reporting-services.md)   
 [RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](../../../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
