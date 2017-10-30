---
title: "Docker で SQL Server データベースをリストア |Microsoft ドキュメント"
description: "このチュートリアルには表示は、新しい Linux Docker コンテナーでの SQL Server データベースのバックアップを復元する方法です。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 51f60c4fecb56aca3f4fb007f8e6a68601a47d11
ms.openlocfilehash: 1f3cc214be4eaac2199c17c3bea1da7fd02956f1
ms.contentlocale: ja-jp
ms.lasthandoff: 10/14/2017

---
# <a name="restore-a-sql-server-database-in-a-linux-docker-container"></a>Linux Docker コンテナーでの SQL Server データベースを復元します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このチュートリアルでは、移動して、Docker で実行されている SQL Server 2017 Linux コンテナー イメージに SQL Server のバックアップ ファイルを復元する方法を示します。

> [!div class="checklist"]
> * プルし、最新の SQL Server 2017 Linux コンテナー イメージを実行します。
> * コンテナーには、World Wide Importers のデータベース ファイルをコピーします。
> * コンテナー内のデータベースを復元します。
> * 表示およびデータベースを変更する TRANSACT-SQL ステートメントを実行します。
> * 変更されたデータベースをバックアップします。

## <a name="prerequisites"></a>前提条件

* Docker エンジン 1.8 + 任意の Linux ディストリビューションまたは Docker は Mac/windows のサポート。 詳細については、次を参照してください。[インストール Docker](https://docs.docker.com/engine/installation/)です。
* 4 GB のディスク領域の最小値
* 4 GB の RAM の最小値
* [Linux 上の SQL Server のシステム要件](sql-server-linux-setup.md#system)です。

> [!IMPORTANT]
> Mac 用 Docker と Docker for Windows での既定値は Moby VM 用に 2 GB は、4 GB に変更する必要があります。 Mac で Windows を実行している場合を使用して、メモリ設定を増やす、 [Docker クイック スタート手順](quickstart-install-connect-docker.md)です。

## <a name="pull-and-run-the-container-image"></a>プルし、コンテナー イメージを実行

1. Linux または Mac でバッシュ端末または Windows 上の管理者特権の PowerShell セッションを開きます。

1. SQL Server 2017 Linux コンテナー イメージを Docker Hub からプルします。

    ```bash
    sudo docker pull microsoft/mssql-server-linux:2017-latest
    ```

    ```PowerShell
    docker pull microsoft/mssql-server-linux:2017-latest
    ```

    > [!TIP]
    > このチュートリアルでは、docker コマンドの例は、bash シェル (Linux または Mac) と PowerShell (Windows) の両方で与えられます。

1. Docker によってコンテナー イメージを実行するには、次のコマンドを使用することができます。

    ```bash
    sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
       --name 'sql1' -p 1401:1433 \
       -v sql1data:/var/opt/mssql \
       -d microsoft/mssql-server-linux:2017-latest
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
       --name "sql1" -p 1401:1433 `
       -v sql1data:/var/opt/mssql `
       -d microsoft/mssql-server-linux:2017-latest
    ```

    このコマンドは、Developer edition (既定値) を SQL Server 2017 コンテナーを作成します。 SQL Server ポート**1433**ポートとして、ホストで公開された**1401**です。 省略可能な`-v sql1data:/var/opt/mssql`パラメーターという名前のデータ ボリューム コンテナーを作成する**sql1ddata**です。 SQL Server によって作成されたデータの保持に使用されます。

   > [!NOTE]
   > コンテナーで実稼働 SQL Server のエディションを実行するためのプロセスは若干異なります。 詳細については、次を参照してください。[実稼働環境にコンテナー イメージを実行](sql-server-linux-configure-docker.md#production)です。 同じコンテナー名とポートを使用する場合、このチュートリアルの残りの部分は実稼働のコンテナーで動作します。

1. 表示するには、Docker コンテナーを使用して、`docker ps`コマンド。

    ```bash
    sudo docker ps -a
    ```

    ```PowerShell
    docker ps -a
    ```
 
1. 場合、**ステータス**項目のステータスを表示**を**、コンテナー内の SQL Server を実行しとで指定されたポートでリッスンしている、**ポート**列です。 場合、**ステータス**列、SQL Server のコンテナーの番組を**Exited**を参照してください、[構成ガイド」のセクションのトラブルシューティング](sql-server-linux-configure-docker.md#troubleshooting)です。

   ```
   $ sudo docker ps -a

   CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
   941e1bdf8e1d        microsoft/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour    0.0.0.0:1401->1433/tcp   sql1
   ```

## <a name="change-the-sa-password"></a>SA パスワードを変更します。

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="copy-a-backup-file-into-the-container"></a>コンテナーにバックアップ ファイルをコピーします。

このチュートリアルでは、 [Wide World Importers のサンプル データベース](../sample/world-wide-importers/wide-world-importers-documentation.md)です。 ダウンロードし、SQL Server のコンテナーに、Wide World importers 社のデータベースのバックアップ ファイルをコピーするには、次の手順を使用します。

1. まず、使用して**docker exec**バックアップ フォルダーを作成します。 次のコマンドは、作成、 **/var/optmssql/** SQL Server のコンテナー内のディレクトリ。

   ```bash
   sudo docker exec -it sql1 mkdir /var/opt/mssql/backup
   ```

   ```PowerShell
   docker exec -it sql1 mkdir /var/opt/mssql/backup
   ```

1. 次に、ダウンロード、 [、Wideworldimporters-full.bak](https://github.com/Microsoft/sql-server-samples/releases/tag/wide-world-importers-v1.0)ホスト マシンのファイルです。 ホーム/ユーザー ディレクトリに移動し、として、バックアップ ファイルをダウンロード、次のコマンド**wwi.bak**です。

   ```bash
   cd ~
   curl -L -o wwi.bak 'https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak'
   ```

   ```PowerShell
   curl -OutFile "wwi.bak" "https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak"
   ```

1. 使用して**docker cp**内のコンテナーにバックアップ ファイルをコピーする、 **/var/opt/mssql/backup**ディレクトリ。

   ```bash
   sudo docker cp wwi.bak sql1:/var/opt/mssql/backup
   ```

   ```PowerShell
   docker cp wwi.bak sql1:/var/opt/mssql/backup
   ```

## <a name="restore-the-database"></a>データベースを復元します

バックアップ ファイルは、コンテナー内にあるようになりました。 バックアップを復元する前には、論理ファイル名とバックアップ内のファイルの種類を知る必要があります。 次の TRANSACT-SQL コマンドは、バックアップを検査しを使用して復元を実行**sqlcmd**コンテナーにします。

> [!TIP]
> このチュートリアルでは使用**sqlcmd**コンテナーの中、コンテナーがプレインストールされてこの tool に付属しているためです。 ただし、実行することも TRANSACT-SQL ステートメントの他のクライアントと、コンテナーの外部ツールなど[Visual Studio Code](sql-server-linux-develop-use-vscode.md)または[SQL Server Management Studio](sql-server-linux-develop-use-ssms.md)です。 接続するには、コンテナーのポート 1433 にマップされたホスト ポートを使用します。 この例ではその**localhost、1401**ホスト コンピューター上および**Host_IP_Address、1401**リモートです。

1. 実行**sqlcmd**論理ファイルの名前と、バックアップ内のパスを一覧に、コンテナー内です。 これは、 **RESTORE FILELISTONLY** TRANSACT-SQL ステートメント。

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

1. 呼び出す、 **RESTORE DATABASE**コマンド、コンテナー内のデータベースを復元します。 前の手順で、ファイルごとには、新しいパスを指定します。

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

## <a name="verify-the-restored-database"></a>復元されたデータベースを確認してください。

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

表示されるはず**WideWorldImporters**データベースの一覧にします。

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

   項目の識別子および名前の一覧が表示されます。

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

1. 次の最初の項目の説明を更新**更新**ステートメント。

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

コンテナーに、データベースを復元した後、実行中のコンテナー内のデータベースのバックアップを定期的に作成することがもできます。 手順は、前の手順には、逆の順序で同様のパターンに従います。

1. 使用して、**データベースのバックアップ**コンテナーに、データベースのバックアップを作成する TRANSACT-SQL コマンド。 このチュートリアルで作成、新しいバックアップ ファイル**wwi_2.bak**、以前に作成したで**/var/opt/mssql/backup**ディレクトリ。

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

1. 次に、コンテナかられ、ホスト コンピューターには、バックアップ ファイルをコピーします。

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

## <a name="use-the-persisted-data"></a>持続データを使用します。

データベースのバックアップを取得し、データを保護するため、データ ボリューム コンテナーを使用することもできます。 作成されたこのチュートリアルの先頭、 **sql1**のコンテナー、`-v sql1data:/var/opt/mssql`パラメーター。 **Sql1data**データ ボリューム コンテナーが引き続き発生する、 **/var/opt/mssql**データ コンテナーを削除した後でもです。 次の手順を完全に削除、 **sql1**コンテナーして新しいコンテナーを作成して**sql2**、永続化されたデータを使用します。

1. 停止、 **sql1**コンテナーです。

   ```bash
   sudo docker stop sql1
   ```

   ```PowerShell
   docker stop sql1
   ```

1. コンテナーを削除します。 これは削除されません、以前に作成した**sql1data**データ ボリューム コンテナーとの永続化されたデータ。

   ```bash
   sudo docker rm sql1
   ```

   ```PowerShell
   docker rm sql1
   ```

1. 新しいコンテナーを作成**sql2**、再利用して、 **sql1data**データ ボリューム コンテナーです。

    ```bash
    sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
       --name 'sql2' -e 'MSSQL_PID=Developer' -p 1401:1433 \
       -v sql1data:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
       --name "sql2" -e "MSSQL_PID=Developer" -p 1401:1433 `
       -v sql1data:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
    ```

1. Wide World importers 社のデータベースの新しいコンテナーが開始されました。 クエリを実行して、前の変更を行ったことを確認します。

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
   > SA パスワードが指定したパスワードではありません、 **sql2**コンテナー、`MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>`です。 復元されたすべての SQL Server データ**sql1**チュートリアルの前にから変更されたパスワードを含みます。 実際には、次のようにいくつかのオプションは/var/opt/mssql 内のデータを復元するために無視されます。 このため、パスワードが`<YourNewStrong!Passw0rd>`次に示すようにします。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Windows 上のデータベースをバックアップし、SQL Server 2017 RC2 を実行する Linux サーバーに移動する方法について学習しました。 方法を学習します。
> [!div class="checklist"]
> * SQL Server 2017 Linux コンテナー イメージを作成します。
> * SQL Server データベースのバックアップをコンテナーにコピーします。
> * コンテナー内の TRANSACT-SQL ステートメントを実行**sqlcmd**です。
> * 作成し、コンテナーからのバックアップ ファイルを抽出します。
> * Docker でデータ ボリューム コンテナーを使用して、SQL Server のデータを保持します。

次に、他の Docker 構成とトラブルシューティングのシナリオを確認します。

> [!div class="nextstepaction"]
>[Docker での SQL Server 2017 について構成ガイド](sql-server-linux-configure-docker.md)

