---
title: "配信拡張機能の IDeliveryReportServerInformation インターフェイスの使用 |Microsoft ドキュメント"
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
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: caebc70ede4475cef103d0d76598ea3125231252
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a>配信拡張機能での IDeliveryReportServerInformation インターフェイスの使用
  <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> インターフェイスは、レポート サーバーに関する情報を取得する場合に使用できるいくつかのプロパティを表示します。 この情報を使用して、通知とレポートを配信できます。 配信拡張機能のクラスを実装する場合は、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> インターフェイスに必要な <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> プロパティを実装します。 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> プロパティは、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> インターフェイスを実装するオブジェクトを返します。 このオブジェクトからは、レポート サーバーで現在サポートされる表示拡張機能の一覧を取得できます。  
  
 次**の**ループは、レポート サーバーで現在使用可能な表示拡張機能の一覧を格納するために使用でした、 **ArrayList**オブジェクト。  
  
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
  
 詳細については、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation>インターフェイスを参照してください[IDeliveryReportServerInformation インターフェイス配信拡張機能を使用して](../../../reporting-services/extensions/delivery-extension/using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.ReportingServices.Interfaces>   
 [Implementing a Delivery Extension](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
