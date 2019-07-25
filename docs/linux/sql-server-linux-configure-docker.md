---
title: Docker での SQL Server の構成オプション
description: Docker での SQL Server 2017 および2019プレビューコンテナーイメージの使用方法と操作方法について説明します。 これには、データの保持、ファイルのコピー、およびトラブルシューティングが含まれます。
author: vin-yu
ms.author: vinsonyu
ms.reviewer: vanto
ms.date: 01/17/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: d24bb3566195c71a3b62d16fab867ab5085404b7
ms.sourcegitcommit: d667fa9d6f1c8035f15fdb861882bd514be020d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68388380"
---
# <a name="configure-sql-server-container-images-on-docker"></a>Docker で SQL Server コンテナーイメージを構成する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Docker で[mssql-linux コンテナーイメージ](https://hub.docker.com/_/microsoft-mssql-server)を構成して使用する方法について説明します。 このイメージは、Ubuntu 16.04 の Linux で動作する SQL Server で構成されます。 Linux の Docker エンジン 1.8 + または Docker for Mac/Windows から使用できます。

> [!NOTE]
> この記事では、mssql-linux イメージの使用について特に説明します。 Windows イメージについては説明していませんが、その詳細については、 [mssql-server-Windows Docker Hub のページ](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)を参照してください。

## <a name="pull-and-run-the-container-image"></a>コンテナー イメージのプルと実行

SQL Server 2017 および SQL Server 2019 preview の Docker コンテナーイメージをプルして実行するには、次のクイックスタートの前提条件と手順に従います。

- [Docker を使用して SQL Server 2017 コンテナーイメージを実行する](quickstart-install-connect-docker.md?view=sql-server-2017)
- [Docker を使用して SQL Server 2019 preview コンテナーイメージを実行する](quickstart-install-connect-docker.md?view=sql-server-ver15)

この構成の記事では、次のセクションに示す追加の使用シナリオについて説明します。

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="rhel"></a>RHEL ベースのコンテナーイメージを実行する

SQL Server Linux コンテナーイメージに関するドキュメントはすべて、Ubuntu ベースのコンテナーを指しています。 SQL Server 2019 preview 以降、Red Hat Enterprise Linux (RHEL) に基づくコンテナーを使用できるようになります。 すべての docker コマンドで、コンテナーリポジトリを**mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu**から**mcr.microsoft.com/mssql/rhel/server:2019-CTP3.1**に変更します。

たとえば、次のコマンドは、RHEL を使用する最新の SQL Server 2019 preview コンテナーをプルします。

```bash
sudo docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP3.1
```

```PowerShell
docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP3.1
```

::: moniker-end

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="production"></a>実稼働コンテナーイメージの実行

前のセクションのクイックスタートでは、Docker Hub から SQL Server の無償の Developer エディションを実行します。 Enterprise、Standard、または Web edition などの運用コンテナーイメージを実行する場合でも、ほとんどの情報が適用されます。 ただし、ここではいくつかの違いについて説明します。

