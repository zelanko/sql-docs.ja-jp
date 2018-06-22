---
title: Claims to Windows Token Service (c2wts) と Reporting Services |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- c2wts.exe.config
- SharePoint mode
- C2WTS
- WSS_WPG
ms.assetid: 4d380509-deed-4b4b-a9c1-a9134cc40641
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 479be89681f7c34558c5a7e89d54023feb110d60
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073668"
---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Claims to Windows Token Service (C2WTS) と Reporting Services
  SharePoint Claims to Windows Token Service (c2WTS) が必要[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint モードの SharePoint ファームの外部にあるデータ ソースに対して windows 認証を使用する場合。 これは、Web フロントエンド (WFE) と [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービス間の通信が常に要求認証になるため、ユーザーが Windows 認証を使用してデータ ソースにアクセスする場合にも当てはまります。  
  
 c2WTS は、データ ソースが共有サービスと同じコンピューター上にある場合でも必要です。 ただし、このシナリオでは、制約付き委任は必要ありません。  
  
 c2WTS によって作成されたトークンは、制約付き委任 (特定のサービスへの制約) と "認証プロトコルの使用" 構成オプションでのみ機能します。 既に述べたとおり、データ ソースが共有サービスと同じコンピューター上にある場合は、制約付き委任は必要ありません。  
  
 Kerberos の制約付き委任を使用する環境では、SharePoint Server サービスと外部データ ソースが同じ Windows ドメインに属している必要があります。 Claims to Windows Token Service (c2WTS) に依存する任意のサービスでは、Kerberos の **制約付き** 委任を使用して、c2WTS が Kerberos プロトコル遷移を使用して要求を Windows 資格情報に変換できるようにする必要があります。 これらの要件は、すべての SharePoint 共有サービスに共通です。 詳細については、次を参照してください。 [Microsoft SharePoint 2010 製品の概要の Kerberos 認証 (http://technet.microsoft.com/library/gg502594.aspx)](http://technet.microsoft.com/library/gg502594.aspx)です。  
  
 このトピックでは、手順をまとめています。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
## <a name="prerequisites"></a>前提条件  
  
> [!NOTE]  
>  注: 構成手順によっては、変更されたり、特定のファーム トポロジで機能しない場合があります。 たとえば、シングル サーバー インストールでは Windows Identity Foundation c2WTS サービスをサポートしていないため、Windows トークンに対するクレームの委任シナリオは、このファーム構成では可能でありません。  
  
### <a name="basic-steps-needed-to-configure-c2wts"></a>c2WTS の構成に必要な基本的な手順  
  
1.  c2WTS サービス アカウントを構成します。 c2WTS を実行する各アプリケーション サーバーのローカルの Administrators グループにサービス アカウントを追加します。 さらに、アカウントに次のローカル セキュリティ ポリシー権限があることを確認します。  
  
    -   オペレーティング システムの一部として機能  
  
    -   認証後にクライアントを借用する  
  
    -   サービスとしてログオン  
  
     C2wts に使用するアカウントもプロトコル遷移で制約付き委任用に構成する必要があり、(SQL Server Engine、SQL Server Analysis Services) との通信に必要なサービスに委任する権限を必要があります。委任を構成するには、Active Directory ユーザーとコンピューター スナップインで使用することができます。  
  
    1.  各サービス アカウントを右クリックして、プロパティ ダイアログを開きます。 ダイアログで **[委任]** タブをクリックします。  
  
        > [!NOTE]  
        >  注: 委任タブは、オブジェクトに SPN が割り当てられている場合にのみ表示されます。 c2WTS では、c2WTS アカウントに SPN は必要ありませんが、SPN がない場合は、 **[委任]** タブは表示されません。 制約付き委任を構成する別の方法として、 **ADSIEdit**などのユーティリティを使用するという方法もあります。  
  
    2.  委任タブで重要な構成オプションは、次のとおりです。  
  
        -   [指定されたサービスへの委任でのみこのユーザーを信頼する] を選択する  
  
        -   [任意の認証プロトコルを使う] を選択する  
  
         詳細については、ホワイト ペーパー「 [SharePoint 2010 および SQL Server 2008 R2 製品向けの Kerberos 認証の構成](http://blogs.technet.com/b/tothesharepoint/archive/2010/07/22/whitepaper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products.aspx)」の「コンピューターとサービス アカウント用に Kerberos 制約付き委任を構成する」を参照してください。  
  
2.  c2WTS "AllowedCallers" の構成  
  
     c2WTS「呼び出し元」の id を明示的に必要と構成ファイルに記載されて**c2wtshost.exe.config**。 するように構成されている場合を除き、、c2WTS がシステムで認証されたすべてのユーザーから要求を受け付けられません。 この場合、"呼び出し元" は WSS_WPG Windows グループです。 c2wtshost.exe.confi ファイルは次の場所に保存されます。  
  
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
  
    2.  スタートアップの種類を **[自動]** に変更し、サービスを起動します。  
  
4.  SharePoint "Claims to Windows Token Service" の起動: **[サーバーのサービスの管理]** ページの SharePoint サーバーの全体管理から Claims to Windows Token Service を起動します。 このサービスは、アクションを実行するサーバーで起動する必要があります。 たとえば、WFE サーバーと [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービスを実行しているアプリケーション サーバーを持っている場合は、アプリケーション サーバーで c2WTS を起動するだけでかまいません。 c2WTS は WFE では必要ありません。  
  
## <a name="see-also"></a>参照  
 [概要 (to Windows Token Service (c2WTS) 要求http://msdn.microsoft.com/library/ee517278.aspx)](http://msdn.microsoft.com/library/ee517278.aspx)   
 [Microsoft SharePoint 2010 製品 (の Kerberos 認証の概要http://technet.microsoft.com/library/gg502594.aspx)](http://technet.microsoft.com/library/gg502594.aspx)  
  
  