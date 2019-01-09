---
title: Power Pivot モードで Analysis Services のインストール |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e3e973c30ea178a544b9da3501d88f43cf9b1ddb
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52527751"
---
# <a name="install-analysis-services-in-power-pivot-mode"></a>Power Pivot モードでの Analysis Services のインストール
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  このトピックでは、SharePoint 配置の [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] モードで [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サーバーのシングル サーバー インストールを行う手順について説明します。 手順には、SQL Server インストール ウィザードの実行と、SharePoint サーバーの全体管理を使用する構成タスクが含まれます。  
  
##  <a name="bkmk_background"></a> 背景情報  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint は、SharePoint 2016 (SharePoint 2013) ファームでの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] データ アクセスを提供する中間層のバックエンド サービスです。  
  
-   **バックエンド サービス:** 使用する場合[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]が必要、分析データを含むブックを作成する Excel [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint server 環境では、そのデータにアクセスします。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップは、SharePoint Server がインストールされているコンピューターで実行することも、SharePoint ソフトウェアがインストールされていない別のコンピューターで実行することもできます。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] には、SharePoint との依存関係はありません。  
  
     **注:** このトピックでは、のインストールを説明します、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]サーバーおよびバックエンド サービスです。  
  
-   **中間層:** 機能強化、[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]などの SharePoint エクスペリエンス[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]ギャラリー、定期データ更新、管理ダッシュ ボード、データ プロバイダー。 中間層のインストールと構成の詳細については、以下を参照してください。  
  
    -   [Power Pivot for SharePoint アドインのインストールまたはアンインストール (SharePoint 2016)](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2016.md)  
  
    -   [Power Pivot for SharePoint アドインのインストールまたはアンインストール &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)  
  
    -   [Power Pivot の構成とソリューションの配置 &#40;SharePoint 2016&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2016.md)  
  
    -   [Power Pivot の構成とソリューションの配置 &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)  
  
##  <a name="bkmk_prereq"></a> 前提条件  
  
1.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップを実行するには、ローカル管理者である必要があります。  
  
2.  [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint には SharePoint Server Enterprise Edition が必要です。 評価版の Enterprise Edition を使用することもできます。  
  
3.  コンピューターは、Office Online Server (SharePoint 2016) または Excel Services (SharePoint 2013) と同じ Active Directory フォレスト内のドメインに参加する必要があります。  
  
4.  [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] インスタンスの名前を使用できる必要があります。 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]名前付きインスタンスが既に存在するコンピューターに、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] モードの Analysis Services をインストールすることはできません。  
  
     **注:** インスタンス名は、POWERPIVOT である必要があります。  
  
5.  「 [SharePoint モードの Analysis Services サーバーのハードウェアとソフトウェアの要件](http://msdn.microsoft.com/library/fb86ca0a-518c-4c61-ae78-7680c57fae1f)」を参照してください。  
  
6.  「 [SQL Server 2016 Release Notes](../../../sql-server/sql-server-2016-release-notes.md)」で、リリース ノートを確認します。  
  
###  <a name="bkmk_sqleditions"></a> SQL Server エディションの要件  
 ビジネス インテリジェンス機能は、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のすべてのエディションで利用できるわけではありません。 詳細については、次を参照してください。 [SQL Server 2016 の各エディションでサポートされる Analysis Services 機能](../../../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)と[エディションと SQL Server 2016 のコンポーネントの](../../../sql-server/editions-and-components-of-sql-server-2016.md)します。  
  
##  <a name="InstallSQL"></a> 手順 1:Power Pivot for SharePoint をインストールします。  
 この手順では、SQL Server セットアップを実行して、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] モードの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サーバーをインストールします。 後の手順で、このサーバーをブックのデータ モデルで使用するように Excel Services を構成します。  
  
1.  SQL Server インストール ウィザード (Setup.exe) を実行します。  
  
2.  左側のナビゲーション ウィンドウで、 **[インストール]** を選択します。  
  
3.  **[SQL Server の新規スタンドアロン インストールを実行するか、既存のインストールに機能を追加します]** を選択します。  
  
4.  **[プロダクト キー]** ページが表示されたら、Evaluation Edition を指定するか、Enterprise Edition のライセンス コピーのプロダクト キーを入力します。 **[次へ]** を選択します。 エディションの詳細については、「 [Editions and Components of SQL Server 2016](../../../sql-server/editions-and-components-of-sql-server-2016.md)」を参照してください。  
  
