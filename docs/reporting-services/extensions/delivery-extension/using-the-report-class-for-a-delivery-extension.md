---
title: "配信拡張機能のレポート クラスの使用 |Microsoft ドキュメント"
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
- delivery extensions [Reporting Services], report information
- Report class
ms.assetid: 1145ac63-eafd-452a-82af-16f85b1676dd
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8c062bcf2ef48874a64149269e9eb0cb1ffacd56
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="using-the-report-class-for-a-delivery-extension"></a>配信拡張機能での Report クラスの使用
  <xref:Microsoft.ReportingServices.Interfaces.Report> クラスは、レポート サーバー データベースのレポートを表します。 すべてのサブスクリプションは特定のレポートに関連付けられます。 レポートは通知に含まれます。 配信拡張機能では、通知の一部である <xref:Microsoft.ReportingServices.Interfaces.Report> オブジェクトを使用してレポートを生成できます。 <xref:Microsoft.ReportingServices.Interfaces.Report> オブジェクトには、レポート サーバーのレポートの URL やレポート名など、レポート固有のプロパティも含まれています。 これらのプロパティすべてを配信プロバイダーの一部として使用できます。  
  
 <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> クラスの <xref:Microsoft.ReportingServices.Interfaces.Report> メソッドを使用して、レポートを表示できます。 <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> メソッドは、1 つの表示レポートを構成する <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトの配列を 1 つ以上返します。 1 番目の <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトが表示レポートです。 その他の <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトは、レポート データと一緒に配信される必要があるリソースです (HTML ファイルや関連付けられた画像など)。 表示拡張機能がシングル ストリーム表示拡張機能である場合は (IMAGE、PDF、MHTML、および Excel)、配列の <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトを 1 つだけ返します。  
  
 レポート ストリームを含む <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトは、配信の一部として含めることができます。  
  
 使用する方法の例については、<xref:Microsoft.ReportingServices.Interfaces.Report>クラスを参照してください[SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)  
  
## <a name="see-also"></a>参照  
 [Implementing a Delivery Extension](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)   
 [配信拡張機能の RenderedOutputFile クラスの使用](../../../reporting-services/extensions/delivery-extension/using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
  
  
