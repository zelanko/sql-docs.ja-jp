---
title: データベースの復元
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) のマスター インスタンスにデータベースを復元する方法を示します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: cc1fddfd7aa2e3400dda3d005eb365cde7364dd4
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860314"
---
# <a name="restore-a-database-into-the-sql-server-big-data-cluster-master-instance"></a>SQL Server ビッグ データ クラスターのマスター インスタンスにデータベースを復元します。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) のマスター インスタンスに既存のデータベースを復元する方法について説明します。 使用して、バックアップ、コピー、およびアプローチを復元することをお勧めします。

## <a name="backup-your-existing-database"></a>既存のデータベースをバックアップします。

最初に、Windows 上のいずれかの SQL Server または Linux から、既存の SQL Server データベースをバックアップします。 Transact-sql または SQL Server Management Studio (SSMS) などのツールでは、標準的なバックアップの手法を使用します。

この記事では、AdventureWorks データベースを復元する方法を示していますが、データベースのバックアップを使用することができます。 

> [!TIP]
> AdventureWorks のバックアップをダウンロードする[ここ](https://www.microsoft.com/download/details.aspx?id=49502)します。

## <a name="copy-the-backup-file"></a>バックアップ ファイルをコピーします。

Kubernetes クラスターのマスター インスタンス ポッドの SQL Server のコンテナーにバックアップ ファイルをコピーします。

```bash
kubectl cp <path to .bak file> mssql-master-pool-0:/tmp -c mssql-server -n <name of your cluster>
```

例:

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak mssql-master-pool-0:/tmp -c mssql-server -n clustertest
```

ポッドのコンテナーにバックアップ ファイルをコピーすることを確認してください。

```bash
kubectl exec -it mssql-master-pool-0 -n <name of your cluster> -c mssql-server -- bin/bash
cd /var/
ls /tmp
exit
```

例:

```bash
kubectl exec -it mssql-master-pool-0 -n clustertest -c mssql-server -- bin/bash
ls /tmp
exit
```

## <a name="restore-the-backup-file"></a>バックアップ ファイルを復元します。

次に、マスター インスタンス SQL Server データベースのバックアップを復元します。  Windows 上に作成されたデータベースのバックアップを復元する場合は、ファイルの名前を取得する必要があります。  Azure Data Studio では、マスター インスタンスに接続し、この SQL スクリプトを実行します。

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/<db file name>.bak'
```

例:

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
```

![バックアップ ファイルの一覧](media/restore-database/database-restore-file-list.png)

ここで、データベースを復元します。 次のスクリプトでは、例を示します。 データベースのバックアップによって必要に応じて、名前とパスに置き換えます。

```sql
RESTORE DATABASE AdventureWorks2016CTP3
FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
WITH MOVE 'AdventureWorks2016CTP3_Data' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Data.mdf',
        MOVE 'AdventureWorks2016CTP3_Log' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Log.ldf',
        MOVE 'AdventureWorks2016CTP3_mod' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_mod'
```

## <a name="configure-data-pool-and-hdfs-access"></a>データのプールと HDFS へのアクセスを構成します。

ここで、マスター インスタンスの SQL Server へのアクセスのデータ プールおよび HDFS のデータ プールと記憶域プールに格納されている手順を実行します。 新しく復元されたデータベースに対して次の TRANSACT-SQL スクリプトを実行します。

```sql
USE AdventureWorks2016CTP3
GO
-- Create the SqlDataPool data source:
IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
  CREATE EXTERNAL DATA SOURCE SqlDataPool
  WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');

-- Create the SqlStoragePool data source:
IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
BEGIN
  IF SERVERPROPERTY('ProductLevel') = 'CTP2.3'
    CREATE EXTERNAL DATA SOURCE SqlStoragePool
    WITH (LOCATION = 'sqlhdfs://service-mssql-controller:8080');
  ELSE IF SERVERPROPERTY('ProductLevel') = 'CTP2.4'
    CREATE EXTERNAL DATA SOURCE SqlStoragePool
    WITH (LOCATION = 'sqlhdfs://service-master-pool:50070');
END
GO
```

> [!NOTE]
> SQL Server の以前のバージョンから復元されたデータベースに対してのみこれらのセットアップ スクリプトを実行する必要があります。 Master の SQL Server インスタンスで新しいデータベースを作成する場合のデータ プールと記憶域プールのストアド プロシージャが既に構成します。

## <a name="next-steps"></a>次のステップ

SQL Server のビッグ データ クラスターに関する詳細については、次の概要を参照してください。

- [SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)