5.  マイクロソフト ソフトウェア ライセンス条項を確認して同意し、 **[次へ]** を選択します。  
  
6.  **[グローバル ルール]** ページが表示されたら、セットアップ ウィザードに表示されるすべてのルールの情報を確認します。  
  
7.  **[Microsoft Update]** ページで、Microsoft Update を使用して更新プログラムを確認することをお勧めします。確認したら、 **[次へ]** を選択します。  
  
8.  **[セットアップ ファイルのインストール]** ページが数分間実行されます。 ルールの警告または失敗したルールを確認し、 **[次へ]** を選択します。  
  
9. 別の **[セットアップ サポート ルール]** が表示されたら、警告を確認し、 **[次へ]** を選択します。  
  
     **注:** Windows ファイアウォールが有効になっているため、ポートを開いてリモート アクセスを有効にするよう求める警告が表示されます。  
  
10. **[セットアップ ロール]** ページで、 **[SQL Server 機能のインストール]** を選択します。  
  
     **[次へ]** を選択します。  
  
11. [機能の選択] ページで、 **[Analysis Services]** を選択します。 このオプションを使用すると、3 つの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] モードのいずれかをインストールできます。 モードは後の手順で選択します。 **[次へ]** を選択します。  
  
12. **[インスタンスの構成]** ページで、 **[名前付きインスタンス]** を選択し、インスタンス名に **[POWERPIVOT]** を入力して、 **[次へ]** をクリックします。  
  
     ![SQL のセットアップ - インスタンスの構成のランディング ページ](../../../analysis-services/instances/install-windows/media/sql2016-pp-instance-config-landing-page.png "SQL セットアップ - ランディング ページ インスタンスの構成")  
  
13. **[サーバー構成]** のページで、すべてのサービスの **[スタートアップの種類]** を [自動] に設定します。 **SQL Server Analysis Services**に必要なドメイン アカウントとパスワードを指定します。次の図の **(1)** です。  
  
    -   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]では、 **ドメイン ユーザー** アカウントまたは **NetworkService** アカウントを使用できます。 LocalSystem アカウントまたは LocalService アカウントは使用しないでください。  
  
    -   SQL Server データベース エンジンと SQL Server エージェントを追加した場合は、サービスがドメイン ユーザー アカウントまたは既定の仮想アカウントで実行されるように構成できます。  
  
    -   サービス アカウントには自分のドメイン ユーザー アカウントを指定しないでください。 このようなアカウントを使用すると、ネットワークのリソースに対して持っている権限と同じ権限をサーバーに付与することになります。 悪意のあるユーザーがサーバーに侵入した場合、そのユーザーは管理者のドメイン資格情報を使用してログオンします。 そのユーザーは、管理者と同じデータやアプリケーションをダウンロードしたり使用したりする権限を持ちます。  
  
     **[次へ]** を選択します。  
  
     ![SQL のセットアップ - サーバーの構成のランディング ページ](../../../analysis-services/instances/install-windows/media/sql2016-pp-server-config-landing-page.png "SQL セットアップ - サーバーの構成のランディング ページ")  
  
14. [!INCLUDE[ssDE](../../../includes/ssde-md.md)]をインストールする場合は、 **[データベース エンジンの構成]** ページが表示されます。 [ [!INCLUDE[ssDE](../../../includes/ssde-md.md)] の構成] で、 **[現在のユーザーの追加]** を選択して、データベース エンジン インスタンスに対する管理者権限をユーザー アカウントに付与します。  
  
     **[次へ]** を選択します。  
  
15.  **[Analysis Services の構成]** ページの **[サーバー モード]** で、 **[PowerPivot モード]** を選択します。  
  
     ![SQL のセットアップ - Analysis Services の構成がランディング ページ](../../../analysis-services/instances/install-windows/media/sql2016-pp-as-config-landing-page.png "SQL セットアップ - Analysis Services の構成がランディング ページ")  
  
