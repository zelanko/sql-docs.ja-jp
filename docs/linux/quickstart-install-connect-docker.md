---
title: Docker で SQL Server Linux コンテナーを使ってみる
titleSuffix: SQL Server
description: このクイックスタートでは、Docker を使用して、SQL Server 2017 と2019のコンテナーイメージを実行する方法を示します。 その次に、sqlcmd に接続して、最初のデータベースを作成し、クエリを実行します。
author: vin-yu
ms.author: vinsonyu
ms.reviewer: vanto
ms.date: 05/14/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.custom: sqlfreshmay19
ms.prod_service: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
zone_pivot_groups: cs1-command-shell
ms.openlocfilehash: addb8d43a48247206a59d90bac94b998d5b29a81
ms.sourcegitcommit: 73dc08bd16f433dfb2e8406883763aabed8d8727
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2019
ms.locfileid: "68329254"
---
# <a name="quickstart-run-sql-server-container-images-with-docker"></a>クイック スタート: Docker を使用して SQL Server コンテナーイメージを実行する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

このクイック スタートでは、Docker を使用して SQL Server 2017 コンテナー イメージ [mssql-server-linux](https://hub.docker.com/_/microsoft-mssql-server) をプルして実行します。 その後 **sqlcmd** で接続して最初のデータベースを作成し、クエリを実行します。

> [!TIP]
> SQL Server 2019 preview イメージを試す場合は、[この記事の SQL Server 2019 preview バージョン](quickstart-install-connect-docker.md?view=sql-server-linux-ver15)を参照してください。

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

このクイックスタートでは、Docker を使用して、SQL Server 2019 preview コンテナーイメージ[mssql-Server](https://hub.docker.com/r/microsoft/mssql-server)をプルして実行します。 その後 **sqlcmd** で接続して最初のデータベースを作成し、クエリを実行します。

> [!TIP]
> このクイックスタートでは、SQL Server 2019 のプレビューコンテナーを作成します。 SQL Server 2017 のコンテナーを作成する場合は、[この記事の SQL Server 2017 バージョン](quickstart-install-connect-docker.md?view=sql-server-linux-2017)を参照してください。
::: moniker-end

このイメージは、Ubuntu 16.04 の Linux で動作する SQL Server で構成されます。 Linux の Docker エンジン 1.8 + または Docker for Mac/Windows から使用できます。 このクイックスタートでは、特に**linux**イメージでの SQL Server の使用に焦点を当てています。 Windows イメージについては触れていませんが、[mssql-server-windows-developer Docker Hub ページ](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/) で詳細情報を得ることができます。

## <a id="requirements"></a> 前提条件

- サポートされている任意の Linux ディストリビューションの Docker エンジン 1.8 + または Docker for Mac/Windows。 詳細については「[Install Docker](https://docs.docker.com/engine/installation/)」(Docker のインストール) を参照してください。
- Docker **overlay2** storage ドライバー。 これは、ほとんどのユーザーの既定の設定です。 この記憶域プロバイダーを使用しておらず、変更する必要がある場合は、docker のドキュメントで overlay2 を[構成するための](https://docs.docker.com/storage/storagedriver/overlayfs-driver/#configure-docker-with-the-overlay-or-overlay2-storage-driver)手順と警告を参照してください。
- 2 GB 以上のディスク領域。
- 2 GB 以上の RAM。
- [SQL Server on Linux のシステム要件](sql-server-linux-setup.md#system)。

<!--The following H2 is versioned for 2017 and 2019. Much of the content is duplicated, so
any changes to one section should be duplicated in the other-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="pullandrun2017"></a>コンテナーイメージをプルして実行する

次の手順を開始する前に、この記事の上部にある優先シェル (bash、PowerShell、または cmd) を選択していることを確認してください。

1. Microsoft Container Registry から SQL Server 2017 Linux コンテナーイメージを取得します。

   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker pull mcr.microsoft.com/mssql/server:2017-latest
   ```
   ::: zone-end

   > [!TIP]
   > SQL Server 2019 preview イメージを試す場合は、[この記事の SQL Server 2019 preview バージョン](quickstart-install-connect-docker.md?view=sql-server-linux-ver15#pullandrun2019)を参照してください。

   前のコマンドは、最新の SQL Server 2017 コンテナー イメージをプルします。 特定のイメージをプルするには、コロンとタグ名を追加します (たとえば、 `mcr.microsoft.com/mssql/server:2017-GA-ubuntu`)。 使用可能なすべてのイメージを表示するには、 [mssql-Server Docker hub のページ](https://hub.docker.com/r/microsoft/mssql-server)を参照してください。

   ::: zone pivot="cs1-bash"
   この記事の bash コマンドでは、 `sudo`が使用されます。 MacOS では`sudo` 、が不要な場合があります。 Linux では、を使用`sudo`して docker を実行しない場合は、 **docker**グループを構成し、そのグループにユーザーを追加できます。 詳細については、「 [Linux のインストール後の手順](https://docs.docker.com/install/linux/linux-postinstall/)」を参照してください。
   ::: zone-end

2. Docker でコンテナー イメージを実行するには、bash シェル (Linux/macOS) または管理者特権の PowerShell コマンド プロンプトから次のコマンドを使用できます。

   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" \
      -p 1433:1433 --name sql1 \
      -d mcr.microsoft.com/mssql/server:2017-latest
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1433:1433 --name sql1 `
      -d mcr.microsoft.com/mssql/server:2017-latest
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1433:1433 --name sql1 `
      -d mcr.microsoft.com/mssql/server:2017-latest
   ```
   ::: zone-end

   > [!NOTE]
   > パスワードは SQL Server の既定のパスワード ポリシーに従う必要があります。従わない場合、コンテナーで SQL Server をセットアップできず、動作が停止します。 既定では、パスワードは8文字以上で、次の4つのセットのうちの3つの文字を含んでいる必要があります。大文字、小文字、10進数、および記号。 [docker ログ](https://docs.docker.com/engine/reference/commandline/logs/) コマンドを実行することでエラー ログを調査することができます。

   > [!NOTE]
   > 既定では、これは SQL Server 2017 の Developer エディションのコンテナーを作成します。 コンテナーで実稼働のエディションを実行するためのプロセスは若干異なります。 詳細については 「[実稼働環境のコンテナー イメージを実行する](sql-server-linux-configure-docker.md#production)」を参照してください。

   次の表では、前述の `docker run` の例におけるパラメーターを説明しています。

   | パラメーター | 説明 |
   |-----|-----|
   | **-e 'ACCEPT_EULA=Y'** |  **ACCEPT_EULA** 変数を任意の値に設定し、[使用許諾契約書](https://go.microsoft.com/fwlink/?LinkId=746388)の承諾を確定します。 SQL Server イメージに必須の設定です。 |
   | **-e ' SA_PASSWORD =\<Passw0rd\>'** | 8 文字以上で、 [SQL Server のパスワード要件](../relational-databases/security/password-policy.md) を満たす強力なパスワードを指定します。 SQL Server イメージに必須の設定です。 |
   | **-p 1433:1433** | ホスト環境の TCP ポート (最初の値) を コンテナーの TCP ポート (2 番目の値) にマップします。 この例では、SQL Server がコンテナー内の TCP 1433 でリッスンしており、これはホスト上のポート1433に公開されています。 |
   | **--name sql1** | ランダムに生成されたものではなく、コンテナーのカスタム名を指定します。 2 つ以上のコンテナーを実行する場合、同じ名前を再利用することはできません。 |
   | **mcr.microsoft.com/mssql/server:2017-latest** | SQL Server 2017 Linux コンテナー イメージ。 |

3. Docker コンテナーを表示するには、 `docker ps` コマンドを使用します。


   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker ps -a
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker ps -a
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker ps -a
   ```
   ::: zone-end

   次のスクリーンショットのような出力が表示されます。

   ![Docker ps コマンドの出力](./media/sql-server-linux-setup-docker/docker-ps-command.png)

4. **[STATUS]** 列に **[Up]** の状態が表示されている場合、SQL Server はコンテナーで実行されており、 **[PORTS]** 列に指定されたポートでリッスンしています。 SQL Server コンテナーの **[STATUS]** 列に **[Exited]** と表示されている場合は、[構成ガイドのトラブルシューティングのセクション](sql-server-linux-configure-docker.md#troubleshooting)を参照してください。

`-h` (ホスト名) のパラメーターも役に立ちますが、簡略化のためこのチュートリアルでは使用しません。 これにより、コンテナーの内部名がカスタム値に変更されます。 これは、次の Transact-SQL クエリで返される名前です。

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

`-h` と `--name` を同じ値に設定することは、対象のコンテナーを特定しやすくするためのひとつの良い方法です。

::: moniker-end
<!--End of 2017 "Pull and run" section-->

<!--This is the 2019 version of the "Pull and run" section-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="pullandrun2019"></a>コンテナーイメージをプルして実行する

次の手順を開始する前に、この記事の上部にある優先シェル (bash、PowerShell、または cmd) を選択していることを確認してください。

1. Docker Hub から SQL Server 2019 preview Linux コンテナーイメージをプルします。

   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker pull mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker pull mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker pull mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```
   ::: zone-end

   > [!TIP]
   > このクイックスタートでは、SQL Server 2019 preview Docker イメージを使用します。 SQL Server 2017 イメージを実行する場合は、[この記事の SQL Server 2017 バージョン](quickstart-install-connect-docker.md?view=sql-server-linux-2017#pullandrun2017)を参照してください。

   前のコマンドは、Ubuntu に基づいて SQL Server 2019 preview コンテナーイメージをプルします。 RedHat に基づくコンテナーイメージを使用するには、「 [RHEL ベースのコンテナーイメージを実行](sql-server-linux-configure-docker.md#rhel)する」を参照してください。 利用可能なすべてのイメージを表示するには [mssql-server-linux Docker hub ページ](https://hub.docker.com/_/microsoft-mssql-server) を参照してください。

   ::: zone pivot="cs1-bash"
   この記事の bash コマンドでは、 `sudo`が使用されます。 MacOS では`sudo` 、が不要な場合があります。 Linux では、を使用`sudo`して docker を実行しない場合は、 **docker**グループを構成し、そのグループにユーザーを追加できます。 詳細については、「 [Linux のインストール後の手順](https://docs.docker.com/install/linux/linux-postinstall/)」を参照してください。
   ::: zone-end

2. Docker でコンテナー イメージを実行するには、bash シェル (Linux/macOS) または管理者特権の PowerShell コマンド プロンプトから次のコマンドを使用できます。

   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" \
      -p 1433:1433 --name sql1 \
      -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1433:1433 --name sql1 `
      -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1433:1433 --name sql1 `
      -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
   ```
   ::: zone-end

   > [!NOTE]
   > パスワードは SQL Server の既定のパスワード ポリシーに従う必要があります。従わない場合、コンテナーで SQL Server をセットアップできず、動作が停止します。 既定では、パスワードは8文字以上で、次の4つのセットのうちの3つの文字を含んでいる必要があります。大文字、小文字、10進数、および記号。 [docker ログ](https://docs.docker.com/engine/reference/commandline/logs/) コマンドを実行することでエラー ログを調査することができます。

   > [!NOTE]
   > 既定では、これにより、Developer エディションの SQL Server 2019 preview でコンテナーが作成されます。

   次の表では、前述の `docker run` の例におけるパラメーターを説明しています。

   | パラメーター | 説明 |
   |-----|-----|
   | **-e 'ACCEPT_EULA=Y'** |  **ACCEPT_EULA** 変数を任意の値に設定し、[使用許諾契約書](https://go.microsoft.com/fwlink/?LinkId=746388)の承諾を確定します。 SQL Server イメージに必須の設定です。 |
   | **-e ' SA_PASSWORD =\<Passw0rd\>'** | 8 文字以上で、 [SQL Server のパスワード要件](../relational-databases/security/password-policy.md) を満たす強力なパスワードを指定します。 SQL Server イメージに必須の設定です。 |
   | **-p 1433:1433** | ホスト環境の TCP ポート (最初の値) を コンテナーの TCP ポート (2 番目の値) にマップします。 この例では、SQL Server がコンテナー内の TCP 1433 でリッスンしており、これはホスト上のポート1433に公開されています。 |
   | **--name sql1** | ランダムに生成されたものではなく、コンテナーのカスタム名を指定します。 2 つ以上のコンテナーを実行する場合、同じ名前を再利用することはできません。 |
   | **mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu** | SQL Server 2019 CTP 3.1 Linux コンテナーイメージ。 |

3. Docker コンテナーを表示するには、 `docker ps` コマンドを使用します。

   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker ps -a
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker ps -a
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker ps -a
   ```
   ::: zone-end

   次のスクリーンショットのような出力が表示されます。

   ![Docker ps コマンドの出力](./media/sql-server-linux-setup-docker/docker-ps-command.png)

4. **[STATUS]** 列に **[Up]** の状態が表示されている場合、SQL Server はコンテナーで実行されており、 **[PORTS]** 列に指定されたポートでリッスンしています。 SQL Server コンテナーの **[STATUS]** 列に **[Exited]** と表示されている場合は、[構成ガイドのトラブルシューティングのセクション](sql-server-linux-configure-docker.md#troubleshooting)を参照してください。

`-h` (ホスト名) のパラメーターも役に立ちますが、簡略化のためこのチュートリアルでは使用しません。 これにより、コンテナーの内部名がカスタム値に変更されます。 これは、次の Transact-SQL クエリで返される名前です。

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

`-h` と `--name` を同じ値に設定することは、対象のコンテナーを特定しやすくするためのひとつの良い方法です。

::: moniker-end
<!--End of 2019 "Pull and run" section-->

## <a id="sapassword"></a>SA パスワードの変更

<!-- This section was pasted in from includes/sql-server-linux-change-docker-password.md, to better support zone pivots. 2019/02/11 -->

**SA** アカウントは、セットアップ時に作成される SQL Server インスタンスのシステム管理者です。 SQL Server のコンテナーを作成した後、そのコンテナーで `echo $MSSQL_SA_PASSWORD` を実行すると、指定した環境変数 `MSSQL_SA_PASSWORD` が検索できるようになります。 セキュリティのため、SA のパスワードを変更してください。

1. SA ユーザーに使用する強力なパスワードを選択します。

1. `docker exec` を使用して **sqlcmd** を実行し、Transact-SQL でパスワードを変更します。 次の例では、古いパスワード`<YourStrong!Passw0rd>`と新しい`<YourNewStrong!Passw0rd>`パスワードを実際のパスワード値に置き換えます。

   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P "<YourStrong!Passw0rd>" \
      -Q 'ALTER LOGIN SA WITH PASSWORD="<YourNewStrong!Passw0rd>"'
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourStrong!Passw0rd>" `
      -Q "ALTER LOGIN SA WITH PASSWORD='<YourNewStrong!Passw0rd>'"
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourStrong!Passw0rd>" `
      -Q "ALTER LOGIN SA WITH PASSWORD='<YourNewStrong!Passw0rd>'"
   ```
   ::: zone-end

## <a name="connect-to-sql-server"></a>SQL Server への接続

次の手順では、コンテナー内の SQL Server のコマンドライン ツール **sqlcmd** を使用して、SQL Server に接続します。

1. コマンド `docker exec -it` を使用して、実行中のコンテナー内の対話型 bash シェルを起動します。 次の例にある `sql1` は、コンテナーを作成したときに `--name` パラメーターで指定した名前です。

   ::: zone pivot="cs1-bash"
   ```bash
   sudo docker exec -it sql1 "bash"
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   docker exec -it sql1 "bash"
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   docker exec -it sql1 "bash"
   ```
   ::: zone-end

2. コンテナー内では sqlcmd とローカル接続してください。 既定では sqlcmd はパスにないため、完全なパスを指定する必要があります。

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "<YourNewStrong!Passw0rd>"
   ```

   > [!TIP]
   > コマンド ラインでパスワードを省略すると、入力を求められます。

3. 成功すると、**sqlcmd** のコマンド プロンプトである `1>` が表示されます。

## <a name="create-and-query-data"></a>データの作成とクエリ

次のセクションでは、**sqlcmd** と Transact-SQL を使用して新しいデータベースを作成し、データを追加して簡単なクエリを実行します。

### <a name="create-a-new-database"></a>新しいデータベースの作成

次の手順では、`TestDB` という名前の新しいデータベースを作成します。

1. **sqlcmd** のコマンド プロンプトに次の Transact-SQL コマンドを貼り付け、テスト データベースを作成します。

   ```sql
   CREATE DATABASE TestDB
   ```

2. 次の行に、サーバー上のすべてのデータベースの名前を返すクエリを記述します。

   ```sql
   SELECT Name from sys.Databases
   ```

3. 前の 2 つのコマンドは、すぐに実行されていません。 前のコマンドを実行するには、新しい行に「`GO`」と入力する必要があります。

   ```sql
   GO
   ```

### <a name="insert-data"></a>データの挿入

次に、新しいテーブル `Inventory` を作成し、2 つの新しい行を挿入します。

1. **sqlcmd** のコマンド プロンプトで、新しい `TestDB` データベースのコンテキストに切り替えます。

   ```sql
   USE TestDB
   ```

2. `Inventory` という名前の新しいテーブルを作成します。

   ```sql
   CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
   ```

3. 新しいテーブルにデータを挿入します。

   ```sql
   INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
   ```

4. 「`GO`」と入力して前のコマンドを実行します。

   ```sql
   GO
   ```

### <a name="select-data"></a>データの取得

ここで、`Inventory` テーブルからデータを返すクエリを実行します。

1. **sqlcmd** のコマンド プロンプトで、数量が 152 より大きい`Inventory` テーブルから行を返すクエリを入力します。

   ```sql
   SELECT * FROM Inventory WHERE quantity > 152;
   ```

2. コマンドを実行します。

   ```sql
   GO
   ```

### <a name="exit-the-sqlcmd-command-prompt"></a>sqlcmd コマンド プロンプトの終了

1. **sqlcmd** セッションを終了するには、「`QUIT`」と入力します。

   ```sql
   QUIT
   ```

2. コンテナー内の対話型のコマンド プロンプトを終了するには、`exit`と入力します。 コンテナーは、対話型 bash シェルを終了した後に実行を続けます。

## <a id="connectexternal"></a> コンテナー外部から接続する

SQL 接続をサポートする外部の Linux、Windows、macOS ツールから、Docker コンピューターの SQL Server インスタンスに接続することもできます。

次の手順ではコンテナーの外で **sqlcmd** を使用して、コンテナーで実行されている SQL Server に接続します。 この手順は、コンテナーの外に SQL Server コマンド ライン ツールがインストール済みであることを前提としています。 他のツールを使用する場合も同じ原則が適用されますが、接続プロセスは各ツールに固有です。

1. コンテナーをホストしているコンピューターの IP アドレスを探します。 Linux の場合、 **ifconfig** または **ip addr** を使用します。Windows の場合、**ipconfig** を使用します。

1. この例では、 **sqlcmd**ツールをクライアントコンピューターにインストールします。 詳細については、「 [Windows への sqlcmd のインストール](../tools/sqlcmd-utility.md)」または「 [Linux での sqlcmd のインストール](sql-server-linux-setup-tools.md)」を参照してください。

1. IP アドレスとコンテナーのポート 1433 にマップされたポートを指定して sqlcmd を実行します。 この例では、ホストコンピューター上で同じポート1433が使用されています。 ホストコンピューターで別のマップされたポートを指定した場合は、ここで使用します。

   ::: zone pivot="cs1-bash"
   ```bash
   sqlcmd -S <ip_address>,1433 -U SA -P "<YourNewStrong!Passw0rd>"
   ```
   ::: zone-end

   ::: zone pivot="cs1-powershell"
   ```PowerShell
   sqlcmd -S <ip_address>,1433 -U SA -P "<YourNewStrong!Passw0rd>"
   ```
   ::: zone-end

   ::: zone pivot="cs1-cmd"
   ```cmd
   sqlcmd -S <ip_address>,1433 -U SA -P "<YourNewStrong!Passw0rd>"
   ```
   ::: zone-end

1. Transact-SQL コマンドを実行します。 終了したら `QUIT` を入力します。

SQL Server に接続するその他の一般的なツールには次のものがあります。

- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) on Windows](sql-server-linux-manage-ssms.md)
- [Azure Data Studio](../azure-data-studio/what-is.md)
- [mssql-cli (プレビュー)](https://github.com/dbcli/mssql-cli/blob/master/doc/usage_guide.md)
- [PowerShell コア](sql-server-linux-manage-powershell-core.md)

## <a name="remove-your-container"></a>コンテナーを削除する

このチュートリアルで使用した SQL Server のコンテナーを削除する場合は、次のコマンドを実行します。

::: zone pivot="cs1-bash"
```bash
sudo docker stop sql1
sudo docker rm sql1
```
::: zone-end

::: zone pivot="cs1-powershell"
```PowerShell
docker stop sql1
docker rm sql1
```
::: zone-end

::: zone pivot="cs1-cmd"
```cmd
docker stop sql1
docker rm sql1
```
::: zone-end

> [!WARNING]
> コンテナーを完全に停止して削除すると、コンテナー内のすべての SQL Server データが削除されます。 データを保持する必要がある場合は、[コンテナーからバックアップ ファイルを作成してコピーする](tutorial-restore-backup-in-sql-server-container.md)か、[コンテナー データを永続化する手法](sql-server-linux-configure-docker.md#persist)を使用します。

## <a name="docker-demo"></a>Docker のデモ

Docker の SQL Server コンテナー イメージを使用すると、開発とテストの改善のためにどのように Docker を使用できるかを知りたくなるかもしれません。 次のビデオは、継続的インテグレーションと展開シナリオでどのように Docker を使用できるかを説明しています。

> [!VIDEO https://channel9.msdn.com/Events/Connect/2017/T152/player]

## <a name="next-steps"></a>次のステップ

データベース バックアップファイルをコンテナーに復元する方法については、「[Restore a SQL Server database in a Linux Docker container](tutorial-restore-backup-in-sql-server-container.md)」(Linux の Docker コンテナーで SQL Server データベースを復元する) を参照してください。 複数のコンテナーの実行、データの永続化、トラブルシューティングなど、その他のシナリオについては、「 [Docker でのコンテナーイメージの構成 SQL Server](sql-server-linux-configure-docker.md)」を参照してください。

また、リソース、フィードバック、既知の問題については [mssql-docker GitHub リポジトリ](https://github.com/Microsoft/mssql-docker)をご確認ください。
