---
title: "HTTP 接続マネージャー |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP connection manager
- Web site connections [Integration Services]
- connection managers [Integration Services], HTTP
- Web server connections [Integration Services]
- connections [Integration Services], HTTP
ms.assetid: 26b2b3e1-d02c-46ca-8d31-7aef2bbc3c53
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4cf63461848933530a215a75b19d40128327f356
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="http-connection-manager"></a>HTTP 接続マネージャー
  HTTP 接続により、パッケージが HTTP を使用してファイルを送受信することで、Web サーバーにアクセスできるようになります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれる Web サービス タスクには、この接続マネージャーを使用します。  
  
 HTTP 接続マネージャーをパッケージに追加するときは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって、実行時に HTTP 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定して、接続マネージャーをパッケージの **Connections** コレクションに追加します。  
  
 接続マネージャーの **ConnectionManagerType** プロパティは、 **HTTP**に設定されます。  
  
 HTTP 接続マネージャーは、次の方法で構成できます。  
  
-   資格情報を使用します。 接続マネージャーが資格情報を使用する場合、プロパティにユーザー名、パスワード、およびドメインが含まれます。  
  
    > [!IMPORTANT]  
    >  HTTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。 Windows 認証はサポートされていません。  
  
-   クライアント証明書を使用します。 接続マネージャーがクライアント証明書を使用する場合、プロパティに証明書名が含まれます。  
  
-   サーバーへの接続のタイムアウトと、データを書き込むチャンク サイズを指定します。  
  
-   プロキシ サーバーを使用します。 プロキシ サーバーは、資格情報を使用するように構成することや、プロキシ サーバーをバイパスして、代わりにローカル アドレスを使用するように構成することもできます。  
  
## <a name="configuration-of-the-http-connection-manager"></a>HTTP 接続マネージャーの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[HTTP 接続マネージャー エディター] ([サーバー] ページ)](../../integration-services/connection-manager/http-connection-manager-editor-server-page.md)  
  
-   [[HTTP 接続マネージャー エディター] ([プロキシ] ページ)](../../integration-services/connection-manager/http-connection-manager-editor-proxy-page.md)  
  
 プログラムによる接続マネージャーの構成の詳細については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Web サービス タスク](../../integration-services/control-flow/web-service-task.md)   
 [Integration Services & #40 です。SSIS &#41;接続](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
