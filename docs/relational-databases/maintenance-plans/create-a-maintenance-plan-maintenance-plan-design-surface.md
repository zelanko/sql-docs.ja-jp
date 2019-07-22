---
title: メンテナンス プランの作成 (メンテナンス プラン デザイン画面) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Maintenance Plan Design Surface
ms.assetid: 2ef803ee-a9f8-454a-ad63-fedcbe6838d1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7b39b4391780a8133dae199e39638a6db77d73aa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083903"
---
# <a name="create-a-maintenance-plan-maintenance-plan-design-surface"></a>メンテナンス プランの作成 (メンテナンス プラン デザイン画面)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]でメンテナンス プラン デザイン画面を使用して、単一サーバーまたはマルチサーバーのメンテナンス プランを作成する方法について説明します。 基本的なメンテナンス プランを作成する場合は、 **メンテナンス プラン ウィザード** が最適です。それに対して、デザイン画面を使用してプランを作成すると、高度なワークフローを利用できます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   [メンテナンス プラン デザイン画面を使用したメンテナンス プランの作成](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   マルチサーバー メンテナンス プランを作成するには、1 台のマスター サーバーと 1 台以上のターゲット サーバーを含むマルチサーバー環境を構成する必要があります。 マルチサーバー メンテナンス プランは、マスター サーバー上で作成および管理する必要があります。 このプランはターゲット サーバー上でも表示できますが、ターゲット サーバーでは管理できません。  
  
