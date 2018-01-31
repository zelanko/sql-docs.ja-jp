---
title: "SQL Server 2017 Docker を使ってみる |Microsoft ドキュメント"
description: "この クイックスタートでは、Docker を使用して、SQL Server 2017 コンテナー イメージ をプルして実行します。その次に、sqlcmd に接続して、最初のデータベースを作成し、クエリを実行します。"
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
ms.openlocfilehash: 80d3d05fcd693f6290649c2c63446c400c9ad3b2
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2017
---
# <a name="run-the-sql-server-2017-container-image-with-docker"></a>Docker を使用して SQL Server 2017 コンテナー イメージを実行する

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このクイックスタートでは、 SQL Server 2017 コンテナー イメージ, [mssql-sever-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) をプルし、実行するために Docker を使用します。その次に **sqlcmd** を使用して、最初のデータベースへ接続し、クエリを実行します。

このイメージは、Ubuntu 16.04 の Linux で動作する SQL Server で構成されます。 Linux の Docker エンジン 1.8 + または Docker for Mac/Windows から使用できます。

> [!NOTE]
> このクイック スタートは mssql-server-**linux** イメージの使用に特にフォーカスしています。 Windows イメージについては触れていませんが、[mssql-server-windows-developer Docker Hub ページ](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/) で詳細情報を得ることができます。

## <a id="requirements"></a> 前提条件

- サポートされている任意の Linux ディストリビューションの Docker エンジン 1.8 + または Docker for Mac/Windows。詳細については「[Install Docker](https://docs.docker.com/engine/installation/)」(Docker のインストール) を参照してください。
- 2 GB 以上のディスク領域
- 2 GB 以上の RAM
- [SQL Server on Linux のシステム要件](sql-server-linux-setup.md#system)。

## <a name="pull-and-run-the-container-image"></a>コンテナー イメージのプルと実行

1. SQL Server 2017 Linux コンテナー イメージを Docker Hub からプルします。

   ```bash
   sudo docker pull microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker pull microsoft/mssql-server-linux:2017-latest
   ```

   前のコマンドは、最新の SQL Server 2017 コンテナー イメージをプルします。特定のイメージをプルするには、コロンとタグ名を追加します (たとえば、 `microsoft/mssql-server-linux:2017-GA`)。 利用可能なすべてのイメージを表示するには [mssql-server-linux Docker hub ページ](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/) を参照してください。

1. Docker でコンテナー イメージを実行するには、bash シェル (Linux/macOS) または管理者特権の PowerShell コマンド プロンプトから次のコマンドを使用できます。

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
   > 既定では、これは SQL Server 2017 の Developer エディションのコンテナーを作成します。コンテナーで実稼働のエディションを実行するためのプロセスは若干異なります。詳細については「[実稼働環境のコンテナー イメージを実行する](sql-server-linux-configure-docker.md#production)」を参照してください。

   次の表では、前述の `docker run` の例におけるパラメーターを説明しています。

   | パラメーター | 説明 |
   |-----|-----|
   | **e ' ACCEPT_EULA = Y'** | **ACCEPT_EULA** 変数に [使用許諾契約書](http://go.microsoft.com/fwlink/?LinkId=746388) の同意を確認するための任意の値を設定します。 SQL Server イメージの設定が必要です。 |
   | **e ' MSSQL_SA_PASSWORD =\<YourStrong!Passw0rd\>'** | 8 文字以上で、 [SQL Server のパスワード要件](../relational-databases/security/password-policy.md) を満たす強力なパスワードを指定します。 SQL Server イメージに必須の設定です。 |
   | **-p 1401:1433** | ホスト環境の TCP ポート (最初の値) を コンテナーの TCP ポート (2 番目の値) にマップします。この例では、 SQL Server はコンテナーの TCP 1433 でリッスンし、これがホストのポート 1401 に公開されます。 |
   | **--name sql1** | ランダムに生成されたものではなく、コンテナーのカスタム名を指定します。 2 つ以上のコンテナーを実行する場合、同じ名前を再利用することはできません。 |
   | **microsoft/mssql-server-linux:2017-latest** | SQL Server 2017 Linux コンテナー イメージ。 |

1. Docker コンテナーを表示するには、 `docker ps` コマンドを使用します。

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

`-h` と `--name` を同じ値に設定することは、対象のコンテナーを特定しやすくするためのひとつの良い方法です。

## <a name="change-the-sa-password"></a>SA のパスワードの変更

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="connect-to-sql-server"></a>SQL Server に接続します。

次の手順では、コンテナー内の SQL Server のコマンドライン ツール **sqlcmd** を使用して、SQL Server に接続します。

1. コマンド `docker exec -it` を使用して、実行中のコンテナー内の対話型 bash シェルを起動します。 次の例にある `sql1` は、コンテナーを作成したときに `--name` パラメーターで指定した名前です。

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

1. **sqlcmd** のコマンド プロンプトで、quantity が 152 より大きい `Inventory` テーブルから行を返すクエリを入力します。

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

1. コンテナー内の対話型のコマンド プロンプトを終了するには、`exit` と入力します。 コンテナーは、対話型 bash シェルを終了した後に実行を続けます。

## <a id="connectexternal"></a>コンテナー外部からの接続

コンテナ外の Linux、Windows、または macOS にある任意のSQL 接続ツールから、Docker コンピューターの SQL Server インスタンスへ接続することもできます。

次の手順を使用して**sqlcmd**コンテナーで実行されている SQL Server に接続するコンテナーの外部でします。 次の手順では、SQL Server コマンド ライン ツールが、コンテナーの外にインストール済みであることを前提としています。 同じプリンシパルが、他のツールを使用するときに適用が、接続するプロセスは、各ツールに固有です。 

1. コンテナーをホストしているコンピューターの IP アドレスが見つかりません。 Linux では、次のように使用します。 **ifconfig**または**ip アドレス**です。Windows では、次のように使用します。 **ipconfig**です。 

1. IP アドレスとコンテナーのポート 1433 にマップされたポートを指定して sqlcmd を実行します。 この例では、ホスト マシンのポート 1401 です。

   ```bash
   sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   ```PowerShell
   sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourNewStrong!Passw0rd>"
   ```

1. Transact-SQL コマンドを実行します。 終了したら `QUIT` を入力します。

SQL Server に接続するその他の一般的なツールには次のものがあります:

- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) on Windows](sql-server-linux-develop-use-ssms.md)

## <a name="remove-your-container"></a>コンテナーの削除

このチュートリアルで使用した SQL Server のコンテナーを削除する場合は、次のコマンドを実行します:

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

## <a name="next-steps"></a>次のステップ

コンテナー内にデータベースのバックアップ ファイルを復元する方法のチュートリアルでは、次を参照してください。 [Linux Docker コンテナーでの SQL Server データベースを復元](tutorial-restore-backup-in-sql-server-container.md)です。 複数のコンテナーを実行するなどその他のシナリオを探索するデータの永続性、およびトラブルシューティングを参照してください[Docker でコンテナーのイメージを構成する SQL Server 2017](sql-server-linux-configure-docker.md)です。

また、その他のリソース、フィードバック、および既知の問題については [mssql-docker GitHub リポジトリ](https://github.com/Microsoft/mssql-docker) を参考にしてください。
