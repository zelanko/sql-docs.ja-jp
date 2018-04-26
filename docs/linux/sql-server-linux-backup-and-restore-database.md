---
title: バックアップし、Linux 上の SQL Server データベースを復元 |Microsoft ドキュメント
description: バックアップおよび、Linux 上の SQL Server データベースを復元する方法を説明します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 11/14/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: d30090fb-889f-466e-b793-5f284fccc4e6
ms.workload: On Demand
ms.openlocfilehash: e46a11d935b06f7b2d491c716aa6119dc08f19dd
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="backup-and-restore-sql-server-databases-on-linux"></a>Linux 上のバックアップと復元の SQL Server データベース

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

他のプラットフォームと同じツールを使用して、Linux 上の SQL Server 2017 からのデータベースのバックアップを実行できます。 使用することができます、Linux サーバー **sqlcmd** SQL Server に接続し、バックアップを実行します。 Windows は、Linux 上の SQL Server に接続し、ユーザー インターフェイスとバックアップを実行します。 バックアップ機能は、プラットフォーム間で同じです。 ローカルをリモート ドライブ、またはデータベースをバックアップするなど、 [Microsoft Azure Blob ストレージ サービス](../relational-databases/backup-restore/sql-server-backup-to-url.md)です。

## <a name="backup-a-database"></a>データベースのバックアップ

次の例で**sqlcmd**ローカルの SQL Server インスタンスに接続し、完全をという名前のユーザー データベースのバックアップにかかる`demodb`です。

```bash
sqlcmd -S localhost -U SA -Q "BACKUP DATABASE [demodb] TO DISK = N'/var/opt/mssql/data/demodb.bak' WITH NOFORMAT, NOINIT, NAME = 'demodb-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
```

コマンドを実行するときに、SQL Server は、パスワードを求められます。 パスワードを入力した後は、シェルがバックアップの進行状況の結果を返します。 以下に例を示します。

```
Password:
10 percent processed.
21 percent processed.
32 percent processed.
40 percent processed.
51 percent processed.
61 percent processed.
72 percent processed.
80 percent processed.
91 percent processed.
Processed 296 pages for database 'demodb', file 'demodb' on file 1.
100 percent processed.
Processed 2 pages for database 'demodb', file 'demodb_log' on file 1.
BACKUP DATABASE successfully processed 298 pages in 0.064 seconds (36.376 MB/sec).
```

### <a name="backup-the-transaction-log"></a>トランザクション ログをバックアップします。

データベースが完全復旧モデルの場合はより詳細な復元オプションのトランザクション ログ バックアップもすることができます。 次の例では、 **sqlcmd**ローカルの SQL Server インスタンスに接続し、トランザクション ログのバックアップを受け取る。

```bash
sqlcmd -S localhost -U SA -Q "BACKUP LOG [demodb] TO DISK = N'/var/opt/mssql/data/demodb_LogBackup.bak' WITH NOFORMAT, NOINIT, NAME = N'demodb_LogBackup', NOSKIP, NOREWIND, NOUNLOAD, STATS = 5"
```

## <a name="restore-a-database"></a>データベースを復元します。

次の例で**sqlcmd**は SQL Server のローカル インスタンスに接続し、demodb データベースを復元します。 なお、`NORECOVERY`のログ ファイルのバックアップの復元を追加できるようにするオプションを使用します。 追加のログ ファイルを復元する予定がない場合は、削除、`NORECOVERY`オプション。

```bash
sqlcmd -S localhost -U SA -Q "RESTORE DATABASE [demodb] FROM DISK = N'/var/opt/mssql/data/demodb.bak' WITH FILE = 1, NOUNLOAD, REPLACE, NORECOVERY, STATS = 5"
```

> [!TIP]
> コマンドを実行を誤って、NORECOVERY を使用していて、追加のログ ファイルのバックアップはありません、`RESTORE DATABASE demodb`追加パラメーターなしでします。 これにより、復元を完了し、運用データベース状態のまま。

### <a name="restore-the-transaction-log"></a>トランザクション ログを復元します。

次のコマンドは、以前のトランザクション ログ バックアップを復元します。

```bash
sqlcmd -S localhost -U SA -Q "RESTORE LOG demodb FROM DISK = N'/var/opt/mssql/data/demodb_LogBackup.bak'"
```

## <a name="backup-and-restore-with-sql-server-management-studio-ssms"></a>Backup and Restore with SQL Server Management Studio (SSMS)

Windows コンピューターからは、SSMS を使用して、Linux データベースに接続し、ユーザー インターフェイスからバックアップを実行することができます。

>[!NOTE] 
> SQL Server に接続するには、SSMS の最新バージョンを使用します。 ダウンロードして、最新バージョンをインストールを参照してください。 [SSMS のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)です。 SSMS を使用する方法の詳細については、次を参照してください。 [Linux 上の SQL Server の管理を使用して SSMS](sql-server-linux-manage-ssms.md)です。

次の手順では、SSMS でのバックアップの作成について説明します。 

1. SSMS を起動し、Linux 上の SQL Server 2017 内のサーバーに接続します。

1. オブジェクト エクスプ ローラーでをクリックして、データベースを右クリックして**タスク**、クリックして**をバックアップしています.**.

1. **データベースのバックアップ**ダイアログ ボックスで、パラメーターとオプションを確認し、をクリックして**OK**です。
 
SQL Server では、データベースのバックアップを完了します。

### <a name="restore-with-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) を使用して復元します。 

次の手順では、SSMS でデータベースを復元について説明します。

1. SSMS で、右クリック**データベース** をクリック**データベースの復元しています.**. 

1. **[ソース]** をクリックして**デバイス:** 省略記号 (...) をクリックします。

1. データベースのバックアップ ファイルを見つけてクリックして**OK**です。 

1. **復元プラン**、バックアップ ファイルと設定を確認します。 **[OK]** をクリックします。 

1. SQL Server では、データベースを復元します。 

## <a name="see-also"></a>参照

* [データベースの完全バックアップ (SQL Server) を作成します。](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)
* [トランザクション ログ (SQL Server) のバックアップします。](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)
* [BACKUP (Transact-SQL)](../t-sql/statements/backup-transact-sql.md)
* [SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md)
