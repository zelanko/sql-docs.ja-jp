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
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 10be16cbc85cccce51fafbcd733045c653b7be0a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="connect-to-the-ssisdb-catalog-database-on-azure"></a>Azure 上の SSISDB カタログ データベースへの接続

Azure SQL Database でホストされている SSIS カタログ データベース (SSISDB) に接続するために必要な接続情報を取得します。 接続するには、次の項目が必要です。
- 完全修飾サーバー名
- データベース名
- ログイン情報 

## <a name="prerequisites"></a>前提条件
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

3. **SSISDB データベースに接続します**。 **[オプション]** を選択して、**[サーバーへの接続]** ダイアログ ボックスを展開します。 展開した **[サーバーへの接続]** ダイアログ ボックスで、**[接続プロパティ]** タブを選択します。**[データベースへの接続]** フィールドで、`SSISDB` を選択または入力します。

    > [!IMPORTANT]
    > 接続時に `SSISDB` を選択しないと、オブジェクト エクスプローラーで SSIS カタログが表示されない場合があります。

4. **[接続]** を選択します。

5. オブジェクト エクスプローラーで、**[Integration Services カタログ]**、**[SSISDB]** の順に展開し、SSIS カタログ データベース内のオブジェクトを表示します。

## <a name="next-steps"></a>次の手順
- パッケージを配置します。 詳細については、「[SQL Server Management Studio (SSMS) を使用して SSIS プロジェクトを配置する](../ssis-quickstart-deploy-ssms.md)」を参照してください。
- パッケージを実行します。 詳細については、「[SQL Server Management Studio (SSMS) を使用して SSIS プロジェクトを配置する](../ssis-quickstart-run-ssms.md)」を参照してください。
- パッケージのスケジュールを設定します。 詳細については、「[Azure で SSIS パッケージの実行をスケジュールする](ssis-azure-schedule-packages.md)」を参照してください。
