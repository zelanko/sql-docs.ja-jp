---
title: "SSIS プロジェクトを TRANSACT-SQL (SSMS) の展開 |Microsoft ドキュメント"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: e97fb20f5b0ee10aa3e5de690676b7e0bb797b4c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/22/2017

---
# <a name="deploy-an-ssis-project-from-ssms-with-transact-sql"></a>Transact SQL を使用した SSMS から SSIS プロジェクトを配置します。

このクイック スタートでは、SQL Server Management Studio (SSMS) を使用して、SSIS カタログ データベースに接続し、TRANSACT-SQL ステートメントを使用して、SSIS プロジェクトを SSIS カタログに配置する方法を示します。 

> [!NOTE]
> SSMS で Azure SQL データベース サーバーに接続するときに、この記事で説明されているメソッドを使用できません。 `catalog.deploy_project`ストアド プロシージャへのパスが必要ですが、 `.ispac` (オンプレミス) ローカル ファイル システム内のファイルです。

SQL Server Management Studio は、SQL データベースに SQL Server から SQL のインフラストラクチャを管理するための統合環境です。 SSMS の詳細については、次を参照してください。 [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)です。

## <a name="prerequisites"></a>前提条件

開始する前に、SQL Server Management Studio の最新バージョンであることを確認します。 SSMS をダウンロードするを参照してください。[ダウンロード SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)です。

## <a name="connect-to-the-ssis-catalog-database"></a>SSIS カタログ データベースへの接続します。

SSIS カタログへの接続を確立するために SQL Server Management Studio を使用します。 

> [!NOTE]
> Azure SQL データベース サーバーは、ポート 1433 でリッスンします。 企業のファイアウォール内での Azure SQL データベース サーバーに接続しようとしている場合、このポートが正常に接続するための企業ファイアウォールで開いていなければなりません。

1. SQL Server Management Studio を開きます。

2. **サーバーへの接続** ダイアログ ボックスで、次の情報を入力します。

   | 設定       | 推奨値 | 詳細 | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバーの種類** | データベース エンジン | この値は必須です。 |
   | **サーバー名** | 完全修飾サーバー名 |  |
   | **[認証]** | SQL Server 認証 (SQL Server Authentication) | このクイック スタートでは、SQL 認証を使用します。 |
   | **Login** | サーバーの管理者アカウント | これは、サーバーを作成したときに指定したアカウントです。 |
   | **Password** | サーバーの管理者アカウントのパスワード | これは、サーバーを作成したときに指定したパスワードです。 |

3. **[接続]**をクリックします。 SSMS では、オブジェクト エクスプ ローラー ウィンドウが開きます。 

4. オブジェクト エクスプ ローラーで、 **Integration Services カタログ**順に展開**SSISDB** SSIS カタログ データベースでオブジェクトを表示します。

## <a name="run-the-t-sql-code"></a>T-SQL コードを実行します。
SSIS プロジェクトを配置する次の TRANSACT-SQL コードを実行します。

1.  SSMS では、新しいクエリ ウィンドウを開き、次のコードを貼り付けます。

2.  内のパラメーター値を更新、`catalog.deploy_project`システムのストアド プロシージャです。

3.  SSISDB が現在のデータベースであることを確認してください。

4.  スクリプトを実行します。

5. オブジェクト エクスプ ローラーでの内容を更新**SSISDB**必要に応じて配置したプロジェクトを確認します。

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
- パッケージを配置するには、その他の方法を検討してください。
    - [SSMS で SSIS パッケージを展開します。](./ssis-quickstart-deploy-ssms.md)
    - [Transact SQL (VS Code) を使用した SSIS パッケージを展開します。](ssis-quickstart-deploy-tsql-vscode.md)
    - [コマンド プロンプトから、SSIS パッケージを展開します。](./ssis-quickstart-deploy-cmdline.md)
    - [PowerShell を使用した SSIS パッケージを展開します。](ssis-quickstart-deploy-powershell.md)
    - [C# を使用して、SSIS パッケージを展開します。](./ssis-quickstart-deploy-dotnet.md) 
- 配置されたパッケージを実行します。 パッケージを実行するには、いくつかのツールおよび言語から選択することができます。 詳細については、次の記事を参照してください。
    - [SSMS での SSIS パッケージを実行します。](./ssis-quickstart-run-ssms.md)
    - [TRANSACT-SQL (SSMS) で、SSIS パッケージを実行します。](./ssis-quickstart-run-tsql-ssms.md)
    - [Transact SQL (VS Code) を使用した SSIS パッケージを実行します。](ssis-quickstart-run-tsql-vscode.md)
    - [コマンド プロンプトから、SSIS パッケージを実行します。](./ssis-quickstart-run-cmdline.md)
    - [PowerShell での SSIS パッケージを実行します。](ssis-quickstart-run-powershell.md)
    - [C# を使用して、SSIS パッケージを実行します。](./ssis-quickstart-run-dotnet.md) 