16. **[Analysis Services の構成]** ページで、 **[現在のユーザーの追加]** を選択して、ユーザー アカウントに管理権限を付与します。 セットアップの完了後にサーバーを構成するには、管理権限が必要になります。  
  
    -   同じページで、同じく管理権限が必要なユーザーの Windows ユーザー アカウントを追加します。 たとえば、データベース接続の問題のトラブルシューティングを行うために、 [!INCLUDE[ssGeminiSrv](../../../includes/ssgeminisrv-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] インスタンスに接続するユーザーには、システム管理者権限が必要です。 サーバーのトラブルシューティングや管理を担当する可能性があるユーザーのユーザー アカウントをここで追加しておきます。  
  
    -   > [!NOTE]  
        >  Analysis Services サーバー インスタンスにアクセスする必要があるすべてのサービス アプリケーションに、Analysis Services 管理権限が必要です。 たとえば、Excel Services、Power View、Performance Point Services のサービス アカウントを追加します。 また、サーバーの全体管理をホストする Web アプリケーションの ID として使用される SharePoint ファーム アカウントも追加します。  
  
     **[次へ]** を選択します。  
  
17. **[エラー レポート]** ページで、 **[次へ]** を選択します。  
  
18. **[インストールの準備完了]** ページで、 **[インストール]** を選択します。  
  
19. **[コンピューターの再起動が必要です]** ダイアログ ボックスが表示されたら、 **[OK]** を選択します。  
  
20. インストールが完了したら、 **[閉じる]** を選択します。  
  
21. コンピューターを再起動します。  
  
22. 環境内にファイアウォールがある場合は、SQL Server オンライン ブックの「 [Configure the Windows Firewall to Allow Analysis Services Access](../../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)」を確認します。  
  
### <a name="verify-the-sql-server-installation"></a>SQL Server のインストールの確認  
 Analysis Services サービスが実行されているかどうかを確認します。  
  
1.  Windows の **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** を選択して、 **[Microsoft SQL Server 2016]** を選択します。  
  
2.  **[SQL Server Management Studio]** を選択します。  
  
3.  Analysis Services インスタンス (たとえば、**[サーバー名]\POWERPIVOT**) に接続します。 インスタンスに接続できたら、サービスが実行されていることがわかります。  
  
##  <a name="bkmk_config"></a> 手順 2:基本的な Analysis Services の SharePoint 統合を構成する  
 SharePoint ドキュメント ライブラリ内で Excel の高度なデータ モデルを操作できるようにするには、次の手順を実行して構成を変更する必要があります。 これらの手順は、SharePoint と SQL Server Analysis Services をインストールしてから実行します。  
  
### <a name="sharepoint-2016"></a>SharePoint 2016  
 Excel Services は SharePoint 2016 から削除され、代わりに Office Online Server を使用して Excel がホストされるようになりました。  
  
#### <a name="grant-office-online-server-machine-account-administration-rights-on-analysis-services"></a>Office Online Server マシン アカウントへの Analysis Services に対する管理権限の付与  
 Analysis Services のインストール時に、Analysis Services 管理者として Office Online Server マシン アカウントを追加した場合は、このセクションの手順を実行する必要はありません。  
  
1.  Analysis Services サーバーで、SQL Server Management Studio を起動し、Analysis Services インスタンス (たとえば、`[MyServer]\POWERPIVOT`) に接続します。  
  
2.  オブジェクト エクスプローラーで、インスタンス名を右クリックし、 **[プロパティ]** を選択します。  
  
     ![SSAS サーバーのプロパティを表示](../../../analysis-services/instances/install-windows/media/as-ssms-proeprties.gif "SSAS サーバーのプロパティの表示")  
  
3.  左ペインで、 **[セキュリティ]** を選択します。 Office Online Server がインストールされているマシン アカウントを追加します。  
  
     ![SSAS サーバーのセキュリティ設定](../../../analysis-services/instances/install-windows/media/as-ssms-security.gif "SSAS サーバーのセキュリティ設定")  
  
#### <a name="register-analysis-services-server-with-office-online-server"></a>Office Online Server への Analysis Services サーバーの登録  
 Office Online Server で、次の手順を実行します。  
  
-   管理者として PowerShell コマンド ウィンドウを開きます。  
  
-   `OfficeWebApps` PowerShell モジュールを読み込みます。  
  
     `Import-Module OfficeWebApps`  
  
-   Analysis Services サーバー (たとえば、 `[MyServer]\POWERPIVOT`) を追加します。  
  
     `New-OfficeWebAppsExcelBIServer -ServerId [MyServer]\POWERPIVOT]`  
  
### <a name="sharepoint-2013"></a>SharePoint 2013  
  
#### <a name="grant-excel-services-server-administration-rights-on-analysis-services"></a>Excel Services への Analysis Services に対するサーバー管理権限の付与  
 Analysis Services のインストール時に、Analysis Services 管理者として Excel Services アプリケーションのサービス アカウントを追加した場合は、このセクションの手順を実行する必要はありません。  
  
1.  Analysis Services サーバーで、SQL Server Management Studio を起動し、Analysis Services インスタンス (たとえば、`[MyServer]\POWERPIVOT`) に接続します。  
  
2.  オブジェクト エクスプローラーで、インスタンス名を右クリックし、 **[プロパティ]** を選択します。  
  
     ![SSAS サーバーのプロパティを表示](../../../analysis-services/instances/install-windows/media/as-ssms-proeprties.gif "SSAS サーバーのプロパティの表示")  
  
3.  左ペインで、 **[セキュリティ]** を選択します。 手順 1. で Excel Services アプリケーション用に構成したドメイン ログインを追加します。  
  
     ![SSAS サーバーのセキュリティ設定](../../../analysis-services/instances/install-windows/media/as-ssms-security.gif "SSAS サーバーのセキュリティ設定")  
  
#### <a name="configure-excel-services-for-analysis-services-integration"></a>Analysis Services 統合のための Excel Services の構成  
  
1.  SharePoint サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  サービス アプリケーションの名前をクリックします。既定の名前は **"Excel Services アプリケーション"** です。  
  
3.  **[Excel Services アプリケーションの管理]** ページで、 **[データ モデルの設定]** をクリックします。  
  
4.  **[サーバーの追加]** をクリックします。  
  
5.  **[サーバー名]** に、Analysis Services サーバー名と [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] インスタンス名を入力します。 たとえば、 `MyServer\POWERPIVOT`があります。 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] インスタンス名は必須です。  
  
     説明を入力します。  
  
