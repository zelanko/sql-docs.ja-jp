---
title: "Web サービス認証 | Microsoft Docs"
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
- Web service [Reporting Services], authentication
- XML Web service [Reporting Services], authentication
- Report Server Web service, authentication
ms.assetid: 852b4947-a090-4e54-8555-5a503945ceab
caps.latest.revision: "33"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: edc055eec2dcd3f650b61bc982e80bb05fcaf20f
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="web-service-authentication"></a>Web サービス認証
  Windows 認証または基本認証を使用して、レポート サーバー Web サービスへの呼び出しを認証できます。 レポート サーバーへの SOAP 要求を作成するクライアントは、サポートされる認証プロトコルのいずれかのクライアント部分を実装している必要があります。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] を使っている場合は、マネージ コード HTTP クラスを使って認証を実装できます。 これらの API を使用すると、認証情報を SOAP 要求と一緒に容易に送信できます。  
  
 レポート サーバー Web サービスへの呼び出しを作成する前に適切な資格情報を持っていないと、呼び出しが失敗します。 実行時に、メソッドを呼び出す前の Web サービスを表すクライアント側オブジェクトの **Credentials** プロパティを設定することによって、資格情報を Web サービスに渡すことができます。  
  
 以降のセクションでは、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] を使用して資格情報を送信するコード例を示します。  
  
## <a name="windows-authentication"></a>[Windows 認証]  
 次のコードは、Windows 資格情報を Web サービスに渡します。  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
ReportingService rs = new ReportingService();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
```  
  
## <a name="basic-authentication"></a>基本認証  
 次のコードは、基本資格情報を Web サービスに渡します。  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = New System.Net.NetworkCredential("username", "password", "domain")  
```  
  
```csharp  
ReportingService service = new ReportingService();  
service.Credentials = new System.Net.NetworkCredential("username", "password", "domain");  
```  
  
 資格情報は、レポート サーバー Web サービスのメソッドを呼び出す前に設定しておく必要があります。 資格情報を設定しないと、"HTTP 401 エラー : アクセスが拒否されました。" というエラーが発生します。 サービスを使う前にサービスを認証する必要があります。ただし、資格情報を設定した後は、*rs* などの同じサービス変数を続けて使う限り、再度設定する必要はありません。  
  
## <a name="custom-authentication"></a>カスタム認証  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] にはプログラミング API が含まれ、開発者は、セキュリティ拡張機能と呼ばれるカスタム認証拡張機能を設計および開発できます。 詳細については、「 [Implementing a Security Extension](../../../reporting-services/extensions/security-extension/implementing-a-security-extension.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
