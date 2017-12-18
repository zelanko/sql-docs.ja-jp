---
title: "Transact-SQL (SSMS) を使用して SSIS プロジェクトを配置する | Microsoft Docs"
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
ms.openlocfilehash: 068f54a757e16c7b44760cbb69dee4a4d5cb70ef
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="deploy-an-ssis-project-from-ssms-with-transact-sql"></a>Transact-SQL を使用して SSMS から SSIS プロジェクトを配置する

このクイック スタートでは、SQL Server Management Studio (SSMS) を使用して、SSIS カタログ データベースに接続し、Transact-SQL ステートメントを使用して SSIS プロジェクトを SSIS カタログに配置する方法を示します。 

> [!NOTE]
> この記事で説明されているメソッドは、SSMS を使用して Azure SQL Database サーバーに接続するときには使用できません。 `catalog.deploy_project` ストアド プロシージャでは、ローカル ファイル システム内 (オンプレミス) の `.ispac` ファイルへのパスが必要です。

SQL Server Management Studio は、SQL Server から SQL Database まで、SQL インフラストラクチャを管理するための統合環境です。 SSMS について詳しくは、「[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)」をご覧ください。

## <a name="prerequisites"></a>前提条件

始める前に、最新バージョンの SQL Server Management Studio があることを確認します。 SSMS をダウンロードするには、「[SQL Server Management Studio (SSMS) のダウンロード](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)」をご覧ください。

## <a name="connect-to-the-ssis-catalog-database"></a>SSIS カタログ データベースに接続する

SQL Server Management Studio を使って、SSIS カタログへの接続を確立します。 

> [!NOTE]
> Azure SQL Database サーバーは、ポート 1433 でリッスンします。 企業のファイアウォール内から Azure SQL Database サーバーに接続しようとする場合、正常に接続するには、このポートを企業のファイアウォールで開ける必要があります。

1. SQL Server Management Studio を開きます。

2. **[サーバーへの接続]** ダイアログ ボックスに次の情報を入力します。

   | 設定       | 提案される値 | 詳細 | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバーの種類** | データベース エンジン | この値は必須です。 |
   | **サーバー名** | 完全修飾サーバー名 |  |
   | **[認証]** | SQL Server 認証 (SQL Server Authentication) | このクイック スタートでは、SQL 認証を使います。 |
   | **Login** | サーバー管理者アカウント | これはサーバーを作成したときに指定したアカウントです。 |
   | **Password** | サーバー管理者アカウントのパスワード | これはサーバーを作成したときに指定したパスワードです。 |

3. **[接続]**をクリックします。 SSMS で [オブジェクト エクスプローラー] ウィンドウが開きます。 

4. オブジェクト エクスプローラーで、**[Integration Services カタログ]**、**[SSISDB]** の順に展開し、SSIS カタログ データベース内のオブジェクトを表示します。

## <a name="run-the-t-sql-code"></a>T-SQL コードを実行する
SSIS プロジェクトを配置するには、次の Transact-SQL コードを実行します。

1.  SSMS で、新しいクエリ ウィンドウを開き、次のコードを貼り付けます。

2.  システムの `catalog.deploy_project` ストアド プロシージャ内のパラメーター値を更新します。

3.  SSISDB が現在のデータベースであることを確認します。

4.  スクリプトを実行します。

5. オブジェクト エクスプローラーで、必要に応じて **SSISDB** のコンテンツを更新し、配置したプロジェクトを確認します。

```sql
DECLARE @ProjectBinary AS varbinary(max)
DECLARE @operation_id AS bigint
SET @ProjectBinary =
    (SELECT * FROM OPENROWSET(BULK '<project_file_path>.ispac', SINGLE_BLOB) AS BinaryData)

EXEC catalog.deploy_project @folder_name = '<target_folder>',
    @project_name = '<project_name',
    @Project_Stream = @ProjectBinary,
    @operation_id = @operation_id out
```

## <a name="next-steps"></a>次の手順
- パッケージを配置する他の方法を検討します。
    - [SSMS を使用して SSIS パッケージを配置する](./ssis-quickstart-deploy-ssms.md)
    - [Transact-SQL (VS Code) を使用して SSIS パッケージを配置する](ssis-quickstart-deploy-tsql-vscode.md)
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