-   **db_ssisadmin** ロールおよび **dc_admin** ロールのメンバーは、特権を **sysadmin**に昇格できる可能性があります。 このような特権の昇格が発生するのは、それらのロールが [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを変更でき、これらのパッケージを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの **sysadmin** セキュリティ コンテキストを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行できるためです。 メンテナンス プラン、データ コレクション セット、およびその他の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行時にこの特権の昇格を防ぐには、特権が制限されたプロキシ アカウントを使用するようにパッケージを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを構成するか、 **db_ssisadmin** ロールおよび **dc_admin** ロールには **sysadmin** メンバーのみを追加するようにします。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 メンテナンス プランを作成または管理するには、 **sysadmin** 固定サーバー ロールのメンバーである必要があります。 ユーザーが **sysadmin** 固定サーバー ロールのメンバーである場合のみ、オブジェクト エクスプローラーに **[メンテナンス プラン]** ノードが表示されます。  
  
##  <a name="SSMSProcedure"></a> メンテナンス プラン デザイン画面の使用  
  
#### <a name="to-create-a-maintenance-plan"></a>メンテナンス プランを作成するには  
  
1.  オブジェクト エクスプローラーで、プラス記号をクリックして、メンテナンス プランを作成するサーバーを展開します。  
  
2.  プラス記号をクリックして **[管理]** フォルダーを展開します。  
  
3.  **[メンテナンス プラン]** フォルダーを右クリックし、 **[新しいメンテナンス プラン]** をクリックします。  
  
4.  **[新しいメンテナンス プラン]** ダイアログ ボックスで、 **[名前]** ボックスにプランの名前を入力し、 **[OK]** をクリックします。 ツールボックスと *[maintenance_plan_name* **[デザイン]]** 画面が開き、 **Subplan_1** サブプランがメイン グリッドに作成されます。  
  
     デザイン領域のヘッダーには、次のオプションがあります。  
  
     **[サブプランの追加]**  
     構成できるサブプランを追加します。  
  
     **[サブプランのプロパティ]**  
     メイン グリッドで選択されたサブプランについて、 **[サブプランのプロパティ]** ダイアログ ボックスを表示します。 グリッドでサブプランをダブルクリックして、 **[サブプランのプロパティ]** ダイアログ ボックスを表示することもできます。 このダイアログ ボックスの詳細については、以下を参照してください。  
  
     **[選択したサブプランの削除]**  
     選択されているサブプランを削除します。  
  
     **[サブプランのスケジュール]**  
     選択されているサブプランの **[新しいジョブ スケジュール]** ダイアログ ボックスを表示します。  
  
     **[スケジュールの削除]**  
     選択されているサブプランからスケジュールを削除します。  
  
     **[接続の管理]**  
     **[接続の管理]** ダイアログ ボックスが表示されます。 メンテナンス プランに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス接続を追加する際に使用します。 このダイアログ ボックスの詳細については、以下を参照してください。  
  
     **[レポートとログ記録]**  
     **[レポートとログ記録]** ダイアログ ボックスを表示します。 このダイアログ ボックスの詳細については、以下を参照してください。  
  
     **サーバー**  
     **[サーバー]** ダイアログ ボックスが表示されます。このダイアログ ボックスで、サブプラン タスクを実行するサーバーを選択します。 このオプションは、マルチサーバー環境のマスター サーバーのみで有効になります。 詳細については、「[マルチサーバー環境の作成](../../ssms/agent/create-a-multiserver-environment.md)」と「[メンテナンス プラン &#40;Servers&#41;](../../relational-databases/maintenance-plans/maintenance-plan-servers.md)」を参照してください。  
  
     **[名前]**  
     メンテナンス プランの名前が表示されます。 新しいメンテナンス プランの名前は、メンテナンス プラン デザイナーを開く前にダイアログ ボックスで指定します。 メンテナンス プランの名前を変更するには、オブジェクト エクスプローラーでプランを右クリックし、 **[名前の変更]** をクリックします。  
  
     **[説明]**  
     メンテナンス プランの説明を表示または指定します。 説明の長さは最大 512 文字です。  
  
     **デザイナー画面**  
     メンテナンスプランのデザインとメンテナンスを行います。 デザイナー画面を使用して、プランへのメンテナンス タスクの追加、プランからのタスクの削除、タスク間の優先順位制約の指定、タスクの分岐および並列処理の指定を行います。  
  
     2 つのタスクの間にある優先順位制約により、タスク間の関係が確立されます。 1 番目のタスク ( *先行タスク*) の実行結果が指定の条件を満たした場合のみ、2 番目のタスク ( *依存タスク*) が実行されます。 一般的に指定される実行結果は、 **[成功]** 、 **[失敗]** 、 **[完了]** のいずれかです。 詳細については、下記の「手順 **8** 」を参照してください。  
  
5.  デザイン領域のヘッダーで、 **[Subplan_1]** をダブルクリックし、 **[サブプランのプロパティ]** ダイアログ ボックスにサブプランの名前と説明を入力します。  
  
     **[サブプランのプロパティ]** ダイアログ ボックスでは、次のオプションを使用できます。  
  
     **[名前]**  
     サブプランの名前です。  
  
     **[説明]**  
     サブプランの簡潔な説明です。  
  
     **スケジュール**  
     どのようなスケジュールでサブプランが実行されるかを示します。 **[サブプランのスケジュール]** をクリックして、 **[新しいジョブ スケジュール]** ダイアログ ボックスを開きます。 サブプランからスケジュールを削除するには、 **[スケジュールの削除]** をクリックします。  
  
     **[実行するアカウント名]** 一覧  
     このサブタスクを実行するために使用するアカウントを選択します。  
  
6.  **[サブプランのスケジュール]** をクリックし、 **[新しいジョブ スケジュール]** ダイアログ ボックスでスケジュールの詳細を入力します。  
  
7.  サブプランを作成するには、 **ツールボックス** からデザイン画面にタスク フロー要素をドラッグ アンド ドロップします。 タスクをダブルクリックしてダイアログ ボックスを開き、タスクのオプションを構成します。  
  
     **[ツールボックス]** では、次のメンテナンス プランのタスクを使用できます。  
  
    -   **データベースのバックアップ タスク**  
  
    -   **データベースの整合性確認タスク**  
  
    -   **SQL Server エージェント ジョブの実行タスク**  
  
    -   **T-SQL ステートメントの実行タスク**  
  
    -   **履歴クリーンアップ タスク**  
  
    -   **メンテナンス クリーンアップ タスク**  
  
    -   **オペレーターへの通知タスク**  
  
    -   **インデックスの再構築タスク**  
  
    -   **インデックスの再編成タスク**  
  
    -   **データベースの圧縮タスク**  
  
    -   **統計の更新タスク**  
  
     タスクを **[ツールボックス]** に追加するには:  
  
    1.  **[ツール]** メニューで **[ツールボックス アイテムの選択]** をクリックします。  
  
    2.  **[ツールボックス]** に表示するツールを選択し、 **[OK]** をクリックします。  
  
     メンテナンス プランのタスクを **[ツールボックス]** に追加すると、 **メンテナンス プラン ウィザード**で使用できるようになります。 上記の個々のタスクの詳細については、「 [メンテナンス プラン ウィザードの起動](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure) 」の「 **メンテナンス プラン ウィザードの使用**」を参照してください。  
  
8.  タスク間のワークフローを定義するには:  
  
    1.  先行タスクを右クリックし、 **[優先順位制約の追加]** をクリックします。  
  
    2.  **[制御フロー]** ダイアログ ボックスで、 **[対象]** 一覧から依存タスクを選択し、 **[OK]** をクリックします。  
  
    3.  2 つのタスク間のコネクタをダブルクリックすると、 **[優先順位制約エディター]** ダイアログ ボックスが開きます。  
  
         **[優先順位制約エディター]** ダイアログ ボックスでは次のオプションを使用できます。  
  
         **[制約オプション]**  
         2 つのタスク間の制約の動作を定義します。  
  
         **[評価操作]**  一覧  
         優先順位制約で使用する評価操作を指定します。 操作は次のとおりです: **[制約]** 、 **[式]** 、 **[式と制約]** 、 **[式または制約]** 。  
  
         **[値]** 一覧  
         制約値として次の値を指定します: **[成功]** 、 **[失敗]** 、 **[完了]** 。 デフォルト値は **[成功]** です。  
  
        > [!NOTE]  
        >  優先順位制約を表す線は、 **[成功]** の場合は緑色、 **[失敗]** の場合は赤色、 **[完了]** の場合は青色です。  
  
         **[式]**  
         操作として **[式]** 、 **[式と制約]** 、または **[式または制約]** を使用する場合は、式を入力します。 式はブール値に評価される必要があります。  
  
         **テスト**  
         式を検証します。  
  
         **[複数の制約]**  
         複数の制約がどのように相互運用して制約付きタスクの実行を制御するかを定義します。  
  
         **論理積**  
         同一の実行可能ファイルに対して、複数の優先順位制約を同時に評価することを指定する場合に選択します。 すべての制約が True に評価される必要があります。 これは既定のオプションです。  
  
        > [!NOTE]  
        >  この種類の優先順位制約は、緑色、赤色、または青色の実線で示されます。  
  
         **論理和**  
         同一の実行可能ファイルに対して、複数の優先順位制約を同時に評価することを指定する場合に選択します。 少なくとも 1 つの制約が True に評価される必要があります。  
  
        > [!NOTE]  
        >  この種類の優先順位制約は、緑色、赤色、または青色の点線で示されます。  
  
9. 別のスケジュールで実行されるタスクを制約する別のサブプランを追加するには、ツール バーの **[サブプランの追加]** をクリックし、 **[サブプランのプロパティ]** ダイアログ ボックスを開きます。  
  
10. 別のサーバーに接続を追加するには:  
  
    1.  デザイン画面のツール バーで、 **[接続の管理]** をクリックします。  
  
    2.  **[接続の管理]** ダイアログ ボックスで **[追加]** をクリックします。  
  
    3.  **[接続プロパティ]** ダイアログ ボックスの **[接続名]** ボックスに、作成する接続の名前を入力します。  
  
    4.  **[SQL Server データに接続するための情報を指定してください]** の **[サーバー名の選択または入力]** ボックスで、使用する SQL Server 名を入力するか、参照ボタン **([...])** をクリックして **[SQL Server]** ダイアログ ボックスでサーバーを選択します。 **[SQL Server]** ダイアログ ボックスでサーバーを選択した場合は、 **[OK]** をクリックします。  
  
    5.  **[サーバーにログオンするための情報の入力]** で、 **[Windows NT の統合セキュリティを使用する]** または **[特定のユーザー名とパスワードを使用する]** を選択します。 特定のユーザー名とパスワードを使用するように選択した場合は、 **[ユーザー名]** および **[パスワード]** ボックスにそれぞれ情報を入力します。  
  
    6.  **[接続プロパティ]** ダイアログ ボックスで、 **[OK]** をクリックします。  
  
    7.  **[接続の管理]** ダイアログ ボックスで、 **[閉じる]** をクリックします。  
  
11. レポート オプションを指定するには:  
  
    1.  デザイン画面のツール バーで **[レポートとログ記録]** をクリックします。  
  
    2.  **[レポートとログ記録]** ダイアログ ボックスの **[レポート]** で、 **[テキスト ファイルのレポートを生成する]** または **[電子メール受信者にレポートを送信する]** 、あるいはその両方を選択します。  
  
        1.  **[テキスト ファイルのレポートを生成する]** で、 **[新しいファイルの作成]** または **[ファイルに追加]** を選択します。  
  
        2.  上記の選択内容に応じて、 **[フォルダー]** または **[ファイル名]** ボックスに情報を入力することにより、新しいファイルまたは追加されるファイルの名前および完全なパスを入力します。 または、参照ボタン ( **[...]** ) をクリックし、 **[フォルダーの検索 -** _server\_name_] または **[データベース ファイルの検索 -** _server\_name_] ダイアログ ボックスで、フォルダーへのパスまたはファイル名を選択します。  
  
        3.  **[エージェント オペレーター]** 一覧で **[電子メール受信者にレポートを送信する]** を選択した場合は、電子メール レポートの受信者を選択します。  
  
            > [!NOTE]  
            >  メールを送信するためには、データベース メールを使用するように SQL Server エージェントを構成する必要があります。 詳細については、「 [Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)」をご覧ください。  
  
    3.  より詳細な情報を保存するには、 **[ログ記録]** で、 **[拡張情報をログに記録する]** をオンにします。  
  
    4.  メンテナンス プランの結果情報を別のサーバーに書き込むには、 **[リモート サーバーにログを記録する]** をオンにし、 **[接続]** 一覧からサーバー接続を選択するか、または **[新規]** をクリックして **[接続プロパティ]** ダイアログ ボックスに接続情報を入力します。  
  
    5.  **[レポートとログ記録]** ダイアログ ボックスで、 **[OK]** をクリックします。  
  
12. ログ ファイル ビューアーで結果を参照するには、 **オブジェクト エクスプローラー**で **[メンテナンス プラン]** フォルダーを右クリックするか、特定のメンテナンス プランを右クリックして **[履歴の表示]** を選択します。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     The following options are available on the **Log File Viewer -**_server\_name_ dialog box.  
  
     **Load Log**  
     Open a dialog box where you can specify a log file to load.  
  
     **Export**  
     Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.  
  
     **Refresh**  
     Refresh the view of the selected logs. The **Refresh** button rereads the selected logs from the target server while applying any filter settings.  
  
     **Filter**  
     Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.  
  
     **Search**  
     Search the log file for specific text. Searching with wildcard characters is not supported.  
  
     **Stop**  
     Stops loading the log file entries. For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.  
  
     **Log file summary**  
     This information panel displays a summary of the log file filtering. If the file is not filtered, you will see the following text, **No filter applied**. If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.  
  
     **Date**  
     Displays the date of the event.  
  
     **Source**  
     Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example). This does not appear for all log types.  
  
     **Message**  
     Displays any messages associated with the event.  
  
     **Log Type**  
     Displays the type of log to which the event belongs. All selected logs appear in the log file summary window.  
  
     **Log Source**  
     Displays a description of the source log in which the event is captured.  
  
     **Selected row details**  
     Select a row to display additional details about the selected event row at the bottom of the page. The columns can be reordered by dragging them to new locations in the grid. The columns can be resized by dragging the column separator bars in the grid header to the left or right. Double-click the column separator bars in the grid header to automatically size the column to the content width.  
  
     **Instance**  
     The name of the instance on which the event occurred. This is displayed as *computer name*\\*instance name*.  
  
  
