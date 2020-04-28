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
ms.openlocfilehash: 4a9415e7258216c975dd066995bf347deca1d623
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "75253199"
---
# <a name="troubleshoot-a-reporting-services-installation"></a>Reporting Services インストール時の問題解決
  セットアップ中にエラーが発生して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をインストールできない場合は、このトピックで示す手順に従って、インストール エラーの原因として最も可能性が高い状況に対処してください。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の問題の最新情報については、「 [Reporting Services SQL Server 2012 の役立つヒントおよびトラブルシューティング](https://go.microsoft.com/fwlink/?LinkId=221297)」を参照してください。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に関連するその他のエラーや問題については、「 [SSRS の問題とエラーのトラブルシューティング](https://social.technet.microsoft.com/wiki/contents/articles/ssrs-troubleshooting-issues-and-errors.aspx)」を参照してください。  
  
 発生した問題がリリース ノートに記載されている場合があるので、 [オンライン リリース ノート](https://go.microsoft.com/fwlink/?linkid=236893) を参照してください。  
  
 このトピックの内容は次のとおりです。  
  
-   [セットアップログの確認](#bkmk_setuplogs)  
  
-   [前提条件の確認](#bkmk_prereq)  
  
-   [SharePoint モードのインストールに関する問題のトラブルシューティング](#bkmk_tshoot_sharepoint)  
  
-   [ネイティブモードのインストールに関する問題のトラブルシューティング](#bkmk_tshoot_native)  
  
-   [その他のリソース](#bkmk_additional)  
  
##  <a name="check-setup-logs"></a><a name="bkmk_setuplogs"></a> セットアップ ログのチェック  
 セットアップエラーは、 **Program ARE SQL Server\110\Setup Bootstrap\Log**フォルダー内のログファイルに記録されます。 セットアップを実行するたびにサブフォルダーが作成されます。 サブフォルダー名はセットアップを実行した日時です。 セットアップ ログ ファイルの表示方法については、「 [SQL Server セットアップ ログ ファイルの表示と読み取り](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)」を参照してください。  
  
-   ログ ファイルには複数のファイルが含まれます。  
  
-   製品、コンポーネント、およびインスタンスの情報を表示するには、*_summary.txt ファイルを開きます。  
  
-   セットアップ中に生成されたエラー情報を表示するには、*_errorlog.txt ファイルを開きます。  
  
-   \_\*のセットアップ情報を表示するには、*_RS [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] _ComponentUpdateSetup.log を開きます。  
  
##  <a name="check-prerequisites"></a><a name="bkmk_prereq"></a> 前提条件のチェック  
 セットアップでは、前提条件が自動的にチェックされます。 ただし、セットアップ時の問題のトラブルシューティングを行う場合は、セットアップでチェックされる前提条件を把握しておくと役に立ちます。  
  
-   セットアップを実行するには、アカウントがローカルの Administrators グループのメンバーであることが必要です。 セットアップには、ファイルの追加、レジストリの設定、ローカル セキュリティ グループの作成、および権限の設定を行うための権限が必要です。 既定の構成をインストールする場合は、インストールする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにレポート サーバー データベースを作成する権限がセットアップに必要です。  
  
-   オペレーティング システムが HTTP.SYS 1.1 をサポートしている必要があります。  
  
-   HTTP サービスが有効になっていて、実行されている必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスもインストールする場合は、分散トランザクション コーディネーター (DTC) が実行されている必要があります。  
  
-   System32 フォルダーに Authz.dll があることが必要です。  
  
 インターネット インフォメーション サービス (IIS) または [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]はセットアップでチェックされなくなりました。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]MDAC 2.0 および[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]バージョン2.0 が必要です。これらがまだインストールされていない場合は、セットアップによってインストールされます。  
  
##  <a name="troubleshoot-problems-with-sharepoint-mode-installations"></a><a name="bkmk_tshoot_sharepoint"></a> SharePoint モードのインストールでのトラブルシューティング  
  
-   [Reporting Services 構成マネージャーが起動しない](#bkmk_configmanager_notstart)  
  
-   [SQL Server 2012 SSRS を SharePoint モードでインストールした後、SharePoint サーバーの全体管理に SQL Server Reporting Services サービスが表示されない](#bkmk_no_ssrs_service)  
  
-   [Reporting Services PowerShell コマンドレットが使用できず、コマンドが認識されない](#bkmk_cmdlets_not_recognized)  
  
-   [URL が構成されていないことを示すエラーメッセージが表示される](#bkmk_URL_not_configured)  
  
-   [SharePoint がインストールされているコンピューターが構成されていない場合にセットアップに失敗する](#bkmk_sharepoint_not_confiugred)  
  
-   [SharePoint サーバーの全体管理ページが空白である](#bkmk_central_admin_blank)  
  
-   [新しいレポートビルダーレポートを作成しようとすると、エラーメッセージが表示される](#bkmk_reportbuilder_newreport_error)  
  
-   [PREPAREIMAGE でサポートされていない RS_SHP を示すエラーメッセージが表示される](#bkmk_RS_SHP_notsupported)  
  
###  <a name="reporting-services-configuration-manager-does-not-start"></a><a name="bkmk_configmanager_notstart"></a>Reporting Services Configuration Manager が開始されない  
 **説明:** この問題は [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の仕様です。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は現在、SharePoint サービス アーキテクチャ用に設計されています。 SharePoint モードで [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を構成および管理するために、構成マネージャーを使用する必要はなくなりました。  
  
 **解決方法:** SharePoint モードでレポート サーバーを構成するには、SharePoint サーバーの全体管理を使用します。 詳細については、「 [Reporting Services SharePoint サービス アプリケーションの管理](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)｣を参照してください  
  
###  <a name="you-do-not-see-the-sql-server-reporting-services-service-in-sharepoint-central-administration-after-installing-sql-server-2012-ssrs-in-sharepoint-mode"></a><a name="bkmk_no_ssrs_service"></a>SQL Server 2012 SSRS を SharePoint モードでインストールした後、SharePoint サーバーの全体管理で SQL Server Reporting Services サービスが表示されない  
 **説明:** Sharepoint モードのおよび[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sharepoint 2010 用のアドイン[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]が正常にインストールされた後に、次の2つのメニューに "SQL Server Reporting Services" が表示[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]されない場合は、サービスが登録されていません。  
  
-   SharePoint 2010 サーバーの全体管理-> [アプリケーション管理]-[サーバーのサービスの管理] ページ >  
  
-   SharePoint 2010 サーバーの全体管理-> [アプリケーション管理]-> [サービスアプリケーションの管理]-> [新規] メニュー  
  
 **解決方法:**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Services を登録して起動するには、次の手順を実行します。  
  
1.  SharePoint 2010 サーバーの全体管理を実行するコンピューターで、次を実行します。  
  
    1.  管理者特権を使用して、SharePoint 2010 管理シェルを開きます。 アイコンを右クリックし、[管理者として実行] をクリックします。 シェルから次の 3 つのコマンドレットを実行します。  
  
    2.  ```powershell
        Install-SPRSService  
        ```  
  
    3.  ```powershell
        Install-SPRSServiceProxy  
        ```  
  
    4.  ```powershell
        Get-SPServiceInstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
        ```  
  
2.  サービスの[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [SharePoint 2010 サーバーの全体管理]-> [**アプリケーション管理**]-> [**サーバーのサービスの管理**] ページで、[**開始**] として [状態] が表示されていることを確認します。  
  
###  <a name="reporting-services-powershell-cmdlets-are-not-available-and-commands-are-not-recognized"></a><a name="bkmk_cmdlets_not_recognized"></a> Reporting Services の PowerShell コマンドレットが使用できず、コマンドが認識されない  
 **説明:**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の PowerShell コマンドレットを実行しようとすると、次のようなエラー メッセージが表示されます。  
  
-   用語 'Install-SPRSServiceInstall-SPRSService' は、コマンドレット、関数、スクリプト ファイル、または操作可能なプログラムの名前として **認識されません** 。 名前が正しく記述されていることを確認し、パスが含まれている場合はそのパスが正しいことを確認してから、再試行してください。At line:1 char:39+ Install-SPRSServiceInstall-SPRSService <<<<    + CategoryInfo          : ObjectNotFound: (Install-SPRSServiceInstall-SPRSService:String) [], CommandNotFoundExcep  
  
 **解決方法:** 次のいずれかの手順を実行します。  
  
-   SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインを実行します。 **rssharepoint .msi**。  
  
-   SQL Server のインストール メディアから、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードをインストールします。  
  
 **注:** 解決方法のいずれかを実行したときに **SharePoint 2013 管理シェル** が開いていた場合は、管理シェルをいったん閉じてから開き直します。  
  
 詳細については、「  
  
-   [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
-   [SharePoint 2010 用 Reporting Services SharePoint モードのインストール](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
-   [SharePoint 2013 用 Reporting Services の SharePoint モードのインストール](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
###  <a name="you-see-an-error-message-indicating-the-url-is-not-configured"></a><a name="bkmk_URL_not_configured"></a> URL が構成されていないことを示すエラー メッセージが表示される  
 **説明:** 次のようなエラー メッセージが表示されます。  
  
 この SQL Server Reporting Services (SSRS) の機能はサポートされていません。 サーバーの全体管理を使用して、次の問題を確認し、修正してください: •レポート サーバーの URL が構成されていません。 SSRS の統合ページを使用して設定してください。•SSRS サービス アプリケーション プロキシが構成されていません。 SSRS サービス アプリケーションのページを使用してプロキシを構成してください。•SSRS サービス アプリケーションは、この Web アプリケーションにマップされていません。 SSRS サービス アプリケーションのページを使用して SSRS サービス アプリケーション プロキシをこの Web アプリケーションのアプリケーション プロキシ グループに関連付けてください。  
  
 **解決方法:** このエラー メッセージに、この問題を修正するための 3 つの推奨手順が含まれています。 "レポートサーバーの URL が構成されていません" というメッセージに記載されている最初の提案 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]よりも前のレポート サーバー バージョンとの統合に関連します。 以前のレポート サーバー バージョンの SharePoint 構成は、 **SQL Server Reporting Services (2008 および 2008 R2)** を使用して **[アプリケーションの全体設定]** ページで完了されます。  
  
 **その他の情報:**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスへの接続が必要な [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 機能のいずれかを使用しようとすると、このエラー メッセージが表示されます。 たとえば、次のようなアニメーションや効果を作成できます。  
  
-   SQL Server レポート ビルダーを SharePoint ドキュメント ライブラリから開いている。  
  
-   サブスクリプションを管理する。  
  
-   サービス アプリケーションを管理する。  
  
###  <a name="setup-fails-on-a-computer-with-sharepoint-installed-but-it-is-not-configured"></a><a name="bkmk_sharepoint_not_confiugred"></a> SharePoint がインストールされているコンピューターが構成されていない場合にセットアップに失敗する  
 **説明:** SharePoint がインストールされているものの構成されていないコンピューターに Reporting Services SharePoint モードをインストールするよう選択した場合、次のようなメッセージが表示され、セットアップが停止します。  
  
 SQL Server セットアップは動作を停止しました  
  
 **解決方法:** SharePoint を構成し、その後 SQL Server のインストールを実行します。  
  
 **追加情報:** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を既存の SharePoint 環境にインストールするとき、セットアップで [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint サービスのインストールおよび開始が試行されます。 SharePoint が構成されていないと、このサービスのインストールは失敗し、セットアップがエラーを返します。  
  
###  <a name="sharepoint-central-administration-page-is-blank"></a><a name="bkmk_central_admin_blank"></a>SharePoint サーバーの全体管理ページが空白である  
 **説明:** SharePoint 2010 をインストール エラーなく正常にインストールできた場合でも、 [サーバーの全体管理] を表示すると空白のページしか表示されないことがあります。  
  
 **解決方法:** この問題は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に固有のものではなく、SharePoint 環境全体における権限の構成に関連するものです。 考えられる解決方法は次のとおりです。  
  
-   開発環境に関する SharePoint トピックを参照します。 [Windows Vista、Windows 7、および Windows Server 2008 で SharePoint 2010 の開発環境をセットアップする](https://msdn.microsoft.com/library/ee554869\(office.14\).aspx)  
  
-   フォーラムの投稿「 [Windows 7 へのインストール後、[サーバーの全体管理] が空白ページを返す](https://social.technet.microsoft.com/Forums/en/sharepoint2010setup/thread/a422a3c8-39f6-4b9e-988a-4c4d1e745694)」を参照します。  
  
-   SharePoint サービス (SharePoint 2010 サーバーの全体管理サービスなど) に使用しているサービス アカウントに、ローカル オペレーティング システムの管理者特権を付与します。  
  
###  <a name="you-see-an-error-message-when-you-try-to-create-a-new-report-builder-report"></a><a name="bkmk_reportbuilder_newreport_error"></a> 新しいレポート ビルダー レポートを作成しようとすると、エラー メッセージが表示される  
 **説明:** ドキュメント ライブラリ内でレポート ビルダー レポートを作成しようとすると、次のようなエラー メッセージが表示されます。  
  
 SQL Server Reporting Services サービス アプリケーションが存在しないか、またはレポート サーバーの URL がサーバーの全体管理で構成されていないため、この機能はサポートされません。  
  
 **解決方法:**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションが存在し、正しく構成されていることを確認します。 詳細については、「 [sharepoint 2010 用 Reporting Services Sharepoint モードのインストール](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)」の「Reporting Services サービスアプリケーションの作成」セクションを参照してください。  
  
###  <a name="you-see-an-error-message-that-rs_shp-is-not-supported-with-prepareimage"></a><a name="bkmk_RS_SHP_notsupported"></a> RS_SHP は PREPAREIMAGE でサポートされないことを示すエラー メッセージが表示される  
 **説明:**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に対して PREPAREIMAGE を実行しようとすると、次のようなエラー メッセージが表示されます。  
  
 指定された機能 'RS_SHP' は、SysPrep をサポートしていないため、PREPAREIMAGE アクションの実行中にはサポートされません。 SysPrep と互換性のない機能を削除し、セットアップを再実行してください。  
  
 **解決方法:** 解決方法はありません。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SYSPREP (PREPAREIMAGE) をサポートしていません。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モードでは SYSPREP をサポートしています。  
  
##  <a name="troubleshoot-problems-with-the-native-mode-installations"></a><a name="bkmk_tshoot_native"></a> ネイティブ モードのインストールでのトラブルシューティング  
  
###  <a name="performance-counters-are-not-visible-after-upgrading-to-windows-vista-or-windows-server-2008"></a><a name="PerfCounters"></a> Windows Vista または Windows Server 2008 にアップグレードするとパフォーマンス カウンターが表示されない  
 [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] を実行するコンピューターでオペレーティング システムを [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] または [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]にアップグレードした場合、アップグレード後に [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のパフォーマンス カウンターが設定されなくなります。  
  
#### <a name="to-reinstate-reporting-services-performance-counters"></a>Reporting Services のパフォーマンス カウンターを再設定するには  
  
1.  次のレジストリ キーを削除します。  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service**  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service**  
  
2.  コマンド ウィンドウを開き、コマンド プロンプトで次のコマンドを入力します。  
  
    -   *.net 2.0 Framework ディレクトリ* **> \< \installutil.exe** *レポートサーバーの Bin ディレクトリ* **>** を**実行\< **します。  
  
        > [!NOTE]  
        >  \< *.Net 2.0 Framework ディレクトリ*> を .NET Framework 2.0 ファイルの物理パスに置き換え、 \<*レポートサーバーの bin ディレクトリ*> をレポートサーバーの bin ファイルの物理パスに置き換えます。  
  
3.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスを再開します。  
  
 手順が正しく行われたことを確認するには、Web ブラウザーを開き、レポート マネージャー URL またはレポート サーバー URL に移動します。 その後、パフォーマンス モニターを開き、カウンターが機能していることを確認します。  
  
#### <a name="to-re-add-the-performance-registry-keys-by-using-registry-editor"></a>レジストリ エディターを使用して Performance のレジストリ キーをもう一度追加するには  
  
1.  レジストリ エディターを開きます。  
  
    1.  **[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]** をクリックします。  
  
    2.  [ファイル**の選択] ダイアログボックス**の [**名前**] ボックス`regedit`に、「」と入力します。  
  
2.  レジストリ エディターで、次のレジストリ キーを選択します。 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance`  
  
3.  **[Performance]** ノードを右クリックし、 **[新規]** をポイントして **[複数行文字列値]** をクリックします。  
  
4.  「 `Counter Names` 」と入力し、enter キーを押します。  
  
5.  同じ手順を繰り返して、このノードに `Counter Types` レジストリ キーを追加します。  
  
6.  次のレジストリ キーに移動します。 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance`  
  
7.  **[Performance]** ノードを右クリックし、 **[新規]** をポイントして **[複数行文字列値]** をクリックします。  
  
8.  「 `Counter Names` 」と入力し、enter キーを押します。  
  
9. 同じ手順を繰り返して、このノードに `Counter Types` レジストリ キーを追加します。  
  
 64 ビット インスタンスを修復するか、レジストリ キーをもう一度手動で追加したら、パフォーマンス モニターを使用して、監視する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] パフォーマンス オブジェクトを構成できます。  
  
###  <a name="reportserverexternalurl-and-passthroughcookies-configuration-properties-are-not-configured-after-an-upgrade-from-sql-server-2005"></a><a name="ConfigPropsMissing"></a> SQL Server 2005 からアップグレードすると構成プロパティの ReportServerExternalURL と PassThroughCookies が構成されない  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] から [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] にアップグレードする場合は、構成プロパティの `ReportServerExternalURL` と `PassThroughCookies` がアップグレード プロセスで構成されません。 `ReportServerExternalURL` はオプションのプロパティです。SharePoint 2.0 Web パーツを使用していて、ユーザーがレポートを取得して新しいブラウザー ウィンドウで開くことができるようにする場合にのみ設定する必要があります。 の詳細につい`ReportServerExternalURL`ては、「 [Configuration Files の url &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md)」を参照してください。 `PassThroughCookies` はカスタム認証を使用する場合にのみ必要です。 の詳細につい`PassThroughCookies`ては、「[カスタム認証クッキーを渡すようにレポートマネージャーを構成する](../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)」を参照してください。  
  
> [!NOTE]  
>  カスタム認証を使用する場合は、アップグレードを実行する代わりに現在のインストールを移行することをお勧めします。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の移行については、「[Reporting Services のインストールの移行 &#40;ネイティブ モード&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md)」を参照してください。  
  
 既定では、これらのプロパティは [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] の構成には存在しません。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] でこれらのプロパティを構成していて、その機能が引き続き必要な場合は、アップグレード プロセスの完了後にこれらを手動で **RSReportServer.config** ファイルに追加する必要があります。 詳細については、「 [Modify a Reporting Services Configuration File &#40;RSreportserver. .config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)」を参照してください。  
  
###  <a name="installation-fails-for-a-default-instance-of-sql-server-2005-reporting-services-on-a-computer-that-runs-sql-server-2012reporting-services"></a><a name="Default2005InstallBreaks2008"></a>SQL Server 2012Reporting Services を実行しているコンピューター上の SQL Server 2005 Reporting Services の既定のインスタンスのインストールが失敗する  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]インスタンスを既に実行しているコンピューターにの既定のインスタンスをインストールしようとすると、次のエラーメッセージが表示されてインスタンスのインストールが失敗します。 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]  
  
 "このコンピューターには、同じ名前のインスタンスが既にインストールされています。 SQL Server のセットアップを続行するには、一意なインスタンス名を指定してください。"  
  
 この問題は、 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] インスタンスが既定のインスタンスであっても名前付きインスタンスであっても、その名前の [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] インスタンスが既にコンピューターに存在していてもいなくても、発生します。  
  
 この問題を回避するには次の方法があります。  
  
-   をコンピューター上の[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]既定のインスタンスとして実行する必要がある場合[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]は、インスタンス[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]をインスタンスの前にインストールする必要があります。  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]インスタンスを既定のインスタンスにする必要がない場合は、インスタンスをインストール[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]した後に、インスタンスを名前付きインスタンスとしてインストールできます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
###  <a name="401-unauthorized-error-when-using-windows-authentication-after-an-upgrade-from-sql-server-2005-to-sql-server-2012"></a><a name="WindowsAuthBreaksAfterUpgrade"></a>401-SQL Server 2005 から SQL Server 2012 へのアップグレード後に Windows 認証を使用すると、承認されていないエラーが発生する  
 から[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]に[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]アップグレードし、レポートサーバーサービスアカウントにビルトインアカウントを使用して NTLM 認証を使用すると、レポートサーバーにアクセスするとき、またはアップグレード後にレポートマネージャーするときに、401-未承認のエラーが発生することがあります。  
  
 この問題が発生するのは、 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] で Windows 認証の既定の構成が変更されているためです。 レポート サーバー サービス アカウントが NetworkService または LocalSystem である場合はネゴシエートが構成され、 レポート サーバー サービス アカウントがこれらのビルトイン アカウントではない場合は NTLM が構成されます。 アップグレード後にこの問題を修正するには、RSReportServer.config ファイルを編集して `AuthenticationType` を `RSWindowsNTLM` に設定します。 詳細については、「 [レポート サーバーで Windows 認証を構成する](../security/configure-windows-authentication-on-the-report-server.md)」を参照してください。  
  
###  <a name="uninstalling-32-bit-instance-of-sql-server-2012-reporting-services-in-side-by-side-deployment-with-a-64-bit-instance-breaks-the-64-bit-instance"></a><a name="Uninstall32BitBreaks64Bit"></a>64ビットインスタンスとのサイドバイサイド配置で SQL Server 2012 Reporting Services の32ビットインスタンスをアンインストールすると、64ビットインスタンスが破損する  
 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] の 32 ビット インスタンスと 64 ビット インスタンスをサイド バイ サイドでコンピューターにインストールしている場合に 32 ビット インスタンスをアンインストールすると、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の 4 つのレジストリ キーが削除されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の 64 ビット インスタンスが破損します。 32 ビット インスタンスをアンインストールすると削除されるのは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の以下のレジストリ キーです。  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance:Counter Types` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service\Performance:Counter Types`  
  
 この問題を修正するには、64 ビット インスタンスを修復します。 修復を使用することをお勧めしますが、レジストリ エディターを使用してレジストリ キーをもう一度手動で追加することもできます。  
  
> [!CAUTION]  
>  レジストリを誤って編集すると、システムに重大な障害が発生する場合があります。 レジストリを変更する前に、コンピューター上の重要なデータのバックアップを作成する必要があります。  
  
##  <a name="additional-resources"></a><a name="bkmk_additional"></a> その他のリソース  
 以下に示すのは、問題解決時に役立つ可能性のある追加資料です。  
  
-   TechNet Wiki: トラブルシューティング トピック [SharePoint 統合モードでの SQL Server Reporting Services (SSRS) のトラブルシューティング](https://social.technet.microsoft.com/wiki/contents/articles/troubleshoot-sql-server-reporting-services-ssrs-in-sharepoint-integrated-mode.aspx)  
  
-   [フォーラム: SQL Server Reporting Services](https://social.msdn.microsoft.com/Forums/sqlreportingservices/threads)  
  
