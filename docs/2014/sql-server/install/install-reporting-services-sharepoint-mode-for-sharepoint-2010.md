---
title: Install Reporting Services SharePoint Mode for SharePoint 2010 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47efa72e-1735-4387-8485-f8994fb08c8c
caps.latest.revision: 41
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 765713eba66f571e14328351413011762ec71a4b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178375"
---
# <a name="install-reporting-services-sharepoint-mode-for-sharepoint-2010"></a>SharePoint 2010 用 Reporting Services の SharePoint モードのインストール
  このトピックでは、SharePoint モードでの Reporting Services レポート サーバーのシングル サーバー インストールの手順について説明します。 手順には、SQL Server インストール ウィザードの実行と、SharePoint 2010 サーバーの全体管理を使用する追加構成タスクが含まれます。 また、既存のインストールについての個々の手順 ([!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの作成など) をこのトピックで確認することもできます。 追加を追加する方法について[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、既存のファームにサーバーを参照してください[ファームに追加のレポート サーバーを追加&#40;SSRS スケール アウト&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)と[Reporting Services Web の追加ファームのフロント エンド](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)です。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010|  
  
 シングル サーバー インストールは開発およびテスト シナリオ便利ですが、運用環境にはお勧めしません。  
  
> [!NOTE]  
>  アップグレードして、既存のについて[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint モードのインストールを[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]を参照してください[Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)です。  
  

  
##  <a name="bkmk_prereq"></a> 前提条件  
  
-   > [!IMPORTANT]  
    >  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードを構成および管理するために、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用するまたはサポートする必要はなくなりました。 SharePoint モードでレポート サーバーを構成するには、SharePoint サーバーの全体管理を使用します。 詳細については、次を参照してください。 [Reporting Services SharePoint サービス アプリケーションの管理](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)です。  
  
-   SharePoint 2010 製品を含む要件については、次のトピックを参照してください。  
  
    -   [オンライン リリース ノート](https://msdn.microsoft.com/library/dn169381.aspx)
  
    -   [SharePoint 2010 ファームで SQL Server BI 機能を使用するためのガイド](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
-   このトピックでは、SharePoint 2010 製品のインストールについては説明しません。 詳細については、次を参照してください。 [、SharePoint 2010 ファームで SQL Server BI 機能を使用するためのガイダンス](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)です。  
  
-   ここで説明する手順は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポート サーバーを構成するためのものであり、以前のバージョンのレポート サーバーには使用できません。 以前のバージョンのレポート サーバーでは、SharePoint 共有サービス アーキテクチャが使用されていませんでした。 たとえば、SQL Server 2008 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーや、SQL Server 2008 R2 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーなどです。  
  
-   確認、 **SharePoint 2010 管理**Windows サーバー マネージャーでサービスが開始されています。  
  
 ![1 サーバー インストール上の SSRS コンポーネント](../../../2014/sql-server/install/media/rs-deployment-1-server.gif "1 サーバー インストール上の SSRS コンポーネント")  
  
### <a name="database-considerations-for-a-single-server-configuration"></a>単一のサーバー構成に関するデータベースの注意事項  
  
-   Reporting Services および SharePoint 製品とテクノロジはどちらも、SQL Server のリレーショナル データベースを使用して、アプリケーション データを格納します。  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] には、SQL エンジンの互換性のある SQL Server 評価版インスタンスが必要です。  
  
-   SharePoint 製品では、既存のデータベース インスタンスを使用できます。 データベース エンジンのインスタンスがインストールされていない場合、SharePoint 製品のセットアップ プログラムは、SharePoint アプリケーションのデータベース用 SQL Server Express Edition をインストールします。  
  
-   レポート サーバー インスタンスの場合、データベースに SQL Server Express Edition を使用することはできません。 ただし、SharePoint 製品によってインストールされる SQL Server Express Edition インスタンスは、他のデータベース エンジン エディションと共存できます。  
  

  
##  <a name="bkmk_install_SSRS"></a> SharePoint モードでの Reporting Services レポート サーバーをインストールします。  
  
1.  SQL Server インストール ウィザードを実行します。  
  
2.  ウィザードの左側の **[インストール]** をクリックし、 **[SQL Server の新規スタンドアロン インストールを実行するか、既存のインストールに機能を追加します]** をクリックします。  
  
3.  **[セットアップ サポート ルール]** ページで、すべてのルールに合格したら、 **[OK]** をクリックします。  
  
4.  **[セットアップ サポート ファイル]** ページで、 **[インストール]** をクリックします。  
  
5.  をクリックして **[次へ]** サポート ファイルのインストールが完了し、サポート ルールの状態の表示後**渡される**です。 警告やインストールの障害となる問題を確認します。  
  
6.  **プロダクト キー**ページで、キーを入力するか、"Enterprise Evaluation"エディションの既定値をそのまま使用します。  
  
     **[次へ]** をクリックします。  
  
7.  使用許諾条件を確認して同意します。 マイクロソフトでは、機能使用状況に関するデータを送信することに同意して、製品の機能やサポートの改善にご協力いただき感謝しております。  
  
     **[次へ]** をクリックします。  
  
8.  選択**SQL Server 機能のインストール**上、**セットアップ ロール**ページ。  
  
     **[次へ]** をクリックします。  
  
     ![セットアップ ロールの SQL Server 機能のインストール](../../../2014/sql-server/install/media/rs-setuprole.gif "セットアップ ロールの SQL Server 機能のインストール")  
  
9. **[機能の選択]** ページで、次のオプションを選択します。  
  
    -   **Reporting Services – SharePoint**  
  
    -   **Reporting Services アドインを SharePoint 2010 製品用**です。 ![注](../../../2014/reporting-services/media/rs-fyinote.png "注")アドインをインストールするためのインストール ウィザード オプションはの新機能、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]リリースします。  
  
    -   かどうかしていない SQL Server のインスタンス[!INCLUDE[ssDE](../../includes/ssde-md.md)]、選択することも**データベース エンジン サービス**と**管理ツール-完全**の完全な環境です。  
  
     **[次へ]** をクリックします。  
  
     ![SharePoint モードの SSRS の機能の選択](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "SSRS SharePoint モードの機能の選択")  
  
10. をクリックして**次**上、**インストール ルール**ページ。 警告やインストールの障害となる問題を確認します。  
  
11. データベース エンジン サービスを選択した場合は、 **[インスタンスの構成]** ページで **MSSQLSERVER** の既定のインスタンスを受け入れて、 **[次へ]** をクリックします。 Reporting Services 共有サービス アーキテクチャは、以前の Reporting Services アーキテクチャとは異なり、SQL Server "インスタンス" に基づいていません。  
  
12. **[必要なディスク領域]** ページを確認し、 **[次へ]** をクリックします。  
  
13. **サーバー構成**ページ適切な資格情報を入力します。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のデータ警告機能またはサブスクリプション機能を使用する場合は、SQL Server エージェントの **[スタートアップの種類]** を **[自動]** に変更する必要があります。  
  
     **[次へ]** をクリックします。  
  
14. データベース エンジン サービスを選択した場合は、 **[データベース エンジンの構成]** ページが表示されるので、SQL 管理者の一覧に適切なアカウントを追加して、 **[次へ]** をクリックします。  
  
15. **[Reporting Services の構成]** ページで、 **[インストールのみ]** オプションをクリックします。 このオプションは、レポート サーバーのファイルをインストールし、用の SharePoint 環境を構成しません[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]です。SQL Server のインストールが完了したら、SharePoint 環境を構成するのには、このトピックの他のセクションに従ってください。 これには、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービスのインストールと、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの作成が含まれます。  
  
     ![rs_SQL11_SETUP_SSRS_configpage_withcircles](../../../2014/sql-server/install/media/rs-kj-setup-ssrs-configpage-withcircles.gif "rs_SQL11_SETUP_SSRS_configpage_withcircles")  
  
16. **[エラー レポート]** ページでエラー レポートを送信するためのチェック ボックスをオンにすると、マイクロソフトが SQL Server の機能とサービスを改善するのに役立ちます。  
  
     **[次へ]** をクリックします。  
  
17. **[インストール構成ルール]** ページで警告を確認して、 **[次へ]** をクリックします。  
  
18. **[インストールの準備完了]** ページで、インストールの概要を確認して **[次へ]** をクリックします。 概要が含まれます、 **Reporting Services**のインストール モード値を含むノード**SharePointFilesOnlyMode**とアカウント情報。  
  

  
##  <a name="bkmk_install_SSRS_sharedservice"></a> インストールし、Reporting Services SharePoint サービスを開始  
 ![PowerShell 関連コンテンツ](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")  
  
> [!NOTE]  
>  既存の SharePoint ファームにインストールする場合**する必要はありません**のこのセクションの手順を完了します。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint サービスがインストールされているし、前のセクションで、SQL Server インストール ウィザードを実行するときに開始します。  
  
 必要なファイルは SQL Server インストール ウィザードの中でインストールされていますが、サービスを SharePoint ファームに登録する必要があります。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]リリースの PowerShell のサポートが導入されて[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint モードでします。 以下では、SharePoint 管理シェルを開いてコマンドレットを実行する手順を説明します。  
  
1.  **[スタート]** ボタンをクリックします。  
  
2.  クリックして、 **Microsoft SharePoint 2010 製品**グループ。  
  
3.  右クリック**SharePoint 2010 管理シェル**クリックして**管理者として実行**です。  
  
4.  次の PowerShell コマンドを実行して、SharePoint サービスをインストールします。 コマンドが正常に完了すると、管理シェルの表示が改行されます。 コマンドが正常に完了しても、管理シェルにメッセージは表示されません。  
  
    ```  
    Install-SPRSService  
    ```  
  
5.  サービス プロキシをインストールする次の PowerShell コマンドを実行します。  
  
    ```  
    Install-SPRSServiceProxy  
    ```  
  
6.  サービスを起動したり、SharePoint サーバーの全体管理からサービスを開始する方法については、次のノートを参照してください。 次の PowerShell コマンドを実行します。  
  
    ```  
    get-spserviceinstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
    ```  
  
 3 番目の PowerShell コマンドを実行する代わりに、SharePoint サーバーの全体管理からサービスを開始することもできます。 次の手順を使用すると、サービスが実行していることを確認することもできます。  
  
1.  SharePoint サーバーの全体管理で、 **[システム設定]** の **[サーバーのサービスの管理]** をクリックします。  
  
2.  **[SQL Server Reporting Services サービス]** を探して、[アクション] 列の **[開始]** をクリックします。  
  
3.  Reporting Services サービスのステータスが **[停止]** から **[開始]** に変わります。 Reporting Services サービスが一覧にない場合は、PowerShell を使用してサービスをインストールします。  
  
    > [!NOTE]  
    >  Reporting Services サービス内に保持する場合、**開始**状態に変更されていないと**Started**、"SharePoint 2010 Administration"サービスが Windows サーバー マネージャーを開始することを確認します。  
  

  
##  <a name="bkmk_create_serrviceapplication"></a> Reporting Services サービス アプリケーションを作成します。  
 ここでは、既存のサービス アプリケーションを確認している場合に、サービス アプリケーションおよびプロパティの説明を作成する手順について説明します。  
  
1.  SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  SharePoint リボンで、 **[新規作成]** ボタンをクリックします。  
  
3.  [新規作成] メニューで、 **[SQL Server Reporting Services サービス アプリケーション]** をクリックします。  
  
    > [!WARNING]  
    >  場合、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]オプションは表示されません、ボックスの一覧では、**を示す値を[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]共有サービスがインストールされていない**です。 前のセクションの、PowerShell コマンドレットを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスをインストールする方法を確認してください。  
  
4.  **[SQL Server Reporting Services サービス アプリケーションの作成]** ページで、アプリケーションの名前を入力します。 複数の Reporting Services サービス アプリケーションを作成する場合、わかりやすい名前または名前付け規則整理することが、管理および運用操作します。  
  
5.  **[アプリケーション プール]** セクションで、このアプリケーションのための新しいアプリケーション プールを作成します (推奨)。 新しいアプリケーション プールに同じ名前を使用して、サービス アプリケーションと、管理が容易進行中です。  
  
     そのアプリケーション プールのマネージ アカウントを選択または作成します。 必ずドメイン ユーザー アカウントを指定してください。 ドメイン ユーザー アカウントにより、パスワードやアカウント情報をまとめて更新できる SharePoint のマネージ アカウント機能を使用できるようになります。 ドメイン アカウントは、配置をスケールアウトして、同じ ID で実行されるサービス インスタンスを追加する場合にも必要です。  
  
6.  **[データベース サーバー]** で、現在のサーバーを使用するか、または別の SQL Server を選択することができます。  
  
7.  **[データベース名]** の既定値は " `ReportingService_<guid>`" で、これは一意のデータベース名です。 新しい値を入力する場合は、一意の値を入力します。  
  
8.  **[データベース認証]** の既定値は、"Windows 認証" です。 **[SQL 認証]** を選択する場合は、SharePoint 管理者ガイドを参照して、SharePoint 配置でその認証の種類を使用するためのベスト プラクティスを確認してください。  
  
9. **[Web アプリケーションの関連付け]** セクションで、現在の Reporting Services サービス アプリケーションによるアクセス用に準備する Web アプリケーションを選択します。 1 つの Reporting Services サービス アプリケーションを 1 つの Web アプリケーションに関連付けることができます。 現在のすべての Web アプリケーションが既に Reporting Services サービス アプリケーションと関連付けられている場合は、警告メッセージが表示されます。  
  
10. **[OK]** をクリックします。  
  
11. サービス アプリケーションの作成処理には数分かかることがあります。 完了すると、確認メッセージと、 **[サブスクリプションと警告の準備]** ページへのリンクが表示されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のサブスクリプション機能と警告機能を使用する場合は、準備手順を行います。 詳細については、「[SSRS サービス アプリケーションを使用するためのサブスクリプションと警告の準備](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)」を参照してください。  
  
 ![PowerShell 関連コンテンツ](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")PowerShell を使用して作成する方法については、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]サービス アプリケーションを参照してください[Reporting Services サービス アプリケーションを作成するにはPowerShell を使用して](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp)です。  
  

  
##  <a name="bkmk_powerview"></a> Power View のサイト コレクション機能を有効にします。  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、、の機能[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]用アドイン[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition では、サイト コレクション機能です。 この機能は、ルート サイト コレクションと、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインのインストール後に作成されたサイト コレクションで自動的にアクティブ化されます。 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]を使用する場合は、この機能がアクティブ化されていることを確認してください。  
  
 SharePoint 2010 製品のインストール後に SharePoint 2010 製品用の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールした場合、レポート サーバーの統合機能と Power View の統合機能はルート サイト コレクションでのみアクティブ化されます。 他のサイト コレクションについては、この機能を手動でアクティブ化します。  
  
#### <a name="to-activate-the-power-view-feature"></a>Power View 機能をアクティブ化するには  
  
1.  ブラウザーで目的の SharePoint サイトを開きます。  
  
2.  **[サイトの操作]** をクリックします。  
  
3.  **[サイトの設定]** をクリックします。  
  
4.  [サイト コレクションの管理] グループで **[サイト コレクションの機能]** をクリックします。  
  
5.  一覧で **[Power View 統合機能]** を探します。  
  
6.  **[アクティブ化]** をクリックします。  
  
 この手順は、サイト コレクションごとに実行します。 詳細については、次を参照してください。 [Activate Report Server and Power View Integration Features in SharePoint](../../reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)です。  
  
##  <a name="bkmk_additional_config"></a> その他の構成  
 このセクションでは、SharePoint のほとんどの配置で重要になる追加の構成手順について説明します。  
  
###  <a name="bkmk_provision_agent"></a> [サブスクリプションと警告の準備]  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のサブスクリプションとデータ警告の機能を利用するには、SQL Server エージェントの権限の構成が必要になる場合があります。 SQL Server エージェントが実行中であるにもかかわらず、SQL Server エージェントが必要であることを示すエラー メッセージが表示された場合は、権限を更新します。 サービス アプリケーション作成成功ページの **[サブスクリプションと警告の準備]** リンクをクリックして、SQL Server エージェントを準備するための別のページに移動します。 配置がコンピューターの境界をまたいでいる場合は (たとえば、SQL Server データベース インスタンスが異なるコンピューターにある場合)、準備手順を行う必要があります。 詳細については、「 [SSRS サービス アプリケーションを使用するためのサブスクリプションと警告の準備](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)」をご覧ください  
  

  
### <a name="configure-e-mail-for-a-service-application"></a>サービス アプリケーションの電子メールを構成します。  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のデータ警告機能は、電子メール メッセージで警告を送信します。 電子メールを送信するには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを構成して、このサービス アプリケーションの電子メール配信拡張機能を変更しなければならない場合があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サブスクリプション機能の電子メール配信拡張機能を使用する場合は、電子メールの設定が必要です。 詳細については、「[Reporting Services サービス アプリケーションの電子メールの構成 &#40;SharePoint 2010 および SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)」を参照してください。  
  

  
### <a name="add-reporting-services-content-types"></a>Reporting Services のコンテンツの種類を追加  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、共有データ ソース (.rsds) ファイル、レポート モデル (.smdl)、レポート ビルダーのレポート定義 (.rdl) ファイルを管理する際に使用されるコンテンツの種類が、あらかじめ定義されています。 コンテンツの種類として、 **[レポート ビルダー レポート]**、 **[レポート モデル]**、および **[レポート データ ソース]** をライブラリに追加すると、 **[新規作成]** コマンドが有効になり、その種類のドキュメントを新規作成できるようになります。 詳細については、次を参照してください。[追加レポート サーバー コンテンツ タイプをライブラリに&#40;Reporting Services SharePoint 統合モードで&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)です。  
  

  
### <a name="activate-the-file-sync-feature"></a>ファイル同期機能のアクティブ化  
 ユーザーがパブリッシュ済みレポート アイテムを SharePoint ドキュメント ライブラリに頻繁に直接アップロードする場合は、レポート サーバーのファイル同期機能が役立ちます。 ファイル同期機能では、レポート サーバー カタログとドキュメント ライブラリのアイテムの同期が、より頻繁に行われます。 詳しくは、「 [SharePoint サーバーの全体管理でレポート サーバーのファイル同期機能をアクティブにする](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [Reporting Services SharePoint モード用の PowerShell コマンドレット](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)   
 [SQL Server 2012 の各エディションでサポートされる機能](http://go.microsoft.com/fwlink/?linkid=232473)   
 [Reporting Services SharePoint サービスとサービス アプリケーション](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)  
  
  