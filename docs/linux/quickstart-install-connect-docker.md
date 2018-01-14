---
title: "SQL Server 2017 Docker を使ってみる |Microsoft ドキュメント"
description: "このクイック スタート チュートリアルでは、Docker を使用して、SQL Server 2017 コンテナー イメージを実行する方法を示します。 作成し、sqlcmd によるデータベースのクエリを実行します。"
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
# <a name="run-the-sql-server-2017-container-image-with-docker"></a>Docker を使用した SQL Server 2017 コンテナー イメージを実行します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このクイック スタート チュートリアルでのプルし、SQL Server 2017 コンテナー イメージを実行に Docker を使用する[mssql サーバー linux](https://hub.docker.com/r/microsoft/mssql-server-linux/)です。 接続し、 **sqlcmd**を最初にデータベースを作成し、クエリを実行します。

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

1. Docker コンテナーを表示するには、 `docker ps` コマンドを使用します。

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

   次のスクリーン ショットのような出力が表示されます。

   ![Docker ps コマンドの出力](./media/sql-server-linux-setup-docker/docker-ps-command.png)

1. **ステータス** 項目が **Up** を示している場合、 SQL Server はコンテナー内で実行状態で、 **PORTS** 項目で示されているポート番号でサービスをリッスンしています。 SQL Server のコンテナーの **STATUS** 項目が **Exited** を示している場合、[構成ガイド」のセクションのトラブルシューティング](sql-server-linux-configure-docker.md#troubleshooting) を参照してください。

`-h` パラメーター (ホスト名) も便利なものですが、簡潔さを維持する理由のため、このチュートリアルでは使用されません。 これは、コンテナーの内部名を任意のカスタム値へ変更します。 これは、次の Transact-SQL クエリで返されることになる名前です。

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

1. 1 度、コンテナー内で、sqlcmd を使用してローカルに接続します。 既定では　Sqlcmd がパスにないため、フルパスを指定する必要があります。

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   > [!TIP]
   > コマンド ラインでパスワードを省略すると、入力を求められます。

1. 成功すると、**sqlcmd** のコマンド プロンプトである `1>` が表示されます。

## <a name="create-and-query-data"></a>データの作成とデータの問い合わせ

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

ここで、`Inventory` テーブルからデータを問い合わせるクエリを実行します。

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

次の手順は、コンテナーの外部にある **sqlcmd** を使用して、コンテナの内部で動作している SQL Server へ接続します。 これらの手順は、コンテナーの外に SQL Server コマンドライン ツールがインストール済みであることを前提としています。 他のツールを使用するときと同じプリンシパルが適用されますが、接続プロセスは各ツールでユニークなものです。

1. コンテナーをホストしているコンピューターの IP アドレスを用意してください。 Linux では、 **ifconfig** または **ip addr** を使用します。 Windows では、 **ipconfig** を使用します。

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
> コンテナーを停止して完全に削除すると、コンテナー内にあるすべての SQL Server のデータを削除します。 データを保持する必要がある場合 [コンテナーからバックアップ ファイルを作成して、コピーする](tutorial-restore-backup-in-sql-server-container.md) または [コンテナー データの永続化手法](sql-server-linux-configure-docker.md#persist) を参考にしてください。

## <a name="next-steps"></a>次のステップ

データベースのバックアップ ファイルをコンテナー内に復元する方法のチュートリアルは、 [Linux Docker コンテナーでの SQL Server データベースを復元](tutorial-restore-backup-in-sql-server-container.md) を参照してください。 複数のコンテナーを実行する、データを永続性させる、およびトラブルシューティング等のような、その他のシナリオを探すには [Docker で SQL Server 2017 のコンテナーのイメージを構成する ](sql-server-linux-configure-docker.md) を参照してください。

また、その他のリソース、フィードバック、および既知の問題については [mssql-docker GitHub リポジトリ](https://github.com/Microsoft/mssql-docker) を参考にしてください。