6.  **[OK]** をクリックします。  
  
7.  変更は数分で有効になりますが、 **Excel Calculation Services** サービスを **停止** および **開始**することもできます。 変換先  
  
     別の方法として、管理者特権でコマンド プロンプトを開き、「 `iisreset /noforce`」と入力します。  
  
     ULS ログのエントリを確認することで、サーバーが Excel Services によって認識されているかどうかを確認できます。 実際のエントリの例を次に示します。  
  
    ```  
    Excel Services Application            Data Model        27           Medium                Check Administrator Access ([ServerName]\POWERPIVOT): Pass.        f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Server Version ([ServerName]\POWERPIVOT): Pass (11.0.2809.24 >= 11.0.2800.0).         f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Deployment Mode ([ServerName]\POWERPIVOT): Pass.            f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
  
    ```  
  
##  <a name="bkmk_verify"></a> 手順 3:統合を確認する  
 ここでは、Analysis Services 統合を確認するために、新しいブックを作成し、アップロードする手順を示します。 この手順を実行するには、SQL Server データベースが必要です。  
  
1.  **注:** スライサーやフィルターが含まれた高度なブックが既にある場合は、そのブックを SharePoint ドキュメント ライブラリにアップロードし、[ドキュメント ライブラリ] ビューからスライサーとフィルターを操作できるかどうかを確認します。  
  
2.  Excel で新しいブックを開きます。  
  
3.  [データ] タブの **[外部データの取り込み]** で、 **[その他のデータ ソース]** を選択します。  
  
4.  **[SQL Server]** を選択します。  
  
5.  **データ接続ウィザード**で、使用するデータベースがある SQL Server インスタンスの名前を入力します。  
  
6.  [ログオン資格情報] で、 **[Windows 認証を使用する]** が選択されていることを確認し、 **[次へ]** をクリックします。  
  
7.  使用するデータベースを選択します。  
  
8.  **[指定したテーブルに接続]** チェック ボックスがオンになっていることを確認します。  
  
9. **[複数のテーブルの選択を有効にし、テーブルを Excel データ モデルに追加する]** チェック ボックスをオンにします。  
  
10. インポートするテーブルを選択します。  
  
11. **[選択したテーブル間のリレーションシップをインポートする]** チェック ボックスをオンにし、 **[次へ]** を選択します。 リレーショナル データベースから複数のテーブルをインポートすると、既に関連付けられているテーブルを使用できます。 リレーションシップを手動で作成する必要がないため、手間を省くことができます。  
  
