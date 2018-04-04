---
Title: 'Tutorial: Script Objects in SQL Server Management Studio'
description: SSMS でのオブジェクトのスクリプトの作成に関するチュートリアルです。
keywords: SQL Server, SSMS, SQL Server Management Studio, スクリプト, スクリプト作成
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
helpviewer_keywords:
- projects [SQL Server Management Studio], tutorials
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- solutions [SQL Server Management Studio], tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.openlocfilehash: bc20cc573c6b0890e5b16f4876636534f9fbb916
ms.sourcegitcommit: ccb05cb5a4cccaf7ffa9e85a4684fa583bab914e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-script-objects-in-sql-server-management-studio"></a>チュートリアル: SQL Server Management Studio でオブジェクトのスクリプトを作成する
このチュートリアルでは、SQL Server Management Studio で見つかるさまざまなオブジェクトの Transact-SQL (T-SQL) スクリプトを生成する方法を説明します。  次のオブジェクトのスクリプトを作成する方法の例を示します。 

> [!div class="checklist"]
> * クエリ、GUI 内でアクションを実行する場合
> * データベース、2 種類の方法 ("スクリプト化" と "スクリプトの生成")
> * テーブル
> * ストアド プロシージャ
> * 拡張イベント

このチュートリアルの内容をまとめると、**オブジェクト エクスプローラー**に表示されるすべてのオブジェクトは、オブジェクトを右クリックして **[Script Object As]\(スクリプト化\)** オプションを選択することでスクリプトを作成できます。 


## <a name="prerequisites"></a>Prerequisites
このチュートリアルを実行するには、SQL Server Management Studio、SQL Server へのアクセス、および AdventureWorks データベースが必要です。 

