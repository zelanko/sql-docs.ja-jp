---
title: Visual Studio Code mssql 拡張機能を使用して、SQL Server の |Microsoft Docs
description: このチュートリアルでは、VS Code の mssql 拡張機能を使用する方法を示します。 この拡張機能を使用すると、VS Code で Transact-SQL スクリプトを編集し、実行できます。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: 9766ee75-32d3-4045-82a6-4c7968bdbaa6
ms.custom: sql-linux
ms.openlocfilehash: 3291767b4fa1f7b18e751661f9beeb0e061f8146
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37984334"
---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts-for-sql-server"></a>Visual Studio Code を使用して SQL Server の Transact-SQL スクリプトを作成し、実行する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このトピックでは、Visual Studio Code (VS Code) 用の **mssql** 拡張機能を使用して SQL Server データベースを開発する方法について説明します。

Visual Studio Code は、Linux、macOS、および Windows 用のグラフィカルなコード エディターで、拡張機能をサポートします。 [VS Code 用の **mssql** 拡張機能] により、SQL Server に接続し、 Transact-SQL (T-SQL) でクエリを行い、結果を表示することができます。

## <a name="install-vs-code"></a>VS Code をインストールします。
1. VS Code をまだインストールしていない場合[ダウンロードして、VS Code のインストール]コンピューターにします。

2. VS Code を起動します。

## <a name="install-the-mssql-extension"></a>Mssql 拡張機能をインストールします。
次の手順では、mssql 拡張機能をインストールする方法について説明します。 

1. キーを押して**CTRL + SHIFT + P** (または**F1**) で VS Code コマンド パレットを開きます。 

2. 選択**拡張機能のインストール**と種類**mssql**します。
   > [!TIP] 
   > Macos で、 **CMD**キーが等しく**CTRL** Linux と Windows キー。

2. [インストール] をクリックして**mssql**します。 
   
   <img src="./media/sql-server-linux-develop-use-vscode/vscode-extension.png" alt="Install the extension" style="width: 600px;"/>

3. **Mssql** 拡張機能は、最大 1 分間でインストールされます。 正常にインストールされたことを示すプロンプトを待ちます。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-install-success-notification.png" alt="Installation success notification" style="width: 600px;"/>

   > [!NOTE]
   > MacOS の場合、OpenSSL をインストールする必要があります。 これは、mssql 拡張機能で使用されている.Net Core の前提条件です。 [.Net Core のインストラクション] にある **前提条件のインストール** 手順に従ってください。 または、macOS ターミナルで次のコマンドを実行することもできます。
   >
   >   ```bash
   >   brew update
   >   brew install openssl
   >   ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
   >   ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
   >   ```
   
   > [!NOTE]
   > Windows 8.1、Windows Server 2012、またはより下位のバージョンをダウンロードしてインストールする必要があります、 [Windows 10 ユニバーサル C ランタイム]します。 ダウンロードして、zip ファイルを開きます。 (.Msu ファイル)、現在の OS 構成を対象とする、インストーラーを実行します。

## <a name="create-or-open-a-sql-file"></a>作成したり、SQL ファイルを開く

**mssql** 拡張機能を使用 mssql コマンドと T-SQL は、IntelliSense、エディターで、言語モードが に設定されているときに **SQL** です。

1. キーを押して**CTRL + N**します。 Visual Studio Code では、既定で新しい 'テキスト' ファイルを開きます。 

2. キーを押して**CTRL + K、M**を言語モードを変更および**SQL**します。 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-language-mode.png" alt="SQL language mode" style="width: 500px;" />

3. または、.sql というファイル拡張子を既存のファイルを開きます。 言語モードが自動的に**SQL** .sql 拡張子を持つファイル。  

## <a name="connect-to-sql-server"></a>SQL Server への接続

次の手順では、VS Code での SQL Server に接続する方法を示します。

1. VS Code で **Ctrl + Shift + P** (または **F1**) キーを押して、コマンド パレットを開きます。

2. 型**sql** mssql コマンドを表示します。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-commands.png" alt="mssql commands" style="width: 500px;" />
   

