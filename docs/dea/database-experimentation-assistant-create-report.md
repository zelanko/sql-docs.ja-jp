---
title: データベース実験 Assistant で SQL Server のアップグレードの分析レポートを作成します。
description: データベース実験アシスタントでの分析レポートを作成します。
ms.custom: ''
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
ms.openlocfilehash: d53d8734e0c01fa2056b9d560f3bc65b7f64d9a9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68058969"
---
# <a name="create-analysis-reports-in-database-experimentation-assistant"></a>データベース実験アシスタントでの分析レポートを作成します。

対象サーバーの両方でソースのトレースを再生すると後でデータベース実験アシスタント (DEA) 分析レポートを生成できます。 分析レポートを使用して、提案された変更のパフォーマンスに与える影響についての洞察できます。

## <a name="create-an-analysis-report"></a>分析レポートを作成します。

DEA では、メニュー アイコンを選択します。 展開されたメニューで、次のように選択します。**分析レポート**チェックリストのアイコンの横にあります。

![分析メニュー](./media/database-experimentation-assistant-create-report/dea-create-reports-menu.png)

**分析レポート**、**分析レポートを新しい**。

![新しいレポートの分析 メニュー](./media/database-experimentation-assistant-create-report/dea-create-reports-new-report.png)

入力するか、次の情報を選択します。

- **レポート名**:レポートの名前を入力します。 レポート名が使用される両方 A と B のデータベース。 例: *(A または B)*  + *レポート名* + *一意識別子*します。 
- **[サーバー名]** : A、追加するサーバー コンピューターの名前を入力します。 B、および分析データベース。
- **SQL Server インスタンス名**:レポートに使用する SQL Server インスタンスの名前を入力します。
- **移行元サーバーのトレース**:SQL Server (2008 R2) の最初のトレース (.trc) ファイルを入力します。
- **対象サーバーのトレース**:ターゲット SQL Server (2014) 最初 .trc ファイルを入力します。

![新しい分析レポートのページ](./media/database-experimentation-assistant-create-report/dea-create-reports-inputs.png)

## <a name="generate-a-report"></a>レポートを生成します

