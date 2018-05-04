---
title: SQL Server - Azure SQL DB (MySQLToSQL) に MySQL データの移行 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Data Migration, server side data migration
- Data Migration,client side data migration
ms.assetid: a6a7f4d6-68aa-4a38-93bf-53eba0d7dc82
caps.latest.revision: 24
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: dbf894167f512126c37293ffdd8580ad6fcaafaf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="migrating-mysql-data-into-sql-server---azure-sql-db-mysqltosql"></a>SQL Server - Azure SQL DB (MySQLToSQL) に MySQL データの移行
使用して変換されたオブジェクトが正常に同期後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure に MySQL からデータを移行することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
> [!IMPORTANT]  
> 場合、エンジンが使用されているサーバー側のデータの移行のエンジン、その後、移行する前にデータ、MySQL の拡張機能パックおよび SSMA を実行しているコンピューター上の MySQL プロバイダー、SSMA をインストールする必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェント サービスが実行されてもする必要があります。 拡張機能パックをインストールする方法の詳細については、次を参照してください[SQL Server (MySQL to SQL) 上の SSMA コンポーネントのインストール。](http://msdn.microsoft.com/en-us/6772d0c5-258f-4d7b-afb0-b5f810e71af1)  
  
## <a name="setting-migration-options"></a>移行オプションの設定  
移行する前にデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、プロジェクトの移行オプションの確認、**プロジェクト設定** ダイアログ ボックス。  
  
-   このダイアログ ボックスを使用して、移行のバッチ サイズ、テーブルのロック、制約チェック、null 値の処理、および id 値の処理などのオプションを設定できます。 プロジェクトの移行設定の詳細については、次を参照してください。[プロジェクトの設定 (移行)](http://msdn.microsoft.com/en-us/2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9)です。  
  
    詳細については**データ移行の設定の拡張**を参照してください[データ移行の設定](http://msdn.microsoft.com/en-us/9c396df4-5676-4f32-9c57-70d4f15f9b7a)  
  
-   **移行エンジン**で、**プロジェクト設定**ダイアログ ボックスで、次の 2 つの種類のデータ移行のエンジンを使用して、移行プロセスを実行することができます。  
  
    1.  クライアント側のデータ移行のエンジン  
  
    2.  サーバー側のデータ移行のエンジン  
  
**クライアント側のデータの移行:**  
  
-   クライアント側でのデータ移行を開始するには、選択、**クライアント側のデータ移行のエンジン**オプション、**プロジェクト設定** ダイアログ ボックス。  
  
-   **プロジェクト設定**、**クライアント側のデータ移行のエンジン**オプションを設定します。  
  
    > [!NOTE]  
    > **クライアント側のデータ移行エンジン**SSMA アプリケーション内にあるし、は、そのため、拡張機能パックの可用性に依存しません。  
  
**サーバー側のデータの移行:**  
  
-   サーバー側のデータ移行中に、エンジンは、対象のデータベースに存在します。 拡張機能パックによってインストールされます。 拡張機能パックをインストールする方法の詳細については、次を参照してください[SQL Server (MySQL to SQL) 上の SSMA コンポーネントのインストール。](http://msdn.microsoft.com/en-us/6772d0c5-258f-4d7b-afb0-b5f810e71af1)  
  
-   サーバー側での移行を開始するには、選択、**サーバー側のデータ移行のエンジン**オプション、**プロジェクト設定** ダイアログ ボックス。  
  
> [!IMPORTANT]  
> **クライアント側のデータ移行**オプションは、SQL Azure で使用できるのみです。  
  
## <a name="migrating-data-to-sql-server-or-sql-azure"></a>SQL Server または SQL Azure へのデータの移行  
移行データは、MySQL のテーブルから行のデータを移動する一括読み込み操作[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のテーブルのトランザクションでします。 読み込まれた行の数[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]各トランザクションでは、プロジェクトの設定で構成されています。  
  
移行のメッセージを表示するには、出力ウィンドウが表示されているを確認します。 それ以外の場合から、**ビュー**メニューの **出力**です。  
  
**データを移行するには**  
  
1.  次のことを確認します。  
  
    -   MySQL のプロバイダーは、SSMA を実行しているコンピューターにインストールされます。  
  
    -   ターゲット データベースと変換後のオブジェクトを同期しました (SQL Server または SQL Azure)。  
  
2.  MySQL メタデータ エクスプ ローラーで、移行するデータが含まれているオブジェクトを選択します。  
  
    -   すべてのスキーマのデータを移行する場合は、横にチェック ボックスを選択して**スキーマ**です。  
  
    -   データを移行または個々 のテーブルの省略は、最初にスキーマを展開し、**テーブル**を選択するか、テーブルの横にあるチェック ボックスをオフにします。  
  
3.  データを移行するには、2 つのケースが発生します。  
  
    **クライアント側のデータの移行:**  
  
    -   実行するため**クライアント側のデータ移行**、select、**クライアント側のデータ移行のエンジン**オプション、**プロジェクト設定** ダイアログ ボックス。  
  
    **サーバー側のデータの移行:**  
  
    -   サーバー側でデータ移行を実行する前に次のように確認します。  
  
        1.  SSMA for MySQL の拡張機能パックは、SQL Server のインスタンスにインストールされています。  
  
        2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェント サービスが SQL Server のインスタンスで実行されています。  
  
    -   実行するため**サーバー側のデータ移行**、select、**サーバー側のデータ移行のエンジン**オプション、**プロジェクト設定** ダイアログ ボックス。  
  
4.  右クリック**スキーマ**をクリックして MySQL メタデータ エクスプ ローラーで、**データの移行**です。 個々 のオブジェクトまたはオブジェクトのカテゴリのデータを移行することもできますオブジェクトまたはその親フォルダーを右クリック。選択、**データの移行**オプション。  
  
    > [!NOTE]  
    > SSMA for MySQL の拡張機能パックは、SQL Server のインスタンスにインストールされていない場合、**サーバー側のデータ移行のエンジン**が選択されている、ターゲット データベースにデータを移行中に、次のエラーが発生しました: ' SSMA データ移行のコンポーネントが見つかりませんでした、SQL Server のサーバー側のデータ移行を実行できなくなります。 拡張機能パックが正しくインストールされているかどうかを確認してください ' です。 をクリックして**キャンセル**データ移行を終了します。  
  
5.  **MySQL への接続**ダイアログ ボックスで、接続の資格情報を入力し、をクリックして**接続**です。 MySQL への接続の詳細については、次を参照してください[MySQL への接続&#40;MySQLToSQL。&#41;](../../ssma/mysql/connect-to-mysql-mysqltosql.md)  
  
    ターゲット データベースが SQL Server の場合は、次を入力に接続の資格情報、 **SQL Server への接続** ダイアログ ボックスをクリック**接続**です。 SQL Server への接続の詳細については、次を参照してください[SQL Server への接続。](http://msdn.microsoft.com/en-us/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)  
  
    ターゲット データベースが SQL Azure の場合は、接続の資格情報を入力してください。、 **SQL Azure への接続**ダイアログ ボックスで、とクリック**接続**です。 SQL Azure への接続の詳細については、次を参照してください[Azure SQL DB への接続&#40;MySQLToSQL。&#41;](../../ssma/mysql/connect-to-azure-sql-db-mysqltosql.md)  
  
    メッセージが表示、**出力**ウィンドウです。 移行が完了すると、**データ移行レポート**が表示されます。 すべてのデータが移行されない場合、エラーを含む行をクリックし、をクリックして**詳細**です。 レポートが終了したら、をクリックして**閉じる**です。 データ移行のレポートの詳細については、次を参照してください[データ移行レポート (SSMA 共通)。](http://msdn.microsoft.com/en-us/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> SQL Express エディションは、対象データベースとして使用される、クライアント側のデータの移行のみが許可されているし、サーバー側のデータの移行はサポートされていません。  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB にデータベースを移行する MySQL &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
