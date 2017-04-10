---
title: "HTTP 接続マネージャー | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HTTP 接続マネージャー"
  - "Web サイトの接続 [Integration Services]"
  - "接続マネージャー [Integration Services], HTTP"
  - "Web サーバーの接続 [Integration Services]"
  - "接続 [Integration Services], HTTP"
ms.assetid: 26b2b3e1-d02c-46ca-8d31-7aef2bbc3c53
caps.latest.revision: 44
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 44
---
# HTTP 接続マネージャー
  HTTP 接続により、パッケージが HTTP を使用してファイルを送受信することで、Web サーバーにアクセスできるようになります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれる Web サービス タスクには、この接続マネージャーを使用します。  
  
 HTTP 接続マネージャーをパッケージに追加するときは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって、実行時に HTTP 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定して、接続マネージャーをパッケージの **Connections** コレクションに追加します。  
  
 接続マネージャーの **ConnectionManagerType** プロパティは、**HTTP** に設定されます。  
  
 HTTP 接続マネージャーは、次の方法で構成できます。  
  
-   資格情報を使用します。 接続マネージャーが資格情報を使用する場合、プロパティにユーザー名、パスワード、およびドメインが含まれます。  
  
    > [!IMPORTANT]  
    >  HTTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。 Windows 認証はサポートされていません。  
  
-   クライアント証明書を使用します。 接続マネージャーがクライアント証明書を使用する場合、プロパティに証明書名が含まれます。  
  
-   サーバーへの接続のタイムアウトと、データを書き込むチャンク サイズを指定します。  
  
-   プロキシ サーバーを使用します。 プロキシ サーバーは、資格情報を使用するように構成することや、プロキシ サーバーをバイパスして、代わりにローカル アドレスを使用するように構成することもできます。  
  
## HTTP 接続マネージャーの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[HTTP 接続マネージャー エディター] ([サーバー] ページ)](../Topic/HTTP%20Connection%20Manager%20Editor%20\(Server%20Page\).md)  
  
-   [[HTTP 接続マネージャー エディター] ([プロキシ] ページ)](../Topic/HTTP%20Connection%20Manager%20Editor%20\(Proxy%20Page\).md)  
  
 プログラムによる接続マネージャーの構成の詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>」を参照してください。  
  
## 参照  
 [Web サービス タスク](../../integration-services/control-flow/web-service-task.md)   
 [Integration Services (SSIS) の接続](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  