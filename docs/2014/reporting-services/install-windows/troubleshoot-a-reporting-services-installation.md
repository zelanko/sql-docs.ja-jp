---
title: Reporting Services のインストールのトラブルシューティング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: e2536f7f-d90c-4571-9ffd-6bbfe69018d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5a27cbad6803c2106c0af4cbe4060e72cc8ee970
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66108664"
---
# <a name="troubleshoot-a-reporting-services-installation"></a>Reporting Services インストール時の問題解決
  セットアップ中にエラーが発生して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をインストールできない場合は、このトピックで示す手順に従って、インストール エラーの原因として最も可能性が高い状況に対処してください。  
  
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の問題の最新情報については、「 [Reporting Services SQL Server 2012 の役立つヒントおよびトラブルシューティング](https://go.microsoft.com/fwlink/?LinkId=221297)」を参照してください。  
  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に関連するその他のエラーや問題については、「 [SSRS の問題とエラーのトラブルシューティング](https://social.technet.microsoft.com/wiki/contents/articles/ssrs-troubleshooting-issues-and-errors.aspx)」を参照してください。  
  
 発生した問題がリリース ノートに記載されている場合があるので、 [オンライン リリース ノート](https://go.microsoft.com/fwlink/?linkid=236893) を参照してください。  
  
 このトピックの内容は次のとおりです。  
  
-   [セットアップ ログを確認してください。](#bkmk_setuplogs)  
  
-   [前提条件を確認します。](#bkmk_prereq)  
  
-   [SharePoint モードのインストールに関する問題をトラブルシューティングします。](#bkmk_tshoot_sharepoint)  
  
-   [ネイティブ モードのインストールに関する問題をトラブルシューティングします。](#bkmk_tshoot_native)  
  
-   [その他のリソース](#bkmk_additional)  
  
##  <a name="bkmk_setuplogs"></a> セットアップ ログのチェック  
 セットアップ エラーがログ ファイルに記録された、 **Program files \microsoft SQL server \110\setup bootstrap \log**フォルダー。 セットアップを実行するたびにサブフォルダーが作成されます。 サブフォルダー名はセットアップを実行した日時です。 セットアップ ログ ファイルの表示方法については、「 [SQL Server セットアップ ログ ファイルの表示と読み取り](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)」を参照してください。  
  
-   ログ ファイルには複数のファイルが含まれます。  
  
-   製品、コンポーネント、およびインスタンスの情報を表示するには、*_summary.txt ファイルを開きます。  
  
-   セットアップ中に生成されたエラー情報を表示するには、*_errorlog.txt ファイルを開きます。  
  
-   \_\*のセットアップ情報を表示するには、*_RS [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] _ComponentUpdateSetup.log を開きます。  
  
##  <a name="bkmk_prereq"></a> 前提条件のチェック  
 セットアップでは、前提条件が自動的にチェックされます。 ただし、セットアップ時の問題のトラブルシューティングを行う場合は、セットアップでチェックされる前提条件を把握しておくと役に立ちます。  
  
-   セットアップを実行するには、アカウントがローカルの Administrators グループのメンバーであることが必要です。 セットアップには、ファイルの追加、レジストリの設定、ローカル セキュリティ グループの作成、および権限の設定を行うための権限が必要です。 既定の構成をインストールする場合は、インストールする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにレポート サーバー データベースを作成する権限がセットアップに必要です。  
  
-   オペレーティング システムが HTTP.SYS 1.1 をサポートしている必要があります。  
  
-   HTTP サービスが有効になっていて、実行されている必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスもインストールする場合は、分散トランザクション コーディネーター (DTC) が実行されている必要があります。  
  
-   System32 フォルダーに Authz.dll があることが必要です。  
  
 インターネット インフォメーション サービス (IIS) または [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]はセットアップでチェックされなくなりました。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には MDAC 2.0 および [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 2.0 が必要です。これらがインストールされていない場合は、セットアップで自動的にインストールされます。  
  
##  <a name="bkmk_tshoot_sharepoint"></a> SharePoint モードのインストールでのトラブルシューティング  
  
-   [Reporting Services 構成マネージャーが起動しない](#bkmk_configmanager_notstart)  
  
-   [SQL Server 2012 SSRS を SharePoint モードでインストールした後、SharePoint サーバーの全体管理で、SQL Server Reporting Services サービスが表示されません。](#bkmk_no_ssrs_service)  
  
-   [Reporting Services の PowerShell コマンドレットが使用できず、コマンドが認識されない](#bkmk_cmdlets_not_recognized)  
  
-   [URL が構成されていないことを示すエラー メッセージが表示される](#bkmk_URL_not_configured)  
  
-   [SharePoint がインストールされているコンピューターが構成されていない場合にセットアップに失敗する](#bkmk_sharepoint_not_confiugred)  
  
-   [SharePoint サーバーの全体管理ページが空白である](#bkmk_central_admin_blank)  
  
-   [新しいレポート ビルダー レポートを作成しようとすると、エラー メッセージが表示される](#bkmk_reportbuilder_newreport_error)  
  
-   [RS_SHP は PREPAREIMAGE でサポートされないことを示すエラー メッセージが表示される](#bkmk_RS_SHP_notsupported)  
  
###  <a name="bkmk_configmanager_notstart"></a> Reporting Services 構成マネージャーが起動しない  
 **説明 :** この問題は仕様で[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は現在、SharePoint サービス アーキテクチャ用に設計されています。 SharePoint モードで [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を構成および管理するために、構成マネージャーを使用する必要はなくなりました。  
  
 **回避策:** SharePoint モードでレポート サーバーを構成するには、SharePoint サーバーの全体管理を使用します。 詳細については、「 [Reporting Services SharePoint サービス アプリケーションの管理](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)｣を参照してください  
  
###  <a name="bkmk_no_ssrs_service"></a> SQL Server 2012 SSRS を SharePoint モードでインストールした後、SharePoint サーバーの全体管理で、SQL Server Reporting Services サービスが表示されません。  
 **説明 :** 場合に正常にインストールした後[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードで、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]アドイン、SharePoint 2010 の表示されない"SQL Server Reporting Services"次の 2 つのメニューで、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]サービスには登録されていません。  
  
-   SharePoint 2010 サーバーの全体管理には [アプリケーション管理]-> ["管理サービスのサーバー] ページ  
  
-   -> [アプリケーション管理] の SharePoint 2010 サーバーの全体管理]-> [->"新規作成] メニューの [サービス アプリケーションの管理"  
  
 **回避策:** 登録および起動する、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Services の場合、次の手順します。  
  
1.  SharePoint 2010 サーバーの全体管理を実行するコンピューターで、次を実行します。  
  
    1.  管理者特権を使用して、SharePoint 2010 管理シェルを開きます。 アイコンを右クリックし、[管理者として実行] をクリックします。 シェルから次の 3 つのコマンドレットを実行します。  
  
    2.  ```  
        Install-SPRSService  
        ```  
  
    3.  ```  
        Install-SPRSServiceProxy  
        ```  
  
    4.  ```  
        Get-SPServiceInstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
        ```  
  
2.  確認、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]サービスとしてのステータスを表示する"**開始**"、ページ。SharePoint 2010 サーバーの全体管理]-> ["**アプリケーション管理**"->"**サービス サーバーの管理**"  
  
###  <a name="bkmk_cmdlets_not_recognized"></a> Reporting Services の PowerShell コマンドレットが使用できず、コマンドが認識されない  
 **説明 :** 実行しようとすると、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] PowerShell のコマンドレットには、次のようなエラー メッセージを表示します。  
  
-   用語 'Install-SPRSServiceInstall-SPRSService' は、コマンドレット、関数、スクリプト ファイル、または操作可能なプログラムの名前として **認識されません** 。 名前のスペルを確認するか、パスが正しいことを確認し、もう一度お試しパスが含まれている場合。行: 1 文字: 39 + Install-sprsservice SPRSServiceInstall で <<<< + CategoryInfo:ObjectNotFound:(Install-SPRSServiceInstall-SPRSService:String) [], CommandNotFoundExcep  
  
 **回避策:** 次のいずれかの操作を行います。  
  
-   SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインを実行します。 **rssharepoint.msi**。  
  
-   SQL Server のインストール メディアから、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードをインストールします。  
  
 **注:** 場合、 **SharePoint 2013 管理シェル**の回避策のいずれかを完了、終了して、管理シェルを再起動したときに、開いています。  
  
 詳細については、以下を参照してください。  
  
-   [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
-   [SharePoint 2010 用 Reporting Services の SharePoint モードのインストール](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
-   [For SharePoint 2013 の Reporting Services SharePoint モードをインストールします。](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
###  <a name="bkmk_URL_not_configured"></a> URL が構成されていないことを示すエラー メッセージが表示される  
 **説明 :** 参照してくださいとエラーは、次のようなメッセージします。  
  
 この SQL Server Reporting Services (SSRS) の機能はサポートされていません。 サーバーの全体管理を使用して、次の問題を確認し、修正してください: •レポート サーバーの URL が構成されていません。 SSRS の統合ページを使用して設定してください。•SSRS サービス アプリケーション プロキシが構成されていません。 SSRS サービス アプリケーションのページを使用してプロキシを構成してください。•SSRS サービス アプリケーションは、この Web アプリケーションにマップされていません。 SSRS サービス アプリケーションのページを使用して SSRS サービス アプリケーション プロキシをこの Web アプリケーションのアプリケーション プロキシ グループに関連付けてください。  
  
 **回避策:** エラー メッセージには、この問題を修正する 3 つの推奨される手順が含まれています。 メッセージ「レポート サーバーの URL が構成されていません..」の最初の推奨 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]よりも前のレポート サーバー バージョンとの統合に関連します。 以前のレポート サーバー バージョンの SharePoint 構成は、 **SQL Server Reporting Services (2008 および 2008 R2)** を使用して **[アプリケーションの全体設定]** ページで完了されます。  
  
 **詳細情報:** いずれかを使用すると、このエラー メッセージが表示されます、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]への接続を必要とする機能、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]サービス。 この機能には、次が含まれます。  
  
-   SQL Server レポート ビルダーを SharePoint ドキュメント ライブラリから開いている。  
  
-   サブスクリプションを管理する。  
  
-   サービス アプリケーションを管理する。  
  
###  <a name="bkmk_sharepoint_not_confiugred"></a> SharePoint がインストールされているコンピューターが構成されていない場合にセットアップに失敗する  
 **説明 :** 選択した場合は、SharePoint をあるコンピューター上で Reporting Services SharePoint モードをインストールするインストール、SharePoint が構成されていませんが、セットアップ、次のようなメッセージは停止が表示されます。  
  
 SQL Server セットアップは動作を停止しました  
  
 **回避策:** SharePoint を構成し、SQL Server のインストールを実行します。  
  
 **詳細情報:** インストールするときに[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]に既存の SharePoint のインストール、セットアップ プログラムをインストールして起動を試行し、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint サービス。 SharePoint が構成されていないと、このサービスのインストールは失敗し、セットアップがエラーを返します。  
  
###  <a name="bkmk_central_admin_blank"></a> SharePoint サーバーの全体管理ページが空白である  
 **説明 :** 正常にインストール エラーなく、SharePoint 2010 をインストールできませんでした。 [サーバーの全体管理] を表示すると空白のページしか表示されないことがあります。  
  
 **回避策:** この問題に固有ではない[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]関連 SharePoint 環境全体における権限を構成するものです。 考えられる解決方法は次のとおりです。  
  
-   開発環境に関する SharePoint トピックを参照します。 [Windows vista では、Windows 7、および Windows Server 2008 の SharePoint 2010 の開発環境を設定](https://msdn.microsoft.com/library/ee554869\(office.14\).aspx)  
  
-   フォーラムの投稿を確認してください。[サーバーの全体管理は、Windows 7 のインストール後に空白のページを返します](https://social.technet.microsoft.com/Forums/en/sharepoint2010setup/thread/a422a3c8-39f6-4b9e-988a-4c4d1e745694)  
  
-   SharePoint サービス (SharePoint 2010 サーバーの全体管理サービスなど) に使用しているサービス アカウントに、ローカル オペレーティング システムの管理者特権を付与します。  
  
###  <a name="bkmk_reportbuilder_newreport_error"></a> 新しいレポート ビルダー レポートを作成しようとすると、エラー メッセージが表示される  
 **説明 :** 次のようなエラー メッセージが表示されるは、ドキュメント ライブラリ内でレポート ビルダーのレポートを作成しようとしたときに。  
  
 SQL Server Reporting Services サービス アプリケーションが存在しないか、またはレポート サーバーの URL がサーバーの全体管理で構成されていないため、この機能はサポートされません。  
  
 **回避策:** あることを確認、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]サービス アプリケーションとそれが正しく構成されています。 詳細については、「セクション 'Reporting Services サービス アプリケーション 'で作成[Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
###  <a name="bkmk_RS_SHP_notsupported"></a> RS_SHP は PREPAREIMAGE でサポートされないことを示すエラー メッセージが表示される  
 **説明 :** に対して PREPAREIMAGE を実行しようとすると[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]次のようなエラー メッセージを参照してください。  
  
 指定された機能 'RS_SHP' は、SysPrep をサポートしていないため、PREPAREIMAGE アクションの実行中にはサポートされません。 SysPrep と互換性のない機能を削除し、セットアップを再実行してください。  
  
 **回避策:** 対応策はありません。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SYSPREP (PREPAREIMAGE) をサポートしていません。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モードでは SYSPREP をサポートしています。  
  
##  <a name="bkmk_tshoot_native"></a> ネイティブ モードのインストールでのトラブルシューティング  
  
###  <a name="PerfCounters"></a> Windows Vista または Windows Server 2008 にアップグレードするとパフォーマンス カウンターが表示されない  
 [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] を実行するコンピューターでオペレーティング システムを [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] または [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]にアップグレードした場合、アップグレード後に [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のパフォーマンス カウンターが設定されなくなります。  
  
#### <a name="to-reinstate-reporting-services-performance-counters"></a>Reporting Services のパフォーマンス カウンターを再設定するには  
  
1.  次のレジストリ キーを削除します。  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service**  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service**  
  
2.  コマンド ウィンドウを開き、コマンド プロンプトで次のコマンドを入力します。  
  
    -   **実行\<**  *.NET 2.0 Framework ディレクトリ* **> \InstallUtil.exe \<**  *レポート サーバーの Bin ディレクトリ* **> \ReportingServicesLibrary.dll**  
  
        > [!NOTE]  
        >  置換\< *.NET 2.0 Framework ディレクトリ*> ファイル、.NET Framework 2.0 の物理パスと置き換えます\<*レポート サーバーの Bin ディレクトリ*> を物理パスレポート サーバーの bin ファイル。  
  
3.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスを再開します。  
  
 手順が正しく行われたことを確認するには、Web ブラウザーを開き、レポート マネージャー URL またはレポート サーバー URL に移動します。 その後、パフォーマンス モニターを開き、カウンターが機能していることを確認します。  
  
#### <a name="to-re-add-the-performance-registry-keys-by-using-registry-editor"></a>レジストリ エディターを使用して Performance のレジストリ キーをもう一度追加するには  
  
1.  レジストリ エディターを開きます。  
  
    1.  **[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]** をクリックします。  
  
    2.  **実行** ダイアログ ボックスで、**オープン**ボックスに「`regedit`します。  
  
2.  レジストリ エディターで、次のレジストリ キーを選択します。 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance`  
  
3.  **[Performance]** ノードを右クリックし、 **[新規]** をポイントして **[複数行文字列値]** をクリックします。  
  
4.  型`Counter Names`し、ENTER キーを押します。  
  
5.  同じ手順を繰り返して、このノードに `Counter Types` レジストリ キーを追加します。  
  
6.  次のレジストリ キーに移動します。 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance`  
  
7.  **[Performance]** ノードを右クリックし、 **[新規]** をポイントして **[複数行文字列値]** をクリックします。  
  
8.  型`Counter Names`し、ENTER キーを押します。  
  
9. 同じ手順を繰り返して、このノードに `Counter Types` レジストリ キーを追加します。  
  
 64 ビット インスタンスを修復するか、レジストリ キーをもう一度手動で追加したら、パフォーマンス モニターを使用して、監視する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] パフォーマンス オブジェクトを構成できます。  
  
###  <a name="ConfigPropsMissing"></a> SQL Server 2005 からアップグレードすると構成プロパティの ReportServerExternalURL と PassThroughCookies が構成されない  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] から [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] にアップグレードする場合は、構成プロパティの `ReportServerExternalURL` と `PassThroughCookies` がアップグレード プロセスで構成されません。 `ReportServerExternalURL` はオプションのプロパティです。SharePoint 2.0 Web パーツを使用していて、ユーザーがレポートを取得して新しいブラウザー ウィンドウで開くことができるようにする場合にのみ設定する必要があります。 詳細については`ReportServerExternalURL`を参照してください[構成ファイル内の Url &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md)します。 `PassThroughCookies` はカスタム認証を使用する場合にのみ必要です。 詳細については`PassThroughCookies`を参照してください[カスタム認証クッキーをレポート マネージャーの構成](../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)します。  
  
> [!NOTE]  
>  カスタム認証を使用する場合は、アップグレードを実行する代わりに現在のインストールを移行することをお勧めします。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を移行する方法については、「[Reporting Services のインストールの移行 &#40;ネイティブ モード&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md)」を参照してください。  
  
 既定では、これらのプロパティは [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] の構成には存在しません。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] でこれらのプロパティを構成していて、その機能が引き続き必要な場合は、アップグレード プロセスの完了後にこれらを手動で **RSReportServer.config** ファイルに追加する必要があります。 詳細については、「[Reporting Services の構成ファイルの変更 &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)」を参照してください。  
  
###  <a name="Default2005InstallBreaks2008"></a> SQL Server 2012 reporting Services を実行するコンピューターに SQL Server 2005 Reporting Services の既定のインスタンスのインストールが失敗します。  
 既定のインスタンスをインストールしようとした場合[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のインスタンスが既に実行されているコンピューターで[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]インスタンスは次のエラー メッセージでインストールが失敗します。  
  
 "このコンピューターには、同じ名前のインスタンスが既にインストールされています。 SQL Server のセットアップを続行するには、一意なインスタンス名を指定してください。"  
  
 この問題は、 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] インスタンスが既定のインスタンスであっても名前付きインスタンスであっても、その名前の [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] インスタンスが既にコンピューターに存在していてもいなくても、発生します。  
  
 この問題を回避するには次の方法があります。  
  
-    [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をコンピューター上の既定のインスタンスとして実行する必要がある場合は、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスを [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] インスタンスの前にインストールする必要があります。  
  
-   場合、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]インスタンスが既定のインスタンスにする必要はありませんをインストールすることができます、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]インスタンスをインストールした後に、名前付きインスタンスとして、[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]インスタンス。  
  
###  <a name="WindowsAuthBreaksAfterUpgrade"></a> SQL Server 2005 から SQL Server 2012 へのアップグレード後に Windows 認証を使用するときに 401-エラー  
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] から [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]にアップグレードする場合に、レポート サーバー サービス アカウントにビルトイン アカウントを使用して NTLM 認証を使用していると、アップグレード後にレポート サーバーやレポート マネージャーにアクセスするときに "401 - 権限がありません" エラーが表示される場合があります。  
  
 この問題が発生するのは、 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] で Windows 認証の既定の構成が変更されているためです。 レポート サーバー サービス アカウントが NetworkService または LocalSystem である場合はネゴシエートが構成され、 レポート サーバー サービス アカウントがこれらのビルトイン アカウントではない場合は NTLM が構成されます。 アップグレード後にこの問題を修正するには、RSReportServer.config ファイルを編集して `AuthenticationType` を `RSWindowsNTLM` に設定します。 詳細については、「 [レポート サーバーで Windows 認証を構成する](../security/configure-windows-authentication-on-the-report-server.md)」を参照してください。  
  
###  <a name="Uninstall32BitBreaks64Bit"></a> 64 ビット インスタンスの中断、64 ビット インスタンスとサイド バイ サイド配置での SQL Server 2012 Reporting Services のインスタンスの 32 ビットをアンインストールします。  
 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] の 32 ビット インスタンスと 64 ビット インスタンスをサイド バイ サイドでコンピューターにインストールしている場合に 32 ビット インスタンスをアンインストールすると、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の 4 つのレジストリ キーが削除されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の 64 ビット インスタンスが破損します。 32 ビット インスタンスをアンインストールすると削除されるのは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の以下のレジストリ キーです。  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance:Counter Types` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service\Performance:Counter Types`  
  
 この問題を修正するには、64 ビット インスタンスを修復します。 修復を使用することをお勧めしますが、レジストリ エディターを使用してレジストリ キーをもう一度手動で追加することもできます。  
  
> [!CAUTION]  
>  レジストリを誤って編集すると、システムに重大な障害が発生する場合があります。 レジストリを変更する前に、コンピューター上のすべての重要なデータをバックアップしておくことをお勧めします。  
  
##  <a name="bkmk_additional"></a> その他のリソース  
 以下に示すのは、問題解決時に役立つ可能性のある追加資料です。  
  
-   TechNet Wiki:Shooting トピックを問題[のトラブルシューティングを行う SQL Server Reporting Services (SSRS) の SharePoint 統合モード](https://social.technet.microsoft.com/wiki/contents/articles/troubleshoot-sql-server-reporting-services-ssrs-in-sharepoint-integrated-mode.aspx)  
  
-   [フォーラム:SQL Server Reporting Services](http://social.msdn.microsoft.com/Forums/sqlreportingservices/threads)  
  
 ![SharePoint の設定](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 設定")[フィードバックや連絡先の情報を Microsoft SQL Server の接続を介して送信](https://connect.microsoft.com/SQLServer/Feedback)(https://connect.microsoft.com/SQLServer/Feedback)します。  
  
  