- [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms) をインストールする。
- [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) をインストールする。
- [AdventureWorks サンプル データベース](https://github.com/Microsoft/sql-server-samples/releases)をダウンロードする。 SSMS でデータベースを復元する手順については、[データベースの復元](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)に関するページを参照してください。 


## <a name="script-queries-from-gui"></a>GUI からクエリのスクリプトを作成する
SSMS で GUI を使ってタスクを実行するときはいつでも、そのタスクに関連付けられている T-SQL コードも生成できます。 次の例では、データベースのバックアップを作成するときと、トランザクション ログを圧縮するときについて、その方法を示します。  GUI を使って行うすべてのアクションに、同じ手順を適用できます。 

### <a name="script-t-sql-when-backing-up-a-database"></a>データベースをバックアップするときの T-SQL をスクリプト化する
1. SQL Server に接続します。
2. **[データベース]** ノードを展開します。
3. データベースを右クリックし、**[タスク]** > **[バックアップ]** の順に選択します。

    ![データベースをバックアップする](media/scripting-ssms/backupdb.png)

4. 好みの方法でバックアップを構成します。 このチュートリアルでは、すべてを既定値のままにしました。 ただし、ウィンドウで行った変更もすべて、スクリプトに反映されます。 
5. **[スクリプト]** > **[Script Action to Query Window]\(スクリプト操作を新規クエリ ウィンドウに保存\)** の順にオプションをクリックします。
 
    ![DB バックアップをスクリプト化する](media/scripting-ssms/scriptdbbackup.PNG)
6. クエリ ウィンドウに生成された T-SQL を確認します。 

    ![DB バックアップのスクリプト](media/scripting-ssms/dbbackupscript.PNG)


### <a name="script-t-sql-when-shrinking-the-transaction-log"></a>トランザクション ログを圧縮するときの T-SQL をスクリプト化する
1. データベースを右クリックし、**[タスク]** > **[圧縮]** > **[ファイル]** の順に選択します。

     ![ファイルを圧縮する](media/scripting-ssms/shrinkfiles.png)

2. **[ファイルの種類]** ドロップダウンから **[ログ]** を選択します。

    ![トランザクション ログを圧縮する](media/scripting-ssms/shrinktlog.png)

3. **[スクリプト]** > **[スクリプト操作をクリップボードに保存]** の順にオプションをクリックします。

    ![[スクリプトをクリップボードに保存]](media/scripting-ssms/scriptactiontoclipboard.png)

4. **[新しいクエリ]** ウィンドウを開いて貼り付けます (ウィンドウを右クリックして **[貼り付け]** を選択)。

    ![スクリプトを貼り付ける](media/scripting-ssms/paste.png)


## <a name="script-databases"></a>データベースをスクリプト化する
次のセクションでは、**[スクリプト化]** オプションと **[スクリプトの生成]** オプションの両方を使って、データベースのスクリプトを作成する方法を説明します。  **[スクリプト化]** オプションを使うと、データベースとその構成オプションが再作成されます。 **[スクリプトの生成]** オプションでは、データベース内のすべてのオブジェクトのスクリプトが生成されますが、データはスクリプト化されません。 データのスクリプトも作成するには、[インポートおよびエクスポート ウィザード](https://docs.microsoft.com/en-us/sql/integration-services/import-export-data/start-the-sql-server-import-and-export-wizard)を使う必要があります。  


### <a name="script-database-using-script-option"></a>スクリプト化オプションを使ってデータベースをスクリプト化する
1. SQL Server に接続します。
2. **[データベース]** ノードを展開します。
3. データベースを右クリックして、**[データベースをスクリプト化]** を選択します。

    ![DB をスクリプト化する](media/scripting-ssms/scriptdb.png)

4. ウィンドウでデータベース作成クエリを確認します。 

    ![スクリプト化された DB](media/scripting-ssms/scriptedoutdb.png)
    - このオプションでは、データベース構成オプションだけがスクリプト化されます。  

### <a name="script-database-using-generate-scripts-option"></a>スクリプト生成オプションを使ってデータベースをスクリプト化する
1. SQL Server に接続します。
2. **[データベース]** ノードを展開します。
3. データベースを右クリックし、**[タスク]** > **[スクリプトの生成]** の順に選択します。

    ![DB のスクリプトを生成する](media/scripting-ssms/generatescriptsfordb.png)

4. **[次へ]** を選択すると、データベース全体またはデータベース内の特定のオブジェクトのどちらのスクリプトを生成するかを選択できます。 
 
    ![オブジェクトのスクリプトを生成する](media/scripting-ssms/scriptobjects.png)
 
5. **[次へ]** を選択します。 この画面では、スクリプトを保存する場所を構成できます。 
    - **[詳細]** を選択して、高度なオプションを構成することもできます。

    ![高度なスクリプト オプション](media/scripting-ssms/advancedscripts.png)

6. 次に進む準備ができたら、スクリプトが生成されて **[完了]** と表示されるまで、**[次へ]** をクリックし続けます。 データベースのスクリプトは、ステップ 5 で保存した場所にあります。 
    - データベースのスキーマとさまざまなオブジェクトのスクリプトが生成されますが、データのスクリプトは生成されません。 
 
## <a name="script-tables"></a>テーブルをスクリプト化する
このセクションでは、データベースからテーブルをスクリプト化する方法について説明します。

1. SQL Server に接続します。
2. **[データベース]** ノードを展開します。
3. **AdventureWorks** データベースのノードを展開します。 
4. **[テーブル]** ノードを展開します。
5. スクリプトを作成するテーブルを右クリックして、**[テーブルをスクリプト化]** を選択します。
    - ここには、テーブルの作成やデータの挿入などのさまざまなオプションがあります 
    
    ![Readme_ScriptTable](media/scripting-ssms/scripttable.png)
 
## <a name="script-stored-procedures"></a>ストアド プロシージャをスクリプト化する
このセクションでは、ストアド プロシージャのスクリプトを作成する方法について説明します。 

1. SQL Server に接続します。
2. **[データベース]** ノードを展開します。
3. **[プログラミング]** ノードを展開します。 
4. **[ストアド プロシージャ]** ノードを展開します。
5. 対象のストアド プロシージャを右クリックして、**[ストアド プロシージャをスクリプト化]** を選択します。
    
    ![ストアド プロシージャをスクリプト化する](media/scripting-ssms/scriptstoredprocedure.PNG)

## <a name="script-extended-events"></a>拡張イベントをスクリプト化する
このセクションでは、[拡張イベント](https://docs.microsoft.com/en-us/sql/relational-databases/extended-events/extended-events)のスクリプトを作成する方法について説明します。 

1. SQL Server に接続します。
2. **[管理]** ノードを展開します。
3. **[拡張イベント]** ノードを展開します。
4. **[セッション]** ノードを展開します。
5. 対象の拡張セッションを右クリックして、**[Script Session As]\(セッションをスクリプト化\)** を選択します。

    ![xEvent をスクリプト化する](media/scripting-ssms/scriptxevents.png) 

## <a name="next-steps"></a>次の手順
次の記事では、SSMS で見つかる作成済みのテンプレートについて説明します。 

詳細については、次の記事に進んでください
> [!div class="nextstepaction"]
> [次のステップ ボタン](templates-ssms.md)