3. 選択、 **MS SQL: 接続**コマンド。 入力するだけ**sqlcon**キーを押します**ENTER**します。

4. 選択**接続プロファイルを作成する**します。 これは、SQL Server インスタンスの接続プロファイルを作成します。

5. 指示に従って、新しい接続プロファイルの接続プロパティを指定します。 それぞれの値を指定してから、**Enter** キーを押して続行します。 

   次の表では、接続プロファイルのプロパティについて説明します。

   | 設定 | 説明 |
   |-----|-----|
   | **サーバー名** | SQL Server インスタンス名。 このチュートリアルでは、使用**localhost**コンピューターにローカルの SQL Server インスタンスに接続します。 リモート SQL Server に接続する場合は、対象の SQL Server コンピューターまたは IP アドレスの名前を入力します。 SQL Server インスタンスのポートを指定する必要がある場合は、名前から分離すること、コンマを使用します。 たとえばポート 1401 で実行されているローカル サーバーの入力**localhost、1401**します。 |
   | **[省略可能]データベース名** | 使用するデータベースです。 このチュートリアルの目的を指定しないと、データベース キーを押して**ENTER**を続行します。 |
   | **ユーザー名** | サーバー上のデータベースにアクセス権を持つユーザーの名前を入力します。 このチュートリアルでは、既定値を使用して、 **SA**アカウント、SQL Server セットアップ中に作成します。 |
   | **パスワード (SQL ログイン)** | 指定したユーザーのパスワードを入力します。 | 
   | **パスワードを保存しますか?** | 型**はい**パスワードを保存します。 それ以外の場合、入力**いいえ**接続プロファイルを使用するたびにパスワードを求められます。 |
   | **[省略可能]このプロファイルの名前を入力します。** | 接続プロファイルの名前。 たとえば、プロファイルを名前**localhost プロファイル**します。 

   > [!Tip] 
   > 作成し、ユーザー設定ファイル (settings.json) で接続プロファイルを編集できます。 設定ファイルを選択して開きます** 基本設定**し**ユーザー設定**VS Code メニュー。 詳細については、次を参照してください。[接続プロファイルを管理します]。

6. **Esc** キーを押して、プロファイルが作成され、接続されていることを通知する情報メッセージを閉じます。

   > [!TIP]
   > 接続エラーが発生した場合のエラー メッセージから問題の診断にまず、**出力**VS Code でのパネル (選択**出力**で、**ビュー**メニュー)。 次に、[接続のトラブルシューティングに関する推奨事項]を確認します。

7. ステータス バーで、接続を確認します。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png" alt="Connection status" style="width: 500px;" />

## <a name="create-a-database"></a>データベースの作成

1. エディターで、次のように入力します。 **sql**編集可能なコード スニペットの一覧を表示します。 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-sql-snippets.png" alt="SQL snippets" style="width: 500px;" />

2. 選択**sqlCreateDatabase**します。

3. スニペットでは、次のように入力します。 **TutorialDB**データベース名。

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
   > Mssql 拡張機能コマンドのショートカット キー バインドをカスタマイズすることができます。 参照してください[ショートカットをカスタマイズします]。

## <a name="create-a-table"></a>テーブルの作成

1. エディター ウィンドウの内容を削除します。

2. キーを押して**F1**コマンド パレットを表示します。

3. 型**sql** SQL コマンドの種類を表示するためのコマンド パレットで**sqluse**の**MS SQL:Use データベース**コマンド。

4. クリックして**MS SQL:Use データベース**を選択し、 **TutorialDB**データベース。 これは、前のセクションで作成された新しいデータベースにコンテキストを変更します。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-use-database.png" alt="use database" style="width: 500px;" />

3. エディターで、次のように入力します。 **sql** 、スニペットを表示し、選択する**sqlCreateTable**キーを押します**入力**します。

4. スニペットでは、次のように入力します。**従業員**テーブル名。

5. キーを押して**タブ**、し、入力**dbo**スキーマ名。

   > [!NOTE]
   > スニペットを追加した後、VS コード エディターからフォーカスを変更することがなく、テーブルとスキーマの名前を入力してください。

