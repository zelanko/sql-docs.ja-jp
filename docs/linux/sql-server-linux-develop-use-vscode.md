---
title: "For SQL Server、Visual Studio Code mssql 拡張機能を使用して |Microsoft ドキュメント"
description: "このチュートリアルでは、VS Code の mssql 拡張機能を使用する方法を示します。 この拡張機能を使用すると、編集し、VS コードで TRANSACT-SQL スクリプトを実行できます。"
author: erickangMSFT
ms.author: erickang
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9766ee75-32d3-4045-82a6-4c7968bdbaa6
ms.custom: H1Hack27Feb2017
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 2d8ba0dcd52de143cd935eab6e8bba95e924409d
ms.contentlocale: ja-jp
ms.lasthandoff: 10/10/2017

---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts-for-sql-server"></a>Visual Studio のコードを使用して作成し、SQL Server の TRANSACT-SQL スクリプトを実行

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このトピックの内容を使用する方法を示しています、 **mssql** Visual Studio Code (VS Code) を SQL Server データベースを開発するための拡張機能です。

Visual Studio のコードは、Linux、macOS、および拡張機能をサポートする Windows のグラフィカルなコード エディターです。 [**Mssql** VS Code 拡張機能]、SQL Server transact-sql (T-SQL)、クエリに接続し、結果を表示することができます。

## <a name="install-vs-code"></a>VS Code をインストールします。
1. VS Code をまだインストールしていない場合[をダウンロードしてインストール VS Code]コンピューターにします。

2. VS Code を開始します。

## <a name="install-the-mssql-extension"></a>Mssql 拡張機能をインストールします。
次の手順では、mssql 拡張機能をインストールする方法について説明します。 

1. キーを押して**CTRL + SHIFT + P** (または**F1**) VS コードでコマンド パレットを開きます。 

2. 選択**インストール拡張**および種類**mssql**です。
   > [!TIP] 
   > MacOS などの**CMD**キーに相当**CTRL** Linux と Windows のキー。

2. [インストール] をクリックして**mssql**です。 
   
   <img src="./media/sql-server-linux-develop-use-vscode/vscode-extension.png" alt="Install the extension" style="width: 600px;"/>

3. **Mssql**拡張機能は、最大 1 分間をインストールします。 正常にインストールされていることを示すプロンプトを待ちます。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-install-success-notification.png" alt="Installation success notification" style="width: 600px;"/>

   > [!NOTE]
   > MacOS、OpenSSL をインストールする必要があります。 これは、.Net の前提コア mssql 拡張機能で使用します。 以下の**前提条件をインストール**の手順を[.Net 指示をコア]です。 または、macOS ターミナルで、次のコマンドを実行することができます。
   >
   >   ```bash
   >   brew update
   >   brew install openssl
   >   ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
   >   ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
   >   ```
   
   > [!NOTE]
   > Windows 8.1、Windows Server 2012 または下位のバージョンをダウンロードしてインストールする必要があります、 [Windows 10 の Universal C Runtime]です。 ダウンロードして、zip ファイルを開きます。 現在の OS 構成をターゲットとするインストーラー (.msu ファイル) を実行しています。

## <a name="create-or-open-a-sql-file"></a>作成または SQL ファイルを開く

**Mssql**拡張機能を使用 mssql コマンドと T-SQL は、IntelliSense、エディターで、言語モードが に設定されているときに**SQL**です。

1. キーを押して**CTRL + N**です。 Visual Studio のコードは、既定で新しい 'プレーン テキスト' ファイルを開きます。 

2. キーを押して**CTRL + K、M**に言語モードを変更および**SQL**です。 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-language-mode.png" alt="SQL language mode" style="width: 500px;" />

3. 代わりに、.sql ファイルの拡張子を持つ既存のファイルを開きます。 自動的には、言語モードが**SQL** .sql 拡張子を持つファイルです。  

## <a name="connect-to-sql-server"></a>SQL Server に接続します。

次の手順では、VS コードでの SQL Server に接続する方法を示します。

1. VS Code でキーを押して**CTRL + SHIFT + P** (または**F1**) コマンド パレットを開きます。

2. 型**sql** mssql コマンドを表示します。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-commands.png" alt="mssql commands" style="width: 500px;" />
   

