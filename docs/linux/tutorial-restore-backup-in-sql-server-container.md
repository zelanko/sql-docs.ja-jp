---
title: Docker で SQL Server データベースをリストア |Microsoft Docs
description: このチュートリアルでは、新しい Linux Docker コンテナーで SQL Server データベースのバックアップを復元する方法。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: f688a95135716a41ae37cb86b50bcb90fc6cce5e
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66712819"
---
# <a name="restore-a-sql-server-database-in-a-linux-docker-container"></a>Linux Docker コンテナーでの SQL Server データベースを復元します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

このチュートリアルでは、移動し、Docker で実行されている SQL Server 2017 Linux コンテナー イメージを SQL Server のバックアップ ファイルを復元する方法を示します。

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

このチュートリアルでは、移動し、Docker で実行されている SQL Server 2019 プレビュー Linux コンテナー イメージを SQL Server のバックアップ ファイルを復元する方法を示します。

::: moniker-end

> [!div class="checklist"]
> * プルし、最新の SQL Server Linux コンテナー イメージを実行します。
> * Wide World Importers のデータベース ファイルをコンテナーにコピーします。
> * コンテナー内のデータベースを復元します。
> * データベースを表示したり、TRANSACT-SQL ステートメントを実行します。
> * 変更されたデータベースをバックアップします。

## <a name="prerequisites"></a>前提条件

