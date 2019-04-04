---
title: Claims to Windows Token Service (C2WTS) と Reporting Services |Microsoft Docs
ms.custom: ''
ms.date: 03/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- c2wts.exe.config
- SharePoint mode
- C2WTS
- WSS_WPG
ms.assetid: 4d380509-deed-4b4b-a9c1-a9134cc40641
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0f6443f8015d3b2a4c94c9470a35a5b1433691d8
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53354352"
---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Claims to Windows Token Service (C2WTS) と Reporting Services
  SharePoint Claims to Windows Token Service (c2WTS) が必要[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint モードの SharePoint ファームの外部にあるデータ ソースに対して windows 認証を使用する場合。 これは、Web フロントエンド (WFE) と [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービス間の通信が常に要求認証になるため、ユーザーが Windows 認証を使用してデータ ソースにアクセスする場合にも当てはまります。  
  
 c2WTS は、データ ソースが共有サービスと同じコンピューター上にある場合でも必要です。 ただし、このシナリオでは、制約付き委任は必要ありません。  
  
 c2WTS によって作成されたトークンは、制約付き委任 (特定のサービスへの制約) と "認証プロトコルの使用" 構成オプションでのみ機能します。 既に述べたとおり、データ ソースが共有サービスと同じコンピューター上にある場合は、制約付き委任は必要ありません。  
  
 Kerberos の制約付き委任を使用する環境では、SharePoint Server サービスと外部データ ソースが同じ Windows ドメインに属している必要があります。 Claims to Windows Token Service (c2WTS) に依存する任意のサービスでは、Kerberos の **制約付き** 委任を使用して、c2WTS が Kerberos プロトコル遷移を使用して要求を Windows 資格情報に変換できるようにする必要があります。 これらの要件は、すべての SharePoint 共有サービスに共通です。 詳細については、[Microsoft SharePoint 2010 製品用の概要の Kerberos 認証 (https://technet.microsoft.com/library/gg502594.aspx)](https://technet.microsoft.com/library/gg502594.aspx)を参照してください。  
  
 このトピックでは、手順をまとめています。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
## <a name="prerequisites"></a>前提条件  
  
> [!NOTE]  
>  注:一部の構成手順により、変更可能性があります、または、特定のファーム トポロジで動作しない可能性があります。 たとえば、シングル サーバー インストールでは Windows Identity Foundation c2WTS サービスをサポートしていないため、Windows トークンに対するクレームの委任シナリオは、このファーム構成では可能でありません。  
  
### <a name="basic-steps-needed-to-configure-c2wts"></a>c2WTS の構成に必要な基本的な手順  
  
1.  c2WTS サービス アカウントを構成します。 c2WTS を実行する各アプリケーション サーバーのローカルの Administrators グループにサービス アカウントを追加します。 さらに、アカウントに次のローカル セキュリティ ポリシー権限があることを確認します。  
  
    -   オペレーティング システムの一部として機能  
  
    -   認証後にクライアントを借用する  
  
    -   サービスとしてログオン  
  
     C2WTS に使用するアカウントは、プロトコル遷移で制約付き委任用に構成する必要があるし、(SQL Server の Engine、SQL Server Analysis Services など) との通信に必要なサービスに委任する権限が必要です。委任を構成するには、Active Directory ユーザーとコンピューター スナップインで使用することができます。  
  
    1.  各サービス アカウントを右クリックして、プロパティ ダイアログを開きます。 ダイアログで **[委任]** タブをクリックします。  
  
        > [!NOTE]  
        >  注: 委任タブは、オブジェクトに SPN が割り当てられている場合にのみ表示されます。 c2WTS では、c2WTS アカウントに SPN は必要ありませんが、SPN がない場合は、 **[委任]** タブは表示されません。 制約付き委任を構成する別の方法として、 **ADSIEdit**などのユーティリティを使用するという方法もあります。  
  
    2.  委任タブで重要な構成オプションは、次のとおりです。  
  
        -   "指定されたサービスのみへの委任でこのユーザーを信頼する を選択します。  
  
        -   「任意の認証プロトコルを使用して、」を選択します。  
  
         詳細については、次のホワイト ペーパーの「コンピューターの Kerberos の制約付き委任を構成してサービス アカウント」セクションを参照してください[Kerberos 認証 SharePoint 2010 および SQL Server 2008 R2 製品の構成。](http://blogs.technet.com/b/tothesharepoint/archive/2010/07/22/whitepaper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products.aspx)  
  
2.  C2WTS"AllowedCallers"の構成します。  
  
     c2WTS「呼び出し元」の id を明示的に必要と、構成ファイルに記載**c2wtshost.exe.config**。 行うように構成されていない限り、c2WTS がシステムで認証されたすべてのユーザーからの要求を受け付けられません。 この場合、"呼び出し元" は WSS_WPG Windows グループです。 c2wtshost.exe.confi ファイルは次の場所に保存されます。  
  
     **\Program Files\Windows identity Foundation\v3.5\c2wtshost.exe.config**  
  
     構成ファイルの例を次に示します。  
  
    ```  
    <configuration>  
      <windowsTokenService>  
        <!--  
            By default no callers are allowed to use the Windows Identity Foundation Claims To NT Token Service.  
            Add the identities you wish to allow below.  
          -->  
        <allowedCallers>  
          <clear/>  
          <add value="WSS_WPG" />  
        </allowedCallers>  
      </windowsTokenService>  
    </configuration>  
    ```  
  
3.  オペレーティング システム c2WTS サービスを起動します。  
  
    1.  前の手順で構成したサービス アカウントを使用するようにサービスを構成します。  
  
    2.  スタートアップの種類を変更"**自動**"し、サービスを開始します。  
  
4.  SharePoint"Claims to Windows Token Service"を開始します。**[サーバーのサービスの管理]** ページの SharePoint サーバーの全体管理から Claims to Windows Token Service を起動します。 このサービスは、アクションを実行するサーバーで起動する必要があります。 たとえば、WFE サーバーと [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービスを実行しているアプリケーション サーバーを持っている場合は、アプリケーション サーバーで c2WTS を起動するだけでかまいません。 c2WTS は WFE では必要ありません。  
  
## <a name="see-also"></a>参照  
 [概要 (to Windows Token Service (c2WTS) 要求 https://msdn.microsoft.com/library/ee517278.aspx)](https://msdn.microsoft.com/library/ee517278.aspx)   
 [Microsoft SharePoint 2010 製品 (の Kerberos 認証の概要 https://technet.microsoft.com/library/gg502594.aspx)](https://technet.microsoft.com/library/gg502594.aspx)  
  
  
