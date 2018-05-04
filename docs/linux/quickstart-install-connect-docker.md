---
title: Docker で SQL Server 2017 の使用を開始する | Microsoft Docs
description: このクイック スタートでは、Docker を使用して SQL Server 2017 コンテナー イメージを実行する方法を示します。 その次に、sqlcmd に接続して、最初のデータベースを作成し、クエリを実行します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/07/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.openlocfilehash: 841f5b737742a23e8126d5b5b9bf0d9c7ed55399
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="quickstart-run-the-sql-server-2017-container-image-with-docker"></a>クイック スタート: Docker を使用して SQL Server 2017 コンテナー イメージを実行する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このクイック スタートでは、Docker を使用して SQL Server 2017 コンテナー イメージ [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) をプルして実行します。 次に、**sqlcmd** と接続して最初のデータベースを作成し、クエリを実行します。

このイメージは、Ubuntu 16.04 の Linux で動作する SQL Server で構成されます。 Linux の Docker エンジン 1.8 + または Docker for Mac/Windows から使用できます。

> [!NOTE]
> このクイック スタートは mssql-server-**linux** イメージの使用に特にフォーカスしています。 Windows イメージについては触れていませんが、[mssql-server-windows-developer Docker Hub ページ](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/) で詳細情報を得ることができます。

## <a id="requirements"></a> 前提条件

