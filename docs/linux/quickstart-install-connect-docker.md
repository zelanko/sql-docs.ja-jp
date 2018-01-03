---
title: "SQL Server 2017 Docker を使ってみる |Microsoft ドキュメント"
description: "このクイック スタートでは、Docker を使用して、SQL Server 2017 コンテナー イメージを実行する方法を示します。 作成し、sqlcmd によるデータベースのクエリを実行します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/31/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.workload: Active
ms.openlocfilehash: 0fcd5cefc02359d407b1799e4cc31ed5afa3c818
ms.sourcegitcommit: 73043fe1ac5d60b67e33b44053c0a7733b98bc3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="run-the-sql-server-2017-container-image-with-docker"></a>Docker を使用した SQL Server 2017 コンテナー イメージを実行します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このクイック スタートのプルし、SQL Server 2017 コンテナー イメージを実行に Docker を使用する[mssql サーバー linux](https://hub.docker.com/r/microsoft/mssql-server-linux/)です。 接続し、 **sqlcmd**を最初にデータベースを作成し、クエリを実行します。

このイメージは、Ubuntu 16.04 に基づいて Linux で実行されている SQL Server で構成されます。 Mac/Windows 用の Docker エンジン 1.8 + Linux または Docker を使用できます。

> [!NOTE]
> このクイック スタート特に焦点を mssql を使用して、サーバーの**linux**イメージ。 Windows イメージが含まれていないが、詳細情報を入手するには上、 [mssql server windows 開発者 Docker Hub ページ](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)です。

## <a id="requirements"></a> 前提条件

- Docker エンジン 1.8 + 任意の Linux ディストリビューションまたは Docker は Mac/windows のサポート。 詳細については、次を参照してください。[インストール Docker](https://docs.docker.com/engine/installation/)です。
- 2 GB のディスク領域の最小値
- 2 GB の RAM の最小値
- [Linux 上の SQL Server のシステム要件](sql-server-linux-setup.md#system)です。

## <a name="pull-and-run-the-container-image"></a>プルし、コンテナー イメージを実行

1. SQL Server 2017 Linux コンテナー イメージを Docker Hub からプルします。

   ```bash
   sudo docker pull microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker pull microsoft/mssql-server-linux:2017-latest
   ```

   前のコマンドは、最新の SQL Server 2017 コンテナー イメージを取得します。 コロンとタグ名を追加する場合は、特定のイメージを取得するには、(たとえば、 `microsoft/mssql-server-linux:2017-GA`)。 すべての利用可能なイメージを表示するには、次を参照してください。 [mssql サーバー linux Docker ハブ ページ](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/)です。

1. Docker によってコンテナー イメージを実行するには、bash シェル (Linux/macOS) または管理者特権の PowerShell コマンド プロンプトから次のコマンドを使用できます。

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      -p 1401:1433 --name sql1 \
      -d microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1401:1433 --name sql1 `
      -d microsoft/mssql-server-linux:2017-latest
   ```

   > [!NOTE]
   > 既定では、これは、コンテナーを作成 2017 年 1 SQL Server の Developer edition を使用します。 コンテナーで実稼働のエディションを実行するためのプロセスは若干異なります。 詳細については、次を参照してください。[実稼働環境にコンテナー イメージを実行](sql-server-linux-configure-docker.md#production)です。

   次の表は、前に、パラメーターの説明を示します`docker run`例。

   | パラメーター | Description |
   |-----|-----|
   | **e ' ACCEPT_EULA = Y'** |  設定、 **ACCEPT_EULA**変数への同意を確認する任意の値を[使用許諾契約書](http://go.microsoft.com/fwlink/?LinkId=746388)です。 SQL Server イメージの設定が必要です。 |
   | **e ' MSSQL_SA_PASSWORD =\<YourStrong!Passw0rd\>'** | 8 文字以上には、満たす独自の強力なパスワードを指定、 [SQL Server のパスワード要件](../relational-databases/security/password-policy.md)です。 SQL Server イメージの設定が必要です。 |
   | **-p 1401:1433** | ホスト環境での TCP ポートにマップ (先頭の値)、コンテナーの TCP ポートと (2 番目の値)。 この例では SQL Server がコンテナー内の TCP 1433 でリッスンしていると、ホスト上の 1401 ポートにこの公開されます。 |
   | **-名前 sql1** | ランダムに生成されたものではなく、コンテナーのカスタム名を指定します。 1 つ以上のコンテナーを実行すると場合に、この同じ名前を再利用することはできません。 |
   | **microsoft/mssql-サーバー-linux:2017-最新** | SQL Server 2017 Linux コンテナー イメージ。 |

1. 表示するには、Docker コンテナーを使用して、`docker ps`コマンド。

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

   次のスクリーン ショットのような出力が表示されます。

   ![Docker ps コマンドの出力](./media/sql-server-linux-setup-docker/docker-ps-command.png)

1. 場合、**ステータス**項目のステータスを表示**を**、コンテナー内の SQL Server を実行しとで指定されたポートでリッスンしている、**ポート**列です。 場合、**ステータス**列、SQL Server のコンテナーの番組を**Exited**を参照してください、[構成ガイド」のセクションのトラブルシューティング](sql-server-linux-configure-docker.md#troubleshooting)です。

`-h` (ホスト名) のパラメーターも、役立ちますが、わかりやすくするためには、このチュートリアルでは使用されません。 これは、カスタム値をコンテナーの内部名を変更します。 これは、次の TRANSACT-SQL クエリで返される名前が表示されます。

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

設定`-h`と`--name`同じ値には、ターゲット コンテナーを特定しやすくすることをお勧めします。

## <a name="change-the-sa-password"></a>SA パスワードを変更します。

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="connect-to-sql-server"></a>SQL Server に接続します。

次の手順は、SQL Server コマンド ライン ツールを使用して**sqlcmd**、SQL Server に接続するコンテナーの内部です。

1. 使用して、`docker exec -it`実行中のコンテナー内の対話型 bash シェルを起動するコマンド。 次の例で`sql1`によって指定された名前、`--name`コンテナーを作成した場合のパラメーターです。

   ```bash
   sudo docker exec -it sql1 "bash"
   ```

   ```PowerShell
   docker exec -it sql1 "bash"
   ```

1. 1 回、コンテナー内の接続ローカル sqlcmd でします。 Sqlcmd がパスにない、既定では、完全なパスを指定する必要があるようにします。

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   > [!TIP]
   > コマンド ラインでパスワードを省略すると、入力を求められます。

1. 成功すると、**sqlcmd** コマンド プロンプト `1>` が表示されます。

## <a name="create-and-query-data"></a>データの作成とクエリ

以下のセクションでは、**sqlcmd** と Transact-SQL を使用して新しいデータベースを作成し、データを追加して簡単なクエリを実行します。

### <a name="create-a-new-database"></a>新しいデータベースの作成

次の手順では、`TestDB` という名前の新しいデータベースを作成します。

1. **sqlcmd** のコマンド プロンプトに次の Transact-SQL コマンドを貼り付け、テスト データベースを作成します。

   ```sql
   CREATE DATABASE TestDB
   ```

1. 次の行に、サーバー上のすべてのデータベースの名前を返すクエリを記述します。

   ```sql
   SELECT Name from sys.Databases
   ```

1. 前の 2 つのコマンドは、すぐに実行されていません。 前のコマンドを実行するには、新しい行に「`GO`」と入力する必要があります。

   ```sql
   GO
   ```

### <a name="insert-data"></a>データの挿入

次に、新しいテーブル `Inventory` を作成し、2 つの新しい行を挿入します。

1. **sqlcmd** のコマンド プロンプトで、コンテキストを新しい `TestDB` データベースに切り替えます。

   ```sql
   USE TestDB
   ```

1. `Inventory` という名前の新しいテーブルを作成します。

   ```sql
   CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
   ```

1. 新しいテーブルにデータを挿入します。

   ```sql
   INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
   ```

1. 「`GO`」と入力して前のコマンドを実行します。

   ```sql
   GO
   ```

### <a name="select-data"></a>データの選択

ここで、`Inventory` テーブルからデータを返すクエリを実行します。

1. **sqlcmd** のコマンド プロンプトで、数量が 152 より大きい`Inventory` テーブルから行を返すクエリを入力します。

   ```sql
   SELECT * FROM Inventory WHERE quantity > 152;
   ```

1. コマンドを実行します。

   ```sql
   GO
   ```

### <a name="exit-the-sqlcmd-command-prompt"></a>sqlcmd コマンド プロンプトの終了

1. **sqlcmd** セッションを終了するには、「`QUIT`」と入力します。

   ```sql
   QUIT
   ```

1. 終了するには、コンテナー内の対話型のコマンド プロンプトを入力`exit`です。 コンテナーは、対話型 bash シェルを終了した後に実行を続けます。

## <a id="connectexternal"></a>コンテナーの外から接続します。

できますも接続する SQL Server インスタンスに Docker コンピューターに、外部 Linux、Windows、または macOS ツールから SQL 接続をサポートします。

次の手順を使用して**sqlcmd**コンテナーで実行されている SQL Server に接続するコンテナーの外部でします。 次の手順では、SQL Server コマンド ライン ツールが、コンテナーの外にインストール済みであることを前提としています。 同じプリンシパルが、他のツールを使用するときに適用が、接続するプロセスは、各ツールに固有です。

1. コンテナーをホストしているコンピューターの IP アドレスが見つかりません。 Linux では、次のように使用します。 **ifconfig**または**ip アドレス**です。Windows では、次のように使用します。 **ipconfig**です。

1. IP アドレスとポート 1433、コンテナー内にマップされているポートを指定する sqlcmd を実行します。 この例では、ホスト マシン上のポート 1401 であります。

   ```bash
   sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   ```PowerShell
   sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourNewStrong!Passw0rd>"
   ```

1. TRANSACT-SQL コマンドを実行します。 終了したら、入力`QUIT`です。

SQL Server に接続するその他の一般的なツールは次のとおりです。

- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [Windows で SQL Server Management Studio (SSMS)](sql-server-linux-develop-use-ssms.md)
- [SQL Server 操作 Studio (プレビュー)](../sql-operations-studio/what-is.md)
- [mssql cli (プレビュー)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

## <a name="remove-your-container"></a>コンテナーを削除します。

このチュートリアルで使用される SQL Server のコンテナーを削除する場合は、次のコマンドを実行します。

```bash
sudo docker stop sql1
sudo docker rm sql1
```

```PowerShell
docker stop sql1
docker rm sql1
```

> [!WARNING]
> コンテナーの完全に削除を停止して、コンテナー内の任意の SQL Server データを削除します。 データを保持する必要がある場合[を作成し、コンテナーからのバックアップ ファイルをコピー](tutorial-restore-backup-in-sql-server-container.md)か使用して、[コンテナー データの永続化手法](sql-server-linux-configure-docker.md#persist)です。

## <a name="docker-demo"></a>Docker のデモ

Docker の SQL Server のコンテナー イメージを使用しようとしましたが後、は、Docker を開発およびテストを向上させるために使用する方法を知ることができます。 次のビデオでは、継続的インテグレーションと展開シナリオで Docker を使用する方法を説明します。

> [!VIDEO https://channel9.msdn.com/Events/Connect/2017/T152/player]

## <a name="next-steps"></a>次の手順

コンテナー内にデータベースのバックアップ ファイルを復元する方法のチュートリアルでは、次を参照してください。 [Linux Docker コンテナーでの SQL Server データベースを復元](tutorial-restore-backup-in-sql-server-container.md)です。 複数のコンテナーを実行するなどその他のシナリオを探索するデータの永続性、およびトラブルシューティングを参照してください[Docker でコンテナーのイメージを構成する SQL Server 2017](sql-server-linux-configure-docker.md)です。

また、チェック アウト、 [mssql docker GitHub リポジトリ](https://github.com/Microsoft/mssql-docker)リソース、フィードバック、および既知の問題です。