6. 列名を変更**Column1**に**名前**と**Column2**に**場所**します。

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

1. 次の 4 つの行を挿入するには、次のステートメントを追加、**従業員**テーブル。 すべての行を選択します。

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
   > 入力するときに、T-SQL での IntelliSense のサポートを使用します。
   >   <img src="./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png" alt="TSQL IntelliSense" style="width: 500px;" />

2. キーを押して**CTRL + SHIFT + E**コマンドを実行します。 2 つの結果の表示を設定、**結果**ウィンドウ。 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png" alt="Results" style="width: 300px;" />

## <a name="view-and-save-the-result"></a>表示し、結果の保存

1. **ビュー**メニューの **エディターの切り替えグループ レイアウト**垂直または水平方向の分割のレイアウトに切り替える。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-split.png" alt="Vertical split" style="width: 500px;" />

2. をクリックして、**結果**と**メッセージ**パネル ヘッダー パネルを展開および折りたたみます。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png" alt="Toggle Messages" style="width: 500px;" />

   > [!TIP]
   > Mssql 拡張機能の既定の動作をカスタマイズできます。 参照してください[拡張機能のオプションをカスタマイズします]。

2. ズームインする 2 つ目の結果グリッドで最大化 [グリッド] アイコンをクリックします。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-maximize-grid.png" alt="Maximize grid" style="width: 500px;" />

   > [!NOTE]
   > T-SQL スクリプトがある 2 つまたは複数の結果グリッドと最大化アイコンが表示されます。

3. グリッド上でマウスの右ボタンをグリッドのコンテキスト メニューを開きます。 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-grid-context-menu.png" alt="Context menu" style="width: 500px;" />

4. 選択**すべて選択**します。

5. グリッドのコンテキスト メニューを開き、選択**JSON として保存**.json ファイルを結果を保存します。

6. JSON ファイルのファイル名を指定します。 このチュートリアルでは、入力**employees.json**します。

7. JSON ファイルが保存され、VS Code で開かれていることを確認します。

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-save-as-json.png" alt="Save as Json" style="width: 500px;" />

## <a name="next-steps"></a>次のステップ

実際のシナリオでは、保存および実行する必要のあるスクリプトを作成する場合があります (管理または大規模な開発プロジェクトの一部として) 以降。 ここでスクリプトを保存することができます、 **.sql**拡張機能。

T-SQL に慣れていない場合は、次を参照してください。[チュートリアル: TRANSACT-SQL ステートメントの作成]と[TRANSACT-SQL リファレンス (データベース エンジン)]します。

またはを使用して、mssql 拡張機能に影響する詳細については、次を参照してください。 [mssql 拡張機能プロジェクトの wiki]します。

VS Code の使用に関する詳細については、次を参照してください。、 [Visual Studio Code のドキュメント](https://code.visualstudio.com/docs)します。

[**mssql** VS Code 拡張機能]:https://aka.ms/mssql-marketplace
[ダウンロードして、VS Code のインストール]:https://code.visualstudio.com/Download
[.Net Core のインストラクション]:https://www.microsoft.com/net/core
[接続プロファイルを管理します]:https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles
[接続のトラブルシューティングに関する推奨事項]:./sql-server-linux-troubleshooting-guide.md#connection
[ショートカットをカスタマイズします]:https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts
[チュートリアル: Transact-SQL ステートメントの作成]:https://msdn.microsoft.com/library/ms365303.aspx
[TRANSACT-SQL リファレンス (データベース エンジン)]:https://msdn.microsoft.com/library/bb510741.aspx
[Visual Studio Code documentation]:https://code.visualstudio.com/docs
[Windows 10 ユニバーサル C ランタイム]:https://github.com/Microsoft/vscode-mssql/wiki/windows10-universal-c-runtime-requirement
[拡張機能のオプションをカスタマイズします]: https://github.com/Microsoft/vscode-mssql/wiki/customize-options
[mssql 拡張機能プロジェクトの wiki]: https://github.com/Microsoft/vscode-mssql/wiki
