---
title: "Web サービス メソッドの呼び出し | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: report-server-web-service
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Web service [Reporting Services], calls
- calling Web service
- Report Server Web service, SOAP
- XML Web service [Reporting Services], calls
- Report Server Web service, calls
- XML Web service [Reporting Services], SOAP
- SOAP [Reporting Services], calls
ms.assetid: f6f0c6e3-8bb5-4c44-9d19-1872edc72746
caps.latest.revision: "38"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 935fc8e46a62131a79d695ffd4ad112220037138
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="calling-web-service-methods"></a>Web サービス メソッドの呼び出し
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] プロキシ クラスを使って Web サービス操作を呼び出す場合、そのクラスのメソッドを使います。 これらのメソッドは、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] クラス ライブラリにあるクラスの他のメソッドと同じように応答します。 すべての Web サービス メソッドにはパブリック アクセスがあり、適切な数の引数および引数の型を指定する必要があります。 プロジェクトにプロキシ クラスのインスタンスを作成した後は、メソッドを呼び出し、レポート サーバー経由でレポートの操作を実行できます。 次の C# コードは、<xref:ReportService2010.ReportingService2010> プロキシ クラスの <xref:ReportService2010.ReportingService2010.ListChildren%2A> メソッドの使用方法を表しています。 このコードは、Web サービスの再帰呼び出しに使用します。Web サービスでは、レポート サーバー データベースのすべてのアイテムの一覧が入った <xref:ReportService2010.CatalogItem> オブジェクトの配列を返します。  
  
```vb  
Dim rs As New ReportingService2010()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
Dim items As CatalogItem() = rs.ListChildren("/", True)  
```  
  
```csharp  
ReportingService2010 rs = new ReportingService2010();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
CatalogItem[] items = rs.ListChildren("/", true);  
```  
  
## <a name="see-also"></a>参照  
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [テクニカル リファレンス (SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
