---
title: SSMS で SSIS プロジェクトを配置する | Microsoft Docs
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
ms.openlocfilehash: c13783a7bbd5a23c2329151932f4438255babb9b
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="deploy-an-ssis-project-with-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) を使用して SSIS プロジェクトを配置する
このクイック スタートでは、SQL Server Management Studio (SSMS) を使って、SSIS カタログ データベースに接続した後、Integration Services 配置ウィザードを実行して SSIS カタログに SSIS プロジェクトを配置する方法を説明します。 

SQL Server Management Studio は、SQL Server から SQL Database まで、SQL インフラストラクチャを管理するための統合環境です。 SSMS については、「[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)」をご覧ください。

## <a name="prerequisites"></a>Prerequisites

始める前に、最新バージョンの SQL Server Management Studio があることを確認します。 SSMS をダウンロードするには、「[SQL Server Management Studio (SSMS) のダウンロード](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)」を参照してください。

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

3. **[接続]** をクリックします。 SSMS で [オブジェクト エクスプローラー] ウィンドウが開きます。 

4. オブジェクト エクスプローラーで、**[Integration Services カタログ]**、**[SSISDB]** の順に展開し、SSIS カタログ データベース内のオブジェクトを表示します。

## <a name="start-the-integration-services-deployment-wizard"></a>Integration Services 配置ウィザードを開始する
1. オブジェクト エクスプローラーで、**[Integration Services カタログ]** ノードと **[SSISDB]** を展開した状態で、プロジェクト フォルダーを展開します。

2.  **[プロジェクト]** ノードを選びます。

3.  **[プロジェクト]** ノードを右クリックして、**[プロジェクトの配置]** を選びます。 Integration Services 配置ウィザードが開きます。 現在のカタログから、またはファイル システムから、プロジェクトを配置することができます。

## <a name="deploy-a-project-with-the-wizard"></a>ウィザードを使用してプロジェクトを配置する
1. ウィザードの **[概要]** ページで、概要を確認します。 **[次へ]** をクリックして、**[ソースの選択]** ページを開きます。

2. **[ソースの選択]** ページで、配置する既存の SSIS プロジェクトを選びます。
    -   作成したプロジェクト配置ファイルを配置するには、 **[プロジェクト配置ファイル]** を選択して .ispac ファイルのパスを入力します。
    -   SSIS カタログにあるプロジェクトを配置するには、**[Integration Services カタログ]** を選び、サーバー名とカタログ内のプロジェクトのパスを入力します。
    **[次へ]** をクリックして、 **[配置先の選択]** ページを表示します。
  
3.  **[配置先の選択]** ページで、プロジェクトの配置先を選びます。
    -   完全修飾サーバー名を入力します。 対象サーバーが Azure SQL Database サーバーの場合、名前は次の形式になります。`<server_name>.database.windows.net`
    -   **[参照]** をクリックして、SSISDB でターゲット フォルダーを選びます。
    **[次へ]** をクリックして **[レビュー]** ページを開きます。  
  
4.  **[レビュー]** ページで、選択した設定を確認します。
    -   選択内容を変更するには、 **[戻る]** をクリックするか、左ペインでいずれかの手順をクリックします。
    -   **[配置]** をクリックして、配置プロセスを開始します。
  
5.  配置プロセスが完了すると、**[結果]** ページが開きます。 このページでは、各アクションが成功したか、失敗したかを表示します。
    -   アクションが失敗した場合は、**[結果]** 列の **[失敗]** をクリックすると、エラーの説明が表示されます。
    -   必要に応じて、**[レポートの保存]** をクリックして結果を XML ファイルに保存します。
    -   **[閉じる]** をクリックしてウィザードを終了します。

## <a name="next-steps"></a>次の手順
- パッケージを配置する他の方法を検討します。
    - [Transact-SQL (SSMS) を使用して SSIS パッケージを配置する](./ssis-quickstart-deploy-tsql-ssms.md)
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
