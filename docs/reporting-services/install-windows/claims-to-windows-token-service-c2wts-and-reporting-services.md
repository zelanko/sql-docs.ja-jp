---
title: "Claims to Windows Token Service (c2wts) と Reporting Services |Microsoft ドキュメント"
ms.custom: The Claims to Windows Token Service (C2WTS) is used by SharePoint and needs to be configured for Kerberos constrained delegation to work with SQL Server Reporting Services properly.
ms.date: 09/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: a9397f427cac18d0c8bfc663f6bd477b0440b8a3
ms.openlocfilehash: 8a478bba3cde66967594d5ef02f867de5b33edd7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/15/2017

---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Claims to Windows Token Service (C2WTS) と Reporting Services

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

内でネイティブ モードのレポートを表示する場合に SharePoint Claims to Windows Token Service (C2WTS) が必要、 [SQL Server Reporting Services レポート ビューアー web パーツ](../report-server-sharepoint/deploy-report-viewer-web-part.md)です。

C2WTS が SharePoint ファームの外部にあるデータ ソースに対して Windows 認証を使用する場合にも SQL Server Reporting Services SharePoint モードで必要です。 C2WTS は、データ ソースが共有サービスと同じコンピューター上にある場合でも必要です。 ただし、このシナリオでは、制約付き委任は必要ありません。

> [!NOTE]
> SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。

## <a name="report-viewer-web-part-configuration"></a>レポート ビューアー web パーツの構成

SharePoint サイト内の SQL Server Reporting Services ネイティブ モードのレポートを埋め込むには、レポート ビューアー web パーツを使用できます。 この web パーツは SharePoint 2013 と SharePoint 2016 で使用可能です。 SharePoint 2013 と SharePoint 2016 の両方の要求の認証を使用します。 SQL Server Reporting Services (ネイティブ モード) は、既定では、Windows 認証を使用します。 その結果、C2WTS では、正しく表示するためにレポート用に正しく構成する必要があります。

## <a name="sharepoint-mode-integaration"></a>SharePoint モードの integaration

**このセクションでは、SQL Server 2016 Reporting Services および以前にのみ適用されます。**

SharePoint Claims to Windows Token Service (C2WTS) は、SharePoint ファームの外部にあるデータ ソースに対して Windows 認証を使用する場合は、SQL Server Reporting Services SharePoint モードで必要です。 これは、間の通信、web フロント エンド (WFE) と Reporting Services 共有サービスは、必ず要求認証のため、ユーザーは Windows 認証を使用してデータ ソースにアクセスする場合でも当てはまります。

## <a name="steps-needed-to-configure-c2wts"></a>C2WTS の構成に必要な手順

C2WTS によって作成されたトークンは、制約付き委任 (特定のサービスへの制約) と "認証プロトコルの使用" 構成オプションでのみ機能します。 既に述べたとおり、データ ソースが共有サービスと同じコンピューター上にある場合は、制約付き委任は必要ありません。

Kerberos の制約付き委任を使用する環境では、SharePoint Server サービスと外部データ ソースが同じ Windows ドメインに属している必要があります。 Claims to Windows Token Service (c2WTS) に依存する任意のサービスでは、Kerberos の **制約付き** 委任を使用して、c2WTS が Kerberos プロトコル遷移を使用して要求を Windows 資格情報に変換できるようにする必要があります。 これらの要件は、すべての SharePoint 共有サービスに共通です。 詳細については、「 [SharePoint 2013 で Kerberos 認証を計画する](http://technet.microsoft.com/library/ee806870.aspx)」を参照してください。  

1. C2WTS サービス アカウントを構成します。 各サーバーが C2WTS を使用することで、ローカルの Administrators グループにサービス アカウントを追加します。

    **レポート ビューアー web パーツ**、Web フロント エンド (WFE) サーバーになります。 **SharePoint 統合モード**、Reporting Services サービスが実行されているアプリケーション サーバーになります。

2. C2WTS サービス アカウントの委任を構成します。

    アカウントには、制約付き委任プロトコル遷移および (つまり SQL Server データベース エンジン、SQL Server Analysis Services) との通信に必要なサービスに委任する権限を持つ必要があります。 委任を構成するには、Active Directory ユーザーとコンピューター スナップインを使用できるし、ドメイン管理者である必要があります。

    > [!IMPORTANT]
    > どのような設定を構成する C2WTS サービス アカウントの委任 タブで、使用されているメインのサービス アカウントと一致する必要があります。 **レポート ビューアー web パーツ**、SharePoint web アプリケーションのサービス アカウントになります。 **SharePoint 統合モード**、Reporting Services サービス アカウントになります。
    >
    > たとえば、SQL サービスに委任する C2WTS サービス アカウントを許可する場合は、SharePoint 統合モードの Reporting Services サービス アカウントで同じ操作を実行する必要があります。

    * 各サービス アカウントを右クリックして、プロパティ ダイアログを開きます。 ダイアログで **[委任]** タブをクリックします。

        [委任] タブでは、オブジェクトがサービス プリンシパル名 (SPN) に割り当てられている表示のみです。 C2WTS は必要ありませんが、C2WTS アカウントに SPN ただし、SPN せず、**委任** タブは表示されません。 制約付き委任を構成する別の方法として、 **ADSIEdit**などのユーティリティを使用するという方法もあります。

    * 委任タブで重要な構成オプションは、次のとおりです。

        * 選択**このユーザーに指定されたサービスのみ委任に対して信頼**
        * 選択**任意の認証プロトコルを使用します。**

    * **[追加]** を選択して、委任するサービスを追加します。

    * 選択**ユーザーまたはコンピューターしています.*** し、サービスをホストしているアカウントを入力します。 たとえば、SQL Server がという名前のアカウントで実行されている*sqlservice*、入力`sqlservice`です。 

    * サービス一覧を選択します。 そのアカウントで使用できる SPN が表示されます。 そのアカウントのサービス一覧が表示されない場合は、サービスがないか、別のアカウントのサービスの可能性があります。 SPN の調整には、SetSPN ユーティリティを使用できます。

    * [OK] を選択してダイアログを閉じます。

3. C2WTS の構成*AllowedCallers*です。

    必要です「呼び出し元」の id を明示的に C2WTS の構成ファイルに記載されて**C2WTShost.exe.config**です。C2WTS は、そのように構成されていない限り、システム内のすべての認証ユーザーからの要求を受け入れません。 ここでは、"呼び出し元' は、WSS_WPG Windows グループです。 C2WTShost.exe.confi ファイルは、次の場所に保存されます。

    C2WTS サービスについて、SharePoint サーバーの全体管理内でサービス アカウントを変更すると、そのアカウントが WSS_WPG グループに追加されます。

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

4. 使用して、SharePoint サーバーの全体管理の Windows トークン サービスに対するクレームを開始、**管理サーバーのサービスの**ページ。 このサービスは、アクションを実行するサーバーで起動する必要があります。 たとえば、WFE とだけを実行して、SQL Server Reporting Services 共有サービスを持つアプリケーション サーバーである別のサーバーは、アプリケーション サーバーで C2WTS を起動する必要があります。 サーバーがある場合。 C2WTS は、レポート ビューアー web パーツを実行している場合に、WFE サーバーにのみ必要です。

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)

