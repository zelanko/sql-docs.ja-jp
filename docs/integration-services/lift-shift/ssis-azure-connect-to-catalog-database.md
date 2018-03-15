---
title: "Azure 上の SSISDB カタログ データベースへの接続 | Microsoft Docs"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 218890a01c98c51c570255dce0ad2c34bc5c26db
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="connect-to-the-ssisdb-catalog-database-on-azure"></a>Azure 上の SSISDB カタログ データベースへの接続

Azure SQL Database でホストされている SSIS カタログ データベース (SSISDB) に接続するために必要な接続情報を取得します。 接続するには、次の項目が必要です。
- 完全修飾サーバー名
- データベース名
- ログイン情報 

> [!IMPORTANT]
> この時点では、Azure Data Factory バージョン 2 での Azure SSIS Integration Runtime の作成とは切り離して、Azure SQL Database に SSISDB カタログ データベースを作成することはできません。 Azure SSIS IR は、Azure 上で SSIS パッケージを実行するからです。 詳細については、「[Azure Data Factory UI を使用した Azure SSIS 統合ランタイムのプロビジョニング](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal)」を参照してください。 

## <a name="prerequisites"></a>Prerequisites
始める前に、バージョン 17.2 以降の SQL Server Management Studio があることを確認します。 最新バージョンの SSMS をダウンロードするには、「[SQL Server Management Studio (SSMS) のダウンロード](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)」を参照してください。

## <a name="get-the-connection-info-from-the-azure-portal"></a>Azure Portal から接続情報を取得する
1. [Azure ポータル](https://portal.azure.com/)にログインします。
2. Azure Portal で、左側のメニューから **[SQL Databases]** を選択し、**[SQL データベース]** ページで [`SSISDB` データベース] を選択します。 
3. `SSISDB` データベースの **[概要]** ページで、次の図のように、完全修飾サーバー名を確認します。 **[クリックしてコピー]** オプションを呼び出すには、サーバー名にマウス ポインターを移動します。

    ![サーバー接続情報](media/ssis-azure-connect-to-catalog-database/server-name.png) 

4. SQL Database サーバーのログイン情報を忘れてしまった場合は、[SQL Database サーバー] ページに移動します。 ここでは、サーバー管理者名を表示でき、必要に応じて、パスワードをリセットできます。

## <a name="connect-with-ssms"></a>SSMS との接続
1. SQL Server Management Studio を開きます。

2. **サーバーに接続します**。 **[サーバーへの接続]** ダイアログ ボックスに次の情報を入力します。

   | 設定       | 提案される値 | Description | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバーの種類** | データベース エンジン | この値は必須です。 |
   | **サーバー名** | 完全修飾サーバー名 | 名前は **mysqldbserver.database.windows.net** の形式である必要があります。 |
   | **[認証]** | SQL Server 認証 (SQL Server Authentication) | このクイック スタートでは、SQL 認証を使います。 |
   | **Login** | サーバー管理者アカウント | これはサーバーを作成したときに指定したアカウントです。 |
   | **Password** | サーバー管理者アカウントのパスワード | これはサーバーを作成したときに指定したパスワードです。 |

    ![SSMS を使用してサーバーに接続する](media/ssis-azure-connect-to-catalog-database/ssisdb-connect-1.png)

3. **SSISDB データベースに接続します**。 **[オプション]** を選択して、**[サーバーへの接続]** ダイアログ ボックスを展開します。 展開した **[サーバーへの接続]** ダイアログ ボックスで、**[接続プロパティ]** タブを選択します。**[データベースへの接続]** フィールドで、`SSISDB` を選択または入力します。

    > [!IMPORTANT]
    > 接続時に `SSISDB` を選択しないと、オブジェクト エクスプローラーで SSIS カタログが表示されない場合があります。

    ![接続に SSISDB データベースを選択する](media/ssis-azure-connect-to-catalog-database/ssisdb-connect-2.png)

4. **[接続]** を選択します。

5. オブジェクト エクスプローラーで、**[Integration Services カタログ]**、**[SSISDB]** の順に展開し、SSIS カタログ データベース内のオブジェクトを表示します。

    ![SSMS のオブジェクト エクスプローラーで SSISDB データベースを探す](media/ssis-azure-connect-to-catalog-database/ssisdb-connect-3.png)

## <a name="next-steps"></a>次の手順
- パッケージを配置します。 詳細については、「[SQL Server Management Studio (SSMS) を使用して SSIS プロジェクトを配置する](../ssis-quickstart-deploy-ssms.md)」を参照してください。
- パッケージを実行します。 詳細については、「[SQL Server Management Studio (SSMS) を使用して SSIS プロジェクトを配置する](../ssis-quickstart-run-ssms.md)」を参照してください。
- パッケージのスケジュールを設定します。 詳細については、「[Azure で SSIS パッケージの実行をスケジュールする](ssis-azure-schedule-packages.md)」を参照してください。
