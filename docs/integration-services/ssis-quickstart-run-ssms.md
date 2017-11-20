---
title: "SSMS で、SSIS パッケージを実行 |Microsoft ドキュメント"
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
ms.openlocfilehash: bbc17907311785ef98560493cb453b7b9b6d1556
ms.contentlocale: ja-jp
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-with-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) で、SSIS パッケージを実行します。
このクイック スタートでは、SQL Server Management Studio (SSMS) を使用して、SSIS カタログ データベースに接続し、SSMS のオブジェクト エクスプ ローラーから、SSIS カタログに格納されている SSIS パッケージを実行する方法を示します。

SQL Server Management Studio は、SQL データベースに SQL Server から SQL のインフラストラクチャを管理するための統合環境です。 SSMS の詳細については、次を参照してください。 [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)です。

## <a name="prerequisites"></a>前提条件

開始する前に、最新バージョンの SQL Server Management Studio (SSMS) であることを確認します。 SSMS をダウンロードするを参照してください。[ダウンロード SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)です。

## <a name="connect-to-the-ssisdb-database"></a>SSISDB データベースへの接続します。

SSIS カタログへの接続を確立するために SQL Server Management Studio を使用します。 

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

3. **[接続]**をクリックします。 SSMS では、オブジェクト エクスプ ローラー ウィンドウが開きます。 

4. オブジェクト エクスプ ローラーで、 **Integration Services カタログ**順に展開**SSISDB** SSIS カタログ データベースでオブジェクトを表示します。

## <a name="run-a-package"></a>パッケージを実行します。

1. オブジェクト エクスプ ローラーで実行するパッケージを選択します。

2. 右クリックし  **Execute**です。 **パッケージ実行** ダイアログ ボックスが表示されます。

3.  上の設定を使用して、パッケージの実行を構成、**パラメーター**、**接続マネージャー**、および**詳細設定**パッケージの実行 ダイアログ ボックスのタブにします。

4.  パッケージを実行するには、[ok] をクリックします。

## <a name="next-steps"></a>次の手順
- パッケージを実行するには、その他の方法を検討してください。
    - [TRANSACT-SQL (SSMS) で、SSIS パッケージを実行します。](./ssis-quickstart-run-tsql-ssms.md)
    - [Transact SQL (VS Code) を使用した SSIS パッケージを実行します。](ssis-quickstart-run-tsql-vscode.md)
    - [コマンド プロンプトから、SSIS パッケージを実行します。](./ssis-quickstart-run-cmdline.md)
    - [PowerShell での SSIS パッケージを実行します。](ssis-quickstart-run-powershell.md)
    - [C# を使用して、SSIS パッケージを実行します。](./ssis-quickstart-run-dotnet.md) 