3. 選択、 **MS SQL: 接続**コマンド。 入力する**sqlcon**とキーを押します**ENTER**です。

4. 選択**接続プロファイルの作成**です。 これは、SQL Server インスタンスの接続プロファイルを作成します。

5. 指示に従って、新しい接続プロファイルの接続プロパティを指定します。 それぞれの値を指定してからキーを押します。 **ENTER**を続行します。 

   次の表では、接続プロファイルのプロパティについて説明します。

   | 設定 | Description |
   |-----|-----|
   | **サーバー名** | SQL Server インスタンス名。 このチュートリアルでは、使用**localhost**コンピューターにローカルの SQL Server インスタンスに接続します。 リモートの SQL Server への接続している場合、は、対象の SQL Server コンピューターまたは IP アドレスの名前を入力します。 |
   | **[オプション]データベース名** | 使用するデータベースです。 このチュートリアルの目的を指定しないと、データベース キーを押して**ENTER**を続行します。 |
   | **ユーザー名** | サーバー上のデータベースにアクセス権を持つユーザーの名前を入力します。 このチュートリアルでは、既定値を使用して**SA**アカウント、SQL Server のセットアップ中に作成します。 |
   | **パスワード (SQL ログイン)** | 指定したユーザーのパスワードを入力します。 | 
   | **パスワードを保存しますか。** | 型**はい**パスワードを保存します。 それ以外の場合、入力**いいえ**を求めるには、パスワード、接続プロファイルが使用されるたびにします。 |
   | **[オプション]このプロファイルの名前を入力してください。** | 接続プロファイルの名前。 たとえば、プロファイルを名前でした**localhost プロファイル**です。 

   > [!Tip] 
   > 作成してユーザー設定ファイル (settings.json) で接続プロファイルを編集します。 選択して、設定ファイルを開きます**優先**し**ユーザー設定**VS Code メニューでします。 詳細については、次を参照してください。[接続プロファイルの管理]です。

6. キーを押して、 **ESC**プロファイルが作成され、接続されていることを通知する情報メッセージを閉じるにはキー。

   > [!TIP]
   > 接続エラーが発生する場合は、まず、内のエラー メッセージから、問題を診断、**出力**VS Code のパネル (選択**出力**上、**ビュー**メニュー)。 次に、[接続のトラブルシューティングに関する推奨事項]を確認します。

7. ステータス バーで、接続を確認します。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png" alt="Connection status" style="width: 500px;" />

## <a name="create-a-database"></a>データベースを作成します。

1. エディターで、次のように入力します。 **sql**編集可能なコード スニペットの一覧を表示します。 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-sql-snippets.png" alt="SQL snippets" style="width: 500px;" />

2. 選択**sqlCreateDatabase**です。

