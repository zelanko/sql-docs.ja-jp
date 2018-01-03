---
title: "SSMS を使用して SSIS パッケージを実行する | Microsoft Docs"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: quick-start
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 53ad81ce3021f14e6d0638e7e60a050f892bb8bf
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="run-an-ssis-package-with-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) を使用して SSIS パッケージを実行する
このクイック スタートでは、SQL Server Management Studio (SSMS) を使用して、SSIS カタログ データベースに接続してから、SSMS のオブジェクト エクスプローラーから SSIS カタログに格納されている SSIS パッケージを実行する方法を示します。

SQL Server Management Studio は、SQL Server から SQL Database まで、SQL インフラストラクチャを管理するための統合環境です。 SSMS については、「[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)」をご覧ください。

## <a name="prerequisites"></a>Prerequisites

開始する前に、最新バージョンの SQL Server Management Studio (SSMS) があることを確認します。 SSMS をダウンロードするには、「[SQL Server Management Studio (SSMS) のダウンロード](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)」を参照してください。

## <a name="connect-to-the-ssisdb-database"></a>SSISDB データベースに接続する

SQL Server Management Studio を使って、SSIS カタログへの接続を確立します。 

> [!NOTE]
> Azure SQL Database サーバーは、ポート 1433 でリッスンします。 企業のファイアウォール内から Azure SQL Database サーバーに接続しようとする場合、正常に接続するには、このポートを企業のファイアウォールで開ける必要があります。

1. SQL Server Management Studio を開きます。

2. **[サーバーへの接続]** ダイアログ ボックスに次の情報を入力します。

   | 設定       | 提案される値 | 詳細 | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバーの種類** | データベース エンジン | この値は必須です。 |
   | **サーバー名** | 完全修飾サーバー名 | Azure SQL Database サーバーに接続する場合、名前は次の形式になります。`<server_name>.database.windows.net` |
   | **[認証]** | SQL Server 認証 (SQL Server Authentication) | このクイック スタートでは、SQL 認証を使います。 |
   | **Login** | サーバー管理者アカウント | これはサーバーを作成したときに指定したアカウントです。 |
   | **Password** | サーバー管理者アカウントのパスワード | これはサーバーを作成したときに指定したパスワードです。 |

3. **[接続]**をクリックします。 SSMS で [オブジェクト エクスプローラー] ウィンドウが開きます。 

4. オブジェクト エクスプローラーで、**[Integration Services カタログ]**、**[SSISDB]** の順に展開し、SSIS カタログ データベース内のオブジェクトを表示します。

## <a name="run-a-package"></a>パッケージの実行

1. オブジェクト エクスプローラーで、実行するパッケージを選択します。

2. 右クリックして、**[実行]** を選択します。 **[パッケージの実行]** ダイアログ ボックスが開きます。

3.  [パッケージの実行] ダイアログ ボックスの **[パラメーター]** タブ、**[接続マネージャー]** タブ、**[詳細設定]** タブの設定を使用して、パッケージの実行を構成します。

4.  [OK] をクリックしてパッケージを実行します。

## <a name="next-steps"></a>次の手順
- パッケージを実行する他の方法を検討します。
    - [Transact-SQL (SSMS) を使用して SSIS パッケージを実行する](./ssis-quickstart-run-tsql-ssms.md)
    - [Transact-SQL (VS Code) を使用して SSIS パッケージを実行する](ssis-quickstart-run-tsql-vscode.md)
    - [コマンド プロンプトから SSIS パッケージを実行する](./ssis-quickstart-run-cmdline.md)
    - [PowerShell を使用して SSIS パッケージを実行する](ssis-quickstart-run-powershell.md)
    - [C# を使用して SSIS パッケージを実行する](./ssis-quickstart-run-dotnet.md) 
