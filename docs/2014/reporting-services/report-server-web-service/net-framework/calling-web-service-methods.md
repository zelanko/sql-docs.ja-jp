---
title: Web サービス メソッドの呼び出し | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
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
caps.latest.revision: 37
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: fce65cf5ed4e8342005e058aec793fa88e6aa182
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074530"
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
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../report-server-web-service.md)   
 [テクニカル リファレンス (SSRS)](../../technical-reference-ssrs.md)  
  
  