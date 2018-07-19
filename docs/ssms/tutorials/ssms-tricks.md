---
Title: 'Tutorial: Additional tips and tricks for using SQL Server Management Studio'
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
- Find SQL Server Instance
- find instance name
- find sql server instance name
ms.openlocfilehash: ef7bbf9b60cb29bee0285d8974a9b97cbe99a3c2
ms.sourcegitcommit: 0dff9dd43e80eee900eb92d25df9ca18397f3485
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37080100"
---
# <a name="tutorial-additional-tips-and-tricks-for-using-ssms"></a>チュートリアル: SSMS を使用するためのヒントとテクニック
このチュートリアルでは、SQL Server Management Studio (SSMS) の使用時に便利なその他のテクニックを紹介します。 この記事で取り上げるテクニック: 

> [!div class="checklist"]
> * Transact-SQL (T-SQL) のテキストをコメント化する/コメント解除する
> * テキストをインデントする
> * オブジェクト エクスプローラーでオブジェクトにフィルターを適用する
> * SQL Server のエラー ログにアクセスする
> * 使っている SQL Server インスタンスの名前を調べる

## <a name="prerequisites"></a>Prerequisites
このチュートリアルを実行するには、SQL Server Management Studio、SQL Server へのアクセス、AdventureWorks データベースが必要です。 

