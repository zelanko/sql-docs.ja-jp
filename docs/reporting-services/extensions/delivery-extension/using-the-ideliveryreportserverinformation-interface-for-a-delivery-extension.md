---
title: "配信拡張機能での IDeliveryReportServerInformation インターフェイスの使用 | Microsoft Docs"
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
caps.latest.revision: "34"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 9f1acb146323a301d90c5c4f4ac1df6fd5b477d6
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a>配信拡張機能での IDeliveryReportServerInformation インターフェイスの使用
  <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> インターフェイスは、レポート サーバーに関する情報を取得する場合に使用できるいくつかのプロパティを表示します。 この情報を使用して、通知とレポートを配信できます。 配信拡張機能のクラスを実装する場合は、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> インターフェイスに必要な <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> プロパティを実装します。 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> プロパティは、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> インターフェイスを実装するオブジェクトを返します。 このオブジェクトからは、レポート サーバーで現在サポートされる表示拡張機能の一覧を取得できます。  
  
 次の **for** ループを使用すると、**ArrayList** オブジェクトのレポート サーバーで現在使用できる表示拡張機能の一覧を格納できます。  
  
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
  
 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> インターフェイスの詳細については、「[配信拡張機能での IDeliveryReportServerInformation インターフェイスの使用](../../../reporting-services/extensions/delivery-extension/using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.ReportingServices.Interfaces>   
 [配信拡張機能の実装](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