* サポートされている任意の Linux ディストリビューションの Docker エンジン 1.8 + または Docker for Mac/Windows。 詳細については「[Install Docker](https://docs.docker.com/engine/installation/)」(Docker のインストール) を参照してください。
* 2 GB 以上のディスク領域
* 2 GB 以上の RAM
* [SQL Server on Linux のシステム要件](sql-server-linux-setup.md#system)。

## <a name="pull-and-run-the-container-image"></a>コンテナー イメージのプルと実行

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. Linux または Mac でバッシュ ターミナルまたは Windows 上の管理者特権の PowerShell セッションを開きます。

1. Docker Hub から SQL Server 2017 Linux コンテナー イメージをプルします。

   ```bash
   sudo docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```

   > [!TIP]
   > このチュートリアルでは、bash シェル (Linux または Mac) と PowerShell (Windows) の両方の docker コマンドの例が与えられます。

1. Docker コンテナー イメージを実行するには、次のコマンドを使用できます。

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      --name 'sql1' -p 1401:1433 \
      -v sql1data:/var/opt/mssql \
      -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      --name "sql1" -p 1401:1433 `
      -v sql1data:/var/opt/mssql `
      -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   このコマンドは、Developer edition (既定値) を使用した SQL Server 2017 コンテナーを作成します。 SQL Server ポート**1433**ポートとホスト上で公開される**1401**します。 省略可能な`-v sql1data:/var/opt/mssql`パラメーターは、という名前のデータ ボリューム コンテナーを作成します。 **sql1ddata**します。 これは、SQL Server によって作成されたデータを永続化に使用されます。

   > [!NOTE]
   > コンテナーで実稼働 SQL Server のエディションを実行するためのプロセスは若干異なります。 詳細については 「[実稼働環境のコンテナー イメージを実行する](sql-server-linux-configure-docker.md#production)」を参照してください。 同じコンテナー名とポートを使用する場合、このチュートリアルの残りの部分は、実稼働のコンテナーで引き続き動作します。

1. Docker コンテナーを表示するには、 `docker ps` コマンドを使用します。

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

1. **[STATUS]** 列に **[Up]** の状態が表示されている場合、SQL Server はコンテナーで実行されており、 **[PORTS]** 列に指定されたポートでリッスンしています。 SQL Server コンテナーの **[STATUS]** 列に **[Exited]** と表示されている場合は、[構成ガイドのトラブルシューティングのセクション](sql-server-linux-configure-docker.md#troubleshooting)を参照してください。

  ```bash
  $ sudo docker ps -a

  CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
  941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour    0.0.0.0:1401->1433/tcp   sql1
  ```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. Linux または Mac でバッシュ ターミナルまたは Windows 上の管理者特権の PowerShell セッションを開きます。

1. SQL Server 2019 プレビューの Linux コンテナー イメージを Docker Hub からプルします。

   ```bash
   sudo docker pull mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

   > [!TIP]
   > このチュートリアルでは、bash シェル (Linux または Mac) と PowerShell (Windows) の両方の docker コマンドの例が与えられます。

1. Docker コンテナー イメージを実行するには、次のコマンドを使用できます。

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      --name 'sql1' -p 1401:1433 \
      -v sql1data:/var/opt/mssql \
      -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      --name "sql1" -p 1401:1433 `
      -v sql1data:/var/opt/mssql `
      -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
   ```

   このコマンドは、Developer edition (既定値)、SQL Server 2019 プレビュー コンテナーを作成します。 SQL Server ポート**1433**ポートとホスト上で公開される**1401**します。 省略可能な`-v sql1data:/var/opt/mssql`パラメーターは、という名前のデータ ボリューム コンテナーを作成します。 **sql1ddata**します。 これは、SQL Server によって作成されたデータを永続化に使用されます。

1. Docker コンテナーを表示するには、 `docker ps` コマンドを使用します。

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

1. **[STATUS]** 列に **[Up]** の状態が表示されている場合、SQL Server はコンテナーで実行されており、 **[PORTS]** 列に指定されたポートでリッスンしています。 SQL Server コンテナーの **[STATUS]** 列に **[Exited]** と表示されている場合は、[構成ガイドのトラブルシューティングのセクション](sql-server-linux-configure-docker.md#troubleshooting)を参照してください。

   ```bash
   $ sudo docker ps -a

   CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
   941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour    0.0.0.0:1401->1433/tcp   sql1
   ```

::: moniker-end

## <a name="change-the-sa-password"></a>SA パスワードを変更する

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="copy-a-backup-file-into-the-container"></a>コンテナーにバックアップ ファイルをコピーします。

このチュートリアルでは、 [Wide World Importers サンプル データベース](../sample/world-wide-importers/wide-world-importers-documentation.md)します。 次の手順を使用して、ダウンロードし、Wide World Importers のデータベースのバックアップ ファイルを SQL Server のコンテナーにコピーします。

1. まず、使用して**docker exec**バックアップ フォルダーを作成します。 次のコマンドを作成、 **/var/opt/mssql/backup** SQL Server のコンテナーの内部ディレクトリ。

   ```bash
   sudo docker exec -it sql1 mkdir /var/opt/mssql/backup
   ```

   ```PowerShell
   docker exec -it sql1 mkdir /var/opt/mssql/backup
   ```

1. 次に、ダウンロード、 [、Wideworldimporters-full.bak](https://github.com/Microsoft/sql-server-samples/releases/tag/wide-world-importers-v1.0)をホスト マシンのファイル。 ホーム/ユーザーのディレクトリに移動し、としてバックアップ ファイルをダウンロードする、次のコマンド**wwi.bak**します。

   ```bash
   cd ~
   curl -L -o wwi.bak 'https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak'
   ```

   ```PowerShell
   curl -OutFile "wwi.bak" "https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak"
   ```

1. 使用**docker cp**でコンテナーにバックアップ ファイルをコピーする、 **/var/opt/mssql/backup**ディレクトリ。

   ```bash
   sudo docker cp wwi.bak sql1:/var/opt/mssql/backup
   ```

   ```PowerShell
   docker cp wwi.bak sql1:/var/opt/mssql/backup
   ```

## <a name="restore-the-database"></a>データベースを復元します

バックアップ ファイルは、コンテナー内にあるようになりました。 バックアップを復元する前に、論理ファイル名と、バックアップ内のファイルの種類を知っておく必要です。 次の TRANSACT-SQL コマンドは、バックアップを検査し、復元を使用して、実行**sqlcmd**コンテナー。

> [!TIP]
> このチュートリアルでは**sqlcmd**コンテナー内で事前にインストールされているこのツールを使用して、コンテナーが含まれているためです。 ただし、実行することも TRANSACT-SQL ステートメントの他のクライアントで、コンテナーの外部ツールなど[Visual Studio Code](sql-server-linux-develop-use-vscode.md)または[SQL Server Management Studio](sql-server-linux-manage-ssms.md)します。 に接続するには、コンテナーのポート 1433 にマップされていたホスト ポートを使用します。 この例では**localhost、1401** 、ホスト コンピューター上と**Host_IP_Address、1401**リモートです。

1. 実行**sqlcmd**論理ファイル名と、バックアップ内のパスを列挙するコンテナー内で。 これは、 **RESTORE FILELISTONLY** TRANSACT-SQL ステートメント。

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd -S localhost \
      -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'RESTORE FILELISTONLY FROM DISK = "/var/opt/mssql/backup/wwi.bak"' \
      | tr -s ' ' | cut -d ' ' -f 1-2
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd -S localhost `
      -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "RESTORE FILELISTONLY FROM DISK = '/var/opt/mssql/backup/wwi.bak'"
   ```

   次のような出力が表示されます。

   ```
   LogicalName   PhysicalName
   ------------------------------------------
   WWI_Primary   D:\Data\WideWorldImporters.mdf
   WWI_UserData   D:\Data\WideWorldImporters_UserData.ndf
   WWI_Log   E:\Log\WideWorldImporters.ldf
   WWI_InMemory_Data_1   D:\Data\WideWorldImporters_InMemory_Data_1
   ```

1. 呼び出す、 **RESTORE DATABASE**コンテナー内でデータベースを復元するコマンド。 前の手順でファイルごとに新しいパスを指定します。

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'RESTORE DATABASE WideWorldImporters FROM DISK = "/var/opt/mssql/backup/wwi.bak" WITH MOVE "WWI_Primary" TO "/var/opt/mssql/data/WideWorldImporters.mdf", MOVE "WWI_UserData" TO "/var/opt/mssql/data/WideWorldImporters_userdata.ndf", MOVE "WWI_Log" TO "/var/opt/mssql/data/WideWorldImporters.ldf", MOVE "WWI_InMemory_Data_1" TO "/var/opt/mssql/data/WideWorldImporters_InMemory_Data_1"'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "RESTORE DATABASE WideWorldImporters FROM DISK = '/var/opt/mssql/backup/wwi.bak' WITH MOVE 'WWI_Primary' TO '/var/opt/mssql/data/WideWorldImporters.mdf', MOVE 'WWI_UserData' TO '/var/opt/mssql/data/WideWorldImporters_userdata.ndf', MOVE 'WWI_Log' TO '/var/opt/mssql/data/WideWorldImporters.ldf', MOVE 'WWI_InMemory_Data_1' TO '/var/opt/mssql/data/WideWorldImporters_InMemory_Data_1'"
   ```

   次のような出力が表示されます。

   ```
   Processed 1464 pages for database 'WideWorldImporters', file 'WWI_Primary' on file 1.
   Processed 53096 pages for database 'WideWorldImporters', file 'WWI_UserData' on file 1.
   Processed 33 pages for database 'WideWorldImporters', file 'WWI_Log' on file 1.
   Processed 3862 pages for database 'WideWorldImporters', file 'WWI_InMemory_Data_1' on file 1.
   Converting database 'WideWorldImporters' from version 852 to the current version 869.
   Database 'WideWorldImporters' running the upgrade step from version 852 to version 853.
   Database 'WideWorldImporters' running the upgrade step from version 853 to version 854.
   Database 'WideWorldImporters' running the upgrade step from version 854 to version 855.
   Database 'WideWorldImporters' running the upgrade step from version 855 to version 856.
   Database 'WideWorldImporters' running the upgrade step from version 856 to version 857.
   Database 'WideWorldImporters' running the upgrade step from version 857 to version 858.
   Database 'WideWorldImporters' running the upgrade step from version 858 to version 859.
   Database 'WideWorldImporters' running the upgrade step from version 859 to version 860.
   Database 'WideWorldImporters' running the upgrade step from version 860 to version 861.
   Database 'WideWorldImporters' running the upgrade step from version 861 to version 862.
   Database 'WideWorldImporters' running the upgrade step from version 862 to version 863.
   Database 'WideWorldImporters' running the upgrade step from version 863 to version 864.
   Database 'WideWorldImporters' running the upgrade step from version 864 to version 865.
   Database 'WideWorldImporters' running the upgrade step from version 865 to version 866.
   Database 'WideWorldImporters' running the upgrade step from version 866 to version 867.
   Database 'WideWorldImporters' running the upgrade step from version 867 to version 868.
   Database 'WideWorldImporters' running the upgrade step from version 868 to version 869.
   RESTORE DATABASE successfully processed 58455 pages in 18.069 seconds (25.273 MB/sec).
   ```

## <a name="verify-the-restored-database"></a>復元されたデータベースを確認します。

コンテナー内のデータベース名の一覧を表示する次のクエリを実行します。

```bash
sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
   -Q 'SELECT Name FROM sys.Databases'
```

```PowerShell
docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
   -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
   -Q "SELECT Name FROM sys.Databases"
```

表示する必要があります**WideWorldImporters**データベースの一覧にします。

## <a name="make-a-change"></a>変更を加える

次の手順では、データベースの変更を加えます。

1. 内の上位 10 個の項目を表示するクエリを実行、 **Warehouse.StockItems**テーブル。

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'SELECT TOP 10 StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems ORDER BY StockItemID'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "SELECT TOP 10 StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems ORDER BY StockItemID"
   ```

   項目の識別子と名前の一覧が表示されます。

   ```
   StockItemID StockItemName
   ----------- -----------------
             1 USB missile launcher (Green)
             2 USB rocket launcher (Gray)
             3 Office cube periscope (Black)
             4 USB food flash drive - sushi roll
             5 USB food flash drive - hamburger
             6 USB food flash drive - hot dog
             7 USB food flash drive - pizza slice
             8 USB food flash drive - dim sum 10 drive variety pack
             9 USB food flash drive - banana
            10 USB food flash drive - chocolate bar
   ```

1. 次の最初の項目の説明を更新**UPDATE**ステートメント。

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'UPDATE WideWorldImporters.Warehouse.StockItems SET StockItemName="USB missile launcher (Dark Green)" WHERE StockItemID=1; SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "UPDATE WideWorldImporters.Warehouse.StockItems SET StockItemName='USB missile launcher (Dark Green)' WHERE StockItemID=1; SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1"
   ```

   次のテキストのような出力が表示されます。

   ```
   (1 rows affected)
   StockItemID StockItemName
   ----------- ------------------------------------
             1 USB missile launcher (Dark Green)
   ```

## <a name="create-a-new-backup"></a>新しいバックアップを作成します。

コンテナーに、データベースを復元した後も定期的に実行中のコンテナー内のデータベースのバックアップを作成する可能性があります。 手順は、前の手順が逆の順序で同様のパターンに従います。

1. 使用して、 **BACKUP DATABASE**コンテナーにデータベースのバックアップを作成する TRANSACT-SQL コマンド。 このチュートリアルは、新しいバックアップ ファイルを作成します。 **wwi_2.bak**、以前に作成したで **/var/opt/mssql/backup**ディレクトリ。

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q "BACKUP DATABASE [WideWorldImporters] TO DISK = N'/var/opt/mssql/backup/wwi_2.bak' WITH NOFORMAT, NOINIT, NAME = 'WideWorldImporters-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "BACKUP DATABASE [WideWorldImporters] TO DISK = N'/var/opt/mssql/backup/wwi_2.bak' WITH NOFORMAT, NOINIT, NAME = 'WideWorldImporters-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
   ```

   次のような出力が表示されます。

   ```
   10 percent processed.
   20 percent processed.
   30 percent processed.
   40 percent processed.
   50 percent processed.
   60 percent processed.
   70 percent processed.
   Processed 1200 pages for database 'WideWorldImporters', file 'WWI_Primary' on file 1.
   Processed 53096 pages for database 'WideWorldImporters', file 'WWI_UserData' on file 1.
   80 percent processed.
   Processed 3865 pages for database 'WideWorldImporters', file 'WWI_InMemory_Data_1' on file 1.
   Processed 938 pages for database 'WideWorldImporters', file 'WWI_Log' on file 1.
   100 percent processed.
   BACKUP DATABASE successfully processed 59099 pages in 25.056 seconds (18.427 MB/sec).
   ```

1. 次に、コンテナーから、ホスト マシンには、バックアップ ファイルをコピーします。

   ```bash
   cd ~
   sudo docker cp sql1:/var/opt/mssql/backup/wwi_2.bak wwi_2.bak
   ls -l wwi*
   ```

   ```PowerShell
   cd ~
   docker cp sql1:/var/opt/mssql/backup/wwi_2.bak wwi_2.bak
   ls -l wwi*
   ```

## <a name="use-the-persisted-data"></a>永続化されたデータを使用します。

データベースのバックアップを取得し、データを保護するため、データ ボリューム コンテナーを使用することもできます。 このチュートリアルの作成の開始、 **sql1**のコンテナー、`-v sql1data:/var/opt/mssql`パラメーター。 **Sql1data**データ ボリューム コンテナーが解決しない、 **/var/opt/mssql**データ、コンテナーが削除された後にもします。 次の手順を完全に削除、 **sql1**コンテナーし、新しいコンテナーを作成および**sql2**、永続化されたデータ。

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

1. 停止、 **sql1**コンテナー。

   ```bash
   sudo docker stop sql1
   ```

   ```PowerShell
   docker stop sql1
   ```

1. コンテナーを削除します。 これは削除されません、以前に作成した**sql1data**データ ボリューム コンテナーと、永続化されたデータ。

   ```bash
   sudo docker rm sql1
   ```

   ```PowerShell
   docker rm sql1
   ```

1. 新しいコンテナーを作成**sql2**、再利用し、 **sql1data**データ ボリューム コンテナー。

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      --name 'sql2' -e 'MSSQL_PID=Developer' -p 1401:1433 \
      -v sql1data:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      --name "sql2" -e "MSSQL_PID=Developer" -p 1401:1433 `
      -v sql1data:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
   ```

1. Wide World Importers のデータベースに新しいコンテナーになります。 以前の変更を行ったことを確認するためのクエリを実行します。

   ```bash
   sudo docker exec -it sql2 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1'
   ```

   ```PowerShell
   docker exec -it sql2 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1"
   ```

   > [!NOTE]
   > SA パスワードは、指定したパスワードではありません、 **sql2**コンテナー、`MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>`します。 すべての SQL Server のデータが復元された**sql1**チュートリアルの前半でから変更されたパスワードを含むです。 実際には、このようないくつかのオプションは/var/opt/mssql でデータを復元するために無視されます。 このため、パスワードは`<YourNewStrong!Passw0rd>`次のようにします。

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

1. 停止、 **sql1**コンテナー。

   ```bash
   sudo docker stop sql1
   ```

   ```PowerShell
   docker stop sql1
   ```

1. コンテナーを削除します。 これは削除されません、以前に作成した**sql1data**データ ボリューム コンテナーと、永続化されたデータ。

   ```bash
   sudo docker rm sql1
   ```

   ```PowerShell
   docker rm sql1
   ```

1. 新しいコンテナーを作成**sql2**、再利用し、 **sql1data**データ ボリューム コンテナー。

    ```bash
    sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
       --name 'sql2' -e 'MSSQL_PID=Developer' -p 1401:1433 \
       -v sql1data:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
       --name "sql2" -e "MSSQL_PID=Developer" -p 1401:1433 `
       -v sql1data:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
    ```

1. Wide World Importers のデータベースに新しいコンテナーになります。 以前の変更を行ったことを確認するためのクエリを実行します。

   ```bash
   sudo docker exec -it sql2 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1'
   ```

   ```PowerShell
   docker exec -it sql2 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1"
   ```

   > [!NOTE]
   > SA パスワードは、指定したパスワードではありません、 **sql2**コンテナー、`MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>`します。 すべての SQL Server のデータが復元された**sql1**チュートリアルの前半でから変更されたパスワードを含むです。 実際には、このようないくつかのオプションは/var/opt/mssql でデータを復元するために無視されます。 このため、パスワードは`<YourNewStrong!Passw0rd>`次のようにします。

::: moniker-end

## <a name="next-steps"></a>次のステップ

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

このチュートリアルでは、Windows 上のデータベースをバックアップし、SQL Server 2017 を実行している Linux サーバーに移動する方法について説明しました。 学習したします。

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

このチュートリアルでは、Windows 上のデータベースをバックアップし、SQL Server 2019 preview を実行して、Linux サーバーに移動する方法について説明しました。 学習したします。

::: moniker-end

> [!div class="checklist"]
> * SQL Server Linux コンテナー イメージを作成します。
> * SQL Server データベースのバックアップをコンテナーにコピーします。
> * コンテナー内の TRANSACT-SQL ステートメントを実行**sqlcmd**します。
> * 作成し、コンテナーからバックアップ ファイルを抽出します。
> * Docker でのデータ ボリューム コンテナーを使用して、SQL Server のデータを保持します。

次に、その他の Docker の構成とトラブルシューティングのシナリオを確認します。

> [!div class="nextstepaction"]
>[Docker で SQL Server 2017 の構成ガイド](sql-server-linux-configure-docker.md)
