---
title: "Azure で SSIS パッケージを配置、実行、および監視する | Microsoft Docs"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4bf9df198105549f481dda8472f7142533fa8f23
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="deploy-run-and-monitor-an-ssis-package-on-azure"></a>Azure で SSIS パッケージを配置、実行、および監視する
このチュートリアルでは、Azure SQL Database の SSISDB カタログ データベースに SQL Server Integration Services プロジェクトを配置する方法、Azure-SSIS Integration Runtime でのパッケージの実行方法、および実行中のパッケージの監視方法を示します。

## <a name="prerequisites"></a>前提条件

始める前に、バージョン 17.2 以降の SQL Server Management Studio があることを確認します。 最新バージョンの SSMS をダウンロードするには、「[SQL Server Management Studio (SSMS) のダウンロード](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)」を参照してください。

また、SSISDB データベースを設定し、Azure-SSIS Integration Runtime をプロビジョニングしていることを確認してください。 Azure で SSIS をプロビジョニングする方法については、「[SQL Server Integration Services パッケージを Azure にデプロイする](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure)」を参照してください。

## <a name="connect-to-the-ssisdb-database"></a>SSISDB データベースに接続する

SQL Server Management Studio を使用して、Azure SQL Database サーバー上の SSIS カタログに接続します。 詳細については、「[Azure 上の SSISDB カタログ データベースへの接続](ssis-azure-connect-to-catalog-database.md)」を参照してください。

> [!IMPORTANT]
> Azure SQL Database サーバーは、ポート 1433 でリッスンします。 企業のファイアウォール内から Azure SQL Database サーバーに接続しようとする場合、正常に接続するには、このポートを企業のファイアウォールで開ける必要があります。

1. SQL Server Management Studio を開きます。

2. **サーバーに接続します**。 **[サーバーへの接続]** ダイアログ ボックスに次の情報を入力します。

   | 設定       | 提案される値 | Description | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバーの種類** | データベース エンジン | この値は必須です。 |
   | **サーバー名** | 完全修飾サーバー名 | 名前は **mysqldbserver.database.windows.net** の形式である必要があります。 サーバー名が必要な場合は、「[Azure 上の SSISDB カタログ データベースへの接続](ssis-azure-connect-to-catalog-database.md)」を参照してください。 |
   | **[認証]** | SQL Server 認証 (SQL Server Authentication) | このクイック スタートでは、SQL 認証を使います。 |
   | **Login** | サーバー管理者アカウント | これはサーバーを作成したときに指定したアカウントです。 |
   | **Password** | サーバー管理者アカウントのパスワード | これはサーバーを作成したときに指定したパスワードです。 |

3. **SSISDB データベースに接続します**。 **[オプション]** を選択して、**[サーバーへの接続]** ダイアログ ボックスを展開します。 展開した **[サーバーへの接続]** ダイアログ ボックスで、**[接続プロパティ]** タブを選択します。**[データベースへの接続]** フィールドで、`SSISDB` を選択または入力します。

4. **[接続]** を選択します。 [オブジェクト エクスプローラー] ウィンドウで、SSMS を開きます。 

5. オブジェクト エクスプローラーで、**[Integration Services カタログ]**、**[SSISDB]** の順に展開し、SSIS カタログ データベース内のオブジェクトを表示します。

## <a name="deploy-a-project"></a>プロジェクトを配置する

### <a name="start-the-integration-services-deployment-wizard"></a>Integration Services 配置ウィザードを起動する
1. SSMS のオブジェクト エクスプローラーで、**[Integration Services カタログ]** ノードと **[SSISDB]** ノードを展開した状態で、プロジェクト フォルダーを展開します。

2.  **[プロジェクト]** ノードを選びます。

3.  **[プロジェクト]** ノードを右クリックして、**[プロジェクトの配置]** を選びます。 Integration Services 配置ウィザードが開きます。 SSIS カタログ データベースから、またはファイル システムから、プロジェクトを配置することができます。

### <a name="deploy-a-project-with-the-deployment-wizard"></a>配置ウィザードを使用してプロジェクトを配置する
1. 配置ウィザードの **[概要]** ページで、概要を確認します。 **[次へ]** を選択して、**[ソースの選択]** ページを開きます。

