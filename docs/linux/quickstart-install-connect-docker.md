---
title: "Docker で SQL Server 2017 の使用を開始する | Microsoft Docs"
description: "このクイック スタートでは、Docker を使用して SQL Server 2017 コンテナー イメージを実行する方法を示します。 その次に、sqlcmd でデータベースを作成し、クエリを実行します。"
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/31/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.workload: Active
ms.openlocfilehash: 1f018dd2b60365d89e912e7ef38499f8a4d14d9b
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2018
---
# <a name="run-the-sql-server-2017-container-image-with-docker"></a>Docker を使用して SQL Server 2017 コンテナー イメージを実行する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このクイック スタートでは、Docker を使用して SQL Server 2017 コンテナー イメージ [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) をプルして実行します。 次に、**sqlcmd** と接続して最初のデータベースを作成し、クエリを実行します。

このイメージは Ubuntu 16.04 に基づく Linux で実行されている SQL Server で構成されます。 イメージは Linux の Docker エンジン 1.8+ または Mac/Windows 用 Docker で使用することができます。

> [!NOTE]
> このクイック スタートでは特に mssql-server-**linux**イメージを使用することに焦点を当てます。 Windows イメージについては言及しませんが、[mssql-server-windows-developer Docker Hub ページ](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)で詳細を確認できます。

## <a id="requirements"></a> 前提条件

- サポートされているいずれかの Linux ディストリビューションの Docker エンジン 1.8+ または Mac/Windows 用 Docker。 詳細については、「[Install Docker](https://docs.docker.com/engine/installation/)」(Docker をインストールする) を参照してください。
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

   前のコマンドから、最新の SQL Server 2017 コンテナー イメージがプルされます。 特定のイメージをプルしたい場合、コロンとタグ名 (たとえば `microsoft/mssql-server-linux:2017-GA`) を追加します。 利用可能なすべてのイメージを表示する方法は、[mssql-server-linux Docker Hub ページ](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/)を参照してください。

1. Docker でコンテナー イメージを実行する場合は、Bash シェル (Linux/macOS) または管理者特権での PowerShell コマンド プロンプトから次のコマンドを使用することができます。

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
   > パスワードは SQL Server の既定のパスワード ポリシーに従う必要があります。従わない場合、コンテナーで SQL Server をセットアップできず、動作が停止します。 既定では、パスワードの長さは少なくとも 8 文字で、大文字、小文字、十進数字、記号の 4 種類のうち 3 種類を含んでいる必要があります。 [docker ログ](https://docs.docker.com/engine/reference/commandline/logs/) コマンドを実行することでエラー ログを調査することができます。

   > [!NOTE]
   > 既定では、これにより SQL Server 2017 Developer Edition のコンテナーが作成されます。 コンテナーで実稼働エディションを実行するためのプロセスは若干異なります。 詳細については、「[Run production container images](sql-server-linux-configure-docker.md#production)」(実稼働のコンテナー イメージを実行する) を参照してください。

   次の表は、前の `docker run` の例のパラメーターについて説明しています。

   | パラメーター | Description |
   |-----|-----|
   | **-e 'ACCEPT_EULA=Y'** |  **ACCEPT_EULA** 変数を任意の値に設定し、[使用許諾契約書](http://go.microsoft.com/fwlink/?LinkId=746388)の承諾を確定します。 SQL Server イメージの設定が必要です。 |
   | **-e 'MSSQL_SA_PASSWORD=\<YourStrong!Passw0rd\>'** | 8 文字以上の、[SQL Server のパスワード要件](../relational-databases/security/password-policy.md)を満たす強力なパスワードを指定します。 SQL Server イメージの設定が必要です。 |
   | **-p 1401:1433** | ホスト環境の TCP ポート (最初の値) とコンテナーの TCP ポート (2 番目の値) をマップします。 この例では、SQL Server がコンテナー内の TCP 1433 でリッスンしており、これがホスト上のポート 1401 に公開されています。 |
   | **--name sql1** | ランダムに生成された名前ではなく、コンテナーのカスタム名を指定します。 複数のコンテナーを実行する場合は、この同じ名前を再利用することはできません。 |
   | **microsoft/mssql-server-linux:2017-latest** | SQL Server 2017 Linux コンテナー イメージ。 |

1. Docker コンテナーを表示するには、`docker ps` コマンドを使用します。

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

ターゲット コンテナーを特定しやすくするため、`-h` と `--name` を同じ値に設定することをお勧めします。

## <a name="change-the-sa-password"></a>SA パスワードの変更

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="connect-to-sql-server"></a>SQL Server への接続

次の手順ではコンテナー内で SQL Server に接続するために SQL Server コマンド ライン ツールである **sqlcmd** を使用します。

1. 実行中のコンテナー内で対話型の Bash シェルを開始するには、`docker exec -it` コマンドを使用します。 次の例の `sql1` は、コンテナーを作成したときに `--name` パラメーターによって指定された名前です。

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

1. コンテナー内で対話型のコマンド プロンプトを終了するには、`exit` と入力します。 コンテナーは、対話型の Bash シェルを終了した後も引き続き実行されます。

## <a id="connectexternal"></a> コンテナーの外からの接続

SQL 接続をサポートする外部の Linux、Windows、macOS ツールから、Docker コンピューターの SQL Server インスタンスに接続することもできます。

次の手順ではコンテナーの外で **sqlcmd** を使用して、コンテナーで実行されている SQL Server に接続します。 この手順は、コンテナーの外に SQL Server コマンド ライン ツールがインストール済みであることを前提としています。 どのツールを使用しても同じプリンシパルが適用されますが、接続するプロセスはツールごとに固有です。

1. コンテナーをホストしているコンピューターの IP アドレスを探します。 Linux の場合、 **ifconfig** または **ip addr** を使用します。Windows の場合、**ipconfig** を使用します。

1. コンテナーのポート 1433 にマップされた IP アドレスとポートを指定して sqlcmd を実行します。 この例では、ホスト コンピューター上のポート 1401 です。

   ```bash
   sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   ```PowerShell
   sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourNewStrong!Passw0rd>"
   ```

1. Transact-SQL コマンドを実行します。 終わったら、`QUIT` と入力します。

SQL Server に接続するその他の一般的なツールは次のとおりです。

- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [Windows の SQL Server Management Studio (SSMS)](sql-server-linux-develop-use-ssms.md)
- [SQL Server Operations Studio (プレビュー)](../sql-operations-studio/what-is.md)
- [mssql-cli (プレビュー)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

## <a name="remove-your-container"></a>コンテナーの削除

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

## <a name="next-steps"></a>次の手順

データベース バックアップファイルをコンテナーに復元する方法については、「[Restore a SQL Server database in a Linux Docker container](tutorial-restore-backup-in-sql-server-container.md)」(Linux の Docker コンテナーで SQL Server データベースを復元する) を参照してください。 複数のコンテナーの実行、データの永続性、トラブルシューティングなどのその他のシナリオを調べるには、「[Configure SQL Server 2017 container images on Docker](sql-server-linux-configure-docker.md)」(Docker で SQL Server 2017 コンテナー イメージを構成する) を参照してください。

リソース、フィードバック、既知の問題について、[mssql-docker GitHub リポジトリ](https://github.com/Microsoft/mssql-docker)も参照してください。
