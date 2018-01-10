---
title: "レポート サーバーのサービス プリンシパル名 (SPN) の登録 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-server
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dda91d4f-77cc-4898-ad03-810ece5f8e74
caps.latest.revision: "7"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: d8f339aea53a9da7ee183bb2a6efee25bc603c13
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="register-a-service-principal-name-spn-for-a-report-server"></a>レポート サーバーのサービス プリンシパル名 (SPN) の登録
  相互認証に Kerberos プロトコルを使用するネットワークに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を配置する場合に、レポート サーバー サービスをドメイン ユーザー アカウントとして実行するように構成するには、レポート サーバー サービスのサービス プリンシパル名 (SPN) を作成する必要があります。  
  
## <a name="about-spns"></a>SPN について  
 SPN は、Kerberos 認証を使用するネットワークでのサービスの一意識別子です。 SPN は、サービス クラス、ホスト名、およびポートで構成されます。 Kerberos 認証を使用するネットワークでは、ビルトイン コンピューター アカウント (NetworkService や LocalSystem など) またはユーザー アカウントにサーバーの SPN を登録する必要があります。 ビルトイン アカウントには、自動的に SPN が登録されます。 一方、ドメイン ユーザー アカウントでサービスを実行する場合は、使用するアカウントに手動で SPN を登録する必要があります。  
  
 SPN を作成するには、 **SetSPN** コマンド ライン ユーティリティを使用します。 詳細については、以下を参照してください。  
  
-   [Setspn](http://technet.microsoft.com/library/cc731241\(WS.10\).aspx) (http://technet.microsoft.com/library/cc731241(WS.10).aspx)。  
  
-   [Service Principal Names (SPNs) SetSPN Syntax (Setspn.exe)](http://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) (サービス プリンシパル名 (SPN) SetSPN の構文 (Setspn.exe)) (http://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx)。  
  
 このユーティリティをドメイン コントローラーで実行するには、ドメイン管理者であることが必要です。  
  
## <a name="syntax"></a>構文  
 SetSPN ユーティリティを使用してレポート サーバーの SPN を作成する場合は、次のようなコマンド構文を使用します。  
  
```  
Setspn -s http/<computername>.<domainname>:<port> <domain-user-account>  
```  
  
 **SetSPN** は、Windows Server で使用できます。 **-s** 引数は、重複する SPN がないことを検証してから、SPN を追加します。 **注: -s** は Windows Server 2008 以降の Windows Server で使用できます。  
  
 **HTTP** はサービス クラスです。 レポート サーバー Web サービスは、HTTP.SYS で実行されます。 HTTP 用に SPN を作成すると、副次的に、HTTP.SYS で実行される同じコンピューター上のすべての Web アプリケーション (IIS でホストされるアプリケーションを含む) に対して、ドメイン ユーザー アカウントに基づいてチケットが付与されます。 これらのサービスを別のアカウントで実行すると、認証要求が失敗します。 この問題を回避するには、すべての HTTP アプリケーションが同じアカウントで実行されるように構成するか、またはアプリケーションごとにホスト ヘッダーを作成し、作成したホスト ヘッダーごとに個別の SPN を作成することを検討してください。 ホスト ヘッダーを構成する場合、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成にかかわらず DNS を変更する必要があります。  
  
 \<*computername*>、\<*domainname*>、\<*port*> に指定した値で、レポート サーバーをホストするコンピューターのネットワーク アドレスが一意に識別されます。 これは、ローカル ホスト名にすることも、完全修飾ドメイン名 (FQDN) にすることもできます。 ドメインが 1 つしかなく、かつポート 80 を使用している場合は、コマンド ラインで \<*domainname*> と \<*port*> を省略できます。 \<*domain-user-account*> は、レポート サーバー サービスが実行され、SPN を登録する必要があるユーザー アカウントです。  
  
## <a name="register-an-spn-for-domain-user-account"></a>ドメイン ユーザー アカウントに対する SPN の登録  
  
#### <a name="to-register-an-spn-for-a-report-server-service-running-as-a-domain-user"></a>ドメイン ユーザーとして実行されるレポート サーバー サービスの SPN を登録するには  
  
1.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をインストールし、レポート サーバー サービスをドメイン ユーザー アカウントとして実行するように構成します。 この手順が完了しないと、ユーザーはレポート サーバーに接続できないので注意してください。  
  
2.  ドメイン コントローラーにドメイン管理者としてログオンします。  
  
3.  コマンド プロンプト ウィンドウを開きます。  
  
4.  次のコマンドをコピーし、プレースホルダーの値を実際のネットワークで有効な値で置き換えます。  
  
    ```  
    Setspn -s http/<computer-name>.<domain-name>:<port> <domain-user-account>  
    ```  
  
     例: `Setspn -s http/MyReportServer.MyDomain.com:80 MyDomainUser`  
  
5.  コマンドを実行します。  
  
6.  **RsReportServer.config** ファイルを開き、 `<AuthenticationTypes>` セクションを探します。  
  
7.  このセクションの最初のエントリとして `<RSWindowsNegotiate/>` を追加して、NTLM を有効にします。  
  
## <a name="see-also"></a>参照  
 [サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;](http://msdn.microsoft.com/library/25000ad5-3f80-4210-8331-d4754dc217e0)   
 [レポート サーバー サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Reporting Services ネイティブ モードのレポート サーバーの管理](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)  
  
  
