---
title: Transact-SQL (VS Code) を使用して SSIS プロジェクトを配置する | Microsoft Docs
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: quick-start
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f55f50ce68e2401da09794863b4d02f30b45c3df
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="deploy-an-ssis-project-from-visual-studio-code-with-transact-sql"></a>Transact-SQL を使用して Visual Studio Code から SSIS プロジェクトを配置する
このクイック スタートでは、Visual Studio Code を使用して、SSIS カタログ データベースに接続し、Transact-SQL ステートメントを使用して SSIS プロジェクトを SSIS カタログに配置する方法を示します。

> [!NOTE]
> この記事で説明されているメソッドは、VS Code を使用して Azure SQL Database サーバーに接続しているときには使用できません。 `catalog.deploy_project` ストアド プロシージャでは、ローカル ファイル システム内 (オンプレミス) の `.ispac` ファイルへのパスが必要です。

Visual Studio Code は、拡張機能をサポートする Windows、macOS、および Linux のコード エディターです。拡張機能には、Microsoft SQL Server、Azure SQL Database、または Azure SQL Data Warehouse に接続するための `mssql` 拡張機能が含まれます。 VS Code の詳細については、「[Visual Studio Code](https://code.visualstudio.com/)」を参照してください。

## <a name="prerequisites"></a>Prerequisites

開始する前に、最新バージョンの Visual Studio Code がインストールされ、`mssql` 拡張機能が読み込まれていることを確認します。 これらのツールをダウンロードするには、次のページを参照してください。
-   [Visual Studio Code のダウンロード](https://code.visualstudio.com/Download)
-   [mssql 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="set-language-mode-to-sql-in-vs-code"></a>VS Code で言語モードを SQL に設定する

`mssql` コマンドと T-SQL IntelliSense を有効にするには、Visual Studio Code で言語モードを **SQL** に設定します。

1. Visual Studio Code を開き、新しいウィンドウを開きます。 

2. ステータス バーの右下隅にある **[プレーン テキスト]** をクリックします。
 
3. 開いた **[言語モードの選択]** ドロップダウン メニューで、**[SQL]** を選択または入力して、**Enter** キーを押して言語モードを SQL に設定します。 

## <a name="connect-to-the-ssis-catalog-database"></a>SSIS カタログ データベースに接続する

Visual Studio Code を使用して、SSIS カタログへの接続を確立します。

> [!IMPORTANT]
> 続行する前に、サーバー、データベース、およびログイン情報が準備されていることを確認します。 接続プロファイル情報の入力を開始した後、Visual Studio Code からフォーカスを変更した場合は、接続プロファイルを作り直す必要があります。

1. VS Code で **Ctrl + Shift + P** (または **F1**) キーを押して、コマンド パレットを開きます。

2. 「**sqlcon**」と入力し、**Enter** キーを押します。

3. **Enter** キーを押して、**[接続プロファイルの作成]** を選択します。 この手順では、SQL Server インスタンスの接続プロファイルを作成します。

4. 指示に従って、新しい接続プロファイルの接続プロパティを指定します。 それぞれの値を指定してから、**Enter** キーを押して続行します。 

   | 設定       | 提案される値 | 詳細 |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバー名** | 完全修飾サーバー名 |  |
   | **データベース名** | **SSISDB** | 接続先となるデータベースの名前。 |
   | **[認証]** | SQL ログイン| このクイック スタートでは、SQL 認証を使います。 |
   | **User name** | サーバー管理者アカウント | これはサーバーを作成したときに指定したアカウントです。 |
   | **パスワード (SQL ログイン)** | サーバー管理者アカウントのパスワード | これはサーバーを作成したときに指定したパスワードです。 |
   | **パスワードを保存しますか?** | はい、いいえ | 毎回パスワードを入力したくない場合は、[はい] を選択します。 |
   | **このプロファイルの名前を入力してください** | **mySSISServer** などのプロファイル名 | プロファイル名が保存されていると、その後のログインの接続が高速化します。 | 

5. **Esc** キーを押して、プロファイルが作成され、接続されていることを通知する情報メッセージを閉じます。

6. ステータス バーで、接続を確認します。

## <a name="run-the-t-sql-code"></a>T-SQL コードを実行する
SSIS プロジェクトを配置するには、次の Transact-SQL コードを実行します。

1. **エディター** ウィンドウで、空のクエリ ウィンドウに次のクエリを入力します。

2. システムの `catalog.deploy_project` ストアド プロシージャ内のパラメーター値を更新します。

3. **Ctrl + Shift + E** キーを押してコードを実行し、プロジェクトを配置します。

```sql
DECLARE @ProjectBinary AS varbinary(max)
DECLARE @operation_id AS bigint
SET @ProjectBinary = (SELECT * FROM OPENROWSET(BULK '<project_file_path>.ispac', SINGLE_BLOB) AS BinaryData)

EXEC catalog.deploy_project @folder_name = '<target_folder>',
    @project_name = '<project_name',
    @Project_Stream = @ProjectBinary,
    @operation_id = @operation_id out
```

## <a name="next-steps"></a>次の手順
- パッケージを配置する他の方法を検討します。
    - [SSMS を使用して SSIS パッケージを配置する](./ssis-quickstart-deploy-ssms.md)
    - [Transact-SQL (SSMS) を使用して SSIS パッケージを配置する](./ssis-quickstart-deploy-tsql-ssms.md)
    - [コマンド プロンプトから SSIS パッケージを配置する](./ssis-quickstart-deploy-cmdline.md)
    - [PowerShell を使用して SSIS パッケージを配置する](ssis-quickstart-deploy-powershell.md)
    - [C# を使用して SSIS パッケージを配置する](./ssis-quickstart-deploy-dotnet.md) 
- 配置されたパッケージを実行します。 パッケージを実行するには、いくつかのツールおよび言語から選択することができます。 詳細については、次の記事をご覧ください。
    - [SSMS を使用して SSIS パッケージを実行する](./ssis-quickstart-run-ssms.md)
    - [Transact-SQL (SSMS) を使用して SSIS パッケージを実行する](./ssis-quickstart-run-tsql-ssms.md)
    - [Transact-SQL (VS Code) を使用して SSIS パッケージを実行する](ssis-quickstart-run-tsql-vscode.md)
    - [コマンド プロンプトから SSIS パッケージを実行する](./ssis-quickstart-run-cmdline.md)
    - [PowerShell を使用して SSIS パッケージを実行する](ssis-quickstart-run-powershell.md)
    - [C# を使用して SSIS パッケージを実行する](./ssis-quickstart-run-dotnet.md) 
