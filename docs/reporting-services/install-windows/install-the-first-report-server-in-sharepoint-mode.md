---
title: "SharePoint モードでの最初のレポート サーバーのインストール |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 10/05/2017
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
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 140c0f085919b504ab2263abbc944b80897751fe
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="install-the-first-report-server-in-sharepoint-mode"></a>SharePoint モードでの最初のレポート サーバーをインストールします。

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

  このトピックの手順では、Reporting Services の SharePoint モードでのシングル サーバー インストールについて説明します。 手順には、SQL Server インストール ウィザードの実行と、SharePoint サーバーの全体管理を使用する構成タスクが含まれます。 トピックは、Reporting Services サービス アプリケーションを作成する例については、既存のインストールの更新について個々 の手順も使用できます。  
  
> [!NOTE]
> SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。
  
 既存のファームに複数の Reporting Services サーバーを追加する方法については、次を参照してください。  
  
-   [ファームへのレポート サーバーの追加 &#40;SSRS スケールアウト&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
-   [ファームへの Reporting Services Web フロントエンドの追加](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 シングル サーバー インストールは、開発およびテストのシナリオには便利ですが、運用環境にはお勧めしません。  
  
##  <a name="bkmk_singleserver"></a>シングル サーバー配置の例

 シングル サーバー インストールは、開発およびテストのシナリオには便利ですが、シングル サーバーは運用環境にはお勧めしません。 シングル サーバー環境は、同じコンピューターにインストールされている SharePoint と Reporting Services のコンポーネントが含まれる 1 台のコンピューターを指します。 トピックでは、複数の Reporting Services サーバーとスケール アウトは説明しません。  
  
 次の図は、単一のサーバー Reporting Services の展開の一部であるコンポーネントを示しています。  
 
 > [!NOTE]
 > SharePoint 2016 については、Excel Services が Office Online Server に移動したため、シングル サーバー配置では使用できません。 Office Online Server は、別のサーバーに配置する必要があります。 詳細については、「 [Office Online Server overview (Office Online Server の概要)](https://technet.microsoft.com/library/jj219437\(v=office.16\).aspx) 」と「 [Configure Excel Online administrative settings (Excel Online の管理設定の構成)](https://technet.microsoft.com/library/jj219698\(v=office.16\).aspx)」をご覧ください。
  
|||  
|-|-|  
|**(1)**|SharePoint サービス: SQL Server をインストールすると、インストールされます。 1 つまたは複数の Reporting Services サービス アプリケーションを作成することができます。|  
|**(2)**|Reporting Services アドインを SharePoint 製品用ユーザー インターフェイス コンポーネント提供、SharePoint サーバーにします。|  
|**(3)**|Power View と [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]で使用される Excel サービス アプリケーション。 これは、SharePoint 2016 のシングル サーバー配置では使用できません。 [Office Online Server](https://technet.microsoft.com/library/jj219437\(v=office.16\).aspx) が必要です。|  
|**(4)**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションの作成など) をこのトピックで確認することもできます。|  
  
 ![SSRS SharePoint モードのシングル サーバー配置](../../reporting-services/install-windows/media/rs-sharepoint-1server-deployment.gif "SSRS SharePoint モードのシングル サーバー配置")  
  
> [!TIP]  
>  より複雑な配置例については、「 [Deployment Topologies for SQL Server BI Features in SharePoint (SharePoint での SQL Server BI 機能の配置トポロジ)](http://msdn.microsoft.com/library/39f76bc7-94e6-4dbc-bfa5-d56f4430bb26)」を参照してください。  
  
##  <a name="bkmk_setupaccounts"></a> セットアップ アカウント

 このセクションでは、アカウントと手順については、プライマリ展開 Reporting Services の SharePoint モードで使用される権限について説明します。  
  
 **インストールと Reporting Services サービスを登録します。**  
  
-   インストール中に ('セットアップ' アカウントと呼ばれる) Reporting Services の SharePoint モードでの現在のアカウントは、ローカル コンピューターで管理者権限を持っている必要があります。 SharePoint がインストールされているし、'セットアップ' アカウントが SharePoint ファーム管理者グループのメンバーでも後に、Reporting Services をインストールする場合は、Reporting Services のインストールは、Reporting Services サービスを登録します。 SharePoint がインストールされているか、'セットアップ' アカウントがファーム管理者グループのメンバーではない前に、Reporting Services をインストールする場合は、手動でサービスを登録します。 「 [手順 2。 Reporting Services SharePoint サービスの登録と開始](#bkmk_install_SSRS_sharedservice)。  
  
 **サービス アプリケーションをサービス レポートを作成します。**  
  
-   次のインストールと Reporting Services サービスの登録は、1 つまたは複数の Reporting Services サービス アプリケーションを作成します。 Reporting Services サービス アプリケーションを作成できるように、"SharePoint ファーム サービス アカウント" を一時的にローカルの Administrators グループのメンバーにする必要があります。 SharePoint 2013 のアカウント権限の詳細については、「 [SharePoint 2013 のアカウントのアクセス許可とセキュリティ設定](http://technet.microsoft.com/library/cc678863.aspx) 」(http://technet.microsoft.com/library/cc678863.aspx) をご覧ください。または、SharePoint 2016 の場合は、「 [SharePoint Server 2016 のアカウントのアクセス許可とセキュリティ設定](https://technet.microsoft.com/library/cc678863\(v=office.16\).aspx)」をご覧ください。  
  
     セキュリティ上、SharePoint ファーム管理者アカウントがローカル オペレーティング システムの管理者アカウントを兼ねないことをお勧めします。 インストール プロセスの一環としてファーム管理者アカウントをローカルの Administrators グループに追加する場合は、インストールの完了後にローカルの Administrators グループからそのアカウントを削除することをお勧めします。  
  
##  <a name="bkmk_install_SSRS"></a> 手順 1. SharePoint モードの Reporting Services レポート サーバーのインストール

 このステップでは、SharePoint モードと SharePoint 製品用の Reporting Services アドインで Reporting Services レポート サーバーをインストールします。 コンピューターに既にインストールされている内容によっては、次の手順で説明するインストール ページの一部は表示されない場合があります。  
 
 > [!IMPORTANT]
 > 必要で SharePoint 2016 の Reporting Services SharePoint サーバーをインストールする、**カスタム**サーバーの役割です。 Reporting Services の展開に含まれていないを SharePoint サーバーでも成功、**カスタム**の役割を次の SharePoint メンテナンス期間中に MinRole は、Reporting Services サービス停止を検出したため、Reporting Services を SharePoint 統合モードでは、その他の SharePoint サーバーの役割のいずれかのサポートは示されません。 Reporting Services サービス アプリケーションだけがサポートする、**カスタム**ロール。
 
 > [!NOTE]
 > Power Pivot サービスも SharePoint 2016 上にインストールする予定の場合は、Reporting Services をインストールする前にインストールしてください。 Power Pivot サービスは、 **ユーザー定義** のロールの SharePoint サーバーにはインストールできません。 これにより、ロールを何回も切り替えずに済みます。
 
 ### <a name="apply-the-custom-server-role-to-a-sharepoint-2016-server"></a>SharePoint 2016 サーバーに、カスタム サーバーの役割を適用します。
 
 > [!NOTE]
 > これは、SharePoint 2013 には適用されません。
 
 1. インストールする SharePoint サーバーにログオン[!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]です。
 
 2. **SharePoint 2016 管理シェル** を、管理者として起動します。 
  
    **[SharePoint 2016 管理シェル]** を右クリックし、 **[管理者として実行]**を選びます。

3. PowerShell コマンド プロンプトで、次のコマンドを実行します。

    > [!NOTE]
    > SharePoint サーバーの正しい名前を指定していることを確認してください。
    
        Set-SPServer SERVERNAME -Role Custom

4. タイマー ジョブがスケジュールされたという応答が表示されます。 ジョブが実行されるまで待機する必要があります。

5. 次のコマンドを使用すると、サーバーの割り当てられたロールを確認できます。

        Get-SPServer SERVERNAME 
 
 6. **[ロール]** の一覧に **[ユーザー定義]**が含まれているはずです。
 
 ### <a name="install-reporting-services"></a>Reporting Services のインストール
  
1.  SQL Server インストール ウィザード (Setup.exe) を実行します。  
  
2.  ウィザードの左側の **[インストール]** を選び、 **[SQL Server の新規スタンドアロン インストールを実行するか、既存のインストールに機能を追加します]**を選びます。  

3.  **[プロダクト キー]** ページが表示されたら、キーを入力するか、既定の "Enterprise Evaluation" を受け入れます。  
  
     [ **次へ**] を選択します。  
  
4.  [ライセンス条項] ページが表示されたら、ライセンス条項を確認して同意します。 マイクロソフトでは、お客様の機能使用状況に関するデータを送信することに同意し、製品の機能やサポートの改善にご協力いただいていることを感謝しております。  
  
     [ **次へ**] を選択します。  

5.  **[Microsoft Update を使用して更新プログラムを確認する (推奨)]**を選ぶことをお勧めします。 これは省略可能です。
  
     [ **次へ**] を選択します。   
  
6.  **[セットアップ ファイルのインストール]** ページでは、コンピューターに既にインストールされている内容によっては、次のメッセージが表示される場合があります。  
  
    -   「影響を受けた 1 つ以上のファイルで操作が保留されています。 セットアップ プロセスが完了した後で、コンピューターを再起動する必要があります。」  
  
    -   [ **次へ**] を選択します。  
  
7.  **[インストール ルール]** ページが表示されたら、 警告やインストールの障害となる問題を確認します。 **[次へ]**を選択します。
 
8. **[機能の選択]** ページで、次のオプションを選択します。  
  
    -   **Reporting Services – SharePoint**  
  
    -   **SharePoint 製品用 Reporting Services アドイン**。  
  
    -   必要に応じて、完全な環境にするために **[データベース エンジン サービス]** を選ぶこともできます。ただし、SharePoint データベースをホストする SQL Server データベース エンジンのインスタンスが必要です。  
  
     [ **次へ**] を選択します。  
  
     ![rs_SetupFeatureSelection_SharePoint_with_circles](../../reporting-services/install-windows/media/rs-setupfeatureselection-sharepoint-with-circles.png)
  
9. データベース エンジン サービスを選択した場合は、 **[インスタンスの構成]** ページで **MSSQLSERVER** の既定のインスタンスを受け入れて、 **[次へ]**をクリックします。  
  
     ![注](../../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "注")以前の Reporting Services アーキテクチャと、Reporting Services SharePoint サービス アーキテクチャは SQL Server「インスタンス」に基づいていません。  
  
10. **[サーバーの構成]** ページが表示されたら、適切な資格情報を入力します。 Reporting Services のデータ警告機能またはサブスクリプション機能を使用する場合は、変更する必要があります、**スタートアップの種類**に SQL Server エージェントの**自動**です。 コンピューターに既にインストールされている内容によっては、 **[サーバーの構成]** ページは表示されない場合があります。  
  
     [ **次へ**] を選択します。  
  
11. データベース エンジン サービスを選択した場合は、 **[データベース エンジンの構成]** ページが表示されるので、SQL 管理者の一覧に適切なアカウントを追加して、 **[次へ]**を選びます。  
  
12. **[Reporting Services の構成]** ページで、 **[インストールのみ]** オプションをクリックします。 このオプションは、レポート サーバーのファイルをインストールし、Reporting Services の SharePoint 環境を構成しません。  
  
    > [!NOTE]
    > SQL Server のインストールが完了したら、このトピックの他のセクションに従って SharePoint 環境を構成します。 これには、Reporting Services 共有サービスをインストールし、Reporting Services サービス アプリケーションの作成が含まれます。  
  
     ![ssRS-2016-setup-configuration](../../reporting-services/install-windows/media/ssrs-2016-setup-configuration.png)
  
13. 警告があればそれを確認し、このページで停止する場合は、 **[機能構成ルール]** ページで **[次へ]** を選びます。  
  
14. **[インストールの準備完了]** ページで、インストールの概要を確認します。 概要には、 **SharePointFilesOnlyMode** の値を示す **[Reporting Services SharePoint モード]**子ノードが含まれます。 **[インストール]**を選択します。  
  
15. インストールには数分かかります。 機能の一覧と各機能の状態が表示された **[完了]** ページが表示されます。 コンピューターの再起動が必要であることを示す情報ダイアログが表示される場合もあります。  
  
##  <a name="bkmk_install_SSRS_sharedservice"></a>手順 2: 登録し、Reporting Services SharePoint サービスの開始  
 ![PowerShell 関連コンテンツ](../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")  
  
> [!NOTE]
> 既存の SharePoint ファームにインストールしている場合は、このセクションの手順を実行する必要はありません。 Reporting Services SharePoint サービスがインストールされ、このドキュメントの前のセクションの一部として、SQL Server インストール ウィザードを実行したときに開始します。  
  
 Reporting Services サービスを手動で登録が必要な理由の一般的な理由を次に示します。  
  
-   Reporting Services SharePoint モードは、SharePoint のインストール前にインストールします。  
  
-   Reporting Services SharePoint モードのインストールに使用するアカウントは、SharePoint ファーム管理者グループのメンバーをでした。 詳細については、「 [Setup accounts](#bkmk_setupaccounts)」を参照してください。  
  
 必要なファイルは SQL Server インストール ウィザードの中でインストールされていますが、サービスを SharePoint ファームに登録する必要があります。  
  
 以下では、SharePoint 管理シェルを開いて PowerShell コマンドレットを実行する手順を説明します。  
  
1.  **[スタート]** ボタンを選びます  
  
2.  **[Microsoft SharePoint 2016 製品]** または **[Microsoft SharePoint 2013 製品]** グループを選びます。  
  
3.  **[SharePoint 2016 管理シェル]**または **[SharePoint 2013 管理シェル]**を右クリックし、 **[管理者として実行]**を選びます。 

    > [!NOTE]
    > SharePoint コマンドは、標準の Windows PowerShell ウィンドウでは認識されません。 **[SharePoint 管理シェル]**を使います。  
  
4.  次の PowerShell コマンドを実行して、Reporting Services SharePoint サービスをインストールします。 コマンドが正常に完了すると、管理シェルの表示が改行されます。 コマンドが正常に完了しても、管理シェルに**メッセージは表示されません** 。  
  
    ```  
    Install-SPRSService  
    ```  
  
5.  次の PowerShell コマンドを実行して、Reporting Services サービス プロキシをインストールします。 コマンドが正常に完了すると、管理シェルの表示が改行されます。 コマンドが正常に完了しても、管理シェルに**メッセージは表示されません** 。  
  
    ```  
    Install-SPRSServiceProxy  
    ```  
  
6.  次の PowerShell コマンドを実行してサービスを開始するか、または SharePoint サーバーの全体管理からサービスを開始する方法に関する後の注意事項を参照してください。  
  
    ```  
    get-spserviceinstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
    ```  
  
    > [!IMPORTANT]
    > 次のようなエラー メッセージが表示される場合があります。  
    >   
    >     Install-sprsservice: 用語 'Install-sprsservice'**は認識されません**コマンドレット、関数、スクリプト ファイル、または操作可能なプログラムの名前とします。 名前が正しく記述されていることを確認し、パスが含まれている場合はそのパスが正しいことを確認してから、再試行してください。  
    >
    > SharePoint 管理シェルでなく、Windows Powershell を使用しているか、Reporting Services SharePoint モードがインストールされていません。 Reporting Services と PowerShell の詳細については、次を参照してください。 [Reporting Services SharePoint モード用の PowerShell コマンドレット](../../reporting-services/report-server-sharepoint/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)です。  
  
 3 番目の PowerShell コマンドを実行する代わりに、SharePoint サーバーの全体管理からサービスを開始することもできます。 次の手順を使用すると、サービスが実行していることを確認することもできます。  
  
1.  SharePoint サーバーの全体管理で、 **[システム設定]** の **[サーバーのサービスの管理]** をクリックします。  
  
2.  **[SQL Server Reporting Services サービス]** を探して、[アクション] 列の **[開始]** をクリックします。  
  
3.  Reporting Services サービスのステータスが **[停止]** から **[開始]**に変わります。 Reporting Services サービスが一覧にない場合は、PowerShell を使用してサービスをインストールします。  
  
    > [!NOTE]  
    >  Reporting Services サービスが **[開始中]** ステータスのままで、 **[開始]**に変わらない場合は、Windows サーバー マネージャーで "SharePoint 2013 Administration" サービスが開始されていることを確認します。  
  
##  <a name="bkmk_create_serrviceapplication"></a>手順 3: Reporting Services サービス アプリケーションを作成します。  
 ここでは、既存のサービス アプリケーションを確認している場合に、サービス アプリケーションおよびプロパティの説明を作成する手順について説明します。  
  
1.  SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]** グループの **[サービス アプリケーションの管理]**を選びます。  
  
2.  SharePoint リボンで、 **[新規作成]** ボタンを選びます。  
  
3.  [新規作成] メニューで、 **[SQL Server Reporting Services サービス アプリケーション]**を選びます。  
  
    > [!IMPORTANT]  
    >  Reporting Services のオプションが一覧に表示されない場合は、 **Reporting Services 共有サービスであることを示す値がインストールされていない**です。 PowerShell コマンドレットを使用して、Reporting Services サービスをインストールする方法については、前のセクションを確認します。  
  
4.  **[SQL Server Reporting Services サービス アプリケーションの作成]** ページで、アプリケーションの名前を入力します。 複数の Reporting Services サービス アプリケーションを作成する場合は、わかりやすい名前または名前付け規則を使用すると、管理および運用操作を体系化できます。  
  
5.  **[アプリケーション プール]** セクションで、このアプリケーションのための新しいアプリケーション プールを作成します (推奨)。 新しいアプリケーション プールの名前をサービス アプリケーションと同じにすると、日常の管理が簡単になります。 また、これは、作成するサービス アプリケーションの数や、シングル アプリケーション プールで複数使用する必要があるかどうかによっても影響を受ける場合があります。 アプリケーション プール管理の推奨事項とベスト プラクティスに関する SharePoint Server のドキュメントを参照してください。  
  
     そのアプリケーション プールのセキュリティ アカウントを選択または作成します。 必ずドメイン ユーザー アカウントを指定してください。 ドメイン ユーザー アカウントにより、パスワードやアカウント情報をまとめて更新できる SharePoint のマネージ アカウント機能を使用できるようになります。 ドメイン アカウントは、配置をスケールアウトして、同じ ID で実行されるサービス インスタンスを追加する場合にも必要です。  
  
6.  **[データベース サーバー]**で、現在のサーバーを使用するか、または別の SQL Server を選択することができます。  
  
7.  **[データベース名]** の既定値は " `ReportingService_<guid>`" で、これは一意のデータベース名です。 新しい値を入力する場合は、一意の値を入力します。 これは、サービス アプリケーションを明確な対象として作成される新しいデータベースです。  
  
8.  **[データベース認証]**の既定値は、"Windows 認証" です。 **[SQL 認証]**を選択する場合は、SharePoint のドキュメントを参照して、SharePoint 配置でその認証の種類を使用するためのベスト プラクティスを確認してください。  
  
9. **[Web アプリケーションの関連付け]** セクションで、現在の Reporting Services サービス アプリケーションによるアクセス用に準備する Web アプリケーションを選択します。 1 つの Reporting Services サービス アプリケーションを 1 つの Web アプリケーションに関連付けることができます。 現在のすべての Web アプリケーションが既に Reporting Services サービス アプリケーションと関連付けられている場合は、警告メッセージが表示されます。  
  
10. [ **OK**] を選択します。  
  
11. サービス アプリケーションの作成処理には数分かかることがあります。 完了すると、確認メッセージと、 **[サブスクリプションと警告の準備]** ページへのリンクが表示されます。 Reporting Services のサブスクリプション機能とデータ警告機能を使用する場合は、準備手順を完了します。 詳細については、「 [Provision Subscriptions and Alerts for SSRS Service Applications](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)」を参照してください。  
  
 ![PowerShell 関連コンテンツ](../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")PowerShell を使用して、Reporting Services サービス アプリケーションを作成する方法についてを参照してください。  
  
-   「 [手順 1 ～ 4 に対応する Windows PowerShell スクリプト](#bkmk_full_script)」を参照してください。  
  
-   トピック「[PowerShell を使用して Reporting Services サービス アプリケーションを作成するには](../../reporting-services/report-server-sharepoint/reporting-services-sharepoint-service-and-service-applications.md)」。  

##  <a name="bkmk_powerview"></a>手順 4:、Power View のサイト コレクション機能が有効にします。

 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]での SQL Server 2016 Reporting Services アドインの機能[!INCLUDE[msCoName](../../includes/msconame-md.md)]SharePoint 製品は、サイト コレクション機能です。 機能はルート サイト コレクションと、Reporting Services アドインをインストールした後に作成されたサイト コレクションを自動的にアクティブ化します。 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]を使用する場合は、この機能がアクティブ化されていることを確認してください。  
  
 SharePoint サーバーのインストール後に SharePoint 製品用 Reporting Services アドインをインストールする場合、レポート サーバーの統合機能と Power View の統合機能はでのみアクティブ化ルート サイト コレクション。 他のサイト コレクションについては、この機能を手動でアクティブ化します。  
  
#### <a name="to-activate-or-verify-the-power-view-site-collection-feature"></a>アクティブ化または Power View のサイト コレクション機能を確認します。  
  
1.  次の手順は、SharePoint 2013 の場合に、SharePoint サイトが 2013 の **体験版**用に構成されていることを前提としています。  
  
     ブラウザーで目的の SharePoint サイトを開きます。 たとえば http://\<servername >/サイト/bi  
  
2.  選択**設定**![SharePoint 設定](../../analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 設定")です。  
  
3.  **[サイトの設定]**を選びます。  
  
4.  **[サイト コレクションの管理]** グループで **[サイト コレクションの機能]**を選びます。  
  
5.  一覧で **[Power View 統合機能]** を探します。  
  
6.  **[アクティブ化]**を選びます。 機能の状態が **[アクティブ]**に変化します。  
  
 この手順は、サイト コレクションごとに実行します。 詳しくは、「 [Activate the Report Server and Power View Integration Features in SharePoint](../../reporting-services/report-server-sharepoint/site-collection-features-report-server-and-power-view.md)」をご覧ください。  
  
##  <a name="bkmk_full_script"></a>手順 1 ~ 4 の Windows PowerShell スクリプト  
 このセクション内の PowerShells スクリプトは、前のセクションで手順 1 ～ 4 を実行するときに使用したものと同じです。 このスクリプトは、次の作業を実行します。  
  
-   Reporting Services サービスおよびサービス プロキシをインストールし、サービスを開始します。  
  
-   "Reporting Services" という名前のサービス プロキシを作成します。  
  
-   "Reporting Services Application"という名前の Reporting Services サービス アプリケーションを作成します。  
  
-   サイト コレクションに対応する [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 機能を有効にします。  
  
 パラメーター  
  
-   サービス プロキシに合わせて **-Account** を更新します。 このアカウントは、SharePoint ファーム内で管理されるサービス アカウントであることが必要です。 詳細については、SharePoint のトピック「 [SharePoint 2013 の管理アカウントとサービス アカウントを計画する](http://technet.microsoft.com/library/cc263445.aspx)」を参照してください。  
  
-   サービス アプリケーションに合わせて **–DatabaseServer** パラメーターを更新します。 このパラメーターは、データベース エンジンのインスタンスを意味します  
  
-   **機能を有効にするサイトの** –url [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] パラメーターを更新します。  
  
 **スクリプトを使用するには**  
  
1.  管理者特権で Windows PowerShell を開きます。  
  
2.  次のコードをスクリプト ウィンドウにコピーします。  
  
3.  前のセクションで説明した 3 つのパラメーターを更新し、スクリプトを実行します。  
  
```  
#This script Configures SQL Server Reporting Services SharePoint mode  
  
$starttime=Get-Date  
write-host -foregroundcolor DarkGray StartTime>> $starttime   
  
Write-Host -ForegroundColor Green "Import the SharePoint PowerShell snappin"  
Add-PSSnapin Microsoft.Sharepoint.Powershell –EA 0  
  
Write-Host -ForegroundColor Green "Install SSRS Service and Service Proxy, and start the service"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
  
    Write-Host -ForegroundColor Green "Install the Reporting Services Shared Service"  
    Install-SPRSService  
  
    Write-Host -ForegroundColor Green " Install the Reporting Services Service Proxy"  
    Install-SPRSServiceProxy  
  
    # Get the ID of the RS Service Instance and start the service   
    Write-Host -ForegroundColor Green "Start the Reporting Services Service"  
    $RS = Get-SPServiceInstance | Where {$_.TypeName -eq "SQL Server Reporting Services Service"}  
    Start-SPServiceInstance -Identity $RS.Id.ToString()  
  
    # Wait for the Reporting Services Service to start...  
    $Status = Get-SPServiceInstance $RS.Id.ToString()  
    While ($Status.Status -ne "Online")  
    {  
        Write-Host -ForegroundColor Green "SSRS Service Not Online...Current Status = " $Status.Status  
        Start-Sleep -Seconds 2  
        $Status = Get-SPServiceInstance $RS.Id.ToString()  
    }  
  
$time=Get-Date  
write-host -foregroundcolor DarkGray StartTime>> $starttime   
write-host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Create a new application pool and Reporting Services service application"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Write-Host -ForegroundColor Green "Create a new application pool"  
#!!!! update "-Account" with an existing Managed Service Account  
New-SPServiceApplicationPool -Name "Reporting Services" -Account "<domain>\User name>"  
$appPool = Get-SPServiceApplicationPool "Reporting Services"  
  
Write-Host -ForegroundColor Green " Create the Reporting Services Service Application"  
#!!!! Update "-DatabaseServer", an instance of the SQL Server database engine   
$rsService = New-SPRSServiceApplication -Name "Reporting Services Application" -ApplicationPool $appPool -DatabaseName "Reporting_Services_Application" -DatabaseServer "<server name>"  
  
Write-Host -ForegroundColor Green "Create the Reporting Services Service Application Proxy"  
$rsServiceProxy = New-SPRSServiceApplicationProxy -Name "Reporting Services Application Proxy" -ServiceApplication $rsService  
  
Write-Host -ForegroundColor Green "Associate service application proxy to default web site and grant web applications rights to SSRS application pool"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"     
# Associate the Reporting Services Service Applicatoin Proxy to the default web site...  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $rsServiceProxy  
  
$time=Get-Date  
write-host -foregroundcolor DarkGray StartTime>> $starttime   
write-host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Enable the PowerView and reportserver site features"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
#!!!! update "-url"  of the site where you want the features enabled  
Enable-SPfeature -identity "powerview" -Url http://server/sites/bi  
Enable-SPfeature -identity "reportserver" -Url http://server/sites/bi  
  
####To Verify, you can run the following:  
#Get-SPRSServiceApplication  
#Get-SPServiceApplicationPool | where {$_.name -like "reporting*"}  
#Get-SPRSServiceApplicationProxy  
  
```  
  
##  <a name="bkmk_additional_config"></a>追加の構成  
 このセクションでは、SharePoint のほとんどの配置で重要になる追加の構成手順について説明します。  
  
###  <a name="bkmk_configure_ECS"></a> Excel Services と PowerPivot の構成  
 SharePoint で Excel 2016 または Excel 2013 ブックの [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポートを表示する場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーを Power Pivot モードで使用するように Excel Services を構成する必要があります。 
 
 SharePoint 2016 の場合は、Excel Services を使うために [Office Online Server](https://technet.microsoft.com/library/jj219456\(v=office.16\).aspx) を構成する必要があります。 詳細については、次のホワイト ペーパーを参照してください。
 
 - [SharePoint 2016 での SQL Server 2016 PowerPivot と Power View の配置](../../analysis-services/instances/install-windows/deploying-sql-server-2016-powerpivot-and-power-view-in-sharepoint-2016.md)
 
 - [多層 SharePoint 2016 ファームでの SQL Server 2016 PowerPivot と Power View の配置](../../analysis-services/instances/install-windows/deploy-powerpivot-and-power-view-multi-tier-sharepoint-2016-farm.md)
 
 SharePoint 2016 の場合は、Excel Services アプリケーションを作成して構成する必要があります。 詳細については、以下を参照してください。  
  
-   「 [Power Pivot モードでの Analysis Services のインストール](../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)」の「Analysis Services 統合のための Excel Services の構成」セクション。  
  
-   [Excel Services のデータ モデルの設定を管理する (SharePoint Server 2013)](http://technet.microsoft.com/library/jj219780.aspx)。  

また、Reporting Services サービス アプリケーションによって使用されるアプリケーション プールのセキュリティ アカウントは、Analysis Services サーバーの管理者をする必要があります。
  
###  <a name="bkmk_provision_agent"></a>サブスクリプションと警告準備  
 Reporting Services のサブスクリプションとデータ警告機能には、SQL Server エージェントの権限の構成がある場合があります。 SQL Server エージェントが実行中であるにもかかわらず、SQL Server エージェントが必要であることを示すエラー メッセージが表示された場合は、権限を更新します。 サービス アプリケーション作成成功ページの **[サブスクリプションと警告の準備]** リンクをクリックして、SQL Server エージェントを準備するための別のページに移動します。 配置がコンピューターの境界をまたいでいる場合は (たとえば、SQL Server データベース インスタンスが異なるコンピューターにある場合)、準備手順を行う必要があります。 詳細については、「 [SSRS サービス アプリケーションを使用するためのサブスクリプションと警告の準備](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)」をご覧ください  
  
### <a name="configure-e-mail-for-ssrs-service-applications"></a>SSRS サービス アプリケーション用電子メールを構成します。  
 Reporting Services のデータ警告機能は、電子メール メッセージで警告を送信します。 サービス アプリケーションの電子メール配信拡張機能を変更する必要がありますおよび電子メールを送信するは、Reporting Services サービス アプリケーションを構成する必要があります。 Reporting Services のサブスクリプション機能の電子メール配信拡張機能を使用する場合は、電子メールの設定が必要です。 詳細については、次を参照してください[Reporting Services サービス アプリケーション &#40; 用の電子メールの構成。SharePoint 2013 と SharePoint 2016 &#41;](http://msdn.microsoft.com/38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f). 
  
### <a name="add-reporting-services-content-types-to-content-libraries"></a>コンテンツ ライブラリに Reporting Services コンテンツ タイプを追加します。  
 Reporting Services 共有データ ソース (.rsds) ファイル、レポート モデル (.smdl)、およびレポート ビルダーのレポート定義 (.rdl) ファイルを管理するために使用される定義済みのコンテンツの種類を提供します。 コンテンツの種類として、 **[レポート ビルダー レポート]**、 **[レポート モデル]**、および **[レポート データ ソース]** をライブラリに追加すると、 **[新規作成]** コマンドが有効になり、その種類のドキュメントを新規作成できるようになります。 詳細については、「 [SharePoint ライブラリへの Reporting Services のコンテンツの種類の追加](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)」を参照してください。  
  
### <a name="activate-the-report-server-file-sync-feature"></a>レポート サーバーのファイル同期機能をアクティブにする  
 ユーザーがパブリッシュされたレポート アイテムを SharePoint ドキュメント ライブラリに頻繁に直接アップロードする場合は、サイト レベルの **レポート サーバー ファイル同期** 機能が役立ちます。 ファイル同期機能では、レポート サーバー カタログとドキュメント ライブラリのアイテムの同期が、より頻繁に行われます。 詳しくは、「 [Activate the Report Server File Sync Feature in SharePoint Central Administration](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)」をご覧ください。  
  
##  <a name="bkmk_verify_installation"></a> インストールの確認  
 推奨される手順と Reporting Services SharePoint モードの展開を検証する手順を次に示します。  
  
-   検証トピック「 [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)」の「SharePoint」を参照してください。  
  
-   SharePoint ドキュメント ライブラリでは、たとえばタイトル、テキスト ボックスのみを含む基本的な Reporting Services レポートを作成します。 このレポートには、データ ソースやデータセットは何も含めません。 目標は、レポート ビルダーを開き、基本的なレポートを作成し、そのレポートをプレビューできることの確認です。  
  
     レポートをドキュメント ライブラリに保存し、ライブラリからレポートを実行します。 レポート ビルダーでレポートを作成する方法の詳細については、「 [レポート ビルダーの起動 (レポート ビルダー)](http://technet.microsoft.com/library/ms159221.aspx)」を参照してください。  
  
## <a name="next-steps"></a>次の手順

[Reporting Services SharePoint モード用の PowerShell コマンドレット](../../reporting-services/report-server-sharepoint/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)   
[Reporting Services のアップグレードと移行](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
[SQL Server 2016 のエディションとサポートされている機能](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)   
[Reporting Services の SharePoint サービスとサービス アプリケーション](../../reporting-services/report-server-sharepoint/reporting-services-sharepoint-service-and-service-applications.md)  

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
