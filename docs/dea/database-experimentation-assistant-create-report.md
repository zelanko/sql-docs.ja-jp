---
title: 分析レポートの作成
description: Database Experimentation Assistant で分析レポートを作成する
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 39c82d145a27a46ccc59ec4805e27ffd299f0d96
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056595"
---
# <a name="create-analysis-reports-in-database-experimentation-assistant-sql-server"></a>Database Experimentation Assistant で分析レポートを作成する (SQL Server)

両方の対象サーバーでソーストレースを再生した後、Database Experimentation Assistant (DEA) で分析レポートを生成できます。 分析レポートは、提案された変更のパフォーマンスへの影響についての洞察を得るのに役立ちます。

## <a name="create-an-analysis-report"></a>分析レポートを作成する

DEA で、メニューアイコンを選択します。 展開されたメニューで、チェックリストアイコンの横にある **[分析レポート]** を選択します。

![[分析] メニュー](./media/database-experimentation-assistant-create-report/dea-create-reports-menu.png)

**[分析レポート]** で、 **[新しい分析レポート]** を選択します。

![新しい分析レポートメニュー](./media/database-experimentation-assistant-create-report/dea-create-reports-new-report.png)

次の情報を入力または選択します。

- **レポート名**: レポートの名前を入力します。 レポート名は、A と B の両方のデータベースで使用されます。 例:*レポート名* + *一意の識別子* *の + (または B)* 。 
- **サーバー名**:、B、および分析データベースに含めるサーバーコンピューターの名前を入力します。
- **SQL Server インスタンス名**: レポートに使用する SQL Server インスタンスの名前を入力します。
- **[ソースサーバーのトレース]** : SQL Server (2008 R2) 最初のトレース (.trc) ファイルを入力します。
- **[対象サーバーのトレース]** : ターゲット SQL Server (2014) の最初の .Trc ファイルを入力します。

![[新しい分析レポート] ページ](./media/database-experimentation-assistant-create-report/dea-create-reports-inputs.png)

## <a name="generate-a-report"></a>レポートの生成

**[新しい分析レポート]** ページで必要な情報を入力または選択したら、 **[開始]** を選択してレポートの作成を開始します。 入力した情報が有効な場合は、分析レポートが作成されます。 そうしないと、無効な情報を含むテキストボックスが赤色で強調表示されます。 正しい値を入力し、 **[開始]** を選択してください。 

新しい分析レポートが生成されます。 分析データベースは、名前付けスキーム分析 +*ユーザー指定のレポート名* + *一意識別子*に従います。

## <a name="frequently-asked-questions-about-analysis-reports"></a>分析レポートに関してよく寄せられる質問

### <a name="what-does-my-analysis-report-tell-me"></a>私の分析レポートでは、どのような情報が表示されるのでしょうか。
    
DEA は、統計テストを使用してワークロードを分析し、各クエリがターゲット1からターゲット2にどのように実行されたかを判断します。 各クエリのパフォーマンスの詳細が表示されます。 DEA の詳細については、「[はじめ](database-experimentation-assistant-get-started.md)に」を参照してください。
    
### <a name="can-i-create-a-new-analysis-report-while-another-report-is-being-generated"></a>別のレポートが生成されている間に新しい分析レポートを作成できますか。
    
不可。  現時点では、競合を防ぐために一度に生成できるレポートは1つだけです。 ただし、複数のキャプチャと再生を同時に実行することはできます。

### <a name="i-upgraded-dea-to-version-20-can-i-still-view-and-use-my-old-reports"></a>DEA をバージョン2.0 にアップグレードしました。 古いレポートを表示して使用することはできますか。
    
