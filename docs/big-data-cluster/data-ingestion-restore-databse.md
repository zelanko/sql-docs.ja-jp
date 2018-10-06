---
title: SQL Server のビッグ データ クラスターへ、データベースの復元 |Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 04514fb0184fa28e0ba959f3dd33cb2e1ec945cb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796446"
---
# <a name="restore-a-database-into-the-sql-server-big-data-cluster-master-instance"></a>SQL Server ビッグ データ クラスターのマスター インスタンスにデータベースを復元します。

既存の SQL Server データベースをマスター インスタンスにまとめるには、私たちには、バックアップ、コピーの使用が推奨し、アプローチを復元します。  この例では、AdventureWorks データベースを復元する方法を紹介しますが、必要のあるデータベースのバックアップを使用することができます。  AdventureWorks のバックアップをダウンロードする[ここ](https://www.microsoft.com/en-us/download/details.aspx?id=49502)します。

最初に、Windows 上のいずれかの SQL Server または Linux を使用してデータベース バックアップの作成の一般的な方法のいずれかで、既存の SQL Server データベースをバックアップします。

Kubernetes クラスターのマスター インスタンス ポッドの SQL Server のコンテナーにバックアップ ファイルをコピーします。

```bash
kubectl cp <path to .bak file> mssql-data-pool-master-0:/tmp/ -c mssql-data-pool-data -n <name of your cluster>
```

例:

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak mssql-data-pool-master-0:/tmp/ -c mssql-data-pool-data -n clustertest
```

ポッドのコンテナーにバックアップ ファイルをコピーすることを確認してください。

```bash
kubectl exec -it mssql-data-pool-master-0 -n <name of your cluster> -c mssql-data-pool-data -- bin/bash
root@mssql-data-pool-master-0:/# ls /tmp
root@mssql-data-pool-master-0:/# exit
```

例:

```bash
kubectl exec -it mssql-data-pool-master-0 -n clustertest -c mssql-data-pool-data -- bin/bash
root@mssql-data-pool-master-0:/# ls /tmp
```

次に、マスター インスタンス SQL Server データベースのバックアップを復元します。  Windows 上に作成されたデータベースのバックアップを復元する場合は、ファイルの名前を取得する必要があります。  マスター インスタンスに接続されている Ops Studio では、この SQL スクリプトを実行します。

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/<db file name>.bak'
```

例:

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
```

![バックアップ ファイルの一覧](media/restore-database/database-restore-file-list.png)

ここで、データベースのバックアップによって必要に応じて、名前とパスを置き換えて、このようなスクリプトを使用してデータベースを復元します。

```sql
RESTORE DATABASE AdventureWorks2016CTP3
FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
WITH MOVE 'AdventureWorks2016CTP3_Data' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Data.mdf',
        MOVE 'AdventureWorks2016CTP3_Log' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Log.ldf',
        MOVE 'AdventureWorks2016CTP3_mod' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_mod'
```

ここで、する場合、値が高いデータベースにアクセスできるデータ プールのデータ プールはストアド プロシージャを開き、GitHub リポジトリからこれらのスクリプトを実行してセットアップする必要があります。

実行、**値-db configuration\data_pool_ddl_install します。SQL**スクリプト。

- セットアップのサポートが格納されている手順

実行、**値-db configuration\supportability します。SQL**スクリプト。
