---
title: Transact-SQL (SSMS) を使用して SSIS プロジェクトを配置する | Microsoft Docs
ms.date: 05/21/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: quick-start
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6bbcae0e5aea6521ad75401002d0a1488b5dbdf6
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34455165"
---
# <a name="deploy-an-ssis-project-from-ssms-with-transact-sql"></a>Transact-SQL を使用して SSMS から SSIS プロジェクトを配置する

このクイックスタートでは、SQL Server Management Studio (SSMS) を使用して SSIS カタログ データベースに接続し、Transact-SQL ステートメントを使用して SSIS プロジェクトを SSIS カタログに配置する方法を示します。 

SQL Server Management Studio は、SQL Server から SQL Database まで、SQL インフラストラクチャを管理するための統合環境です。 SSMS については、「[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)」をご覧ください。

## <a name="prerequisites"></a>Prerequisites

始める前に、最新バージョンの SQL Server Management Studio があることを確認します。 SSMS をダウンロードするには、「[SQL Server Management Studio (SSMS) のダウンロード](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)」を参照してください。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

このクイックスタートの情報を使用して、次のプラットフォームに SSIS プロジェクトを配置することができます。

-   SQL Server on Windows。

Azure SQL Database に SSIS パッケージを配置する場合は、このクイックスタートの情報を使用することはできません。 `catalog.deploy_project` ストアド プロシージャでは、ローカル ファイル システム内 (オンプレミス) の `.ispac` ファイルへのパスが必要です。 Azure でのパッケージの配置と実行の詳細については、「[SQL Server Integration Services ワークロードをクラウドにリフト アンド シフトする](lift-shift/ssis-azure-lift-shift-ssis-packages-overview.md)」を参照してください。

SQL Server on Linux に SSIS パッケージを配置する場合は、このクイックスタートの情報を使用することはできません。 Linux でのパッケージの実行の詳細については、「[Extract, transform, and load data on Linux with SSIS](../linux/sql-server-linux-migrate-ssis.md)」 (SSIS で Linux 上のデータの抽出、変換、読み込みを行う) を参照してください。

## <a name="connect-to-the-ssis-catalog-database"></a>SSIS カタログ データベースに接続する

SQL Server Management Studio を使って、SSIS カタログへの接続を確立します。 

1. SQL Server Management Studio を開きます。

2. **[サーバーへの接続]** ダイアログ ボックスに次の情報を入力します。

   | 設定       | 提案される値 | 詳細 | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバーの種類** | データベース エンジン | この値は必須です。 |
   | **サーバー名** | 完全修飾サーバー名 |  |
   | **[認証]** | SQL Server 認証 (SQL Server Authentication) | |
   | **Login** | サーバー管理者アカウント | このアカウントは、サーバーを作成したときに指定したアカウントです。 |
   | **Password** | サーバー管理者アカウントのパスワード | このパスワードは、サーバーを作成したときに指定したパスワードです。 |

3. **[接続]** をクリックします。 SSMS で [オブジェクト エクスプローラー] ウィンドウが開きます。 

4. オブジェクト エクスプローラーで、**[Integration Services カタログ]**、**[SSISDB]** の順に展開し、SSIS カタログ データベース内のオブジェクトを表示します。

## <a name="run-the-t-sql-code"></a>T-SQL コードを実行する
SSIS プロジェクトを配置するには、次の Transact-SQL コードを実行します。

1.  SSMS で、新しいクエリ ウィンドウを開き、次のコードを貼り付けます。

2.  システムの `catalog.deploy_project` ストアド プロシージャ内のパラメーター値を更新します。

3.  **SSISDB** が現在のデータベースであることを確認します。

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
