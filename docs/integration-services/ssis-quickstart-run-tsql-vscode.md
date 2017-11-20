---
title: "Transact SQL (VS Code) を使用した SSIS パッケージを実行 |Microsoft ドキュメント"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: a912bf7f7944d4af3d41c5596e67aa77f3214112
ms.contentlocale: ja-jp
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-from-visual-studio-code-with-transact-sql"></a>Transact SQL を使用した Visual Studio のコードから SSIS パッケージを実行します。
このクイック スタートでは、Visual Studio のコードを使用して、SSIS カタログ データベースに接続し、SSIS カタログに格納されている SSIS パッケージを実行する TRANSACT-SQL ステートメントを使用する方法を示します。

Visual Studio のコードは、Windows、macOS、およびなど、拡張機能をサポートする Linux のコード エディター、 `mssql` Microsoft SQL Server、Azure SQL データベース、または Azure SQL Data Warehouse に接続するための拡張機能です。 VS Code の詳細については、次を参照してください。 [Visual Studio Cod](https://code.visualstudio.com/)です。

## <a name="prerequisites"></a>前提条件

開始する前に確認の最新バージョンの Visual Studio Code のインストールし、読み込まれたが、`mssql`拡張機能です。 これらのツールをダウンロードするには、次のページを参照してください。
-   [Visual Studio Code のダウンロード](https://code.visualstudio.com/Download)
-   [mssql 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="set-language-mode-to-sql-in-vs-code"></a>VS コードでの sql 言語モードに設定します。

有効にする`mssql`セット言語モードに設定されているコマンドと T-SQL は、IntelliSense、 **SQL** Visual Studio のコードにします。

1. Visual Studio のコードを開き、新しいウィンドウを開きます。 

2. をクリックして**プレーン テキスト**ステータス バーの右下隅にします。

3. **言語の選択 モード**ドロップダウン メニューが開き、選択または入力する**SQL**、キーを押します**ENTER**言語モードは SQL に設定します。 

## <a name="connect-to-the-ssis-catalog-database"></a>SSIS カタログ データベースへの接続します。

Visual Studio のコードを使用すると、SSIS カタログへの接続を確立できます。

> [!IMPORTANT]
> 続行する前に、サーバー、データベース、および準備のログイン情報があることになっていることを確認します。 接続プロファイル情報の入力を開始した後、Visual Studio のコードから、フォーカスを変更した場合は、接続プロファイルの作成を再起動する必要です。

1. VS Code でキーを押して**CTRL + SHIFT + P** (または**F1**) コマンド パレットを開きます。

2. 型**sqlcon**とキーを押します**ENTER**です。

3. キーを押して**ENTER**を選択する**接続プロファイルの作成**です。 この手順では、SQL Server インスタンスの接続プロファイルを作成します。

4. 指示に従って、新しい接続プロファイルの接続プロパティを指定します。 それぞれの値を指定してからキーを押します。 **ENTER**を続行します。 

   | 設定       | 推奨値 | 詳細 |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバー名** | 完全修飾サーバー名 | 名前がこの形式では、Azure SQL Database サーバーに接続する場合:`<server_name>.database.windows.net`です。 |
   | **データベース名** | **SSISDB** | 接続先データベースの名前。 |
   | **[認証]** | SQL ログイン| このクイック スタートでは、SQL 認証を使用します。 |
   | **ユーザー名** | サーバーの管理者アカウント | これは、サーバーを作成したときに指定したアカウントです。 |
   | **パスワード (SQL ログイン)** | サーバーの管理者アカウントのパスワード | これは、サーバーを作成したときに指定したパスワードです。 |
   | **パスワードを保存しますか。** | はい、いいえ | 毎回パスワードを入力したくない場合は、[はい] を選択します。 |
   | **このプロファイルの名前を入力してください。** | プロファイル名など、 **mySSISServer** | 保存されているプロファイル名には、その後のログインの接続が高速化します。 | 

5. キーを押して、 **ESC**プロファイルが作成され、接続されていることを通知する情報メッセージを閉じるにはキー。

6. ステータス バーで、接続を確認します。

## <a name="run-the-t-sql-code"></a>T-SQL コードを実行します。
SSIS パッケージを実行する次の TRANSACT-SQL コードを実行します。

1. **エディター**ウィンドウで、空のクエリ ウィンドウに次のクエリを入力します。 (このコードは、によって生成されたコード、**スクリプト**オプション、**パッケージ実行**SSMS でのダイアログ ボックス)。

2. 内のパラメーター値を更新、`catalog.create_execution`システムのストアド プロシージャです。

3. キーを押して**CTRL + SHIFT + E**コードを実行してパッケージを実行します。

```sql
Declare @execution_id bigint
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx',
    @execution_id=@execution_id OUTPUT,
    @folder_name=N'Deployed Projects',
      @project_name=N'Integration Services Project1',
    @use32bitruntime=False,
      @reference_id=Null
Select @execution_id
DECLARE @var0 smallint = 1
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,
    @object_type=50,
      @parameter_name=N'LOGGING_LEVEL',
      @parameter_value=@var0
EXEC [SSISDB].[catalog].[start_execution] @execution_id
GO
```

## <a name="next-steps"></a>次の手順
- パッケージを実行するには、その他の方法を検討してください。
    - [SSMS での SSIS パッケージを実行します。](./ssis-quickstart-run-ssms.md)
    - [TRANSACT-SQL (SSMS) で、SSIS パッケージを実行します。](./ssis-quickstart-run-tsql-ssms.md)
    - [コマンド プロンプトから、SSIS パッケージを実行します。](./ssis-quickstart-run-cmdline.md)
    - [PowerShell での SSIS パッケージを実行します。](ssis-quickstart-run-powershell.md)
    - [C# を使用して、SSIS パッケージを実行します。](./ssis-quickstart-run-dotnet.md) 

