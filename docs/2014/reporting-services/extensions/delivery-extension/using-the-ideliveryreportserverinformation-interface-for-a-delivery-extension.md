---
title: 配信拡張機能での IDeliveryReportServerInformation インターフェイスの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: d211842a43af771e953fd74a15403ba9321f2860
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56028003"
---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a>配信拡張機能での IDeliveryReportServerInformation インターフェイスの使用
  <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> インターフェイスは、レポート サーバーに関する情報を取得する場合に使用できるいくつかのプロパティを表示します。 この情報を使用して、通知とレポートを配信できます。 配信拡張機能のクラスを実装する場合は、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> インターフェイスに必要な <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> プロパティを実装します。 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> プロパティは、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> インターフェイスを実装するオブジェクトを返します。 このオブジェクトからは、レポート サーバーで現在サポートされる表示拡張機能の一覧を取得できます。  
  
 次`for`でレポート サーバーで現在使用可能な表示拡張機能の一覧を格納するループを使用する可能性があります、 **ArrayList**オブジェクト。  
  
```vb  
Dim renderFormats As New ArrayList()  
Dim e As Microsoft.ReportingServices.Interfaces.Extension  
For Each e In  ReportServerInformation.RenderingExtension  
   If e.Visible Then  
      renderFormats.Add(e.Name)  
   End If  
Next e  
```  
  
```csharp  
ArrayList renderFormats = new ArrayList();  
foreach (Microsoft.ReportingServices.Interfaces.Extension e in ReportServerInformation.RenderingExtension)  
{   
   if (e.Visible)  
   {  
      renderFormats.Add(e.Name);  
   }  
}  
```  
  
 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> インターフェイスの詳細については、「[配信拡張機能での IDeliveryReportServerInformation インターフェイスの使用](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.ReportingServices.Interfaces>   
 [配信拡張機能の実装](implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../reporting-services-extension-library.md)  
  
  
