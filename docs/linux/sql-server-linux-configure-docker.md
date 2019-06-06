---
title: Docker で SQL Server の構成オプション |Microsoft Docs
description: さまざまな方法を使用して、SQL Server 2017 と Docker の 2019 プレビュー コンテナー イメージとの対話について説明します。 これには、データ永続化ファイルのコピー、およびトラブルシューティングにはが含まれます。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/17/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: f6364755ee1719a17f4927cfd157b757c6097830
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66705558"
---
# <a name="configure-sql-server-container-images-on-docker"></a>Docker で SQL Server のコンテナー イメージを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、構成および使用する方法をについて説明します、 [mssql server-linux コンテナー イメージ](https://hub.docker.com/_/microsoft-mssql-server)Docker を使用します。 このイメージは、Ubuntu 16.04 の Linux で動作する SQL Server で構成されます。 Linux の Docker エンジン 1.8 + または Docker for Mac/Windows から使用できます。

> [!NOTE]
> この記事では、具体的には、mssql のサーバーの linux イメージを使用してについて説明します。 Windows イメージは取り上げませんで詳細情報を入手することができます、 [mssql server-windows の Docker Hub ページ](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)します。

## <a name="pull-and-run-the-container-image"></a>コンテナー イメージのプルと実行

プルし、Docker コンテナー イメージの SQL Server 2017 と SQL Server 2019 のプレビューを実行、前提条件と次のクイック スタートの手順に従います。

- [Docker を使用した SQL Server 2017 コンテナー イメージを実行します。](quickstart-install-connect-docker.md?view=sql-server-2017)
- [Docker を使用した SQL Server 2019 プレビューのコンテナー イメージを実行します。](quickstart-install-connect-docker.md?view=sql-server-ver15)

この構成に関する記事では、次のセクションでは、追加の使用シナリオを提供します。

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="rhel"></a> RHEL ベースのコンテナー イメージを実行します。

すべての SQL Server Linux コンテナー イメージのドキュメントは、Ubuntu ベースのコンテナーをポイントします。 SQL Server 2019 プレビュー以降、Red Hat Enterprise Linux (RHEL) に基づくコンテナーを使用できます。 コンテナー リポジトリから変更**mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu**に**mcr.microsoft.com/mssql/rhel/server:2019-CTP2.4**ですべての docker コマンド。

たとえば、次のコマンドでは、RHEL を使用する最新の SQL Server 2019 プレビュー コンテナーは取得します。

```bash
sudo docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP2.4
```

```PowerShell
docker pull mcr.microsoft.com/mssql/rhel/server:2019-CTP2.4
```

::: moniker-end

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="production"></a> 運用環境にコンテナー イメージを実行します。

前のセクションで、クイック スタートでは、Docker Hub から SQL Server の無料の Developer edition を実行します。 ほとんどの情報は、Enterprise、Standard、または Web edition などのコンテナー イメージを運用環境に実行する場合にも適用されます。 ただし、ここに記載されているいくつかの違いがあります。

