---
Title: 'Tutorial: Additional Tips and Tricks for using SSMS'
description: 'SSMS の使用に関するその他のヒントとテクニックについてのチュートリアルです。 '
keywords: SQL Server, SSMS, SQL Server Management Studio
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod: sql
ms.technology: ssms
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
helpviewer_keywords:
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- SQL Server Management Studio [SQL Server], tutorials
ms.openlocfilehash: 4f41aaa169e87a246b91304d24142195e7a21988
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="tutorial-additional-tips-and-tricks-for-using-ssms"></a>チュートリアル: SSMS を使用するためのヒントとテクニック
この記事では、SQL Server Management Studio の使用に関する他のテクニックについて説明します。 以下の方法を示します。 

> [!div class="checklist"]
> * Transact-SQL (T-SQL) のテキストをコメント化/コメント解除する
> * テキストをインデントする
> * オブジェクト エクスプローラーでオブジェクトをフィルター処理する
> * SQL Server のエラー ログにアクセスする
> * 使っている SQL Server インスタンスの名前を調べる

## <a name="prerequisites"></a>Prerequisites
このチュートリアルを実行するには、SQL Server Management Studio、SQL Server へのアクセス、および AdventureWorks データベースが必要です。 

- [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms) をインストールする。
- [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) をインストールする。
- [AdventureWorks サンプル データベース](https://github.com/Microsoft/sql-server-samples/releases)をダウンロードする。 SSMS でデータベースを復元する手順については、[データベースの復元](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)に関するページを参照してください。 

## <a name="comment--uncomment-your-t-sql-code"></a>T-SQL コードをコメント化する/コメント解除する
ツール バーのコメント ボタンを使って、テキストの一部をコメント化したり、コメント解除したりできます。 コメント化されたテキストは実行されません。 

1. SQL Server Management Studio を開きます。 
2. SQL Server に接続します。
3. **[新しいクエリ]** ウィンドウを開きます。 
4. 次の T-SQL コード スニペットをテキスト ウィンドウに貼り付けます。 

  ```sql
    USE master
    GO

    -- Drop the database if it already exists
    IF  EXISTS (
        SELECT name 
            FROM sys.databases 
            WHERE name = N'TutorialDB'
            )

    DROP DATABASE TutorialDB
    GO

    CREATE DATABASE TutorialDB
    GO

    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
 ``` 


5. テキストの **Alter Database** の部分を強調表示にして、ツール バーの **[コメント]** をクリックします。 

    ![解説](media/ssms-tricks/comment.png)
6. **[実行]** をクリックして、テキストのコメント解除された部分を実行します。 
7. **Alter Database** コマンド以外のすべての部分を強調表示にして、ツール バーの **[コメント]** をクリックします。

    ![すべてをコメント化する](media/ssms-tricks/commenteverything.png)

8. **Alter Database** の部分を強調表示にして **[コメント解除]** をクリックし、コメントを解除します。

    ![コメントを解除する](media/ssms-tricks/uncomment.png)
    
9. **[実行]** をクリックして、テキストのコメント解除された部分を実行します。 

## <a name="indent-your-text"></a>テキストをインデントする
インデント ボタンを使うと、テキストのインデントを増減することができます。 

1. **[新しいクエリ]** ウィンドウを開きます。 
2. 次の T-SQL コード スニペットをテキスト ウィンドウに貼り付けます。 

  ```sql
    USE master
    GO

    -- Drop the database if it already exists
    IF  EXISTS (
        SELECT name 
            FROM sys.databases 
            WHERE name = N'TutorialDB'
            )

    DROP DATABASE TutorialDB
    GO

    CREATE DATABASE TutorialDB
    GO

    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
 ``` 
 
3. テキストの **Alter Database** の部分を強調表示にし、ツール バーの **[インデント]** をクリックして、このテキストを右に移動します。

    ![[インデント]](media/ssms-tricks/increaseindent.png)

4. テキストの **Alter Database** の部分を再び強調表示にし、今度は **[インデント解除]** をクリックして、このテキストを左に移動します。 
    ![インデント解除](media/ssms-tricks/decreaseindent.png)


## <a name="filter-objects-in-object-explorer"></a>オブジェクト エクスプローラーでオブジェクトをフィルター処理する
データベースに多くのオブジェクトがある場合、特定のオブジェクトを見つけるのが難しい場合があります。 オブジェクトのフィルター処理機能を使って、簡単に見つけることができます。 このセクションではテーブルをフィルター処理する方法について説明しますが、**オブジェクト エクスプローラー**内の他のノードにも同じ手順を使用できます

1. SQL Server に接続します。
2. **[データベース]** ノードを展開します。
3. **AdventureWorks** データベースのノードを展開します。 
4. **[テーブル]** ノードを展開します。 
   - データベースに存在するすべてのテーブルが表示されます。
5. **[テーブル]** ノードを右クリックして、**[フィルター]** > **[フィルターの設定]** の順に選択します。

    ![[フィルターの設定]](media/ssms-tricks/filtersettings.png)

6. [フィルターの設定] ウィンドウでは、フィルターの設定を変更できます。 いくつか例を示します。
    - 名前によるフィルター処理: ![名前によるフィルター](media/ssms-tricks/filterbyname.png)
    - スキーマによるフィルター処理: ![スキーマによるフィルター](media/ssms-tricks/filterbyschema.png)

7. フィルターをクリアするには、**[テーブル]** を右クリックして、**[フィルターの削除]** を選択します

    ![[フィルターの削除]](media/ssms-tricks/removefilter.png)
    


## <a name="access-your-sql-server-error-log"></a>SQL Server のエラー ログにアクセスする
エラー ログは、SQL Server 内で発生したことに関する詳細な情報を含むファイルです。 SSMS で参照してクエリを実行することができます。 ディスクで .log ファイルとして検索することもできます。

### <a name="open-error-log-within-ssms"></a>SSMS でエラー ログを開く
1. SQL Server に接続します。
2. **[管理]** ノードを展開します。 
3. **[SQL Server ログ]** ノードを展開します。 
4. **[現在]** のエラー ログを右クリックして、**[SQL Server ログの表示]** を選択します。

    ![SSMS でエラー ログを表示する](media/ssms-tricks/viewerrorloginssms.png)

### <a name="query-error-log-within-ssms"></a>SSMS でエラー ログのクエリを行う
1. SQL Server に接続します。
2. **[新しいクエリ]** ウィンドウを開きます。
3. クエリ ウィンドウに次の T-SQL コード スニペットを貼り付けます。

 ```sql
   sp_readerrorlog 0,1,'Server process ID' 
  ``` 
4. 単一引用符で囲まれたテキストを検索するテキストに変更します。
5. クエリを実行して結果を確認します。
   
    ![エラー ログのクエリ](media/ssms-tricks/queryerrorlog.png)


### <a name="find-error-log-location-if-youre-connected-to-sql"></a>SQL に接続されている場合にエラー ログの場所を検索する
1. SQL Server に接続します。
2. **[新しいクエリ]** ウィンドウを開きます。
3. クエリ ウィンドウに次の T-SQL コード スニペットを貼り付けて、**[実行]** をクリックします。

 ```sql
    SELECT SERVERPROPERTY('ErrorLogFileName') AS 'Error log file location'  
  ``` 

4. 結果で、ファイル システム内のエラー ログの場所が示されます。 

    ![クエリでエラー ログを見つける](media/ssms-tricks/finderrorlogquery.png)

### <a name="find-error-log-location-if-you-cannot-connect-to-sql"></a>SQL に接続できない場合にエラー ログの場所を検索する
1. SQL Server 構成マネージャーを開きます。 
2. **[サービス]** ノードを展開します。
3. SQL Server インスタンスを右クリックして、**[プロパティ]** を選択します。

    ![構成マネージャーのサーバーのプロパティ](media/ssms-tricks/serverproperties.PNG)

4. **[起動時のパラメーター]** タブを選択します。
5. **[Existing Parameters]\(既存のパラメーター\)** 領域で、"-e" の後のパスがエラー ログの場所です。 
    
    ![エラー ログ](media/ssms-tricks/errorlog.png)
    - この場所には複数の errorlog.* があることがわかります。 *.log で終わっているのが現在のものです。 数字で終わっているのは以前のログです。SQL Server が再起動するたびに、新しいログが作成されます。 
6. このファイルをメモ帳で開きます。 

## <a name="determine-sql-server-name"></a>SQL Server 名を確認する...
SQL Server に接続する前と後では、SQL Server 名を確認する方法が異なります。  

### <a name="when-you-dont-know-it"></a>...インスタンス名がわからないとき
1. 手順に従って[ディスク上の SQL Server エラー ログ](#finding-your-error-log-if-you-cannot-connect-to-sql)を探します。 
2. メモ帳で errorlog.log を開きます。 
3. "サーバー名は" で始まるテキストを探します。
  - 単一引用符で囲まれているのが、これから接続する SQL Server の名前です。![エラー ログでのサーバー名](media/ssms-tricks/servernameinlog.png) 名前の形式は 'HOSTNAME\INSTANCENAME' です。 ホスト名しか表示されないが、既定のインスタンスをインストールしている場合、インスタンス名は 'MSSQLSERVER' です。 既定のインスタンスに接続している場合、SQL Server に接続するにはホスト名のみを入力する必要があります。  

### <a name="once-youre-connected-to-sql"></a>...SQL に接続した後 
接続している SQL Server は 3 つの場所で確認できます。 

1. サーバーの名前は、**オブジェクト エクスプローラー**に表示されます。

    ![オブジェクト エクスプローラーでのインスタンス名](media/ssms-tricks/nameinobjectexplorer.png)
2. サーバーの名前は、クエリ ウィンドウに表示されます。

    ![クエリ ウィンドウでの名前](media/ssms-tricks/nameinquerywindow.png)
3. サーバーの名前は、**プロパティ ウィンドウ**にも表示されます。
    - アクセスするには、**[表示]** メニューを開き、**[プロパティ ウィンドウ]** を選択します。

    ![プロパティでの名前](media/ssms-tricks/nameinproperties.png)

### <a name="if-youre-connected-to-an-alias-or-availability-group-listener"></a>...別名または可用性グループ リスナーに接続している場合 
別名または可用性グループ リスナーに接続しているときは、**オブジェクト エクスプローラー**と**プロパティ**にはそれが表示されます。 その場合、SQL Server の名前はすぐにはわからないことがあり、クエリを行う必要があります。 

1. SQL Server に接続します。
2. **[新しいクエリ]** ウィンドウを開きます。
3. ウィンドウに次の T-SQL コード スニペットを貼り付けます。 

  ```sql
   select @@Servername 
 ``` 
4. クエリの結果を見て、接続している SQL Server の名前を確認します。 
    
    ![サーバー名のクエリ](media/ssms-tricks/queryservername.png)


