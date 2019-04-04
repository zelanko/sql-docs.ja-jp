---
title: Visual Studio Code mssql 拡張機能を使用して、SQL Server on Linux の |Microsoft Docs
description: Visual Studio Code 用 mssql 拡張機能を使用して、編集を Linux 上の SQL Server の TRANSACT-SQL スクリプトを実行します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/18/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 9766ee75-32d3-4045-82a6-4c7968bdbaa6
ms.custom: sql-linux
ms.openlocfilehash: 583c7ac13b49370b333e80568c4b52885b58dcf3
ms.sourcegitcommit: 78e32562f9c1fbf2e50d3be645941d4aa457e31f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54100567"
---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts-on-linux"></a>Visual Studio Code を使用して作成し、Linux での TRANSACT-SQL スクリプトを実行するには

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、使用する方法を示します、 *mssql* for Linux での SQL Server データベースの開発に Visual Studio Code 拡張機能。

## <a name="install-and-start-visual-studio-code"></a>インストールして Visual Studio Code を起動

Visual Studio Code は、Linux、macOS、および Windows 用のグラフィカルなコード エディターで、拡張機能をサポートします。 

1. [ダウンロードして Visual Studio Code のインストール]コンピューターにします。
   
1. Visual Studio Code を起動します。
   
   >[!NOTE]
   >Xrdp のリモート デスクトップ セッションを介して接続しているときに Visual Studio Code が起動しない場合は、[VS Code の XRDP の使い方を接続すると、Ubuntu 上で動作していない](https://github.com/Microsoft/vscode/issues/3451)を参照してください。

## <a name="install-the-mssql-extension"></a>Mssql 拡張機能をインストールします。

[Visual Studio Code 用 mssql 拡張機能]を SQL Server に接続することができますが transact-sql (T-SQL) クエリを実行し、結果を表示します。

1. Visual Studio code では、次のように選択します**ビュー** > **コマンド パレット**、またはキーを押します**Ctrl**+**Shift** 。+**P**、またはキーを押します**F1**を開く、**コマンド パレット**します。 
   
1. **コマンド パレット**、**拡張機能。拡張機能をインストール**ドロップダウン リストから。 
   
1. **拡張** ウィンドウで「 *mssql*します。
   
1. 選択、 **SQL Server (mssql)** 拡張機能、および選択**インストール**します。 
   
   ![Mssql 拡張機能をインストールします。](./media/sql-server-linux-develop-use-vscode/vscode-extension.png)   
   
1. インストールが完了すると、選択**再読み込み**拡張機能を有効にします。 

## <a name="create-or-open-a-sql-file"></a>作成したり、SQL ファイルを開く

Mssql 拡張機能により、mssql コマンドと T-SQL IntelliSense、コード エディターで言語モードが 設定されている**SQL**します。

1. 選択**ファイル** > **新しいファイル**またはキーを押します**Ctrl**+**N**します。 Visual Studio Code では、既定で新しいテキスト ファイルを開きます。 

1. 選択**プレーン テキスト**下部のステータス バー上でキーを押して**Ctrl**+**K** > **M**を選択します **。SQL**言語ドロップダウン リストから。 
   
   ![SQL 言語モード](./media/sql-server-linux-develop-use-vscode/vscode-language-mode.png)   
   
持つ既存のファイルを開いた場合、 *.sql*ファイルの拡張機能、言語モードは SQL には設定されて自動的にします。  

## <a name="connect-to-sql-server"></a>SQL Server への接続

接続プロファイルを作成し、SQL Server に接続するこれらの手順に従います。

> [!TIP] 
> 作成し、ユーザー設定ファイルで接続プロファイルを編集できます (*settings.json*)。 設定ファイルを開くには、次のように選択します。**ファイル** > **設定** > **設定**します。 詳細については、[接続プロファイルの管理]を参照してください。
   
1. キーを押して**Ctrl**+**Shift**+**P**または**F1**を開く、**コマンド パレット**. 
   
1. 型*sql* mssql を表示するコマンド、または型*sqlcon*、し、 **MS SQL:接続**ドロップダウン リストから。
   
   ![mssql コマンド](./media/sql-server-linux-develop-use-vscode/vscode-commands.png)   
   
   >[!NOTE]
   >SQL ファイルに作成した空の SQL ファイルなどが必要、コード エディターにフォーカスを mssql コマンドを実行する前にです。 

1. 選択**接続プロファイルの作成**SQL Server の新しい接続プロファイルを作成します。
   
1. 指示に従って、新しい接続プロファイルのプロパティを指定します。 それぞれの値を指定するには、後にキーを押して **」と入力**を続行します。 
   
   1. **サーバー名または ADO 接続文字列**:SQL Server のインスタンス名を指定します。 使用*localhost*ローカル コンピューターに SQL Server インスタンスに接続します。 リモート SQL Server に接続するには、SQL Server では、ターゲットの名前または IP アドレスを入力します。 ポートを指定する必要がある場合は、コンマを使用して、名前から分離することです。 たとえば、ポート 1401 で実行されているローカル サーバーは、次のように入力します。 *localhost、1401*します。 
      
      >[!NOTE]
      >データベースここでは、キーを押してを ADO 接続文字列を入力することもできます。 **」と入力**、必要に応じて名前、接続プロファイルとキーを押して **」と入力**もう一度に接続し、プロファイルを作成します。 
      
   1. **データベース名**(省略可能)。使用するデータベースです。 新しいデータベースを作成するには、データベースを指定しない名、およびキーを押して **」と入力**を続行します。 
      
   1. **認証の種類**:キーを押して**Enter**を選択する**SQL ログイン**します。 
      
   1. **ユーザー名**:サーバー上のデータベースにアクセス権を持つユーザーの名前を入力します。
      
   1. **パスワード**:指定したユーザーのパスワードを入力します。
      
   1. **パスワードの保存**:キーを押して **」と入力**を選択する **[はい]** し、パスワードを保存します。 選択**いいえ**接続プロファイルを使用するたびにパスワードを求められます。 
      
   1. **プロファイル名**(省略可能)。接続プロファイルの名前を入力します。 *localhost プロファイル*します。 
   
   選択した後**Enter**、Visual Studio Code が接続プロファイルが作成され、SQL Server に接続します。 
   
   > [!TIP]
   > 内のエラー メッセージから問題を診断しよう、接続に失敗した場合、**出力**Visual Studio Code でパネル。 開くには、**出力**パネルで、**ビュー** > **出力**します。 確認することも、[接続のトラブルシューティングに関する推奨事項]します。
   
1. 下部のステータス バーで、接続を確認します。
   
  ![[接続状態]](./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png)   
   
## <a name="create-a-sql-database"></a>SQL database を作成します。

1. 前に開始する新しい SQL ファイルに次のように入力します。 *sql*編集可能なコード スニペットの一覧を表示します。 

  ![SQL スニペット](./media/sql-server-linux-develop-use-vscode/vscode-sql-snippets.png)   
   
1. 選択**sqlCreateDatabase**します。
   
1. スニペットでは、置き換える`DatabaseName`で`TutorialDB`:
   
   ```sql
   -- Create a new database called 'TutorialDB'
   -- Connect to the 'master' database to run this snippet
   USE master
   GO
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
   CREATE DATABASE [TutorialDB]
   GO
   ```
   
1. キーを押して**Ctrl**+**Shift**+**E** TRANSACT-SQL コマンドを実行します。 クエリ ウィンドウで、結果を表示します。
   
  ![データベースのメッセージを作成します。](./media/sql-server-linux-develop-use-vscode/vscode-create-database-messages.png)   
   
> [!TIP]
> Mssql コマンドのショートカット キーをカスタマイズすることができます。 参照してください[ショートカットをカスタマイズする]します。

## <a name="create-a-table"></a>テーブルの作成

1. コード エディター ウィンドウの内容を削除します。
   
1. キーを押して**Ctrl**+**Shift**+**P**または**F1**を開く、**コマンド パレット**. 
   
1. 型*sql* mssql を表示するコマンド、または型*sqluse*を選び、 **MS SQL:Use データベース**コマンド。
   
1. 新しい**TutorialDB**データベース。 
   
   ![データベースの使用](./media/sql-server-linux-develop-use-vscode/vscode-use-database.png)   
   
1. コード エディターで次のように入力します。 *sql* 、スニペットを表示するには、次のように選択します。 **sqlCreateTable**、およびキーを押します **」と入力**します。
   
1. スニペットでは、次のように入力します。*従業員*テーブル名と*dbo*スキーマ名。
   
1. 次のコードに示すように、列を作成します。
   
   ```sql
   -- Create a new table called 'Employees' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Employees', 'U') IS NOT NULL
   DROP TABLE dbo.Employees
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Employees
   (
      EmployeesId        INT    NOT NULL   PRIMARY KEY, -- primary key column
      Name      [NVARCHAR](50)  NOT NULL,
      Location   [NVARCHAR](50)  NOT NULL
   );
   GO
   ```
   
1. キーを押して**Ctrl**+**Shift**+**E**テーブルを作成します。

## <a name="insert-and-query"></a>挿入とクエリ

1. 次の 4 つの行を挿入するには、次のステートメントを追加、**従業員**テーブル。 

   ```sql
   -- Insert rows into table 'Employees'
   INSERT INTO Employees
      ([EmployeesId],[Name],[Location])
   VALUES
      ( 1, N'Jared', N'Australia'),
      ( 2, N'Nikita', N'India'),
      ( 3, N'Tom', N'Germany'),
      ( 4, N'Jake', N'United States')   
   GO   
   -- Query the total count of employees
   SELECT COUNT(*) as EmployeeCount FROM dbo.Employees;
   -- Query all employee information
   SELECT e.EmployeesId, e.Name, e.Location 
   FROM dbo.Employees as e
   GO
   ```
   
   > [!TIP]
   > 入力するときに、ステートメントを完了させるために T-SQL IntelliSense を使用します。
   >![T-SQL での IntelliSense](./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png)   
   
1. キーを押して**Ctrl**+**Shift**+**E**コマンドを実行します。 2 つの結果の表示を設定、**結果**ウィンドウ。 
   
   ![[結果]](./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png)   

## <a name="view-and-save-the-result"></a>表示し、結果の保存
   
1. 選択**ビュー** > **エディター レイアウト** > **レイアウトの反転**垂直または水平方向の分割のレイアウトに切り替える。
   
1. 選択、**結果**と**メッセージ**パネル、パネルを展開および折りたたむヘッダー。
   
   ![ヘッダーの切り替え](./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png)   
   
   > [!TIP]
   > Mssql 拡張機能の既定の動作をカスタマイズできます。 参照してください[拡張機能のオプションのカスタマイズ]します。
   
1. これらの結果を拡大する 2 つ目の結果グリッドで最大化 [グリッド] アイコンを選択します。
   
   ![グリッドを最大化します。](./media/sql-server-linux-develop-use-vscode/vscode-maximize-grid.png)   
   
   > [!NOTE]
   > T-SQL スクリプトが 2 つまたは複数の結果のグリッドを生成するとき、最大化アイコンを表示します。
   
1. グリッドを右クリックして、グリッドのコンテキスト メニューを開きます。 
   
   ![コンテキスト メニュー](./media/sql-server-linux-develop-use-vscode/vscode-grid-context-menu.png)   
   
1. 選択**すべて選択**します。
   
1. グリッド コンテキスト メニューを開き、もう一度選択**JSON として保存**、結果を保存する、 *.json*ファイル。
   
1. JSON ファイルのファイル名を指定します。 
   
1. JSON ファイルを保存し、Visual Studio Code で開きますを確認します。
   
   ![JSON として保存します。](./media/sql-server-linux-develop-use-vscode/vscode-save-as-json.png)   

保存し、管理や、大規模な開発プロジェクトのため、後で SQL スクリプトを実行する必要がある場合を使用してスクリプトを保存、 *.sql*拡張機能。

## <a name="next-steps"></a>次の手順

T-SQL に慣れていない場合は、次を参照してください。[チュートリアル:TRANSACT-SQL ステートメントを記述します。]と[TRANSACT-SQL リファレンス (データベース エンジン)]します。

またはを使用して、mssql 拡張機能に影響する詳細については、、 [mssql 拡張機能プロジェクトの wiki]を参照してください。

Visual Studio Code の使用に関する詳細については、、 [Visual Studio Code のドキュメント](https://code.visualstudio.com/docs)を参照してください。

[Visual Studio Code 用 mssql 拡張機能]:https://aka.ms/mssql-marketplace
[ダウンロードして Visual Studio Code のインストール]:https://code.visualstudio.com/Download
[.Net Core instructions]:https://www.microsoft.com/net/core
[接続プロファイルの管理]:https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles
[接続のトラブルシューティングに関する推奨事項]:./sql-server-linux-troubleshooting-guide.md#connection
[ショートカットをカスタマイズする]:https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts
[チュートリアル:TRANSACT-SQL ステートメントを記述します。]:https://docs.microsoft.com/sql/t-sql/tutorial-writing-transact-sql-statements
[TRANSACT-SQL リファレンス (データベース エンジン)]:https://docs.microsoft.com/sql/t-sql/language-reference
[Visual Studio Code documentation]:https://code.visualstudio.com/docs
[Windows 10 Universal C Runtime]:https://github.com/Microsoft/vscode-mssql/wiki/windows10-universal-c-runtime-requirement
[拡張機能のオプションのカスタマイズ]: https://github.com/Microsoft/vscode-mssql/wiki/customize-options
[mssql 拡張機能プロジェクトの wiki]: https://github.com/Microsoft/vscode-mssql/wiki
