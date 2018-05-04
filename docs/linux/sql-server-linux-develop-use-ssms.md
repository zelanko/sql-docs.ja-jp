---
title: SSMS での Linux に SQL Server の管理 |Microsoft ドキュメント
description: このチュートリアルでは、Linux で実行されている Windows 上で SQL Server Management Studio を使用して SQL Server に接続する方法を示します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 30cc4564-f389-4707-9b25-8ba782cc5150
ms.openlocfilehash: 95f97fdb3b35d50e671f9569a8b58315014fc509
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="use-sql-server-management-studio-ssms-on-windows-to-manage-sql-server-on-linux"></a>Windows 上の SQL Server Management Studio (SSMS) を使用して、Linux 上の SQL Server を管理するには

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事は、使用する方法を示します[SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) Linux 上の SQL Server 2017 に接続します。 SSMS は、Windows アプリケーション、ので Linux 上のリモート SQL Server インスタンスに接続できる Windows コンピューターがある場合に SSMS を使用します。

正常に接続すると、データベースとの通信を確認する簡単な TRANSACT-SQL (T-SQL) クエリを実行します。

## <a name="install-the-newest-version-of-sql-server-management-studio"></a>SQL Server Management Studio の最新バージョンをインストールします。

SQL Server を使用する場合は、常に最新バージョンの SQL Server Management Studio (SSMS) を使用する必要があります。 SSMS の最新バージョンは継続的に更新および最適化されている 2017 on Linux を SQL Server で現在動作します。 ダウンロードして、最新バージョンをインストールを参照してください。 [SQL Server Management Studio のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)です。 最新の状態に、SSMS の最新バージョンように求められますダウンロード可能な新しいバージョンがある場合。 

## <a name="connect-to-sql-server-on-linux"></a>Linux 上の SQL Server への接続します。

次の手順では、SSMS での Linux 上の SQL Server 2017 に接続する方法を示します。

1. 入力して、SSMS を起動**Microsoft SQL Server Management Studio** Windows の検索ボックスで、およびデスクトップ アプリをクリックします。

    ![SQL Server Management Studio](./media/sql-server-linux-develop-use-ssms/ssms.png)

2. **サーバーへの接続** ウィンドウで、次の情報を入力してください (SSMS が既に実行されている場合はクリックして**接続 > データベース エンジン**を開くには、**サーバーへの接続**ウィンドウ)。

   | 設定 | Description |
   |-----|-----|
   | **サーバーの種類** | 既定では、データベース エンジンです。この値を変更することはできません。 |
   | **サーバー名** | 対象の Linux SQL Server コンピューターまたは IP アドレスの名前を入力します。 |
   | **[認証]** | Linux 上の SQL Server 2017、使用**SQL Server 認証**です。 |
   | **Login** | サーバー上のデータベースにアクセス権を持つユーザーの名前を入力してください (たとえば、既定値**SA**セットアップ中に作成したアカウント)。 |
   | **Password** | 指定したユーザーのパスワードを入力 (用、 **SA**アカウントを作成したセットアップ時に)。 |

    ![SQL Server Management Studio: SQL データベース サーバーへの接続します。](./media/sql-server-linux-develop-use-ssms/connect.png)

3. **[接続]** をクリックします。

    > [!TIP]
    > 接続エラーが発生した場合は、まずエラー メッセージから問題を診断します。 次に、[接続のトラブルシューティングに関する推奨事項](sql-server-linux-troubleshooting-guide.md#connection)を確認します。
 
5. SQL のサーバーに正常に接続した後**オブジェクト エクスプ ローラー**が開き、データベース管理タスクを実行またはデータをクエリにアクセスできます。
 
     ![オブジェクト エクスプ ローラー](./media/sql-server-linux-develop-use-ssms/object-explorer.png)
     
## <a name="run-sample-queries"></a>サンプル クエリを実行します。

サーバーに接続した後は、データベースに接続し、サンプル クエリを実行します。 新しいクエリを記述する場合を参照してください。 [TRANSACT-SQL ステートメントの記述](../t-sql/tutorial-writing-transact-sql-statements.md)です。

1. に対するクエリの実行に使用するデータベースを識別します。 新しいデータベースで作成した可能性があります、 [TRANSACT-SQL チュートリアル](../t-sql/tutorial-writing-transact-sql-statements.md)です。 ことも、 **AdventureWorks**サンプル データベースを[ダウンロードされ、復元](sql-server-linux-migrate-restore-database.md)です。
2. **オブジェクト エクスプ ローラー**サーバー上のターゲット データベースに移動します。
2. データベースを右クリックし、**新しいクエリ**:

    ![新しいクエリ。 SQL データベース サーバーに接続します SQL Server Management Studio。](./media/sql-server-linux-develop-use-ssms/new-query.png)

3. クエリ ウィンドウで、一方のテーブルからデータを選択する TRANSACT-SQL クエリを記述します。 次の例からのデータの選択、 **Production.Product**のテーブル、 **AdventureWorks**データベース。

        SELECT TOP 10 Name, ProductNumber
        FROM Production.Product
        ORDER BY Name ASC

4. クリックして、 **Execute**ボタンをクリックします。

    ![正常終了しました。 SQL データベース サーバーに接続します SQL Server Management Studio。](./media/sql-server-linux-develop-use-ssms/execute-query.png)

## <a name="next-steps"></a>次の手順

だけでなく、クエリを作成し、データベースを管理する T-SQL ステートメントを使用できます。

T-SQL を新しい場合を参照してください[チュートリアル: TRANSACT-SQL ステートメントの記述](../t-sql/tutorial-writing-transact-sql-statements.md)と[TRANSACT-SQL リファレンス (データベース エンジン)](https://msdn.microsoft.com/library/bb510741.aspx)です。

SSMS を使用する方法の詳細については、次を参照してください。 [SQL Server Management Studio を使用して](https://msdn.microsoft.com/library/ms174173.aspx)です。