3. スニペットは、入力**TutorialDB**データベース名にします。

   ```sql
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
   
4. キーを押して**CTRL + SHIFT + E** TRANSACT-SQL コマンドを実行します。 クエリ ウィンドウで、結果を表示します。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-create-database-messages.png" alt="create database messages" style="width: 500px;" />

   > [!TIP]
   > Mssql 拡張機能コマンドのショートカット キー バインディングをカスタマイズすることができます。 参照してください[ショートカットをカスタマイズする]です。

## <a name="create-a-table"></a>テーブルの作成

1. エディター ウィンドウの内容を削除します。

2. キーを押して**F1**コマンド パレットを表示します。

3. 型**sql** SQL コマンドまたは型を表示するコマンド パレットで**sqluse**の**MS SQL:Use データベース**コマンド。

4. をクリックして**MS SQL:Use データベース**を選択し、 **TutorialDB**データベース。 これは、前のセクションで作成した新しいデータベースをコンテキストを変更します。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-use-database.png" alt="use database" style="width: 500px;" />

3. エディターで、次のように入力します。 **sql** 、スニペットを表示し、選択する**sqlCreateTable**とキーを押します**入力**です。

4. このスニペットでは、入力**従業員**テーブル名をします。

5. キーを押して**タブ**、し、入力**dbo**スキーマ名。

   > [!NOTE]
   > スニペットを追加した後は、VS コード エディターからフォーカスを変更することがなく、テーブル名とスキーマ名を入力してください。

6. 列名の変更**Column1**に**名前**と**Column2**に**場所**です。

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

7. キーを押して**CTRL + SHIFT + E**テーブルを作成します。

## <a name="insert-and-query"></a>挿入とクエリ

1. 4 行を挿入する次のステートメントを追加、**従業員**テーブル。 すべての行を選択します。

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
   > 入力したときに、T-SQL で IntelliSense のアシスタンスを使用します。
   >   <img src="./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png" alt="TSQL IntelliSense" style="width: 500px;" />

2. キーを押して**CTRL + SHIFT + E**コマンドを実行します。 2 つの結果の表示を設定、**結果**ウィンドウです。 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png" alt="Results" style="width: 300px;" />

## <a name="view-and-save-the-result"></a>表示し、結果の保存

1. **ビュー**メニューの **エディターの切り替えグループ レイアウト**垂直または水平方向の分割レイアウトに切り替える。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-split.png" alt="Vertical split" style="width: 500px;" />

2. をクリックして、**結果**と**メッセージ**パネル ヘッダー パネルを展開したり、折りたたんだりします。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png" alt="Toggle Messages" style="width: 500px;" />

   > [!TIP]
   > Mssql 拡張機能の既定の動作をカスタマイズすることができます。 参照してください[拡張子のオプションをカスタマイズ]です。

2. ズーム インする 2 番目の結果グリッドで最大にする [グリッド] アイコンをクリックします。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-maximize-grid.png" alt="Maximize grid" style="width: 500px;" />

   > [!NOTE]
   > T-SQL スクリプトは 2 つ以上の結果グリッドと最大化 アイコンが表示されます。

3. グリッドでマウスの右ボタンで、グリッドのコンテキスト メニューを開きます。 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-grid-context-menu.png" alt="Context menu" style="width: 500px;" />

4. 選択**すべて選択**です。

5. グリッドのコンテキスト メニューを開き、選択**JSON として保存**.json ファイルを結果を保存します。

6. JSON ファイルのファイル名を指定します。 このチュートリアルでは、次のように入力します。 **employees.json**です。

7. JSON ファイルが保存され、VS コードで開かれていることを確認します。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-save-as-json.png" alt="Save as Json" style="width: 500px;" />

## <a name="next-steps"></a>次の手順

現実のシナリオでは、保存および実行する必要のあるスクリプトを作成する場合があります (管理用または大規模な開発プロジェクトの一部として) 以降。 ここを使用してスクリプトを保存することができます、 **.sql**拡張機能です。

T-SQL を新しい場合を参照してください[チュートリアル: TRANSACT-SQL ステートメントの記述]と[TRANSACT-SQL リファレンス (データベース エンジン)]です。

使用してまたは mssql 拡張機能に影響を与えるの詳細については、次を参照してください。 [mssql 拡張機能プロジェクト wiki]です。

VS Code を使用する方法については、次を参照してください。、 [Visual Studio のコード ドキュメント](https://code.visualstudio.com/docs)です。

[* * mssql * * の VS Code 拡張機能]:https://aka.ms/mssql-marketplace
[をダウンロードしてインストール VS Code]:https://code.visualstudio.com/Download
[.Net 指示をコア]:https://www.microsoft.com/net/core
[接続プロファイルの管理]:https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles
[接続のトラブルシューティングに関する推奨事項]:./sql-server-linux-troubleshooting-guide.md#connection
[ショートカットをカスタマイズする]:https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts
[チュートリアル: TRANSACT-SQL ステートメントの記述]:https://msdn.microsoft.com/library/ms365303.aspx
[TRANSACT-SQL リファレンス (データベース エンジン)]:https://msdn.microsoft.com/library/bb510741.aspx
[Visual Studio Code documentation]:https://code.visualstudio.com/docs
[Windows 10 の Universal C Runtime]:https://github.com/Microsoft/vscode-mssql/wiki/windows10-universal-c-runtime-requirement
[拡張子のオプションをカスタマイズ]: https://github.com/Microsoft/vscode-mssql/wiki/customize-options
[mssql 拡張機能プロジェクト wiki]: https://github.com/Microsoft/vscode-mssql/wiki

