---
title: バックアップし、Linux 上の SQL Server データベースの復元 |Microsoft Docs
description: バックアップおよび Linux 上の SQL Server データベースを復元する方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 11/14/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: d30090fb-889f-466e-b793-5f284fccc4e6
ms.openlocfilehash: f07885aaef22da63d1c94e669db17e7536ccc933
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66713345"
---
# <a name="backup-and-restore-sql-server-databases-on-linux"></a>Linux に SQL Server データベースのバックアップと復元

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

その他のプラットフォームと同じツールで、SQL Server 2017 on Linux からのデータベースのバックアップを実行できます。 Linux サーバーで使用することができます**sqlcmd** SQL Server に接続し、バックアップを実行します。 、Windows からは、Linux 上の SQL Server に接続して、ユーザー インターフェイスとバックアップを実行します。 バックアップの機能は、プラットフォーム間で同じです。 ローカル、リモート ドライブ、またはデータベースをバックアップするなど、 [Microsoft Azure Blob ストレージ サービス](../relational-databases/backup-restore/sql-server-backup-to-url.md)します。

## <a name="backup-a-database"></a>データベースのバックアップ

次の例では**sqlcmd**はローカルの SQL Server インスタンスに接続し、という名前のユーザー データベースのバックアップは、完全な`demodb`します。

```bash
sqlcmd -S localhost -U SA -Q "BACKUP DATABASE [demodb] TO DISK = N'/var/opt/mssql/data/demodb.bak' WITH NOFORMAT, NOINIT, NAME = 'demodb-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
```

コマンドを実行するときに SQL Server は、パスワードの入力を求められます。 パスワードを入力すると、シェルはバックアップの進行状況の結果を返します。 以下に例を示します。

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

完全復旧モデルがデータベースにある場合より詳細な復元オプションのトランザクション ログ バックアップこともできます。 次の例では、 **sqlcmd**はローカルの SQL Server インスタンスに接続し、トランザクション ログ バックアップは、します。

```bash
sqlcmd -S localhost -U SA -Q "BACKUP LOG [demodb] TO DISK = N'/var/opt/mssql/data/demodb_LogBackup.bak' WITH NOFORMAT, NOINIT, NAME = N'demodb_LogBackup', NOSKIP, NOREWIND, NOUNLOAD, STATS = 5"
```

## <a name="restore-a-database"></a>データベースの復元

次の例では**sqlcmd**は SQL Server のローカル インスタンスに接続し、demodb データベースを復元します。 なお、`NORECOVERY`のログ ファイルのバックアップの復元を追加できるようにするオプションを使用します。 追加のログ ファイルを復元する予定がない場合は、削除、`NORECOVERY`オプション。

```bash
sqlcmd -S localhost -U SA -Q "RESTORE DATABASE [demodb] FROM DISK = N'/var/opt/mssql/data/demodb.bak' WITH FILE = 1, NOUNLOAD, REPLACE, NORECOVERY, STATS = 5"
```

> [!TIP]
> 誤って、NORECOVERY を使用しても、追加のログ ファイルのバックアップがない場合のコマンドを実行します。`RESTORE DATABASE demodb`追加のパラメーターはなし。 これは、復元が完了するし、データベースを運用のままになります。

### <a name="restore-the-transaction-log"></a>トランザクション ログを復元します。

次のコマンドは、前のトランザクション ログ バックアップを復元します。

```bash
sqlcmd -S localhost -U SA -Q "RESTORE LOG demodb FROM DISK = N'/var/opt/mssql/data/demodb_LogBackup.bak'"
```

## <a name="backup-and-restore-with-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) でバックアップと復元

Windows コンピューターから SSMS を使用して、Linux データベースに接続し、ユーザー インターフェイスからバックアップを実行することができます。

>[!NOTE] 
> 最新バージョンの SSMS を使用して、SQL Server に接続します。 ダウンロードして、最新バージョンをインストールを参照してください。 [SSMS のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)します。 SSMS を使用する方法の詳細については、次を参照してください。 [Linux 上の SQL Server の管理を使用して SSMS](sql-server-linux-manage-ssms.md)します。

SSMS を使用したバックアップを利用して、次の手順が説明します。 

1. SSMS を起動し、SQL Server 2017 on Linux で、サーバーに接続します。

1. オブジェクト エクスプ ローラーをクリックして、データベースを右クリックし**タスク**、 をクリックし、**をバックアップしています.** .

1. **データベースのバックアップ**ダイアログ ボックスで、パラメーターとオプションを確認し、クリックして**OK**。
 
SQL Server では、データベースのバックアップを完了します。

### <a name="restore-with-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) を使用して復元します。 

次の手順には、SSMS でデータベースを復元について説明します。

1. SSMS で、右クリック**データベース**クリック**データベースの復元しています.** . 

1. **ソース**クリックして**デバイス:** 省略記号 (...) を順にクリックします。

1. データベースのバックアップ ファイルを見つけてクリックして**OK**します。 

1. **復元プラン**、バックアップ ファイルと設定を確認します。 **[OK]** をクリックします。 

1. SQL Server では、データベースを復元します。 

## <a name="see-also"></a>関連項目

* [データベースの完全バックアップ (SQL Server) の作成します。](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)
* [トランザクション ログ (SQL Server) をバックアップします。](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)
* [BACKUP (Transact-SQL)](../t-sql/statements/backup-transact-sql.md)
* [SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md)