- [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) をインストールする。
- [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads) をインストールする。
- [AdventureWorks サンプル データベース](https://github.com/Microsoft/sql-server-samples/releases)をダウンロードする。 SSMS でデータベースを復元する方法については、[データベースの復元](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)に関するページを参照してください。 


## <a name="commentuncomment-your-t-sql-code"></a>T-SQL コードをコメント化する/コメント解除する
ツール バーの **[コメント]** ボタンを使用し、テキストの一部をコメント化したり、コメント化を解除したりできます。 コメント化されたテキストは実行されません。 

1. SQL Server Management Studio を開きます。 
2. SQL Server に接続します。
3. [新しいクエリ] ウィンドウを開きます。 
4. 次の T-SQL コードをテキスト ウィンドウに貼り付けます。 

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


5. テキストの **Alter Database** 部分を強調表示し、ツール バーの **[コメント]** ボタンを選択します。 

    ![[コメント] ボタン](media/ssms-tricks/comment.png)
6. **[実行]** を選択し、テキストのコメント解除された部分を実行します。 
7. **Alter Database** コマンド以外をすべて強調表示し、**[コメント]** ボタンを選択します。

    ![すべてをコメント化する](media/ssms-tricks/commenteverything.png)

8. テキストの **Alter Database** 部分を強調表示し、ツール バーの **[Uncomment]\(コメントを解除する\)** ボタンを選択してコメントを解除します。

    ![テキストのコメントを解除する](media/ssms-tricks/uncomment.png)
    
9. **[実行]** を選択し、テキストのコメント解除された部分を実行します。 

## <a name="indent-your-text"></a>テキストをインデントする
ツール バーのインデント ボタンを使用し、テキストのインデントを増減できます。 

1. [新しいクエリ] ウィンドウを開きます。 
2. 次の T-SQL コードをテキスト ウィンドウに貼り付けます。 

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
 
3. テキストの **Alter Database** の部分を強調表示し、ツール バーの **[インデント]** を選択してこのテキストを右に移動します。

    ![インデントを増やす](media/ssms-tricks/increaseindent.png)

4. テキストの **Alter Database** の部分を強調表示し、**[インデント解除]** ボタンを選択してこのテキストを左に移動します。

    ![インデントを減らす](media/ssms-tricks/decreaseindent.png)


## <a name="filter-objects-in-object-explorer"></a>オブジェクト エクスプローラーでオブジェクトにフィルターを適用する
データベースにオブジェクトがたくさんある場合、オブジェクトにフィルターを適用することで特定のオブジェクトが見つけやすくなります。 このセクションでは、テーブルにフィルターを適用する方法について説明しますが、次の手順はオブジェクト エクスプローラーの他のノードでも利用できます。

1. SQL Server に接続します。
2. **[データベース]** > **[AdventureWorks]** > **[テーブル]** の順に展開します。 データベース内のすべてのテーブルが表示されます。
5. **[テーブル]** を右クリックし、**[フィルター]** > **[フィルターの設定]** の順に選択します。

    ![フィルターの設定](media/ssms-tricks/filtersettings.png)

6. **[フィルターの設定]** ウィンドウで、次のフィルター設定の一部を変更できます。
    - 名前でフィルター: 
   
      ![名前でフィルター](media/ssms-tricks/filterbyname.png)

    - スキーマでフィルター: 
    
      ![スキーマでフィルター](media/ssms-tricks/filterbyschema.png)

7. フィルターを消去するには、**[テーブル]** を右クリックし、**[フィルターの削除]** を選択します。

    ![フィルターの削除](media/ssms-tricks/removefilter.png)
    


## <a name="access-your-sql-server-error-log"></a>SQL Server のエラー ログにアクセスする
エラー ログは、SQL Server インスタンス内で発生したことに関する詳細な情報を含むファイルです。 SSMS では、エラー ログを参照したり、クエリを実行したりできます。 エラー ログは、ディスクに置かれている .log ファイルです。

### <a name="open-the-error-log-in-ssms"></a>SSMS でエラー ログを開く
1. SQL Server に接続します。  
2. **[管理]** > **[SQL Server ログ]** の順に展開します。 
4. **[現在]** のエラー ログを右クリックし、**[SQL Server ログの表示]** を選択します。

    ![SSMS でエラー ログを表示する](media/ssms-tricks/viewerrorloginssms.png)

### <a name="query-the-error-log-in-ssms"></a>SSMS でエラー ログにクエリを実行する
1. SQL Server に接続します。
2. [新しいクエリ] ウィンドウを開きます。
3. 次の T-SQL コードをクエリ ウィンドウに貼り付けます。

 ```sql
   sp_readerrorlog 0,1,'Server process ID' 
  ``` 

4. 単一引用符で囲まれたテキストを検索するテキストに変更します。
5. クエリを実行し、結果を確認します。
   
    ![エラー ログにクエリを実行する](media/ssms-tricks/queryerrorlog.png)


### <a name="find-the-error-log-location-if-youre-connected-to-sql-server"></a>SQL Server に接続されている場合にエラー ログの場所を検索する
1. SQL Server に接続します。
2. [新しいクエリ] ウィンドウを開きます。
3. クエリ ウィンドウに次の T-SQL コードを貼り付け、**[実行]** を選択します。

 ```sql
    SELECT SERVERPROPERTY('ErrorLogFileName') AS 'Error log file location'  
  ``` 

4. 結果に、ファイル システム内のエラー ログの場所が示されます。 

    ![クエリでエラー ログを見つける](media/ssms-tricks/finderrorlogquery.png)

### <a name="find-the-error-log-location-if-you-cant-connect-to-sql-server"></a>SQL Server に接続できない場合にエラー ログの場所を検索する
1. SQL Server 構成マネージャーを開きます。 
2. **[サービス]** を展開します。
3. SQL Server インスタンスを右クリックし、**[プロパティ]** を選択します。

    ![構成マネージャー サーバーのプロパティ](media/ssms-tricks/serverproperties.PNG)

4. **[起動時のパラメーター]** タブを選択します。
5. **[既存のパラメーター]** 領域で、"-e" の後のパスがエラー ログの場所です。 
    
    ![エラー ログ](media/ssms-tricks/errorlog.png)
    
    この場所には複数の errorlog.* ファイルがあります。 *.log で終わるファイル名が現在のエラー ログ ファイルです。 数字で終わるファイル名は以前のログ ファイルです。 SQL Server が再起動するたびに新しいログが作成されます。

6. メモ帳で errorlog.log ファイルを開きます。 

## <a name="determine-sql-server-name"></a>SQL Server インスタンス名を見つける
SQL Server に接続する前に、あるいは接続した後に、いくつかの方法で SQL server の名前を検索できます。  

### <a name="before-you-connect-to-sql-server"></a>SQL Server に接続する前
1. 次の手順で[ディスク上の SQL Server エラー ログ](#finding-your-error-log-if-you-cannot-connect-to-sql)を探します。 
2. メモ帳で errorlog.log ファイルを開きます。  
3. *Server name is* というテキストを探します。
    
    単一引用符で囲まれているのが、これから接続する SQL Server インスタンスの名前です。

    ![エラー ログでサーバー名を見つける](media/ssms-tricks/servernameinlog.png)
    
    名前の形式は "ホスト名\インスタンス名" です。 ホスト名しか表示されない場合、既定のインスタンスをインストールしており、インスタンス名は MSSQLSERVER です。 既定のインスタンスに接続するとき、ホスト名だけを入力して SQL Server に接続できます。  

### <a name="when-youre-connected-to-sql-server"></a>SQL Server に接続しているとき 
SQL Server に接続しているとき、3 か所でサーバー名が見つかります。 

1. サーバーの名前はオブジェクト エクスプローラーに表示されます。

    ![オブジェクト エクスプローラーの SQL Server インスタンス名](media/ssms-tricks/nameinobjectexplorer.png)
2. サーバーの名前はクエリ ウィンドウに表示されます。

    ![クエリ ウィンドウの SQL Server インスタンス名](media/ssms-tricks/nameinquerywindow.png)
3. サーバーの名前は **[プロパティ]** に表示されます。
    - **[表示]** メニューで、**[プロパティ ウィンドウ]** を選択します。

      ![プロパティ ウィンドウの SQL Server インスタンス名](media/ssms-tricks/nameinproperties.png)

### <a name="if-youre-connected-to-an-alias-or-availability-group-listener"></a>別名または可用性グループ リスナーに接続している場合 
別名または可用性グループ リスナーに接続している場合、その情報がオブジェクト エクスプローラーとプロパティに表示されます。 その場合、SQL Server の名前はすぐにはわからないことがあり、クエリを行う必要があります。 

1. SQL Server に接続します。
2. [新しいクエリ] ウィンドウを開きます。
3. 次の T-SQL コードをウィンドウに貼り付けます。 

  ```sql
   select @@Servername 
 ``` 
4. クエリの結果を見て、接続している SQL Server インスタンスの名前を確認します。 
    
    ![SQL Server 名を問い合わせる](media/ssms-tricks/queryservername.png)