- のみ、有効なライセンスがある場合、SQL Server を運用環境で使用できます。 無料の SQL Server Express の運用環境ライセンスを取得する[ここ](https://go.microsoft.com/fwlink/?linkid=857693)します。 SQL Server Standard および Enterprise Edition のライセンスを利用[Microsoft ボリューム ライセンス](https://www.microsoft.com/licensing/default.aspx)します。


- 同様に運用エディションを実行する開発者のコンテナー イメージを構成できます。 実稼働エディションを実行するのにには、次の手順を使用します。

プロシージャを実行し、要件を確認、[クイック スタート](quickstart-install-connect-docker.md)します。 実稼働エディションを指定する必要があります、 **MSSQL_PID**環境変数。 次の例では、Enterprise Edition の最新の SQL Server 2017 コンテナー イメージを実行する方法を示します。

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
> 値を渡すことによって**Y**環境変数に**ACCEPT_EULA**にエディションの値と**MSSQL_PID**、有効であり、既存のライセンスがあることを表現する、使用する SQL Server のバージョンとエディション。 また、Docker コンテナー イメージをで実行されている SQL Server ソフトウェアの使用は、SQL Server ライセンスの条項に準拠するものを同意するものです。

> [!NOTE]
> 使用できる値の完全な一覧については**MSSQL_PID**を参照してください[on Linux の環境変数と SQL Server の構成設定](sql-server-linux-configure-environment-variables.md)します。

::: moniker-end

## <a name="connect-and-query"></a>接続し、クエリ

接続してクエリまたは内から、コンテナーの外部からのコンテナー内の SQL Server のコンテナー。 次のセクションでは、両方のシナリオについて説明します。 

### <a name="tools-outside-the-container"></a>コンテナーの外部ツール

どの外部 Linux、Windows、または macOS ツールから SQL 接続をサポートする Docker コンピューターに SQL Server インスタンスに接続できます。 いくつかの一般的なツールは次のとおりです。

- [sqlcmd](sql-server-linux-setup-tools.md)
- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) on Windows](sql-server-linux-manage-ssms.md)

次の例では**sqlcmd** Docker コンテナーで実行される SQL Server に接続します。 接続文字列で IP アドレスは、コンテナーを実行して、ホスト コンピューターの IP アドレスです。

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

ホスト ポートが既定値を割り当てたかどうか**1433**、接続文字列にそのポートを追加します。 たとえば、指定した`-p 1400:1433`で、`docker run`コマンドを使用しを明示的に接続 1400 のポートを指定します。

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>コンテナー内のツール

SQL Server 2017 のプレビュー以降、 [SQL Server コマンド ライン ツール](sql-server-linux-setup-tools.md)コンテナー イメージに含まれます。 対話型コマンド プロンプトで、イメージをアタッチする場合は、ローカルのツールを実行できます。

1. コマンド `docker exec -it` を使用して、実行中のコンテナー内の対話型 bash シェルを起動します。 次の例では`e69e056c702d`はコンテナーの ID です。

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > 常に、全体のコンテナーの id を指定する必要はありません。のみ、それを一意に識別するための十分な文字を指定する必要があるとします。 この例で使用するのに十分なする可能性があります`e6`または`e69`完全な id ではなく。

2. コンテナー内では sqlcmd とローカル接続してください。 その sqlcmd がパスにない、既定では、完全なパスを指定する必要があるので注意してください。

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. 終了したら、sqlcmd を使用した、入力`exit`します。

4. 対話型のコマンド プロンプトを終了したら、入力`exit`します。 コンテナーは、対話型 bash シェルを終了した後に実行を続けます。

## <a name="run-multiple-sql-server-containers"></a>複数の SQL Server のコンテナーを実行します。

Docker は、同じホスト コンピューターで複数の SQL Server のコンテナーを実行する方法を提供します。 これは、同じホスト上の SQL Server の複数のインスタンスを必要とするシナリオのアプローチです。 各コンテナーは、別のポートで自体を公開する必要があります。

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

次の例は、2 つの SQL Server 2017 コンテナーを作成し、ポートにマッピング**1401**と**1402**ホスト コンピューターにします。

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

次の例は、2 つの SQL Server 2019 プレビュー コンテナーを作成し、ポートにマッピング**1401**と**1402**ホスト コンピューターにします。

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

::: moniker-end

2 つの個別のコンテナーで実行されている SQL Server インスタンスがあるようになりました。 クライアントは、コンテナーの Docker ホストとポート番号の IP アドレスを使用して、各 SQL Server インスタンスに接続できます。

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="customcontainer"></a> カスタマイズされたコンテナーを作成します。

