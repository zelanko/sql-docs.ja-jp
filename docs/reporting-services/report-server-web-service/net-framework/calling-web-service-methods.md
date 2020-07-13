---
title: Web サービス メソッドの呼び出し | Microsoft Docs
description: プロキシ クラスのメソッドを呼び出して、レポート サーバーでレポート操作を実行します。 Web サービス メソッドにはパブリック アクセスがあり、適切な引数が必要です。
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
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
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0e7347bfcb93d327bc6e56eb91c903bbc5e1f38f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "79198327"
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
  
  