12. ウィザードの **[データ接続ファイルを保存して終了]** ページで、接続の名前を入力し、 **[完了]** を選択します。  
  
13. **[データのインポート]** ダイアログ ボックスが表示されます。 **[ピボットテーブル レポート]** を選択し、 **[OK]** を選択します。  
  
14. ブックにピボットテーブル フィールド リストが表示されます。   
    フィールド リストで、 **[すべて]** タブを選択します。  
  
15. フィールド リストの [行]、[列]、[値] の各領域にフィールドを追加します。  
  
16. ピボットテーブルにスライサーまたはフィルターを追加します。 **この手順は省略しないでください**。 スライサーまたはフィルターは、Analysis Services のインストールの確認に役立つ要素です。  
  
17. SharePoint ファーム内のドキュメント ライブラリにブックを保存します。 また、ブックをファイル共有に保存し、SharePoint ドキュメント ライブラリにアップロードすることもできます。  
  
18. ブックの名前を選択して Excel Online で表示し、スライサーをクリックするか、以前に追加したフィルターを変更します。 データ更新が行われたら、Analysis Services がインストールされ、Excel で利用できることがわかります。 ブックを Excel で開いた場合は、Analysis Services サーバーではなく、キャッシュ コピーが使用されます。  
  
##  <a name="bkmk_firewall"></a> Analysis Services のアクセスを許可するための Windows ファイアウォールの構成  
 「 [Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) 」では、Analysis Services または [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint には SharePoint Server Enterprise Edition が必要です。 このトピックに示された手順に従って、ポートとファイアウォールを構成できます。 実際に Analysis Services サーバーへのアクセスを許可するためには、これらの手順を組み合わせて実行する必要があります。  
  
##  <a name="bkmk_upgrade_workbook"></a> ブックのアップグレードと定期データ更新  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] の以前のバージョンで作成したブックのアップグレードに必要な手順は、そのブックを作成した [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] のバージョンによって異なります。 詳細については、「 [ブックのアップグレードと定期データ更新 &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)」を参照してください。  
  
##  <a name="bkmk_multiple_servers"></a> -シングル サーバー インストールではない Power Pivot for Microsoft SharePoint  
 **Web フロント エンド (WFE)** または**中間層:**:使用する、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]大規模な SharePoint ファームで追加インストールして、SharePoint モードのサーバー[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]インストーラー パッケージを実行して、ファームに機能**spPowerPivot16.msi (SharePoint 2016)、または spPowerPivot.msi (SharePoint2013 年)** 各 SharePoint サーバー上でします。 spPowerPivot16.msi (spPowerPivot.msi) では、必要なデータ プロバイダーと [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2016 (2013) の構成ツールをインストールします。  
  
 中間層のインストールと構成の詳細については、以下を参照してください。  
  
-   [Power Pivot for SharePoint アドインのインストールまたはアンインストール &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)  
  
-   [Power Pivot for SharePoint アドインのインストールまたはアンインストール &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)  
  
-   .msi をダウンロードするには、「 [Microsoft SQL Server 2016 Power Pivot for Microsoft SharePoint 2016](http://go.microsoft.com/fwlink/?LinkID=324854)」を参照してください。  
  
-   [Power Pivot の構成とソリューションの配置 &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)  
  
 **冗長性とサーバー負荷:** インストール、1 秒以上[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]内のサーバー[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]モードでの冗長性が実現、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]サーバーの機能。 サーバーを追加すると、サーバー間の負荷分散も行われます。 詳細については、以下を参照してください。  
  
-   [Excel Services (SharePoint 2013) でデータ モデルを処理するための Analysis Services を構成する](http://technet.microsoft.com/library/jj614437(v=office.15))します。  
  
-   [Excel Services データ モデルの設定 (SharePoint 2013) を管理](http://technet.microsoft.com/library/jj219780(v=office.15))します。  
  
 ![SharePoint の設定](../../../analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 設定")[フィードバックや連絡先の情報を SQL Server に関するフィードバックを送信](https://feedback.azure.com/forums/908035-sql-server)します。  
  
## <a name="see-also"></a>参照  
 [SharePoint 2013 への Power Pivot の移行](../../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)   
 [Power Pivot for SharePoint アドインのインストールまたはアンインストール &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)   
 [ブックのアップグレードと定期データ更新 &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