- 有効なライセンスを持っている場合は、運用環境でのみ SQL Server を使用できます。 無料の SQL Server Express 運用ライセンスを[こちらで](https://go.microsoft.com/fwlink/?linkid=857693)入手できます。 SQL Server Standard および Enterprise Edition のライセンスは、 [Microsoft ボリュームライセンス](https://www.microsoft.com/licensing/default.aspx)を通じて入手できます。


- Developer コンテナーイメージは、実稼働エディションも実行するように構成できます。 実稼働エディションを実行するには、次の手順に従います。

要件を確認し、[クイックスタート](quickstart-install-connect-docker.md)の手順を実行します。 **MSSQL_PID**環境変数を使用して、実稼働エディションを指定する必要があります。 次の例は、Enterprise Edition の最新の SQL Server 2017 コンテナーイメージを実行する方法を示しています。

```bash
docker run --name sqlenterprise \
      -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      -e 'MSSQL_PID=Enterprise' -p 1433:1433 \
      -d store/microsoft/mssql-server-linux:2017-latest
```

```PowerShell
docker run --name sqlenterprise `
      -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      -e "MSSQL_PID=Enterprise" -p 1433:1433 `
      -d "store/microsoft/mssql-server-linux:2017-latest"
 ```

> [!IMPORTANT]
> 値**Y**を環境変数**ACCEPT_EULA**に渡し、エディション値を**MSSQL_PID**に渡すことによって、使用する SQL Server のエディションとバージョンに対して、有効で既存のライセンスを持っていることが表現されます。 Docker コンテナーイメージで実行されている SQL Server ソフトウェアの使用は、SQL Server ライセンスの条項によって管理されることにも同意します。

> [!NOTE]
> **MSSQL_PID**で使用できる値の完全な一覧については、「 [Linux での環境変数を使用した SQL Server 設定の構成](sql-server-linux-configure-environment-variables.md)」を参照してください。

::: moniker-end

## <a name="connect-and-query"></a>接続とクエリ

コンテナーの外部またはコンテナー内から、コンテナー内の SQL Server に接続してクエリを実行できます。 次のセクションでは、両方のシナリオについて説明します。 

### <a name="tools-outside-the-container"></a>コンテナーの外部のツール

SQL 接続をサポートする任意の外部 Linux、Windows、または macOS ツールから、Docker マシンの SQL Server インスタンスに接続できます。 いくつかの一般的なツールを次に示します。

- [sqlcmd](sql-server-linux-setup-tools.md)
- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) on Windows](sql-server-linux-manage-ssms.md)

次の例では、 **sqlcmd**を使用して、Docker コンテナーで実行されている SQL Server に接続します。 接続文字列の IP アドレスは、コンテナーを実行しているホストコンピューターの IP アドレスです。

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

既定の**1433**ではないホストポートをマップした場合は、そのポートを接続文字列に追加します。 たとえば、 `docker run`コマンドでを指定`-p 1400:1433`した場合は、ポート1400を明示的に指定して接続します。

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>コンテナー内のツール

SQL Server 2017 preview 以降では、 [SQL Server のコマンドラインツール](sql-server-linux-setup-tools.md)がコンテナーイメージに含まれています。 対話型のコマンドプロンプトを使用してイメージにアタッチする場合は、ツールをローカルで実行できます。

1. コマンド `docker exec -it` を使用して、実行中のコンテナー内の対話型 bash シェルを起動します。 次の例`e69e056c702d`では、コンテナー ID です。

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > 常にコンテナー id 全体を指定する必要はありません。一意に識別するのに十分な文字を指定するだけで済みます。 したがって、この例では、完全な id `e6`で`e69`はなく、またはを使用することができます。

2. コンテナー内では sqlcmd とローカル接続してください。 既定では sqlcmd はパスにないため、完全なパスを指定する必要があります。

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. Sqlcmd が終了したら、 `exit`「」と入力します。

4. 対話型コマンドプロンプトでの操作が完了したら`exit`、「」と入力します。 コンテナーは、対話型 bash シェルを終了した後に実行を続けます。

## <a name="run-multiple-sql-server-containers"></a>複数の SQL Server コンテナーを実行する

Docker には、同じホストコンピューター上で複数の SQL Server コンテナーを実行する方法が用意されています。 これは、同じホストに複数の SQL Server インスタンスを必要とするシナリオの場合のアプローチです。 各コンテナーは、別のポートで公開する必要があります。

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

次の例では、2つの SQL Server 2017 コンテナーを作成し、ホストコンピューター上のポート**1401**と**1402**にマップします。

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

次の例では、2つの SQL Server 2019 プレビューコンテナーを作成し、ホストコンピューター上のポート**1401**と**1402**にマップします。

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

これで、SQL Server の2つのインスタンスが別々のコンテナーで実行されるようになりました。 クライアントは、Docker ホストの IP アドレスとコンテナーのポート番号を使用して、各 SQL Server インスタンスに接続できます。

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="customcontainer"></a>カスタマイズしたコンテナーを作成する

