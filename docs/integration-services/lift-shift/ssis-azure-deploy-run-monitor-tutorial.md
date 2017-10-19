---
title: "配置、実行、および Azure で SSIS パッケージの監視 |Microsoft ドキュメント"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 560965a241b24a09f50a23faf63ce74d0049d5a7
ms.openlocfilehash: 2e16666c412870cc55024e7156752f43ddbc1800
ms.contentlocale: ja-jp
ms.lasthandoff: 10/13/2017

---
# <a name="deploy-run-and-monitor-an-ssis-package-on-azure"></a>配置、実行、および Azure で SSIS パッケージの監視
このチュートリアルでは、Azure SQL データベース上の SSISDB カタログ データベースに SQL Server Integration Services プロジェクトを配置、ランタイムでは、Azure SSIS の統合、パッケージの実行、および実行中のパッケージを監視する方法を示します。

## <a name="prerequisites"></a>前提条件

開始する前に 17.2 または SQL Server Management Studio のそれ以降のバージョンであることを確認します。 SSMS の最新バージョンをダウンロードするを参照してください。[ダウンロード SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)です。

また、SSISDB データベースを設定している Azure SSIS の統合ランタイムをプロビジョニングすることを確認してください。 Azure での SSIS をプロビジョニングする方法については、次を参照してください。[を Azure に SQL Server Integration Services (SSIS) パッケージのリフト アンド シフト](https://docs.microsoft.com/en-us/azure/data-factory/tutorial-deploy-ssis-packages-azure)です。

## <a name="connect-to-the-ssisdb-database"></a>SSISDB データベースへの接続します。

SQL Server Management Studio を使用して、Azure SQL データベース サーバーで SSIS カタログに接続します。 詳細については、次を参照してください。 [Azure 上の SSISDB カタログ データベースへの接続](ssis-azure-connect-to-catalog-database.md)です。

> [!IMPORTANT]
> Azure SQL データベース サーバーは、ポート 1433 でリッスンします。 企業のファイアウォール内での Azure SQL データベース サーバーに接続しようとする場合、このポートが正常に接続するための企業ファイアウォールで開いていなければなりません。

1. SQL Server Management Studio を開きます。

2. **サーバーへの接続**です。 **サーバーへの接続** ダイアログ ボックスで、次の情報を入力します。

   | 設定       | 推奨値 | Description | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバーの種類** | データベース エンジン | この値は必須です。 |
   | **サーバー名** | 完全修飾サーバー名 | 名前は、この形式でなければなりません: **mysqldbserver.database.windows.net**です。 サーバー名を必要がある場合は、次を参照してください。 [Azure 上の SSISDB カタログ データベースへの接続](ssis-azure-connect-to-catalog-database.md)です。 |
   | **[認証]** | SQL Server 認証 (SQL Server Authentication) | このクイック スタートでは、SQL 認証を使用します。 |
   | **Login** | サーバーの管理者アカウント | これは、サーバーを作成したときに指定したアカウントです。 |
   | **Password** | サーバーの管理者アカウントのパスワード | これは、サーバーを作成したときに指定したパスワードです。 |

3. **SSISDB データベースに接続**です。 選択**オプション**を展開、**サーバーへの接続** ダイアログ ボックス。 展開済み**サーバーへの接続**ダイアログ ボックスで、**接続プロパティ**タブです。**データベースへの接続**フィールドを選択または入力`SSISDB`です。

4. 選択し、**接続**です。 SSMS では、オブジェクト エクスプ ローラー ウィンドウが開きます。 

5. オブジェクト エクスプ ローラーで、 **Integration Services カタログ**順に展開**SSISDB** SSIS カタログ データベースでオブジェクトを表示します。

## <a name="deploy-a-project"></a>プロジェクトを配置します。

### <a name="start-the-integration-services-deployment-wizard"></a>Integration Services 配置ウィザードを開始します。
1. SSMS では、オブジェクト エクスプ ローラーで、 **Integration Services カタログ**ノードおよび**SSISDB**ノードを展開すると、プロジェクト フォルダーを展開します。

2.  選択、**プロジェクト**ノード。

3.  右クリックし、**プロジェクト**ノード**プロジェクトの配置**です。 Integration Services 配置ウィザードを開きます。 SSIS カタログ データベースとは、ファイル システムからプロジェクトを配置することができます。

### <a name="deploy-a-project-with-the-deployment-wizard"></a>配置ウィザードを使用してプロジェクトを配置します。
1. **概要**ページの展開ウィザードの概要を確認します。 選択**次**を開くには、**ソースの選択**ページ。

2. **ソースの選択** ページで、展開する既存の SSIS プロジェクトを選択します。
    -   作成したプロジェクト配置ファイルを配置するには、 **[プロジェクト配置ファイル]** を選択して .ispac ファイルのパスを入力します。
    -   SSIS カタログに存在するプロジェクトを配置するには選択**Integration Services カタログ**、カタログ内のプロジェクトに、サーバー名とパスを入力します。
    -   選択**次**を表示する、**先の選択**ページ。
  
3.  **先の選択** ページで、プロジェクトの対象を選択します。
    -   形式で完全修飾サーバー名を入力`<server_name>.database.windows.net`です。
    -   選択し、**参照**SSISDB では、対象フォルダーを選択します。
    -   選択**次**を開くには、**レビュー**ページ。  
  
4.  **確認** ページで選択した設定を確認します。
    -   選択して、選択内容を変更することができます**前**、または左側のウィンドウで、手順のいずれかを選択しています。
    -   選択**展開**展開プロセスを開始します。
  
5.  展開処理が完了した後、**結果**ページが開きます。 このページでは、各アクションが成功したか、失敗したかを表示します。
    -   操作が失敗した場合は、選択**失敗**で、**結果**エラーの説明を表示する列。
    -   必要に応じて、選択**レポートを保存しています.**結果を XML ファイルに保存します。
    -   選択**閉じる**ウィザードを終了します。

## <a name="run-a-package"></a>パッケージを実行します。

1. Ssms オブジェクト エクスプ ローラーで実行するパッケージを選択します。

2. 右クリックし [ **Execute**を開くには、**パッケージ実行**] ダイアログ ボックス。

3.  **パッケージ実行** ダイアログ ボックスで、上の設定を使用して、パッケージの実行を構成、**パラメーター**、**接続マネージャー**、および**詳細設定**タブです。

4.  選択**OK**パッケージを実行します。

## <a name="monitor-the-running-package-in-ssms"></a>SSMS での実行中のパッケージを監視します。

現在、配置、検証、および、パッケージの実行など、Integration Services サーバー上の Integration Services の操作を実行中の状態を表示するには使用、 **Active Operations** SSMS でのダイアログ ボックス。 開くには、 **Active Operations** ] ダイアログ ボックスを右クリックして**SSISDB**、し、[**アクティブな操作**です。

オブジェクト エクスプ ローラーで右クリックして選択で、パッケージを選択することもできます。**レポート**、し**標準レポート**、し**すべての実行**です。

SSMS での実行中のパッケージを監視する方法の詳細については、次を参照してください。[モニター実行中のパッケージとその他の操作](https://docs.microsoft.com/en-us/sql/integration-services/performance/monitor-running-packages-and-other-operations)です。

## <a name="monitor-the-azure-ssis-integration-runtime"></a>Azure SSIS の統合の実行時を監視します。

パッケージが実行されている Azure SSIS の統合ランタイムに関する状態情報を取得するには、次の PowerShell コマンドを使用: コマンドごとに、データ ファクトリ、Azure SSIS IR およびリソース グループの名前を指定します。

### <a name="get-metadata-about-the-azure-ssis-integration-runtime"></a>Azure SSIS の統合ランタイムはメタデータを取得します。

```powershell
Get-AzureRmDataFactoryV2IntegrationRuntime -DataFactoryName $DataFactoryName -Name $AzureSsisIRName -ResourceGroupName $ResourceGroupName
```

### <a name="get-the-status-of-the-azure-ssis-integration-runtime"></a>Azure SSIS の統合の実行時の状態を取得します。

```powershell
Get-AzureRmDataFactoryV2IntegrationRuntimeStatus -DataFactoryName $DataFactoryName -Name $AzureSsisIRName -ResourceGroupName $ResourceGroupName
```

## <a name="next-steps"></a>次の手順
- パッケージの実行をスケジュールする方法を説明します。 詳細については、次を参照してください[スケジュール SSIS パッケージを Azure での実行。](ssis-azure-schedule-packages.md)

