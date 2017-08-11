---
title: "Web サービスの認証 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- Web service [Reporting Services], authentication
- XML Web service [Reporting Services], authentication
- Report Server Web service, authentication
ms.assetid: 852b4947-a090-4e54-8555-5a503945ceab
caps.latest.revision: 33
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 727d9ccd8cd1e40d89cfe74291edae92988b407c
ms.openlocfilehash: be7e76aa26ca4b94afd2e32b40b9fbfbe92b170d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="web-service-authentication"></a>Web サービス認証
  Windows 認証または基本認証を使用して、レポート サーバー Web サービスへの呼び出しを認証できます。 レポート サーバーへの SOAP 要求を作成するクライアントは、サポートされる認証プロトコルのいずれかのクライアント部分を実装している必要があります。 使用している場合、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]認証を実装するマネージ コード HTTP クラスを使用することができます。 これらの API を使用すると、認証情報を SOAP 要求と一緒に容易に送信できます。  
  
 レポート サーバー Web サービスへの呼び出しを作成する前に適切な資格情報を持っていないと、呼び出しが失敗します。 、実行時に資格情報を渡せます Web サービスを設定して、**資格情報**、メソッドを呼び出す前に、Web サービスを表すクライアント側オブジェクトのプロパティです。  
  
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
  
 資格情報は、レポート サーバー Web サービスのメソッドを呼び出す前に設定しておく必要があります。 資格情報を設定しないと、"HTTP 401 エラー : アクセスが拒否されました。" というエラーが発生します。 使用する資格情報を設定すると、後にする必要はありませんを引き続き同じサービス変数を使用する限り、再度設定する前に、サービスを認証する必要があります (など*rs*)。  
  
## <a name="custom-authentication"></a>カスタム認証  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] にはプログラミング API が含まれ、開発者は、セキュリティ拡張機能と呼ばれるカスタム認証拡張機能を設計および開発できます。 詳細については、「 [Implementing a Security Extension](../../../reporting-services/extensions/security-extension/implementing-a-security-extension.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
