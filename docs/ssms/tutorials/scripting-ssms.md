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
ms.openlocfilehash: a931ddb3cf3229970de4b301e18002484acbaf53
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
- [AdventureWorks2016 サンプル データベース](https://github.com/Microsoft/sql-server-samples/releases)をダウンロードする。 SSMS でデータベースを復元する手順については、[データベースの復元](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)に関するページを参照してください。 


## <a name="script-queries-from-gui"></a>GUI からクエリのスクリプトを作成する
SSMS で GUI を使ってタスクを実行するときはいつでも、そのタスクに関連付けられている T-SQL コードも生成できます。 次の例では、データベースのバックアップを作成するときと、トランザクション ログを圧縮するときについて、その方法を示します。  GUI を使って行うすべてのアクションに、同じ手順を適用できます。 

### <a name="script-t-sql-when-backing-up-a-database"></a>データベースをバックアップするときの T-SQL をスクリプト化する
1. SQL Server に接続します。
2. **[データベース]** ノードを展開します。
3. **Adventureworks2016** データベースを右クリックし、**[タスク]** > **[バックアップ]** の順に選択します。

    ![データベースをバックアップする](media/scripting-ssms/backupdb.png)

4. 好みの方法でバックアップを構成します。 このチュートリアルでは、すべてを既定値のままにしました。 ただし、ウィンドウで行った変更もすべて、スクリプトに反映されます。 
5. **[スクリプト]** > **[Script Action to Query Window]\(スクリプト操作を新規クエリ ウィンドウに保存\)** の順にオプションを選択します。
 
    ![DB バックアップをスクリプト化する](media/scripting-ssms/scriptdbbackup.PNG)
6. クエリ ウィンドウに生成された T-SQL を確認します。 

    ![DB バックアップのスクリプト](media/scripting-ssms/dbbackupscript.PNG)
7. **[実行]** を選択して、T-SQL を使用してデータベースをバックアップするクエリを実行します。 


### <a name="script-t-sql-when-shrinking-the-transaction-log"></a>トランザクション ログを圧縮するときの T-SQL をスクリプト化する
1. **AdventureWorks2016** データベースを右クリックし、**[タスク]** > **[圧縮]** > **[ファイル]** の順に選択します。

     ![ファイルを圧縮する](media/scripting-ssms/shrinkfiles.png)

2. **[ファイルの種類]** ドロップダウンから **[ログ]** を選択します。

    ![トランザクション ログを圧縮する](media/scripting-ssms/shrinktlog.png)

3. **[スクリプト]**、**[スクリプト操作をクリップボードに保存]** の順にオプションをクリックします。

    ![[スクリプトをクリップボードに保存]](media/scripting-ssms/scriptactiontoclipboard.png)

4. **[新しいクエリ]** ウィンドウを開いて貼り付けます (ウィンドウを右クリックして **[貼り付け]** を選択)。

    ![スクリプトを貼り付ける](media/scripting-ssms/paste.png)
5. **[実行]** を選択してクエリを実行し、トランザクション ログを圧縮します。 


## <a name="script-databases"></a>データベースをスクリプト化する
次のセクションでは、**[スクリプト化]** オプションと **[スクリプトの生成]** オプションの両方を使って、データベースのスクリプトを作成する方法を説明します。  **[スクリプト化]** オプションを使うと、データベースとその構成オプションが再作成されます。 **[スクリプトの生成]** オプションでは、スキーマとデータの両方のスクリプトを作成することができます。 このセクションでは、2 つの新しいデータベースを作成します。*AdventureWorks2016a* は **[スクリプト化]** オプションを使用して作成されます。 *AdventureWorks2016b* は **[スクリプトの生成]** オプションを使用して作成されます。 


### <a name="script-database-using-script-option"></a>スクリプト化オプションを使ってデータベースをスクリプト化する
1. SQL Server に接続します。
2. **[データベース]** ノードを展開します。
3. **AdventureWorks2016** データベースを右クリックして、**[Script Database As]\(データベースをスクリプト化\)** > **[Create To]\(作成先\)** > **[新しいクエリ ウィンドウ]** の順に選択します。

    ![DB をスクリプト化する](media/scripting-ssms/scriptdb.png)

4. ウィンドウでデータベース作成クエリを確認します。 

    ![スクリプト化された DB](media/scripting-ssms/scriptedoutdb.png)
    - このオプションでは、データベース構成オプションだけがスクリプト化されます。
5. キーボードの **Ctrl キーを押しながら F キーを押して** **[検索]** ダイアログ ボックスを開き、下矢印を選択して **[置換]** オプションを開きます。 上部の **[検索]** 行に「*AdventureWorks2016*」と入力し、下部の **[置換]** 行に、「*AdventureWorks2016a*」と入力します。 
6. *AdventureWorks2016* のインスタンスをすべて *AdventureWorks2016a* に置き換えるには、**[すべて置換]** を選択します。 

    ![[検索と置換]](media/scripting-ssms/findandreplace.png)

1. **[実行]** を選択してクエリを実行し、*AdventureWorks2016a* データベースを新しく作成します。 

### <a name="script-database-using-generate-scripts-option"></a>スクリプト生成オプションを使ってデータベースをスクリプト化する
1. SQL Server に接続します。
2. **[データベース]** ノードを展開します。
3. **AdventureWorks2016** データベースを右クリックし、**[タスク]** > **[スクリプトの生成]** の順に選択します。

    ![DB のスクリプトを生成する](media/scripting-ssms/generatescriptsfordb.png)

4. **[Introduction]\(説明\)** ページが開いたら、**[次へ]** を選択して **[オブジェクトの選択]** ページを開きます。 データベース全体、またはデータベース内の特定のオブジェクトを選択することができます。 **[データベース全体とすべてのデータベース オブジェクトのスクリプトを作成]** のオプションを選択します 
 
    ![オブジェクトのスクリプトを生成する](media/scripting-ssms/scriptobjects.png)
 
5. **[次へ]** を選択して **[スクリプト作成オプションの設定]** ページを開きます。ここで、スクリプトの保存先やその他の高度なオプションを構成することができます。 

    A. **[新しいクエリ ウィンドウに保存]** のオプションを選択します。 

    B. **[詳細設定]** を選択し、次のオプションを設定します。 

      - **[統計のスクリプトを作成]** を *[統計のスクリプトを作成]* に設定します
      - **[Types of data to script]\(スクリプトを作成するデータの種類\)** を *[Schema only]\(スキーマのみ\)* に設定します
      - **[インデックスのスクリプトを作成]** を *[True]* に設定します

   ![オブジェクトをスクリプト化する](media/scripting-ssms/advancedscripts.png)

   > [!NOTE]
   > **[Types of data to script]\(スクリプトを作成するデータの種類\)** オプションに *[Schema and data]\(スキーマとデータ\)* を選択すると、データベースのデータをスクリプト化することができます。 ただし、大規模なデータベースでは SSMS で割り当てられる以上のメモリが使用されることがあるため、適していません。 小規模なデータベースでは問題ありませんが、より大きなデータベースにデータを移動する場合は、[インポートおよびエクスポート ウィザード](https://docs.microsoft.com/en-us/sql/integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard)を使用する必要があります。



1. **[OK]** を選択し、**[次へ]** を選択します。 
2. **[概要]** で **[次へ]** を選択してからもう一度 **[次へ]** を選択して、スクリプトを **[新しいクエリ]** ウィンドウに生成します。  
3. キーボードの **Ctrl キーを押しながら F キーを押して** **[検索]** ダイアログ ボックスを開き、下矢印を選択して **[置換]** オプションを開きます。 上部の **[検索]** 行に「*AdventureWorks2016*」と入力し、下部の **[置換]** 行に、「*AdventureWorks2016b*」と入力します。 
    A. *AdventureWorks2016* のインスタンスをすべて *AdventureWorks2016b* に置き換えるには、**[すべて置換]** を選択します。 

    ![AdventureWorks2016b](media/scripting-ssms/adventureworks2016b.png)
7. **[実行]** を選択してクエリを実行し、*AdventureWorks2016b* データベースを新しく作成します。 
 
## <a name="script-tables"></a>テーブルをスクリプト化する
このセクションでは、データベースからテーブルをスクリプト化する方法について説明します。 このオプションを使用すると、テーブルの作成またはテーブルの削除と作成ができます。 このオプションを使用して、テーブルへの挿入、テーブルの更新といったテーブルの変更に関連する T-SQL をスクリプト化することもできます。 このセクションでは、テーブルを削除して、再作成します。 

1. SQL Server に接続します。
2. **[データベース]** ノードを展開します。
3. **AdventureWorks** データベースのノードを展開します。 
4. **[テーブル]** ノードを展開します。
5. **dbo.ErrorLog** を右クリックし、 >  **[Script Table as]\(テーブルをスクリプト化\)** > **[Drop and Create To]\(削除および作成先\)** > **[新しいクエリ エディター ウィンドウ]** の順に選択します。
    
    ![Readme_ScriptTable](media/scripting-ssms/scripttable.png)

6. **[実行]** を選択してクエリを実行します。これにより、*Errorlog* テーブルが削除され、再作成されます。 

    >[!NOTE]
    > AdventureWorks2016 データベースの *Errorlog* テーブルは既定では空のため、テーブルを削除してもデータが失われることはありません。 ただし、データが含まれるテーブルで次の手順を実行すると、データが失われます。 
 
## <a name="script-stored-procedures"></a>ストアド プロシージャをスクリプト化する
このセクションでは、ストアド プロシージャを削除して作成する方法について説明します。  

1. SQL Server に接続します。
2. **[データベース]** ノードを展開します。
3. **[プログラミング]** ノードを展開します。 
4. **[ストアド プロシージャ]** ノードを展開します。
5. ストアド プロシージャ **dbo.uspGetBillOfMaterials** を右クリックし、> **[Script Stored Procedure As]\(ストアド プロシージャをスクリプト化\)** > **[Drop and Create to]\(削除および作成先\)** > **[新しいクエリ ウィンドウ]** の順に選択します。
    
    ![ストアド プロシージャをスクリプト化する](media/scripting-ssms/scriptstoredprocedure.PNG)

## <a name="script-extended-events"></a>拡張イベントをスクリプト化する
このセクションでは、[拡張イベント](https://docs.microsoft.com/en-us/sql/relational-databases/extended-events/extended-events)のスクリプトを作成する方法について説明します。 

1. SQL Server に接続します。
2. **[管理]** ノードを展開します。
3. **[拡張イベント]** ノードを展開します。
4. **[セッション]** ノードを展開します。
5. 対象の拡張セッションを右クリックして、**[Script Session As]\(セッションをスクリプト化\)** > **[新しいクエリ エディター ウィンドウ]** を選択します。

    ![xEvent をスクリプト化する](media/scripting-ssms/scriptxevents.png) 
6. **[新しいクエリ ウィンドウ]** でセッションの新しい名前を *system_health* から *system_health2* に変更して **[実行]** を選択し、クエリを実行します。 

    A. **オブジェクト エクスプローラー**で **セッション** を右クリックし、**[更新]** を選択して、新しい拡張イベント セッションを表示します。 セッションの横にある緑色のアイコンはセッションが実行中であることを示し、赤色のアイコンはセッションが停止していることを示しています。 

    ![新しい xEvent](media/scripting-ssms/newxevent.png)

    >[!NOTE]
    > セッションを右クリックして **[開始]** を選択すると、セッションを開始できます。 ただし、これは、既に実行されている *system_health* セッションのコピーであるため、この手順はスキップすることができます。 拡張したイベント セッションのコピーを削除するには、右クリックして **[削除]** を選択します。 

## <a name="next-steps"></a>次の手順
次の記事では、SSMS で見つかる作成済みの T-SQL のテンプレートについて説明します。 

詳細については、次の記事に進んでください。
> [!div class="nextstepaction"]
> [次の手順](templates-ssms.md)