可能。 以前に生成されたレポートを表示するには、レポートのスキーマを更新する必要があります。 詳細については、「dea [2.0: データベーススキーマを更新する](https://blogs.msdn.microsoft.com/datamigration/2017/03/24/dea-2-0-updating-db-schema-for-analysis-report-in-the-database-experimentation-assistant/)」を参照してください。
    
### <a name="can-i-generate-an-analysis-report-by-using-the-command-prompt"></a>コマンドプロンプトを使用して分析レポートを生成することはできますか。
    
可能。 分析レポートは、コマンドプロンプトで生成できます。 その後、UI でレポートを表示できます。 詳細については、「[コマンドプロンプトでの実行](database-experimentation-assistant-run-command-prompt.md)」を参照してください。
    
## <a name="troubleshoot-analysis-reports"></a>分析レポートのトラブルシューティング

###  <a name="what-security-permissions-do-i-need-to-generate-and-view-an-analysis-report-on-my-server"></a>サーバーで分析レポートを生成して表示するには、どのようなセキュリティ権限が必要ですか。
    
DEA にログインしているユーザーには、分析サーバーの sysadmin 権限が必要です。 ユーザーがグループに属している場合は、グループに sysadmin 権限があることを確認します。

|考えられるエラー|解決方法|  
|---|---|  
|データベースに接続できません。 レポートを分析および表示するための sysadmin 権限を持っていることを確認します。|サーバーまたはデータベースに対するアクセス権または sysadmin 権限を持っていない可能性があります。 ログイン権限を確認してから、操作をやり直してください。|  
|サーバー**サーバー名**に**レポート名**を生成できません。 詳細については、**レポート名**レポートを確認してください。|新しいレポートを生成するために必要な sysadmin 権限を持っていない可能性があります。 詳細なエラーを表示するには、エラーが発生したレポートを選択し、% temp%\\DEA のログを確認してください。|  
|現在のユーザーには、操作を実行するために必要なアクセス許可がありません。 トレースを実行し、レポートを分析するための sysadmin 権限を持っていることを確認します。|新しいレポートを生成するために必要な sysadmin 権限がありません。|  

### <a name="i-cant-connect-to-the-computer-running-sql-server"></a>を実行しているコンピューターに接続できない SQL Server
    
- SQL Server を実行しているコンピューターの名前が有効であることを確認します。 確認するには、SQL Server Management Studio (SSMS) を使用してサーバーに接続してみてください。
- ファイアウォール構成で SQL Server を実行しているコンピューターへの接続がブロックされていないことを確認します。
- ユーザーが必要なユーザー権限を持っていることを確認します。 

詳細については、% temp%\\DEA のログを参照してください。 問題が解決しない場合は、製品チームにお問い合わせください。

### <a name="i-see-an-error-when-i-generate-an-analysis-report"></a>分析レポートを生成するときにエラーが表示する
    
DEA をインストールした後に初めて分析レポートを生成するときは、インターネットアクセスが必要です。 統計分析に必要なパッケージをダウンロードするには、インターネットアクセスが必要です。

レポートの作成中にエラーが発生した場合は、[進行状況] ページに分析の生成に失敗した特定の手順が表示されます。 詳細については、% temp%\\DEA のログを参照してください。 必要なユーザー権限を持つサーバーへの接続が有効であることを確認してから、再試行してください。 問題が解決しない場合は、製品チームにお問い合わせください。

|考えられるエラー|解決方法|  
|---|---|  
|RInterop は起動時にエラーになります。 RInterop ログを確認してから、操作をやり直してください。|DEA は、依存する R パッケージをダウンロードするためにインターネットアクセスを必要とします。 % Temp%\\RInterop の RInterop ログを確認し、% temp%\\DEA のログを破棄してください。 RInterop が正しく初期化されなかった場合、または正しい R パッケージを使用せずに初期化された場合は、DEA ログの初期化前の手順の後に "新しい分析レポートを生成できませんでした" という例外が表示されることがあります。<br><br>RInterop ログには、"jsonlite パッケージが使用できません" というエラーが表示されることもあります。 コンピューターがインターネットにアクセスできない場合は、必要な jsonlite R パッケージを手動でダウンロードできます。<br><br><li>コンピューターのファイルシステムの% userprofile%\\DEARPackages フォルダーにアクセスします。 このフォルダーは、DEA で R が使用するパッケージで構成されています。</li><br><li>インストールされているパッケージの一覧に jsonlite フォルダーがない場合は、インターネットにアクセスできるコンピューターで、 [https://cran.r-project.org/web/packages/jsonlite/index.html](https://cran.r-project.org/web/packages/jsonlite/index.html)からの jsonlite\_1.4 .zip のリリースバージョンをダウンロードする必要があります。</li><br><li>DEA を実行しているコンピューターに .zip ファイルをコピーします。  Jsonlite フォルダーを抽出し、% userprofile%\\DEARPackages にコピーします。 この手順により、自動的に jsonlite パッケージが R にインストールされます。フォルダーは**jsonlite**という名前にする必要があります。コンテンツは、以下の1レベルではなくフォルダー内に直接配置する必要があります。</li><br><li>DEA を閉じて再度開いてから、もう一度分析を試してください。</li><br>RGUI を使用することもできます。 **Zip からインストール > の** **パッケージ**にアクセスします。 前の手順でダウンロードしたパッケージにアクセスし、をインストールします。<br><br>RInterop が初期化され、正しく設定されている場合は、RInterop ログに "依存する R パッケージ jsonlite をインストールしています" と表示されます。|  
|SQL Server インスタンスに接続できません。サーバー名が正しいことを確認し、ログインしているユーザーに必要なアクセス権があるかどうかを確認してください。|サーバーにアクセス権がないか、サーバー名が正しくない可能性があります。| 
|RInterop プロセスがタイムアウトしました。DEA および RInterop ログを確認し、タスクマネージャーで RInterop プロセスを停止してから、操作をやり直してください。<br><br>固定サーバー ロールまたは<br><br>RInterop は faulted 状態にあります。 タスクマネージャーで RInterop プロセスを停止してから、操作をやり直してください。|% Temp%\\RInterop でログを確認して、エラーを確認してください。 タスクマネージャーから RInterop プロセスを削除してから、操作をやり直してください。 問題が解決しない場合は、製品チームにお問い合わせください。| 

### <a name="the-report-is-generated-but-data-appears-to-be-missing"></a>レポートが生成されましたが、データが不足しています
    
SQL Server を実行している分析コンピューターのデータベースを確認して、データが存在することを確認します。 分析データベースが存在することを確認し、そのテーブルを確認します。 たとえば、TblBatchesA、TblBatchesB、および TblSummaryStats の各テーブルを確認します。

データが存在しない場合は、データが正しくコピーされていないか、データベースが破損している可能性があります。 一部のデータのみが不足している場合は、キャプチャまたは再生で作成されたトレースファイルがワークロードを正確にキャプチャしていない可能性があります。 データがある場合は、% temp%\\DEA のログファイルを調べて、エラーがログに記録されたかどうかを確認してください。 その後、もう一度分析レポートの生成を試みます。

他にも質問やフィードバックがありますか? 左下隅にあるスマイルアイコンをクリックして、DEA ツールを通じてフィードバックを送信します。  

## <a name="next-steps"></a>次の手順

- 分析レポートを表示する方法については、「[レポートの表示](database-experimentation-assistant-view-report.md)」を参照してください。

- DEA とデモの19分の概要については、次のビデオをご覧ください。

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
