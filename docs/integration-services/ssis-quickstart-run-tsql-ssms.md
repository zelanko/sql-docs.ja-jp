---
title: "Transact-SQL (SSMS) を使用して SSIS パッケージを実行する | Microsoft Docs"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c4710f13f257f98326f0fa6c7f4550551bff3fd5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="run-an-ssis-package-from-ssms-with-transact-sql"></a>Transact-SQL を使用して SSMS から SSIS パッケージを実行する
このクイック スタートでは、SQL Server Management Studio (SSMS) を使用して、SSIS カタログ データベースに接続し、Transact-SQL ステートメントを使用して SSIS カタログに格納されている SSIS パッケージを実行する方法を示します。

SQL Server Management Studio は、SQL Server から SQL Database まで、SQL インフラストラクチャを管理するための統合環境です。 SSMS の詳細については、「[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)」を参照してください。

## <a name="prerequisites"></a>前提条件

開始する前に、最新バージョンの SQL Server Management Studio (SSMS) があることを確認します。 SSMS をダウンロードするには、「[SQL Server Management Studio (SSMS) のダウンロード](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)」を参照してください。

## <a name="connect-to-the-ssisdb-database"></a>SSISDB データベースに接続する

SQL Server Management Studio を使用して、Azure SQL Database サーバー上の SSIS カタログへの接続を確立します。 

> [!NOTE]
> Azure SQL Database サーバーは、ポート 1433 でリッスンします。 企業のファイアウォール内から Azure SQL Database サーバーに接続しようとする場合、正常に接続するには、このポートを企業のファイアウォールで開ける必要があります。

1. SQL Server Management Studio を開きます。

2. **[サーバーへの接続]** ダイアログ ボックスに次の情報を入力します。

   | 設定       | 提案される値 | 詳細 | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバーの種類** | データベース エンジン | この値は必須です。 |
   | **サーバー名** | 完全修飾サーバー名 | Azure SQL Database サーバーに接続する場合、名前は次の形式になります。`<server_name>.database.windows.net` |
   | **[認証]** | SQL Server 認証 (SQL Server Authentication) | このクイック スタートでは、SQL 認証を使用します。 |
   | **Login** | サーバー管理者アカウント | これはサーバーを作成したときに指定したアカウントです。 |
   | **Password** | サーバー管理者アカウントのパスワード | これはサーバーを作成したときに指定したパスワードです。 |

3.  **[接続]**をクリックします。 [オブジェクト エクスプローラー] ウィンドウで、SSMS を開きます。

4. オブジェクト エクスプローラーで、**[Integration Services カタログ]**、**[SSISDB]** の順に展開し、SSIS カタログ データベース内のオブジェクトを表示します。

## <a name="run-a-package"></a>パッケージの実行
SSIS パッケージを実行するには、次の Transact-SQL コードを実行します。

1.  SSMS で、新しいクエリ ウィンドウを開き、次のコードを貼り付けます  (このコードは、SSMS の **[パッケージ実行]** ダイアログ ボックスの **[スクリプト]** オプションによって生成されたコードです)。

2.  システムの `catalog.create_execution` ストアド プロシージャ内のパラメーター値を更新します。

3.  SSISDB が現在のデータベースであることを確認します。

4.  スクリプトを実行します。

5. オブジェクト エクスプローラーで、必要に応じて **SSISDB** のコンテンツを更新し、配置したプロジェクトを確認します。

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
- パッケージを実行する他の方法を検討します。
    - [SSMS を使用して SSIS パッケージを実行する](./ssis-quickstart-run-ssms.md)
    - [Transact-SQL (VS Code) を使用して SSIS パッケージを実行する](ssis-quickstart-run-tsql-vscode.md)
    - [コマンド プロンプトから SSIS パッケージを実行する](./ssis-quickstart-run-cmdline.md)
    - [PowerShell を使用して SSIS パッケージを実行する](ssis-quickstart-run-powershell.md)
    - [C# を使用して SSIS パッケージを実行する](./ssis-quickstart-run-dotnet.md) 
