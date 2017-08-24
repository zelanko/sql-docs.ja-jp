---
title: "バックアップし、Linux 上の SQL Server データベースを復元 |Microsoft ドキュメント"
description: "バックアップおよび、Linux 上の SQL Server データベースを復元する方法を説明します。"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: d30090fb-889f-466e-b793-5f284fccc4e6
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 6bd05a89f0c06bc03de931b898be18f3cbea0c8c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="backup-and-restore-sql-server-databases-on-linux"></a>Linux 上のバックアップと復元の SQL Server データベース

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

他のプラットフォームと同じツールを使用して、Linux 上の SQL Server 2017 RC2 からのデータベースのバックアップを実行できます。 使用することができます、Linux サーバー `sqlcmd` SQL Server に接続し、バックアップを実行します。 Windows は、Linux 上の SQL Server に接続し、ユーザー インターフェイスとバックアップを実行します。 バックアップ機能は、プラットフォーム間で同じです。 ローカルをリモート ドライブ、またはデータベースをバックアップするなど、 [Microsoft Azure Blob ストレージ サービス](http://msdn.microsoft.com/library/dn435916.aspx)です。 

## <a name="backup-with-sqlcmd"></a>Sqlcmd でのバックアップ

次の例で`sqlcmd`ローカルの SQL Server インスタンスに接続し、完全をという名前のユーザー データベースのバックアップにかかる`demodb`です。

```bash
sqlcmd -H localhost -U SA -Q "BACKUP DATABASE [demodb] TO DISK = N'var/opt/mssql/data/demodb.bak' WITH NOFORMAT, NOINIT, NAME = 'demodb-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
```

コマンドを実行するときに、SQL Server は、パスワードを求められます。 パスワードを入力した後は、シェルがバックアップの進行状況の結果を返します。 例:

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

### <a name="backup-log-with-sqlcmd"></a>Sqlcmd でのバックアップのログ

次の例では、`sqlcmd`はローカルの SQL Server インスタンスに接続し、ログ末尾のバックアップを取得します。 ログ末尾のバックアップが完了したら、データベースは復元中の状態になります。 

```bash
sqlcmd -H localhost -U SA -Q "BACKUP LOG [demodb] TO  DISK = N'var/opt/mssql/data/demodb_LogBackup_2016-11-14_18-09-53.bak' WITH NOFORMAT, NOINIT,  NAME = N'demodb_LogBackup_2016-11-14_18-09-53', NOSKIP, NOREWIND, NOUNLOAD,  NORECOVERY ,  STATS = 5"
```


## <a name="restore-with-sqlcmd"></a>Sqlcmd での復元します。

次の例で`sqlcmd`は SQL Server のローカル インスタンスに接続し、データベースを復元します。

```bash
sqlcmd -H localhost -U SA -Q "RESTORE DATABASE [demodb] FROM  DISK = N'var/opt/mssql/data/demodb.bak' WITH  FILE = 1,  NOUNLOAD,  REPLACE,  STATS = 5"
```

## <a name="backup-and-restore-with-sql-server-management-studio-ssms"></a>Backup and Restore with SQL Server Management Studio (SSMS)

Windows コンピューターからは、SSMS を使用して、Linux データベースに接続し、ユーザー インターフェイスからバックアップを実行することができます。 

>[!NOTE] 
> SQL Server に接続するには、SSMS の最新バージョンを使用します。 ダウンロードして、最新バージョンをインストールを参照してください。 [SSMS のダウンロード](http://msdn.microsoft.com/library/mt238290.aspx)です。 

次の手順では、SSMS でのバックアップの作成について説明します。 

1. SSMS を起動し、Linux 上の SQL Server 2017 RC2 内のサーバーに接続します。

1. オブジェクト エクスプ ローラーでをクリックして、データベースを右クリックして**タスク**、クリックして**をバックアップしています.**.

1. **データベースのバックアップ**ダイアログ ボックスで、パラメーターとオプションを確認し、をクリックして**OK**です。
 
SQL Server では、データベースのバックアップを完了します。

詳細については、次を参照してください。 [Linux 上の SQL Server の管理を使用して SSMS](sql-server-linux-manage-ssms.md)です。

### <a name="restore-with-sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS) を使用して復元します。 

次の手順では、SSMS でデータベースを復元について説明します。

1. SSMS で、右クリック**データベース** をクリック**データベースの復元しています.**. 

1. [**ソース**] をクリックして**デバイス:**省略記号 (...) をクリックします。

1. データベースのバックアップ ファイルを見つけてクリックして**OK**です。 

1. **復元プラン**、バックアップ ファイルと設定を確認します。 **[OK]**をクリックします。 

1. SQL Server では、データベースを復元します。 

## <a name="see-also"></a>参照

* [データベースの完全バックアップ (SQL Server) を作成します。](http://msdn.microsoft.com/library/ms187510.aspx)
* [トランザクション ログ (SQL Server) のバックアップします。](http://msdn.microsoft.com/library/ms179478.aspx)
* [BACKUP (Transact-SQL)](http://msdn.microsoft.com/library/ms186865.aspx)
* [SQL Server Backup to URL](http://msdn.microsoft.com/library/dn435916.aspx)