- サポートされている任意の Linux ディストリビューションの Docker エンジン 1.8 + または Docker for Mac/Windows。 詳細については「[Install Docker](https://docs.docker.com/engine/installation/)」(Docker のインストール) を参照してください。
- 2 GB 以上のディスク領域
- 2 GB 以上の RAM
- [SQL Server on Linux のシステム要件](sql-server-linux-setup.md#system)。

## <a name="pull-and-run-the-container-image"></a>コンテナー イメージのプルと実行

1. Docker Hub から SQL Server 2017 Linux コンテナー イメージをプルします。

   ```bash
   sudo docker pull microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker pull microsoft/mssql-server-linux:2017-latest
   ```

   前のコマンドは、最新の SQL Server 2017 コンテナー イメージをプルします。 特定のイメージをプルするには、コロンとタグ名を追加します (たとえば、 `microsoft/mssql-server-linux:2017-GA`)。 利用可能なすべてのイメージを表示するには [mssql-server-linux Docker hub ページ](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/) を参照してください。
   
   この記事でバッシュ コマンド`sudo`を使用します。 Macos、`sudo`は必要ありません。 使用したくない場合は、Linux 上`sudo`Docker を実行することができます、 **docker**をグループ化し、そのグループにユーザーを追加します。 詳細については、次を参照してください。 [Linux のインストール後のステップ](https://docs.docker.com/install/linux/linux-postinstall/)です。

1. Docker でコンテナー イメージを実行するには、bash シェル (Linux/macOS) または管理者特権の PowerShell コマンド プロンプトから次のコマンドを使用できます。

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      -p 1433:1433 --name sql1 \
      -d microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1433:1433 --name sql1 `
      -d microsoft/mssql-server-linux:2017-latest
   ```

   > [!NOTE]
   > パスワードは SQL Server の既定のパスワード ポリシーに従う必要があります。従わない場合、コンテナーで SQL Server をセットアップできず、動作が停止します。 既定では、パスワードの長さは少なくとも 8 文字で、大文字、小文字、十進数字、記号の 4 種類のうち 3 種類を含んでいる必要があります。 [docker ログ](https://docs.docker.com/engine/reference/commandline/logs/) コマンドを実行することでエラー ログを調査することができます。

   > [!NOTE]
   > 既定では、これは SQL Server 2017 の Developer エディションのコンテナーを作成します。 コンテナーで実稼働のエディションを実行するためのプロセスは若干異なります。 詳細については 「[実稼働環境のコンテナー イメージを実行する](sql-server-linux-configure-docker.md#production)」を参照してください。

   次の表では、前述の `docker run` の例におけるパラメーターを説明しています。

   | パラメーター | 説明 |
   |-----|-----|
   | **-e 'ACCEPT_EULA=Y'** |  **ACCEPT_EULA** 変数に [使用許諾契約書](http://go.microsoft.com/fwlink/?LinkId=746388) の同意を確認するための任意の値を設定します。 SQL Server イメージの設定が必要です。 |
   | **-e 'MSSQL_SA_PASSWORD=\<YourStrong!Passw0rd\>'** | 8 文字以上で、 [SQL Server のパスワード要件](../relational-databases/security/password-policy.md) を満たす強力なパスワードを指定します。 SQL Server イメージに必須の設定です。 |
   | **-p 1433:1433** | ホスト環境の TCP ポート (最初の値) を コンテナーの TCP ポート (2 番目の値) にマップします。 この例では SQL Server がコンテナー内の TCP 1433 でリッスンしていると、ホスト上の 1433 ポートにこの公開されます。 |
   | **--name sql1** | ランダムに生成されたものではなく、コンテナーのカスタム名を指定します。 2 つ以上のコンテナーを実行する場合、同じ名前を再利用することはできません。 |
   | **microsoft/mssql-server-linux:2017-latest** | SQL Server 2017 Linux コンテナー イメージ。 |

1. Docker コンテナーを表示するには、 `docker ps` コマンドを使用します。

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

   次のスクリーンショットのような出力が表示されます。

   ![Docker ps コマンドの出力](./media/sql-server-linux-setup-docker/docker-ps-command.png)

1. **[STATUS]** 列に **[Up]** の状態が表示されている場合、SQL Server はコンテナーで実行されており、**[PORTS]** 列に指定されたポートでリッスンしています。 SQL Server コンテナーの **[STATUS]** 列に **[Exited]** と表示されている場合は、[構成ガイドのトラブルシューティングのセクション](sql-server-linux-configure-docker.md#troubleshooting)を参照してください。

`-h` (ホスト名) のパラメーターも役に立ちますが、簡略化のためこのチュートリアルでは使用しません。 これにより、コンテナーの内部名がカスタム値に変更されます。 これは、次の Transact-SQL クエリで返される名前です。

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

`-h` と `--name` を同じ値に設定することは、対象のコンテナーを特定しやすくするためのひとつの良い方法です。

## <a name="change-the-sa-password"></a>SA パスワードを変更する 

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="connect-to-sql-server"></a>SQL Server への接続

次の手順では、コンテナー内の SQL Server のコマンドライン ツール **sqlcmd** を使用して、SQL Server に接続します。 

1. コマンド `docker exec -it` を使用して、実行中のコンテナー内の対話型 bash シェルを起動します。 次の例にある `sql1` は、コンテナーを作成したときに `--name` パラメーターで指定した名前です。 

   ```bash
   sudo docker exec -it sql1 "bash"
   ```

   ```PowerShell
   docker exec -it sql1 "bash"
   ```

1. コンテナー内では sqlcmd とローカル接続してください。 既定では sqlcmd はパスにないため、完全なパスを指定する必要があります。

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   > [!TIP]
   > コマンド ラインでパスワードを省略すると、入力を求められます。

1. 成功すると、**sqlcmd** のコマンド プロンプトである `1>` が表示されます。 

## <a name="create-and-query-data"></a>データの作成とクエリ

次のセクションでは、**sqlcmd** と Transact-SQL を使用して新しいデータベースを作成し、データを追加して簡単なクエリを実行します。 

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

1. **sqlcmd** のコマンド プロンプトで、新しい `TestDB` データベースのコンテキストに切り替えます。 

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

### <a name="select-data"></a>データの取得

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

1. コンテナー内の対話型のコマンド プロンプトを終了するには、`exit`と入力します。 コンテナーは、対話型 bash シェルを終了した後に実行を続けます。

## <a id="connectexternal"></a> コンテナー外部から接続する

SQL 接続をサポートする外部の Linux、Windows、macOS ツールから、Docker コンピューターの SQL Server インスタンスに接続することもできます。

次の手順ではコンテナーの外で **sqlcmd** を使用して、コンテナーで実行されている SQL Server に接続します。 この手順は、コンテナーの外に SQL Server コマンド ライン ツールがインストール済みであることを前提としています。 どのツールを使用しても同じプリンシパルが適用されますが、接続するプロセスはツールごとに固有です。

1. コンテナーをホストしているコンピューターの IP アドレスを探します。 Linux の場合、 **ifconfig** または **ip addr** を使用します。Windows の場合、**ipconfig** を使用します。

1. IP アドレスとコンテナーのポート 1433 にマップされたポートを指定して sqlcmd を実行します。 この例では、ホスト コンピューターには 1433、同じポートであります。 ホスト コンピューターにマップされている別のポートを指定した場合は、ここ使用します。

   ```bash
   sqlcmd -S 10.3.2.4,1433 -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   ```PowerShell
   sqlcmd -S 10.3.2.4,1433 -U SA -P "<YourNewStrong!Passw0rd>"
   ```

1. Transact-SQL コマンドを実行します。 終了したら `QUIT` を入力します。

SQL Server に接続するその他の一般的なツールには次のものがあります。

- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) on Windows](sql-server-linux-develop-use-ssms.md)
- [SQL Server Operations Studio (プレビュー)](../sql-operations-studio/what-is.md)
- [mssql-cli (プレビュー)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

## <a name="remove-your-container"></a>コンテナーを削除する

このチュートリアルで使用した SQL Server のコンテナーを削除する場合は、次のコマンドを実行します。

```bash
sudo docker stop sql1
sudo docker rm sql1
```

```PowerShell
docker stop sql1
docker rm sql1
```

> [!WARNING]
> コンテナーを完全に停止して削除すると、コンテナー内のすべての SQL Server データが削除されます。 データを保持する必要がある場合は、[コンテナーからバックアップ ファイルを作成してコピーする](tutorial-restore-backup-in-sql-server-container.md)か、[コンテナー データを永続化する手法](sql-server-linux-configure-docker.md#persist)を使用します。

## <a name="docker-demo"></a>Docker のデモ

Docker の SQL Server コンテナー イメージを使用すると、開発とテストの改善のためにどのように Docker を使用できるかを知りたくなるかもしれません。 次のビデオは、継続的インテグレーションと展開シナリオでどのように Docker を使用できるかを説明しています。

> [!VIDEO https://channel9.msdn.com/Events/Connect/2017/T152/player]

## <a name="next-steps"></a>次のステップ

データベース バックアップファイルをコンテナーに復元する方法については、「[Restore a SQL Server database in a Linux Docker container](tutorial-restore-backup-in-sql-server-container.md)」(Linux の Docker コンテナーで SQL Server データベースを復元する) を参照してください。 複数のコンテナーの実行、データの永続性、トラブルシューティングなどのその他のシナリオを調べるには、「[Configure SQL Server 2017 container images on Docker](sql-server-linux-configure-docker.md)」(Docker で SQL Server 2017 コンテナー イメージを構成する) を参照してください。

また、リソース、フィードバック、既知の問題については [mssql-docker GitHub リポジトリ](https://github.com/Microsoft/mssql-docker)をご確認ください。