入力またはで必要な情報を選択した後、**分析レポートを新しい**] ページで、[**開始**レポートの作成を開始します。 入力した情報が有効な場合は、分析レポートが作成されます。 それ以外の場合、無効な情報を持つテキスト ボックスは、赤で強調表示されます。 正しい値を入力しを選択してください**開始**します。 

新しい分析レポートが生成されます。 分析データベースに依存して、名前付けのスキーム解析 +*ユーザー指定のレポート名* + *一意識別子*します。

## <a name="frequently-asked-questions-about-analysis-reports"></a>分析レポートについてよく寄せられる質問

### <a name="what-does-my-analysis-report-tell-me"></a>何が分析レポートわかりますか。
    
DEA では、統計テストを使用して、ワークロードを分析し、ターゲットの 1 から 2 をターゲットに各クエリの実行を決定します。 各クエリのパフォーマンスの詳細を提供します。 DEA で詳細[開始](database-experimentation-assistant-get-started.md)します。
    
### <a name="can-i-create-a-new-analysis-report-while-another-report-is-being-generated"></a>別のレポートの生成中に、新しい分析レポートを作成できますか。
    
No.  現時点では、競合を防ぐには、一度に 1 つのレポートを生成できます。 ただし、1 つ以上のキャプチャを実行し、同時に再生できます。

### <a name="i-upgraded-dea-to-version-20-can-i-still-view-and-use-my-old-reports"></a>DEA をバージョン 2.0 にアップグレードしたとします。 まだ表示および使用できる、古いレポートでしょうか。
    
可能。 以前に生成されたレポートを表示するには、レポートのスキーマを更新する必要があります。 詳細については、次を参照してください。 [DEA 2.0。DEA で分析レポート用データベース スキーマの更新](https://blogs.msdn.microsoft.com/datamigration/2017/03/24/dea-2-0-updating-db-schema-for-analysis-report-in-the-database-experimentation-assistant/)します。
    
### <a name="can-i-generate-an-analysis-report-by-using-the-command-prompt"></a>コマンド プロンプトを使用して、分析レポートを生成できますか。
    
可能。 コマンド プロンプトで、分析レポートを生成することができます。 UI で、レポートを表示できます。 詳細については、次を参照してください。[コマンド プロンプトで実行](database-experimentation-assistant-run-command-prompt.md)します。
    
## <a name="troubleshoot-analysis-reports"></a>分析レポートをトラブルシューティングします。

###  <a name="what-security-permissions-do-i-need-to-generate-and-view-an-analysis-report-on-my-server"></a>生成し、サーバーに、分析レポートを表示する必要があるどのようなセキュリティ アクセス許可をでしょうか。
    
DEA にログインしたユーザーによっては、分析サーバーの sysadmin 権限が必要です。 ユーザーがグループの一部である場合は、グループは sysadmin 権限を持っていることを確認します。

|可能性のあるエラー|ソリューション|  
|---|---|  
|データベースに接続できません。 分析およびレポートを表示するための sysadmin 権限を持っていることを確認します。|サーバーまたはデータベースへのアクセスまたは sysadmin 権限がありません。 ログイン権限を確認し、もう一度やり直してください。|  
|生成できません**レポート名**サーバー**サーバー名**します。 詳細については、確認、**レポート名**レポートします。|新しいレポートを生成するために必要な sysadmin 権限がありません。 詳細なエラーを表示するには、エラーが発生したレポートを選択し、%temp% にログを確認して\\DEA します。|  
|現在のユーザーには、操作を実行する必要なアクセス許可を持っていません。 トレースを実行して、レポートを分析するための sysadmin 権限を持っていることを確認します。|新しいレポートを生成するために必要な sysadmin 権限がありません。|  

### <a name="i-cant-connect-to-the-computer-running-sql-server"></a>SQL Server を実行しているコンピューターに接続できません。
    
- SQL Server を実行しているコンピューターの名前が有効であることを確認します。 で確認するのには、SQL Server Management Studio (SSMS) を使用して、サーバーに接続してみてください。
- ファイアウォールの構成が SQL Server を実行しているコンピューターへの接続をブロックしないことを確認します。
- ユーザーが必要なユーザー権利を持っていることを確認します。 

%Temp% に、ログで詳細を確認できます\\DEA します。 問題が解決しない場合は、製品チームにお問い合わせください。

### <a name="i-see-an-error-when-i-generate-an-analysis-report"></a>分析レポートを生成するときにエラーが表示されます。
    
インターネットへのアクセスが初めて DEA をインストールした後、分析レポートを生成する必要です。 統計分析に必要なパッケージをダウンロードするには、インターネットへのアクセスが必要です。

レポートの作成中にエラーが発生する場合、進行状況 ページには、分析の生成に失敗しましたが、特定の手順が表示されます。 %Temp% に、ログで詳細を確認できます\\DEA します。 必要なユーザー アクセス権を持つサーバーへの有効な接続を再試行してを確認します。 問題が解決しない場合は、製品チームにお問い合わせください。

|可能性のあるエラー|ソリューション|  
|---|---|  
|RInterop には、起動時にエラーが発生します。 RInterop ログを確認し、もう一度やり直してください。|DEA には、依存する R パッケージのダウンロードにインターネット アクセスが必要です。 RInterop が %temp% にログを確認する\\%temp% にログに記録 RInterop と DEA\\DEA します。 RInterop が正しく初期化されていない場合、または適切な R パッケージせずに初期化されている場合は、DEA ログ InitializeRInterop 手順の後に「新しい分析レポートの生成に失敗しました」の例外を参照してください可能性があります。<br><br>RInterop ログもエラーが表示される「パッケージがあるない jsonlite 使用可能です」に似ています コンピューターにはインターネット アクセスを設定しない場合は、必要な jsonlite R パッケージを手動でダウンロードできます。<br><br><li>%Userprofile% に移動して\\DEARPackages、マシンのファイル システム フォルダー。 このフォルダーは、DEA を R で使用されるパッケージで構成されます。</li><br><li>Jsonlite フォルダーがインストールされているパッケージの一覧にない場合、マシンをインターネットにアクセスできる jsonlite のリリース バージョンをダウンロードする必要があります。\_から 1.4.zip [ https://cran.r-project.org/web/packages/jsonlite/index.html](https://cran.r-project.org/web/packages/jsonlite/index.html)します。</li><br><li>DEA を実行しているマシンに .zip ファイルをコピーします。  Jsonlite フォルダーを抽出して、%userprofile% にコピーして\\DEARPackages します。 この手順は、R での jsonlite パッケージを自動的にインストールされます。フォルダーを指定する必要があります**jsonlite**内容をしない 1 レベル下、フォルダー内で直接指定する必要があります。</li><br><li>もう一度 DEA、もう一度開いて、およびお試しください分析を閉じます。</li><br>RGUI を使用することもできます。 移動して**パッケージ** > **zip からインストール**します。 以前ダウンロードしたパッケージに移動し、インストールします。<br><br>RInterop が初期化され、正しく設定されて、"Installing 依存 R パッケージ jsonlite"RInterop ログが表示されます。|  
|SQL Server インスタンスに接続し、サーバー名が正しいことを確認にログオンしているユーザーのアクセス許可を確認できません。|アクセスができないことがあります。 またはユーザー権限をサーバーまたはサーバー名が正しくない可能性があります。| 
|RInterop プロセスがタイムアウトしました。DEA および RInterop ログを確認、タスク マネージャーでは、RInterop プロセスを停止してからやり直してください。<br><br>または<br><br>RInterop はエラーが発生した状態です。 タスク マネージャーでは、RInterop プロセスを停止してからやり直してください。|%Temp% にログに記録チェック\\RInterop をエラーを確認します。 再実行する前にタスク マネージャーから RInterop プロセスを削除します。 問題が解決しない場合は、製品チームにお問い合わせください。| 

### <a name="the-report-is-generated-but-data-appears-to-be-missing"></a>レポートが生成されます。 が、不足している場合、データが表示されます。
    
データが存在することを確認する SQL Server を実行している analysis コンピューター上のデータベースを確認します。 分析データベースが存在することを確認し、そのテーブルを確認します。 たとえば、これらのテーブルを確認します。TblBatchesA、TblBatchesB、および TblSummaryStats です。

データが存在しない場合、データは正しくコピーされない可能性がありますか、データベースが壊れている可能性があります。 一部のデータがない場合のみキャプチャで作成されたトレース ファイルまたは再生がワークロードを正確にキャプチャがない可能性があります。 データが存在する場合は、%temp% に、ログ ファイルを確認してください。\\DEA にエラーが記録された場合を参照してください。 次に、分析レポート生成を再試行します。

詳細についての質問やフィードバックでしょうか。 左上隅にあるスマイル アイコンを選択して、DEA ツールを通じてフィードバックを送信します。  

## <a name="next-steps"></a>次のステップ

- 分析レポートを表示する方法については、次を参照してください。[レポートを表示する](database-experimentation-assistant-view-report.md)します。

- DEA とデモンストレーションを 19 分については、次のビデオをご覧ください。

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