独自に作成することは[Dockerfile](https://docs.docker.com/engine/reference/builder/#usage)カスタマイズされた SQL Server のコンテナーを作成します。 詳細については、次を参照してください。[を SQL Server および Node アプリケーションを組み合わせたデモ](https://github.com/twright-msft/mssql-node-docker-demo-app)します。 独自の Dockerfile を作成する場合は、このプロセスは、コンテナーの有効期間を制御するため、フォア グラウンド プロセスでは、注意します。 セッションを終了する場合に、コンテナーはシャット ダウンします。 たとえば、スクリプトを実行し、SQL Server を起動する場合は、ことを SQL Server プロセスが、右端のコマンドであることを確認します。 その他のすべてのコマンドは、バック グラウンドで実行されます。 これは、Dockerfile 内の次のコマンドに示します。

```bash
/usr/src/app/do-my-sql-commands.sh & /opt/mssql/bin/sqlservr
```

前の例のコマンドを元に戻す場合は、do-マイ-sql-commands.sh スクリプトが完了すると、シャット ダウンは、コンテナー。

## <a id="persist"></a> データを保存します。

コンテナーを再起動する場合でも、SQL Server 構成の変更とデータベース ファイルがコンテナーに永続化`docker stop`と`docker start`します。 ただしのコンテナーを削除する場合`docker rm`、SQL Server データベースなど、削除、コンテナー内のすべて。 次のセクションを使用する方法を説明する**データ ボリューム**関連付けられているコンテナーが削除された場合でも、データベース ファイルを保持します。

> [!IMPORTANT]
> SQL server の Docker でのデータの永続性を理解することが重要です。 このセクションの詳細については、だけでなくで Docker のドキュメントを参照してください。 [Docker コンテナー内のデータを管理する方法](https://docs.docker.com/engine/tutorials/dockervolumes/)します。

### <a name="mount-a-host-directory-as-data-volume"></a>データ ボリュームとしてホスト ディレクトリをマウントします。

最初のオプションでは、ディレクトリをホスト上では、コンテナー データ ボリュームとしてマウントします。 そのために使用して、`docker run`コマンドと、`-v <host directory>:/var/opt/mssql`フラグ。 これにより、コンテナーの実行間で復元するデータ。

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
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

::: moniker-end

この手法では、共有し、Docker の外部でホスト上のファイルを表示することもできます。

> [!IMPORTANT]
> この時点では、SQL Server Linux イメージ上で Mac 上の Docker のホスト ボリュームのマッピングはサポートされていません。 データ ボリューム コンテナーを使用してください。 この制限に固有の`/var/opt/mssql`ディレクトリ。 正常にマウントされたディレクトリ動作からの読み取り。 たとえば、-v を使用して、Mac 上でホスト ディレクトリをマウントでき、ホスト上にある .bak ファイルからバックアップを復元できます。

### <a name="use-data-volume-containers"></a>データ ボリューム コンテナーを使用します。

2 番目のオプションでは、データのボリューム コンテナーを使用します。 データ ボリューム コンテナーを作成するにはホストのディレクトリではなくボリューム名を指定することによって、`-v`パラメーター。 次の例では、という名前の共有データ ボリュームを作成する**sqlvolume**します。

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
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```
::: moniker-end

> [!NOTE]
> 以前のバージョンの Docker run コマンドでデータ ボリュームを暗黙的に作成するためには、この手法が機能しません。 その場合は、Docker のドキュメントに記載されている明示的な手順を使用して、[の作成とデータ ボリューム コンテナーをマウント](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container)します。

停止および、このコンテナーを削除する場合でも、データ ボリュームが永続化します。 表示できます、`docker volume ls`コマンド。

```bash
docker volume ls
```

同じボリュームの名前を持つ別のコンテナーを作成し、新しいコンテナーは、ボリュームに含まれている同じ SQL Server のデータを使用します。

データのボリューム コンテナーを削除するには、使用、`docker volume rm`コマンド。

> [!WARNING]
> データのボリューム コンテナーを削除する場合は、コンテナー内の SQL Server データ、*完全に*削除します。

### <a name="backup-and-restore"></a>バックアップと復元

これらのコンテナー テクノロジだけでなくも標準の SQL Server のバックアップを使用し、復元の手法ことができます。 または別の SQL Server インスタンスにデータを移動するデータを保護するバックアップ ファイルを使用することができます。 詳細については、次を参照してください。 [Linux 上のデータベースを SQL Server のバックアップと復元](sql-server-linux-backup-and-restore-database.md)します。

> [!WARNING]
> バックアップを作成する場合は、作成またはコンテナーの外部でバックアップ ファイルをコピーすることを確認してください。 それ以外の場合、コンテナーが削除された場合、バックアップ ファイルも削除されます。

## <a name="execute-commands-in-a-container"></a>コンテナーでコマンドを実行します。

実行中のコンテナーがある場合は、ターミナルのホストからコンテナー内のコマンドを実行できます。

実行するコンテナー ID を取得します。

```bash
docker ps
```

ターミナルを実行するコンテナーで bash を開始するには。

```bash
docker exec -ti <Container ID> /bin/bash
```

これで、コンテナー内のターミナルで実行している場合と同様にコマンドを実行できます。 終了したら `exit` を入力します。 コマンドの対話型セッションでこれが終了したが、コンテナーの実行が継続されます。

## <a name="copy-files-from-a-container"></a>コンテナーからファイルをコピーします。

コンテナーからファイルをコピーするには、次のコマンドを使用します。

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

## <a name="copy-files-into-a-container"></a>コンテナーにファイルをコピーします。

コンテナーにファイルをコピーするには、次のコマンドを使用します。

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
## <a id="tz"></a> タイム ゾーンを構成します。

特定のタイム ゾーンを使用して、Linux コンテナーで SQL Server を実行するには、構成、 **TZ**環境変数。 右側の timezone の値を見つけるには、実行、 **tzselect** Linux の bash プロンプトからコマンド。

```bash
tzselect
```

タイム ゾーンを選択した後**tzselect**次のような出力が表示されます。

```bash
The following information has been given:

        United States
        Pacific

Therefore TZ='America/Los_Angeles' will be used.
```

この情報を使用して、Linux コンテナーで同じ環境変数を設定することができます。 次の例では、コンテナー内に SQL Server を実行する方法を示しています、`Americas/Los_Angeles`タイム ゾーン。

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
   -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

```PowerShell
sudo docker run -e 'ACCEPT_EULA=Y' -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -p 1433:1433 --name sql1 `
   -e "TZ=America/Los_Angeles" `
   -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```
::: moniker-end

## <a id="tags"></a> 特定の SQL Server のコンテナー イメージを実行します。

最新の SQL Server のコンテナー イメージを使用する可能性がありますいないシナリオがあります。 特定の SQL Server のコンテナー イメージを実行するには、次の手順を使用します。

1. Docker を識別する**タグ**リリースを使用します。 使用可能なタグを表示するを参照してください。 [mssql server-linux の Docker hub ページ](https://hub.docker.com/_/microsoft-mssql-server)します。

2. タグを持つ SQL Server のコンテナー イメージをプルします。 たとえば、RC1 のイメージをプルするには、次のように置換します。`<image_tag>`した次のコマンドで`rc1`します。

   ```bash
   docker pull mcr.microsoft.com/mssql/server:<image_tag>
   ```

3. をそのイメージを新しいコンテナーを実行するには、タグ名を指定します、`docker run`コマンド。 次のコマンドで置き換える`<image_tag>`バージョンを実行するとします。

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d mcr.microsoft.com/mssql/server:<image_tag>
   ```

次の手順を既存のコンテナーをダウン グレードすることもできます。 たとえば、ロールバックするまたは、トラブルシューティングやテストの実行中のコンテナーをダウン グレードする場合があります。 実行中のコンテナーにダウン グレードにはデータ フォルダーの永続化手法を使用する必要があります。 記載されている同じ手順に従って、[アップグレード セクション](#upgrade)が、新しいコンテナーを実行すると、以前のバージョンのタグ名を指定します。

## <a id="version"></a> コンテナーのバージョンを確認してください。

実行中の docker コンテナーで SQL Server のバージョンを確認するには場合、は、表示するには、次のコマンドを実行します。 置換`<Container ID or name>`はターゲット コンテナー ID または名前。 置換`<YourStrong!Passw0rd>`SA ログインの SQL Server のパスワードに置き換えます。

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

SQL Server のバージョンを識別し、ターゲットの docker コンテナー イメージのビルド番号もできます。 次のコマンドは、SQL Server バージョンおよびビルドの情報を表示、 **microsoft/server mssql-linux:2017-最新**イメージ。 これは、環境変数に新しいコンテナーの実行で**PAL_PROGRAM_INFO = 1**します。 結果のコンテナーがすぐに終了して、`docker rm`コマンドで削除します。

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

前のコマンドでは、次の出力のようなバージョン情報を表示します。

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

## <a id="upgrade"></a> コンテナー内の SQL Server をアップグレードします。

Docker でコンテナー イメージをアップグレードするには、最初のアップグレードのリリースのタグを特定します。 レジストリからのこのバージョンのプル、`docker pull`コマンド。

```bash
docker pull mcr.microsoft.com/mssql/server:<image_tag>
```

これを作成すると、すべての新しいコンテナーの SQL Server イメージを更新しますが、実行中のコンテナー内の SQL Server は更新されません。 これを行うには、最新の SQL Server のコンテナー イメージで新しいコンテナーを作成し、その新しいコンテナーにデータを移行する必要があります。

1. いずれかを使用しているかどうかを確認、[データ永続化手法](#persist)の既存の SQL Server のコンテナー。 これにより、同じデータで新しいコンテナーを開始できます。

1. SQL Server のコンテナーを停止、`docker stop`コマンド。

1. 新しい SQL Server コンテナーを作成`docker run`し、マップされたホスト ディレクトリまたはデータのボリューム コンテナーのいずれかを指定します。 SQL Server のアップグレードの特定のタグを使用してください。 新しいコンテナーは、新しいバージョンの SQL Server を使用して、既存の SQL Server データとようになりました。

   > [!IMPORTANT]
   > アップグレードは、この時点で RC1、RC2 では、GA の間のみサポートされます。

1. データベースと新しいコンテナー内のデータを確認します。

1. 必要に応じて、古いコンテナーを削除`docker rm`します。

## <a id="troubleshooting"></a> トラブルシューティング

次のセクションでは、コンテナーで SQL Server を実行するためのトラブルシューティングの方法を説明します。

### <a name="docker-command-errors"></a>Docker コマンドのエラー

いずれかのエラーが発生した場合`docker`コマンド、docker サービスが実行されていることを確認および管理者特権でのアクセス許可で実行しようとしています。

たとえば、linux では、可能性がありますエラーが発生する次の実行時に`docker`コマンド。

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

Linux で、このエラーが発生した場合で始まる同じコマンドを実行していることをお試しください`sudo`します。 失敗した場合、docker サービスが実行されていると、必要に応じて開始を確認します。

```bash
sudo systemctl status docker
sudo systemctl start docker
```

Windows では、PowerShell または管理者としてコマンド プロンプトを起動することを確認します。

### <a name="sql-server-container-startup-errors"></a>SQL Server のコンテナーの起動エラー

SQL Server のコンテナーは、実行に失敗した場合、次のテストを行います。

- など、エラーが発生した場合 **' エンドポイント CONTAINER_NAME をネットワーク ブリッジを作成できませんでした。プロキシの開始エラー: リッスン tcp 0.0.0.0:1433 バインド: 既に使用されているアドレスです '。** 、コンテナーのポート 1433 を既に使用されているポートにマップしようとしています。 これは、ホスト コンピューターのローカル SQL Server を実行している場合に発生することができます。 2 つの SQL Server のコンテナーを開始し、それら両方を同じホストのポートにマップする場合にも発生します。 この場合、使用、`-p`コンテナー ポート 1433 を別のホストのポートにマッピングするパラメーター。 例 : 

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
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu`.
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu`.
```

::: moniker-end

- コンテナーからすべてのエラー メッセージがあるかどうかを確認します。

    ```bash
    docker logs e69e056c702d
    ```

- 指定された最小メモリとディスク要件を満たしていることを確認、[の前提条件](quickstart-install-connect-docker.md#requirements)クイック スタートの記事の「します。

- 任意のコンテナー管理ソフトウェアを使用している場合は、ルートとして実行されているコンテナー プロセスがサポートしているを確認します。 ルートとして、コンテナーでは、sqlservr プロセスが実行されます。

- レビュー、 [SQL Server のセットアップとエラーのログ](#errorlogs)します。

### <a name="enable-dump-captures"></a>ダンプのキャプチャを有効にします。

コンテナー内では、SQL Server プロセスが失敗する場合で新しいコンテナーを作成する必要があります**SYS_PTRACE**を有効にします。 これには、例外のダンプ ファイルを作成するために必要なプロセスをトレースする Linux 機能が追加されます。 ダンプ ファイルは、問題のトラブルシューティングに役立つサポートで使用できます。 次の docker run コマンドでは、この機能を使用できます。

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d mcr.microsoft.com/mssql/server:2019-CTP2.4-ubuntu
```

::: moniker-end

### <a name="sql-server-connection-failures"></a>SQL Server 接続エラー

を、コンテナーで実行されている SQL Server インスタンスに接続できない場合は、次のテストを試してください。

- SQL Server のコンテナーが調べることで実行されていることを確認、**状態**の列、`docker ps -a`出力します。 使用していない場合は、`docker start <Container ID>`を開始します。

- 既定以外のホスト ポート (1433 ではない) にマップした場合、接続文字列でポートを指定することを確認します。 ポートのマッピングを確認できます、**ポート**の列、`docker ps -a`出力します。 たとえば、次のコマンドは、ポート 1401 をリッスンしてコンテナーに sqlcmd を接続します。

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- 使用した場合`docker run`既存のマップされたデータ ボリュームまたはボリューム コンテナーのデータの場合は、SQL Server の値を無視`MSSQL_SA_PASSWORD`します。 代わりに、事前構成済みの SA ユーザーのパスワードは、データ ボリュームまたはデータ ボリューム コンテナー内の SQL Server データから使用されます。 アタッチするデータに関連付けられている SA パスワードを使用していることを確認します。

- レビュー、 [SQL Server のセットアップとエラーのログ](#errorlogs)します。

### <a name="sql-server-availability-groups"></a>SQL Server 可用性グループ

Docker と SQL Server 可用性グループを使用している場合は、2 つの追加要件です。

- レプリカ (既定値は 5022) の通信に使用されるポートをマップします。 たとえば、指定`-p 5022:5022`の一部として、`docker run`コマンド。

- コンテナーのホスト名を明示的に設定、`-h YOURHOSTNAME`のパラメーター、`docker run`コマンド。 可用性グループを構成するときに、このホスト名が使用されます。 指定しない場合`-h`、既定値はコンテナーの id。

### <a id="errorlogs"></a> SQL Server のセットアップとエラー ログ

SQL Server セットアップを見ることができのエラー ログの **/var/opt/mssql/log**します。 コンテナーが実行されていない場合は、まず、コンテナーを開始します。 対話型コマンド プロンプトを使用して、ログを検査します。

```bash
docker start e69e056c702d
docker exec -it e69e056c702d "bash"
```

コンテナー内で bash セッションから、次のコマンドを実行します。

```bash
cd /var/opt/mssql/log
cat setup*.log
cat errorlog
```

> [!TIP]
> マウントするディレクトリをホストしている場合 **/var/opt/mssql**に確認できる代わりに、コンテナーを作成したときに、**ログ**ホスト上のマップされたパスのサブディレクトリ。

## <a name="next-steps"></a>次のステップ

使用する Docker で SQL Server 2017 コンテナー イメージの概要、[クイック スタート](quickstart-install-connect-docker.md)します。

またを参照してください、 [mssql docker GitHub リポジトリ](https://github.com/Microsoft/mssql-docker)リソース、フィードバック、および既知の問題。

[SQL Server のコンテナーの高可用性を調べる](sql-server-linux-container-ha-overview.md)