独自の[Dockerfile](https://docs.docker.com/engine/reference/builder/#usage)を作成して、カスタマイズされた SQL Server コンテナーを作成することができます。 詳細については、 [SQL Server とノードアプリケーションを組み合わせたデモ](https://github.com/twright-msft/mssql-node-docker-demo-app)を参照してください。 独自の Dockerfile を作成する場合は、フォアグラウンドプロセスに注意してください。このプロセスでは、コンテナーの有効期間が制御されるためです。 終了すると、コンテナーがシャットダウンします。 たとえば、スクリプトを実行して SQL Server を開始する場合は、SQL Server プロセスが一番右のコマンドであることを確認します。 その他のコマンドはすべてバックグラウンドで実行されます。 これは、Dockerfile 内の次のコマンドで示されています。

```bash
/usr/src/app/do-my-sql-commands.sh & /opt/mssql/bin/sqlservr
```

前の例のコマンドを元に戻した場合、do-my-sql-commands.sh スクリプトの完了時にコンテナーがシャットダウンします。

## <a id="persist"></a>データを保持する

`docker stop` と`docker start`を使用してコンテナーを再起動しても、SQL Server の構成変更およびデータベースファイルはコンテナーに保持されます。 ただし、を使用`docker rm`してコンテナーを削除すると、SQL Server とデータベースを含むコンテナー内のすべてが削除されます。 次のセクションでは、関連付けられているコンテナーが削除された場合でも、**データボリューム**を使用してデータベースファイルを永続化する方法について説明します。

> [!IMPORTANT]
> SQL Server については、Docker でのデータの永続化について理解しておくことが重要です。 このセクションの説明に加えて、docker[コンテナーでデータを管理する方法](https://docs.docker.com/engine/tutorials/dockervolumes/)については、docker のドキュメントを参照してください。

### <a name="mount-a-host-directory-as-data-volume"></a>データボリュームとしてホストディレクトリをマウントする

1つ目のオプションは、コンテナー内のデータボリュームとしてホストにディレクトリをマウントすることです。 これを行うには、 `docker run`コマンドを`-v <host directory>:/var/opt/mssql`フラグと共に使用します。 これにより、コンテナーの実行間でデータを復元できます。

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

この手法では、Docker の外部にあるホスト上のファイルを共有して表示することもできます。

> [!IMPORTANT]
> 現時点では、SQL Server on Linux イメージを使用した Docker on Mac のホストボリュームマッピングはサポートされていません。 代わりにデータボリュームコンテナーを使用してください。 この制限は、 `/var/opt/mssql`ディレクトリに固有のものです。 マウントされたディレクトリからの読み取りは正常に機能します。 たとえば、Mac で-v を使用してホストディレクトリをマウントし、ホスト上に存在する .bak ファイルからバックアップを復元することができます。

### <a name="use-data-volume-containers"></a>データボリュームコンテナーを使用する

2つ目は、データボリュームコンテナーを使用する方法です。 データボリュームコンテナーを作成するには、 `-v`パラメーターを使用して、ホストディレクトリではなくボリューム名を指定します。 次の例では、 **sqlvolume**という名前の共有データボリュームを作成します。

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```
::: moniker-end

> [!NOTE]
> Run コマンドでデータボリュームを暗黙的に作成するためのこの手法は、以前のバージョンの Docker では動作しません。 その場合は、Docker のドキュメントに記載されている明示的な手順を使用して、[データボリュームコンテナーを作成およびマウント](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container)します。

このコンテナーを停止して削除しても、データボリュームは保持されます。 `docker volume ls`コマンドを使用して表示できます。

```bash
docker volume ls
```

その後、同じボリューム名を持つ別のコンテナーを作成すると、新しいコンテナーは、ボリュームに含まれているのと同じ SQL Server データを使用します。

データボリュームコンテナーを削除するには、 `docker volume rm`コマンドを使用します。

> [!WARNING]
> データボリュームコンテナーを削除すると、コンテナー内のすべての SQL Server データが*完全*に削除されます。

### <a name="backup-and-restore"></a>バックアップと復元

これらのコンテナー手法に加えて、標準の SQL Server バックアップと復元の手法を使用することもできます。 バックアップファイルを使用すると、データを保護したり、別の SQL Server インスタンスにデータを移動したりすることができます。 詳細については、「 [Linux 上の SQL Server データベースのバックアップと復元](sql-server-linux-backup-and-restore-database.md)」を参照してください。

> [!WARNING]
> バックアップを作成する場合は、必ずコンテナーの外部でバックアップファイルを作成またはコピーしてください。 それ以外の場合、コンテナーが削除されると、バックアップファイルも削除されます。

## <a name="execute-commands-in-a-container"></a>コンテナー内のコマンドを実行する

実行中のコンテナーがある場合は、ホストターミナルからコンテナー内でコマンドを実行できます。

コンテナー ID を取得するには、次のように実行します。

```bash
docker ps
```

コンテナーで bash ターミナルを開始するには、次のように実行します。

```bash
docker exec -it <Container ID> /bin/bash
```

これで、コンテナー内のターミナルで実行する場合と同じようにコマンドを実行できるようになりました。 終了したら `exit` を入力します。 これは対話型コマンドセッションで終了しますが、コンテナーは引き続き実行されます。

## <a name="copy-files-from-a-container"></a>コンテナーからファイルをコピーする

ファイルをコンテナーからコピーするには、次のコマンドを使用します。

```bash
docker cp <Container ID>:<Container path> <host path>
```

**例:**

```bash
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog /tmp/errorlog
```

```PowerShell
docker cp d6b75213ef80:/var/opt/mssql/log/errorlog C:\Temp\errorlog
```

## <a name="copy-files-into-a-container"></a>コンテナーへのファイルのコピー

ファイルをコンテナーにコピーするには、次のコマンドを使用します。

```bash
docker cp <Host path> <Container ID>:<Container path>
```

**例:**

```bash
docker cp /tmp/mydb.mdf d6b75213ef80:/var/opt/mssql/data
```

```PowerShell
docker cp C:\Temp\mydb.mdf d6b75213ef80:/var/opt/mssql/data
```
## <a id="tz"></a>タイムゾーンの構成

特定のタイムゾーンを持つ Linux コンテナーで SQL Server を実行するには、 **TZ**環境変数を構成します。 正しいタイムゾーン値を検索するには、Linux bash プロンプトから**tzselect**コマンドを実行します。

```bash
tzselect
```

タイムゾーンを選択すると、 **tzselect**に次のような出力が表示されます。

```bash
The following information has been given:

        United States
        Pacific

Therefore TZ='America/Los_Angeles' will be used.
```

この情報を使用して、Linux コンテナーで同じ環境変数を設定できます。 次の例は、 `Americas/Los_Angeles`タイムゾーン内のコンテナーで SQL Server を実行する方法を示しています。

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -p 1433:1433 --name sql1 \
   -e 'TZ=America/Los_Angeles'\
   -d mcr.microsoft.com/mssql/server:2017-latest 
```

```PowerShell
sudo docker run -e 'ACCEPT_EULA=Y' -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -p 1433:1433 --name sql1 `
   -e "TZ=America/Los_Angeles" `
   -d mcr.microsoft.com/mssql/server:2017-latest 
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -p 1433:1433 --name sql1 \
   -e 'TZ=America/Los_Angeles'\
   -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

```PowerShell
sudo docker run -e 'ACCEPT_EULA=Y' -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -p 1433:1433 --name sql1 `
   -e "TZ=America/Los_Angeles" `
   -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```
::: moniker-end

## <a id="tags"></a>特定の SQL Server コンテナーイメージを実行する

最新の SQL Server コンテナーイメージを使用しないシナリオもあります。 特定の SQL Server コンテナーイメージを実行するには、次の手順に従います。

1. 使用するリリースの Docker**タグ**を特定します。 使用可能なタグを表示するには、 [mssql-server-Linux Docker hub のページ](https://hub.docker.com/_/microsoft-mssql-server)を参照してください。

2. タグを使用して SQL Server コンテナーイメージをプルします。 たとえば、RC1 イメージをプルするには、 `<image_tag>`次のコマンドでを`rc1`に置き換えます。

   ```bash
   docker pull mcr.microsoft.com/mssql/server:<image_tag>
   ```

3. そのイメージで新しいコンテナーを実行するには、 `docker run`コマンドでタグ名を指定します。 次のコマンドで、を`<image_tag>`実行するバージョンに置き換えます。

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

これらの手順は、既存のコンテナーをダウングレードするためにも使用できます。 たとえば、実行中のコンテナーをロールバックまたはダウングレードして、トラブルシューティングやテストを行うことができます。 実行中のコンテナーをダウングレードするには、データフォルダーの永続化手法を使用する必要があります。 [「Upgrade」セクション](#upgrade)で説明したのと同じ手順に従いますが、新しいコンテナーを実行するときは、古いバージョンのタグ名を指定します。

## <a id="version"></a>コンテナーのバージョンを確認する

実行中の docker コンテナー内の SQL Server のバージョンを知りたい場合は、次のコマンドを実行して表示します。 ターゲット`<Container ID or name>`コンテナーの ID または名前で置き換えます。 を`<YourStrong!Passw0rd>` SA ログインの SQL Server パスワードに置き換えます。

```bash
sudo docker exec -it <Container ID or name> /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P '<YourStrong!Passw0rd>' \
   -Q 'SELECT @@VERSION'
```

```PowerShell
docker exec -it <Container ID or name> /opt/mssql-tools/bin/sqlcmd `
   -S localhost -U SA -P "<YourStrong!Passw0rd>" `
   -Q 'SELECT @@VERSION'
```

また、ターゲットの docker コンテナーイメージの SQL Server バージョンとビルド番号を特定することもできます。 次のコマンドは、 **microsoft/mssql-Server-linux: 2017-latest**イメージの SQL Server バージョンとビルド情報を表示します。 これを行うには、環境変数**PAL_PROGRAM_INFO = 1**を使用して新しいコンテナーを実行します。 結果のコンテナーはすぐに終了し`docker rm` 、コマンドによって削除されます。

```bash
sudo docker run -e PAL_PROGRAM_INFO=1 --name sqlver \
   -ti mcr.microsoft.com/mssql/server:2017-latest && \
   sudo docker rm sqlver
```

```PowerShell
docker run -e PAL_PROGRAM_INFO=1 --name sqlver `
   -ti mcr.microsoft.com/mssql/server:2017-latest; `
   docker rm sqlver
```

上記のコマンドでは、次の出力のようなバージョン情報が表示されます。

```Text
sqlservr
  Version 14.0.3029.16
  Build ID ee3d3882f1c48a7a7e590a620153012eaedc2f37143d485df945a079b9d4eeea
  Build Type release
  Git Version 65d42c4
  Built at Sat Jun 16 01:20:11 GMT 2018

PAL
  Build ID 60cfcb134bbae96d311f6a4f56aeb5a685b3809de80bcb61ec587a8f58b555eb
  Build Type release
  Git Version 21a4c11
  Built at Sat Jun 16 01:18:53 GMT 2018

Packages
  system.sfp                    6.2.9200.1,21a4c1178,
  system.common.sfp             10.0.15063.540
  system.certificates.sfp       6.2.9200.1,21a4c1178,
  system.netfx.sfp              4.6.1590.0
  secforwarderxplat.sfp         14.0.3029.16
  sqlservr.sfp                  14.0.3029.16
  sqlagent.sfp                  14.0.3029.16
```

## <a id="upgrade"></a>コンテナーの SQL Server のアップグレード

Docker を使用してコンテナーイメージをアップグレードするには、まず、アップグレードのためにリリースのタグを特定します。 次のコマンドを使用し`docker pull`て、レジストリからこのバージョンをプルします。

```bash
docker pull mcr.microsoft.com/mssql/server:<image_tag>
```

これにより、作成した新しいコンテナーの SQL Server イメージが更新されますが、実行中のコンテナーで SQL Server は更新されません。 これを行うには、最新の SQL Server コンテナーイメージを使用して新しいコンテナーを作成し、その新しいコンテナーにデータを移行する必要があります。

1. 既存の SQL Server コンテナーに[データ永続化手法](#persist)のいずれかを使用していることを確認します。 これにより、同じデータを使用して新しいコンテナーを開始できます。

1. `docker stop`コマンドを使用して、SQL Server コンテナーを停止します。

1. で`docker run`新しい SQL Server コンテナーを作成し、マップされたホストディレクトリまたはデータボリュームコンテナーを指定します。 SQL Server のアップグレードには、必ず特定のタグを使用してください。 新しいコンテナーでは、既存の SQL Server データで新しいバージョンの SQL Server が使用されるようになりました。

   > [!IMPORTANT]
   > 現時点では、アップグレードは RC1、RC2、GA の間のみサポートされています。

1. 新しいコンテナー内のデータベースとデータを確認します。

1. 必要に応じて、古いコンテナー `docker rm`をで削除します。

## <a id="troubleshooting"></a> トラブルシューティング

次のセクションでは、コンテナーで SQL Server を実行するためのトラブルシューティングの推奨事項について説明します。

### <a name="docker-command-errors"></a>Docker コマンドのエラー

いずれか`docker`のコマンドでエラーが発生した場合は、docker サービスが実行されていることを確認し、高度な権限で実行してみてください。

たとえば、Linux では、コマンドの実行時に次のエラー `docker`が表示される場合があります。

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

Linux でこのエラーが発生した場合は、で始まる`sudo`同じコマンドを実行してみてください。 失敗した場合は、docker サービスが実行されていることを確認し、必要に応じて開始します。

```bash
sudo systemctl status docker
sudo systemctl start docker
```

Windows で、管理者として PowerShell またはコマンドプロンプトを起動していることを確認します。

### <a name="sql-server-container-startup-errors"></a>SQL Server コンテナーのスタートアップエラー

SQL Server コンテナーの実行に失敗した場合は、次のテストを試してください。

- **"ネットワークブリッジにエンドポイント CONTAINER_NAME を作成できませんでした。" などのエラーが表示された場合。プロキシの開始エラー: リッスン tcp 0.0.0.0: 1433 バインド: アドレスは既に使用されています。 '** 次に、コンテナーポート1433を既に使用されているポートにマップしようとしています。 これは、ホストコンピューターで SQL Server ローカルに実行している場合に発生する可能性があります。 また、2つの SQL Server コンテナーを開始し、両方を同じホストポートにマップしようとした場合にも発生する可能性があります。 これが発生した場合`-p`は、パラメーターを使用して、コンテナーポート1433を別のホストポートにマップします。 以下に例を示します。 

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d mcr.microsoft.com/mssql/server:2017-latest`.
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d mcr.microsoft.com/mssql/server:2017-latest`.
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu`.
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu`.
```

::: moniker-end

- **"Unix:///var/run/docker.sock で Docker デーモンソケットに接続しようとしているときにアクセス許可が拒否されました。" などのエラーが表示された場合は、次のようになります。Get http://%2Fvar%2Frun%2Fdocker.sock/v1.30tdout=1&tail=all: unix/var/run/docker.sock: connect: アクセス許可が**拒否されました。コンテナーを起動しようとしたときに、Ubuntu の docker グループにユーザーを追加します。 この変更は新しいセッションに影響するため、ログアウトして再度ログインします。 

   ```bash
    usermod -aG docker $USER
    ```
- コンテナーからのエラーメッセージがあるかどうかを確認します。

    ```bash
    docker logs e69e056c702d
    ```

- クイックスタートの記事の「[前提条件](quickstart-install-connect-docker.md#requirements)」セクションで指定されている最小メモリおよびディスク要件を満たしていることを確認してください。

- コンテナー管理ソフトウェアを使用している場合は、ルートとして実行されているコンテナープロセスがサポートされていることを確認してください。 コンテナー内の sqlservr.exe プロセスは、ルートとして実行されます。

- SQL Server の[セットアップログとエラーログ](#errorlogs)を確認します。

### <a name="enable-dump-captures"></a>ダンプキャプチャを有効にする

SQL Server プロセスがコンテナー内で失敗している場合は、 **SYS_PTRACE**が有効になっている新しいコンテナーを作成する必要があります。 これにより、プロセスをトレースする Linux 機能が追加されます。これは、例外でダンプファイルを作成するために必要です。 ダンプファイルは、問題のトラブルシューティングに役立つように、サポートが使用できます。 次の docker run コマンドを使用すると、この機能が有効になります。

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

### <a name="sql-server-connection-failures"></a>SQL Server 接続エラー

コンテナーで実行されている SQL Server インスタンスに接続できない場合は、次のテストを試してください。

- `docker ps -a`出力の**STATUS**列を参照して、SQL Server コンテナーが実行されていることを確認します。 そうでない場合`docker start <Container ID>`は、を使用して開始します。

- (1433 ではなく) 既定以外のホストポートにマップした場合は、接続文字列でポートを指定していることを確認してください。 ポートマッピングは、 `docker ps -a`出力の **ポート**列に表示されます。 たとえば、次のコマンドは、sqlcmd をポート1401でリッスンしているコンテナーに接続します。

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- 既存のマップ`docker run`済みデータボリュームまたはデータボリュームコンテナーと共にを使用した場合`MSSQL_SA_PASSWORD`、SQL Server はの値を無視します。 代わりに、事前に構成された SA ユーザーのパスワードが、データボリュームまたはデータボリュームコンテナーの SQL Server データから使用されます。 アタッチしているデータに関連付けられている SA パスワードを使用していることを確認します。

- SQL Server の[セットアップログとエラーログ](#errorlogs)を確認します。

### <a name="sql-server-availability-groups"></a>可用性グループの SQL Server

SQL Server 可用性グループで Docker を使用している場合は、2つの追加要件があります。

- レプリカ通信に使用されるポートをマップします (既定値は 5022)。 たとえば、 `docker run`コマンドの`-p 5022:5022`一部としてを指定します。

- コマンドのパラメーター`-h YOURHOSTNAME`を使用して、コンテナーのホスト名を明示的に設定します。 `docker run` このホスト名は、可用性グループを構成するときに使用されます。 を指定しない場合、 `-h`既定でコンテナー ID が使用されます。

### <a id="errorlogs"></a>セットアップとエラーログの SQL Server

SQL Server のセットアップログとエラーログは、 **/var/opt/mssql/log**で確認できます。 コンテナーが実行されていない場合は、まずコンテナーを開始します。 次に、対話型のコマンドプロンプトを使用して、ログを検査します。

```bash
docker start e69e056c702d
docker exec -it e69e056c702d "bash"
```

コンテナー内の bash セッションから、次のコマンドを実行します。

```bash
cd /var/opt/mssql/log
cat setup*.log
cat errorlog
```

> [!TIP]
> コンテナーの作成時にホストディレクトリを **/var/opt/mssql**にマウントした場合は、代わりに、ホスト上のマップされたパスの**log**サブディレクトリを調べることができます。

## <a name="next-steps"></a>次のステップ

この[クイックスタート](quickstart-install-connect-docker.md)では、Docker で SQL Server 2017 のコンテナーイメージを使ってみましょう。

また、リソース、フィードバック、既知の問題については、 [mssql-Docker GitHub リポジトリ](https://github.com/Microsoft/mssql-docker)を参照してください。

[SQL Server コンテナーの高可用性について](sql-server-linux-container-ha-overview.md)
