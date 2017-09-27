---
title: "SSMS で、SSIS プロジェクトを配置 |Microsoft ドキュメント"
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
ms.openlocfilehash: b9729343ab14563ee6264795d6f098f3c22e91bf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/22/2017

---
# <a name="deploy-an-ssis-project-with-sql-server-management-studio-ssms"></a>SSIS プロジェクトを SQL Server Management Studio (SSMS) の展開します。
このクイック スタートでは、SQL Server Management Studio (SSMS) を使用して、SSIS カタログ データベースに接続し、SSIS プロジェクトを SSIS カタログに配置する Integration Services 配置ウィザードを実行する方法を示します。 

SQL Server Management Studio は、SQL データベースに SQL Server から SQL のインフラストラクチャを管理するための統合環境です。 SSMS の詳細については、次を参照してください。 [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)です。

## <a name="prerequisites"></a>前提条件

開始する前に、SQL Server Management Studio の最新バージョンであることを確認します。 SSMS をダウンロードするを参照してください。[ダウンロード SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)です。

## <a name="connect-to-the-ssisdb-database"></a>SSISDB データベースへの接続します。

SSIS カタログへの接続を確立するために SQL Server Management Studio を使用します。 

> [!NOTE]
> Azure SQL データベース サーバーは、ポート 1433 でリッスンします。 企業のファイアウォール内での Azure SQL データベース サーバーに接続しようとしている場合、このポートが正常に接続するための企業ファイアウォールで開いていなければなりません。

1. SQL Server Management Studio を開きます。

2. **サーバーへの接続** ダイアログ ボックスで、次の情報を入力します。

   | 設定       | 推奨値 | 詳細 | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバーの種類** | データベース エンジン | この値は必須です。 |
   | **サーバー名** | 完全修飾サーバー名 | 名前がこの形式では、Azure SQL Database サーバーに接続する場合:`<server_name>.database.windows.net`です。 |
   | **[認証]** | SQL Server 認証 (SQL Server Authentication) | このクイック スタートでは、SQL 認証を使用します。 |
   | **Login** | サーバーの管理者アカウント | これは、サーバーを作成したときに指定したアカウントです。 |
   | **Password** | サーバーの管理者アカウントのパスワード | これは、サーバーを作成したときに指定したパスワードです。 |

3. **[接続]**をクリックします。 SSMS では、オブジェクト エクスプ ローラー ウィンドウが開きます。 

4. オブジェクト エクスプ ローラーで、 **Integration Services カタログ**順に展開**SSISDB** SSIS カタログ データベースでオブジェクトを表示します。

## <a name="start-the-integration-services-deployment-wizard"></a>Integration Services 配置ウィザードを開始します。
1. オブジェクト エクスプ ローラーでの**Integration Services カタログ**ノードおよび**SSISDB**プロジェクト フォルダーを展開すると、展開します。

2.  選択、**プロジェクト**ノード。

3.  右クリックし、**プロジェクト**ノード**プロジェクトの配置**です。 Integration Services 配置ウィザードを開きます。 または、ファイル システムから、現在のカタログからプロジェクトを配置することができます。

## <a name="deploy-a-project-with-the-wizard"></a>ウィザードを使用してプロジェクトを配置します。
1. **概要**ページ、ウィザードの概要を確認します。 をクリックして**次**を開くには、**ソースの選択**ページ。

2. **ソースの選択** ページで、展開する既存の SSIS プロジェクトを選択します。
    -   作成したプロジェクト配置ファイルを配置するには、 **[プロジェクト配置ファイル]** を選択して .ispac ファイルのパスを入力します。
    -   SSIS カタログに存在するプロジェクトを配置するには選択**Integration Services カタログ**、カタログ内のプロジェクトに、サーバー名とパスを入力します。
    **[次へ]** をクリックして、 **[配置先の選択]** ページを表示します。
  
3.  **先の選択** ページで、プロジェクトの対象を選択します。
    -   完全修飾サーバー名を入力します。 名前がこの形式では、対象サーバーが Azure SQL データベース サーバーの場合:`<server_name>.database.windows.net`です。
    -   をクリックして**参照**SSISDB では、対象フォルダーを選択します。
    をクリックして**次**を開くには、**レビュー**ページ。  
  
4.  **確認** ページで選択した設定を確認します。
    -   選択内容を変更するには、 **[戻る]**をクリックするか、左ペインでいずれかの手順をクリックします。
    -   **[配置]** をクリックして、配置プロセスを開始します。
  
5.  展開処理が完了した後、**結果**ページが開きます。 このページでは、各アクションが成功したか、失敗したかを表示します。
    -   操作に失敗した場合にをクリックして**失敗**で、**結果**エラーの説明を表示する列。
    -   必要に応じて、をクリックして**レポートを保存しています.**結果を XML ファイルに保存します。
    -   をクリックして**閉じる**ウィザードを終了します。

## <a name="next-steps"></a>次の手順
- パッケージを配置するには、その他の方法を検討してください。
    - [SSIS パッケージにより、TRANSACT-SQL (SSMS) での展開します。](./ssis-quickstart-deploy-tsql-ssms.md)
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