2. **[ソースの選択]** ページで、配置する既存の SSIS プロジェクトを選びます。
    -   作成したプロジェクト配置ファイルを配置するには、 **[プロジェクト配置ファイル]** を選択して .ispac ファイルのパスを入力します。
    -   SSIS カタログにあるプロジェクトを配置するには、**[Integration Services カタログ]** を選び、サーバー名とカタログ内のプロジェクトのパスを入力します。
    -   **[次へ]** を選択して、**[配置先の選択]** ページを表示します。
  
3.  **[配置先の選択]** ページで、プロジェクトの配置先を選びます。
    -   完全修飾サーバー名を `<server_name>.database.windows.net` の形式で入力します。
    -   次に、**[参照]** を選択し、SSISDB でターゲット フォルダーを選択します。
    -   **[次へ]** を選択して **[レビュー]** ページを開きます。  
  
4.  **[レビュー]** ページで、選択した設定を確認します。
    -   選択内容を変更するには、**[戻る]** を選択するか、左ペインで任意の手順を選択します。
    -   **[配置]** をクリックして、配置プロセスを開始します。
  
5.  配置プロセスが完了すると、**[結果]** ページが開きます。 このページでは、各アクションが成功したか、失敗したかを表示します。
    -   アクションが失敗した場合は、**[結果]** 列の **[失敗]** を選択すると、エラーの説明が表示されます。
    -   必要に応じて、**[レポートの保存]** を選択して結果を XML ファイルに保存します。
    -   **[閉じる]** を選択してウィザードを終了します。

## <a name="run-a-package"></a>パッケージの実行

1. SSMS のオブジェクト エクスプローラーで、実行するパッケージを選択します。

2. 右クリックして **[実行]** を選択し、**[パッケージの実行]** ダイアログ ボックスを開きます。

3.  **[パッケージの実行]** ダイアログ ボックスで、**[パラメーター]**タブ、**[接続マネージャー]** タブ、**[詳細設定]** タブの設定を使用して、パッケージの実行を構成します。

4.  **[OK]** を選択してパッケージを実行します。

## <a name="monitor-the-running-package-in-ssms"></a>SSMS で実行中のパッケージを監視する

Integration Services サーバー上で現在実行されている Integration Services 操作 (配置、検証、パッケージの実行など) の状態を表示するには、SSMS の **[アクティブな操作]** ダイアログ ボックスを使用します。 **[アクティブな操作]** ダイアログ ボックスを開くには、**[SSISDB]** を右クリックし、**[アクティブな操作]** を選択します。

また、オブジェクト エクスプローラーでパッケージを選択し、右クリックして **[レポート]** を選択し、**[標準レポート]**、**[すべての実行]** の順に選択することもできます。

SSMS で実行中のパッケージを監視する方法の詳細については、「[パッケージとその他の操作を実行するモニター](https://docs.microsoft.com/sql/integration-services/performance/monitor-running-packages-and-other-operations)」を参照してください。

## <a name="monitor-the-azure-ssis-integration-runtime"></a>Azure-SSIS Integration Runtime の監視

パッケージが実行されている Azure-SSIS Integration Runtime に関する状態情報を取得するには、次の PowerShell コマンドを使用します。コマンドごとに、データ ファクトリ、Azure SSIS IR およびリソース グループの名前を指定します。

### <a name="get-metadata-about-the-azure-ssis-integration-runtime"></a>Azure-SSIS Integration Runtime に関するメタデータを取得する

```powershell
Get-AzureRmDataFactoryV2IntegrationRuntime -DataFactoryName $DataFactoryName -Name $AzureSsisIRName -ResourceGroupName $ResourceGroupName
```

### <a name="get-the-status-of-the-azure-ssis-integration-runtime"></a>Azure-SSIS Integration Runtime の状態を取得する

```powershell
Get-AzureRmDataFactoryV2IntegrationRuntime -Status -DataFactoryName $DataFactoryName -Name $AzureSsisIRName -ResourceGroupName $ResourceGroupName
```

## <a name="next-steps"></a>次の手順
- パッケージ実行をスケジュールする方法を説明します。 詳細については、「[Azure で SSIS パッケージの実行をスケジュールする](ssis-azure-schedule-packages.md)」を参照してください。
