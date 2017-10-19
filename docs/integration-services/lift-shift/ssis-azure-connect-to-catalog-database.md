---
title: "Azure 上の SSISDB カタログ データベースへの接続 |Microsoft ドキュメント"
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
ms.openlocfilehash: ac121e600c3c616006d79892c50f796ca7cd6b3f
ms.contentlocale: ja-jp
ms.lasthandoff: 10/13/2017

---
# <a name="connect-to-the-ssisdb-catalog-database-on-azure"></a>Azure 上の SSISDB カタログ データベースへの接続します。

Azure SQL データベース サーバーでホストされている、SSISDB カタログ データベースに接続する必要があります。 接続情報を取得します。 次の項目を接続する必要があります。
- 完全修飾サーバー名
- データベース名
- ログイン情報 

## <a name="prerequisites"></a>前提条件
開始する前に 17.2 または SQL Server Management Studio のそれ以降のバージョンであることを確認します。 SSMS の最新バージョンをダウンロードするを参照してください。[ダウンロード SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)です。

## <a name="get-the-connection-info-from-the-azure-portal"></a>Azure ポータルからの接続情報を取得します。
1. [Azure ポータル](https://portal.azure.com/)にログインします。
2. Azure ポータルで、次のように選択します。 **SQL データベース**クリックし、左側のメニューから、`SSISDB`上のデータベース、 **SQL データベース**ページ。 
3. **概要**のページ、`SSISDB`データベースで、次の図のように、完全修飾サーバー名を確認します。 サーバー名を合わせ、**をコピーする をクリックします。**オプション。

    ![サーバーの接続情報](media/ssis-azure-connect-to-catalog-database/server-name.png) 

4. SQL データベース サーバーのログイン情報を忘れてしまった場合は、SQL データベース サーバーのページに移動します。 サーバー管理者を表示するが名前を指定し、必要に応じて、パスワードをリセットします。

## <a name="connect-with-ssms"></a>SSMS と接続します。
1. SQL Server Management Studio を開きます。

2. **サーバーへの接続**です。 **サーバーへの接続** ダイアログ ボックスで、次の情報を入力します。

   | 設定       | 推奨値 | Description | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバーの種類** | データベース エンジン | この値は必須です。 |
   | **サーバー名** | 完全修飾サーバー名 | 名前は、この形式でなければなりません: **mysqldbserver.database.windows.net**です。 |
   | **[認証]** | SQL Server 認証 (SQL Server Authentication) | このクイック スタートでは、SQL 認証を使用します。 |
   | **Login** | サーバーの管理者アカウント | これは、サーバーを作成したときに指定したアカウントです。 |
   | **Password** | サーバーの管理者アカウントのパスワード | これは、サーバーを作成したときに指定したパスワードです。 |

3. **SSISDB データベースに接続**です。 選択**オプション**を展開、**サーバーへの接続** ダイアログ ボックス。 展開済み**サーバーへの接続**ダイアログ ボックスで、**接続プロパティ**タブです。**データベースへの接続**フィールドを選択または入力`SSISDB`です。

    > [!IMPORTANT]
    > 選択しない場合`SSISDB`接続するときに表示されないオブジェクト エクスプ ローラーで SSIS カタログ。

4. 選択し、**接続**です。

5. オブジェクト エクスプ ローラーで、 **Integration Services カタログ**順に展開**SSISDB** SSIS カタログ データベースでオブジェクトを表示します。

## <a name="next-steps"></a>次の手順
- パッケージを展開します。 詳細については、次を参照してください。 [SSIS プロジェクトを SQL Server Management Studio (SSMS) を配置](../ssis-quickstart-deploy-ssms.md)です。
- パッケージを実行します。 詳細については、次を参照してください。 [、SSIS パッケージを SQL Server Management Studio (SSMS) で実行](../ssis-quickstart-run-ssms.md)です。
- パッケージのスケジュールを設定します。 詳細については、次を参照してください[スケジュール SSIS パッケージを Azure での実行。](ssis-azure-schedule-packages.md)

