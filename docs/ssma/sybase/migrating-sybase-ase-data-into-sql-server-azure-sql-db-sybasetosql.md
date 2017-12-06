---
title: "SQL Server - Azure SQL DB に Sybase ASE データの移行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Migrating data,Client Side Data Migration
- Migrating data,Server Side Data Migration
ms.assetid: 54a39f5e-9250-4387-a3ae-eae47c799811
caps.latest.revision: "15"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3f7511fc695d70d37ba43e14bdd3ccd500f2a3db
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="migrating-sybase-ase-data-into-sql-server---azure-sql-db--sybasetosql"></a>SQL Server - Azure SQL DB (SybaseToSQL) に Sybase ASE データの移行
Sybase Adaptive Server Enterprise (ASE) データベース オブジェクトを正常に読み込んだ後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB に ASE からデータを移行することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。  
  
> [!IMPORTANT]  
> 使用されているエンジンがサーバー側のデータ移行のエンジンの場合は、データを移行する前にインストールしてください、SSMA for Sybase ASE 拡張機能パックおよび SSMA を実行しているコンピューターで Sybase ASE プロバイダー。 SQL Server エージェント サービスを実行する必要があります。 拡張機能パックをインストールする方法の詳細については、次を参照してください[SQL Server (SybaseToSQL) 上の SSMA コンポーネントのインストール。](http://msdn.microsoft.com/en-us/5ad9e12c-2cdb-4dd2-8703-05a23242d19d)  
  
## <a name="setting-migration-options"></a>移行オプションの設定  
移行する前にデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB、プロジェクトの移行オプションの確認、**プロジェクト設定** ダイアログ ボックス。  
  
-   このダイアログ ボックスを使用して、移行のバッチ サイズ、テーブルのロック、制約チェック、null 値の処理、および id 値の処理などのオプションを設定できます。 プロジェクトの移行設定の詳細については、次を参照してください。[プロジェクトの設定 (移行) (Sybase)](http://msdn.microsoft.com/en-us/82f8857f-7ab1-4738-ab6e-b1e95ea94924)です。  
  
    詳細については**データ移行の設定の拡張**を参照してください[データ移行の設定](http://msdn.microsoft.com/en-us/94d7a083-2dbc-4e3d-94dd-92b7ff9d0c2d)  
  
-   **移行エンジン**で、**プロジェクト設定** ダイアログ ボックスの 2 種類のデータ移行のエンジンを viz を使用して、移行プロセスを実行することができます。  
  
    1.  クライアント側のデータ移行のエンジン  
  
    2.  サーバー側のデータ移行のエンジン  
  
**クライアント側のデータの移行:**  
  
-   クライアント側でデータ移行を開始するオプションを選択**クライアント側のデータ移行のエンジン**で、**プロジェクト設定** ダイアログ ボックス。  
  
-   **プロジェクト設定**、**クライアント側のデータ移行のエンジン**オプションは既定で設定します。  
  
    > [!NOTE]  
    > クライアント側のデータ移行のエンジンは、SSMA アプリケーション内にあるし、そのためは、拡張機能パックの可用性に依存しません。  
  
**サーバー側のデータの移行:**  
  
-   サーバー側のデータ移行中に、エンジンは、対象のデータベースに存在します。 拡張機能パックによってインストールされます。 拡張機能パックをインストールする方法の詳細については、次を参照してください[SQL Server (SybaseToSQL) 上の SSMA コンポーネントのインストール。](http://msdn.microsoft.com/en-us/5ad9e12c-2cdb-4dd2-8703-05a23242d19d)  
  
-   サーバー側での移行を開始するには、選択、**サーバー側のデータ移行のエンジン**オプション、**プロジェクト設定**ダイアログ。  
  
> [!NOTE]  
> のみ対象データベースとしての Azure SQL DB を使用する場合**クライアント側のデータ移行**が許可されたサーバー側のデータの移行はサポートされていません。  
  
## <a name="migrating-data-to-sql-server-or-azure-sql-db"></a>SQL Server または Azure SQL DB へのデータの移行  
移行データを一括読み込み操作をトランザクションでの SQL Server テーブルに ASE テーブルから行のデータを移動します。 各トランザクションで SQL Server または Azure SQL DB に読み込まれる行の数は、プロジェクトの設定で構成されます。  
  
移行のメッセージを表示するには、出力ウィンドウが表示されているを確認します。 それ以外の場合、選択**出力**から、**ビュー**メニュー。  
  
**データを移行するには**  
  
1.  次のことを確認します。  
  
    -   ASE プロバイダーは、SSMA を実行しているコンピューターにインストールされます。  
  
    -   ターゲット データベース (SQL Server または Azure SQL DB) と、変換後のオブジェクトを同期しました。  
  
2.  Sybase メタデータ エクスプ ローラーで、移行するデータが含まれているオブジェクトを選択します。  
  
    -   すべてのスキーマのデータを移行する場合は、横にチェック ボックスを選択して**スキーマ**です。  
  
    -   データを移行または個々 のテーブルの省略は、最初にスキーマを展開し、**テーブル**を選択するか、テーブルの横にあるチェック ボックスをオフにします。  
  
3.  データを移行するには、2 つのケースが発生します。  
  
    **クライアント側のデータの移行:**  
  
    実行するため**クライアント側のデータ移行**、select、**クライアント側のデータ移行のエンジン**オプション、**プロジェクト設定** ダイアログ ボックス。  
  
    **サーバー側のデータの移行:**  
  
    -   サーバー側のデータ移行を実行する前に次のように確認します。  
  
        1.  SSMA for Sybase 拡張機能パックは、SQL Server のインスタンスにインストールされています。  
  
        2.  SQL Server のインスタンスで SQL Server エージェント サービスが実行されています。  
  
    -   実行するため**サーバー側のデータ移行**、select、**サーバー側のデータ移行のエンジン**オプション、**プロジェクト設定** ダイアログ ボックス。  
  
4.  右クリック**スキーマ**をクリックして Sybase メタデータ エクスプ ローラーで、**データの移行**です。 個々 のオブジェクトまたはオブジェクトのカテゴリのデータを移行することもできます: オブジェクトまたはその親フォルダーを右クリックして、**データの移行**オプション。  
  
    > [!NOTE]  
    > SSMA for Sybase 拡張機能パックは、SQL Server のインスタンスにインストールされていない場合、**サーバー側のデータ移行のエンジン**が選択されている、ターゲット データベースにデータを移行中に、次のエラーが発生しました: ' SSMA データ移行のコンポーネントが見つかりませんでした、SQL Server のサーバー側のデータ移行を実行できなくなります。 拡張機能パックが正しくインストールされているかどうかを確認してください ' です。 をクリックして**キャンセル**データ移行を終了します。  
  
5.  **Sybase ASE への接続**ダイアログ ボックスで、接続の資格情報を入力し、をクリックして**接続**です。 Sybase ASE への接続の詳細については、次を参照してください[Sybase &#40; への接続。SybaseToSQL &#41;](../../ssma/sybase/connect-to-sybase-sybasetosql.md)  
  
    ターゲット データベースが SQL Server の場合は、次を入力に接続の資格情報、 **SQL Server への接続** ダイアログ ボックスをクリック**接続**です。 SQL Server への接続の詳細については、次を参照してください[SQL Server(SybaseToSQL) への接続。](http://msdn.microsoft.com/en-us/dd368a1a-45b0-40e9-b4d3-5cdb48c26606)  
  
    ターゲット データベースが Azure SQL DB の場合は、接続の資格情報を入力してください。、 **Azure SQL DB への接続**ダイアログ ボックスで、とクリック**接続**です。 Azure SQL DB への接続の詳細については、次を参照してください[Azure SQL DB &#40; に接続する。SybaseToSQL &#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
    メッセージが表示、**出力**ウィンドウです。 移行が完了すると、**データ移行レポート**が表示されます。 すべてのデータが移行されない場合、エラーを含む行をクリックし、をクリックして**詳細**です。 レポートが終了したら、をクリックして**閉じる**です。 データ移行のレポートの詳細については、次を参照してください[データ移行レポート (SSMA 共通)。](http://msdn.microsoft.com/en-us/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> SQL Express エディションは、対象データベースとして使用される、クライアント側のデータの移行のみが許可されているし、サーバー側のデータの移行はサポートされていません。  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB &#40; への Sybase ASE データベースの移行SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
