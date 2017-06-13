---
title: "Claims to Windows Token Service (c2wts) と Reporting Services |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- c2wts.exe.config
- SharePoint mode
- C2WTS
- WSS_WPG
ms.assetid: 4d380509-deed-4b4b-a9c1-a9134cc40641
caps.latest.revision: 17
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2ab5f4b5d2774d9dc944ad17bb55063388b70a6d
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Claims to Windows Token Service (c2WTS) と Reporting Services

[!INCLUDE[ssrs-appliesto-sql2016-xpreview](../../includes/ssrs-appliesto-sql2016-xpreview.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

  SharePoint ファームの外部にあるデータ ソースに対して Windows 認証を使用する場合、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードでは SharePoint Claims to Windows Token Service (c2WTS) が必要です。 これは、Web フロントエンド (WFE) と [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービス間の通信が常に要求認証になるため、ユーザーが Windows 認証を使用してデータ ソースにアクセスする場合にも当てはまります。  
  
 c2WTS は、データ ソースが共有サービスと同じコンピューター上にある場合でも必要です。 ただし、このシナリオでは、制約付き委任は必要ありません。  
  
 c2WTS によって作成されたトークンは、制約付き委任 (特定のサービスへの制約) と "認証プロトコルの使用" 構成オプションでのみ機能します。 既に述べたとおり、データ ソースが共有サービスと同じコンピューター上にある場合は、制約付き委任は必要ありません。  
  
 Kerberos の制約付き委任を使用する環境では、SharePoint Server サービスと外部データ ソースが同じ Windows ドメインに属している必要があります。 Claims to Windows Token Service (c2WTS) に依存する任意のサービスでは、Kerberos の **制約付き** 委任を使用して、c2WTS が Kerberos プロトコル遷移を使用して要求を Windows 資格情報に変換できるようにする必要があります。 これらの要件は、すべての SharePoint 共有サービスに共通です。 詳細については、「 [SharePoint 2013 で Kerberos 認証を計画する](http://technet.microsoft.com/library/ee806870.aspx)」を参照してください。  
  
 このトピックでは、手順をまとめています。

## <a name="prerequisites"></a>前提条件

> [!NOTE]
>  注: 構成手順によっては、変更されたり、特定のファーム トポロジで機能しない場合があります。 たとえば、シングル サーバー インストールでは Windows Identity Foundation c2WTS サービスをサポートしていないため、Windows トークンに対するクレームの委任シナリオは、このファーム構成では可能でありません。

> [!IMPORTANT]
> Power Pivot ブックに対して Power View を使用している場合、「 [Office Online Server overview](https://technet.microsoft.com/library/jj219437\(v=office.16\).aspx)」(Office Online Server の概要) の追加の構成を実行する必要があります。 詳細については、次のホワイト ペーパーを参照してください。 
>
> - [SharePoint 2016 での SQL Server 2016 PowerPivot と Power View の配置](../../analysis-services/instances/install-windows/deploying-sql-server-2016-powerpivot-and-power-view-in-sharepoint-2016.md)
> 
> - [多層 SharePoint 2016 ファームでの SQL Server 2016 PowerPivot と Power View の配置](../../analysis-services/instances/install-windows/deploy-powerpivot-and-power-view-multi-tier-sharepoint-2016-farm.md)
  
### <a name="basic-steps-needed-to-configure-c2wts"></a>c2WTS の構成に必要な基本的な手順  
  
1.  c2WTS サービス アカウントを構成します。 c2WTS を実行する各アプリケーション サーバーのローカルの Administrators グループにサービス アカウントを追加します。 さらに、アカウントに次のローカル セキュリティ ポリシー権限があることを確認します。  
  
    -   オペレーティング システムの一部として機能  
  
    -   認証後にクライアントを借用する  
  
    -   サービスとしてログオン  
  
2.  c2WTS サービス アカウントの委任を構成します。 アカウントには、プロトコル遷移を使用した制限付き委任に加え、通信に必要なサービス (SQL Server Engine、SQL Server Analysis Services など) に委任する権限も必要です。 委任を構成するには、Active Directory ユーザーとコンピューターのスナップインを使用できます。  

    > [!IMPORTANT]
    > C2WTS サービス アカウントにどのような設定を構成するとしても、[委任] タブで、Reporting Services サービス アカウントと同じにする必要があります。 たとえば、C2WTS サービス アカウントを SQL Service に委任できるようにした場合、Reporting Services サービス アカウントでも同様にする必要があります。
  
    1.  各サービス アカウントを右クリックして、プロパティ ダイアログを開きます。 ダイアログで **[委任]** タブをクリックします。  
  
        > [!NOTE]  
        >  注: 委任タブは、オブジェクトにサービス プリンシパル名 (SPN) が割り当てられている場合にのみ表示されます。 c2WTS では、c2WTS アカウントに SPN は必要ありませんが、SPN がない場合は、 **[委任]** タブは表示されません。 制約付き委任を構成する別の方法として、 **ADSIEdit**などのユーティリティを使用するという方法もあります。  
  
    2.  委任タブで重要な構成オプションは、次のとおりです。  
  
        -   [指定されたサービスへの委任でのみこのユーザーを信頼する] を選択する  
  
        -   [任意の認証プロトコルを使う] を選択する  

    3. **[追加]** を選択して、委任するサービスを追加します。
    
    4. 選択**ユーザーまたはコンピューターしています.*** し、サービスをホストしているアカウントを入力します。 たとえば、SQL Server がという名前のアカウントで実行されている*sqlservice*、入力`sqlservice`です。
    
    5. サービス一覧を選択します。 そのアカウントで使用できる SPN が表示されます。 そのアカウントのサービス一覧が表示されない場合は、サービスがないか、別のアカウントのサービスの可能性があります。 SPN の調整には、SetSPN ユーティリティを使用できます。
    
    6. [OK] を選択してダイアログを閉じます。
  
3.  c2WTS "AllowedCallers" の構成  
  
     c2WTS では、"呼び出し元" の ID が構成ファイル **c2WTShost.exe.config**で明示されている必要があります。 c2WTS は、そのように構成されていない限り、システム内のすべての認証ユーザーからの要求を受け入れません。 この場合、"呼び出し元" は WSS_WPG Windows グループです。 c2WTShost.exe.confi ファイルは次の場所に保存されます。  
     
     > [!NOTE]
     > C2WTS サービスについて、SharePoint サーバーの全体管理内でサービス アカウントを変更すると、そのアカウントが WSS_WPG グループに追加されます。
  
     **\Program Files\Windows Identity Foundation\v3.5\c2WTShost.exe.config**  
  
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
4.  SharePoint "Claims to Windows Token Service" の起動: **[サーバーのサービスの管理]** ページの SharePoint サーバーの全体管理から Claims to Windows Token Service を起動します。 このサービスは、アクションを実行するサーバーで起動する必要があります。 たとえば、WFE サーバーと [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービスを実行しているアプリケーション サーバーを持っている場合は、アプリケーション サーバーで c2WTS を起動するだけでかまいません。 c2WTS は WFE では必要ありません。

## <a name="next-steps"></a>次の手順

[Windows トークン サービスに対するクレーム (c2WTS) の概要](http://msdn.microsoft.com/library/ee517278.aspx)   
[SharePoint 2013 で Kerberos 認証を計画します。](http://technet.microsoft.com/library/ee806870.aspx)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
