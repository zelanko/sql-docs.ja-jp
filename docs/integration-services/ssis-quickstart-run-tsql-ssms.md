---
title: "TRANSACT-SQL (SSMS) で、SSIS パッケージを実行 |Microsoft ドキュメント"
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
ms.openlocfilehash: 1c656661f645ac9f5d1659800893290819525f39
ms.contentlocale: ja-jp
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-from-ssms-with-transact-sql"></a>Transact SQL を使用した SSMS から SSIS パッケージを実行します。
このクイック スタートでは、SQL Server Management Studio (SSMS) を使用して、SSIS カタログ データベースに接続し、SSIS カタログに格納されている SSIS パッケージを実行する TRANSACT-SQL ステートメントを使用する方法を示します。

SQL Server Management Studio は、SQL データベースに SQL Server から SQL のインフラストラクチャを管理するための統合環境です。 SSMS の詳細については、次を参照してください。 [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)です。

## <a name="prerequisites"></a>前提条件

開始する前に、最新バージョンの SQL Server Management Studio (SSMS) であることを確認します。 SSMS をダウンロードするを参照してください。[ダウンロード SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)です。

## <a name="connect-to-the-ssisdb-database"></a>SSISDB データベースへの接続します。

Azure SQL データベース サーバーで SSIS カタログへの接続を確立するために SQL Server Management Studio を使用します。 

> [!NOTE]
> Azure SQL データベース サーバーは、ポート 1433 でリッスンします。 企業のファイアウォール内での Azure SQL データベース サーバーに接続しようとしている場合、このポートが正常に接続するための企業ファイアウォールで開いていなければなりません。

1. SQL Server Management Studio を開きます。

2. **サーバーへの接続** ダイアログ ボックスで、次の情報を入力します。

   | 設定       | 推奨値 | 詳細 | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバーの種類** | データベース エンジン | この値は必須です。 |
   | **サーバー名** | 完全修飾サーバー名 | 名前がこの形式では、Azure SQL Database サーバーに接続する場合:`<server_name>.database.windows.net`です。 |
   | **[認証]** | SQL Server 認証 (SQL Server Authentication) | このクイック スタートでは、SQL 認証を使用します。 |
   | **Login** | サーバーの管理者アカウント | これは、サーバーを作成したときに指定したアカウントです。 |
   | **Password** | サーバーの管理者アカウントのパスワード | これは、サーバーを作成したときに指定したパスワードです。 |

3.  **[接続]**をクリックします。 SSMS では、オブジェクト エクスプ ローラー ウィンドウが開きます。

4. オブジェクト エクスプ ローラーで、 **Integration Services カタログ**順に展開**SSISDB** SSIS カタログ データベースでオブジェクトを表示します。

## <a name="run-a-package"></a>パッケージを実行します。
SSIS パッケージを実行する次の TRANSACT-SQL コードを実行します。

1.  SSMS では、新しいクエリ ウィンドウを開き、次のコードを貼り付けます。 (このコードは、によって生成されたコード、**スクリプト**オプション、**パッケージ実行**SSMS でのダイアログ ボックス)。

2.  内のパラメーター値を更新、`catalog.create_execution`システムのストアド プロシージャです。

3.  SSISDB が現在のデータベースであることを確認してください。

4.  スクリプトを実行します。

5. オブジェクト エクスプ ローラーでの内容を更新**SSISDB**必要に応じて配置したプロジェクトを確認します。

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
    - [Transact SQL (VS Code) を使用した SSIS パッケージを実行します。](ssis-quickstart-run-tsql-vscode.md)
    - [コマンド プロンプトから、SSIS パッケージを実行します。](./ssis-quickstart-run-cmdline.md)
    - [PowerShell での SSIS パッケージを実行します。](ssis-quickstart-run-powershell.md)
    - [C# を使用して、SSIS パッケージを実行します。](./ssis-quickstart-run-dotnet.md) 

