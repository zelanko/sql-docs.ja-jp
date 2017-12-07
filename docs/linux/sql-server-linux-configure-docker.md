---
title: "Docker では、SQL Server 2017 の構成オプション |Microsoft ドキュメント"
description: "使用して、Docker でコンテナー イメージの SQL Server 2017 やり取りのさまざまな方法について説明します。 これには、データ永続化ファイルのコピー、トラブルシューティングにはが含まれます。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.technology: database-engine
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.custom: 
ms.workload: On Demand
ms.openlocfilehash: 3a29c6580a4163bd69d2bb2ee1d037afc04f8108
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="configure-sql-server-2017-container-images-on-docker"></a>Docker でコンテナー イメージの SQL Server 2017 を構成します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

構成および使用する方法を説明する、 [mssql サーバー linux コンテナー イメージ](https://hub.docker.com/r/microsoft/mssql-server-linux/)docker です。 このイメージは、Ubuntu 16.04 に基づいて Linux で実行されている SQL Server で構成されます。 Mac/Windows 用の Docker エンジン 1.8 + Linux または Docker を使用できます。

> [!NOTE]
> このトピックは、mssql サーバー linux イメージを使用して上に特に注目します。 Windows イメージが含まれていないが、詳細情報を入手するには上、 [mssql server windows Docker Hub ページ](https://hub.docker.com/r/microsoft/mssql-server-windows/)です。

## <a name="pull-and-run-the-container-image"></a>プルし、コンテナー イメージを実行

プルし、SQL Server 2017 の Docker コンテナー イメージを実行するには、次のクイック スタート チュートリアルの前提条件と手順に従ってください。

- [Docker を使用した SQL Server 2017 コンテナー イメージを実行します。](quickstart-install-connect-docker.md)

この構成のトピックでは、以下のセクションに追加の使用シナリオを示します。

## <a id="production"></a>実稼働環境にコンテナー イメージを実行します。

前のセクションでのクイック スタート チュートリアルでは、Docker Hub から SQL Server の無償の Developer エディションを実行します。 情報の大部分は、Enterprise、Standard、または Web edition などのコンテナー イメージの運用を実行する場合にも適用されます。 ただし、ここで説明されている、いくつかの違いがあります。

- のみ、有効なライセンスがある場合、SQL Server を実稼働環境で使用できます。 無料の SQL Server Express の運用環境ライセンスを取得する[ここ](https://go.microsoft.com/fwlink/?linkid=857693)です。 を通じて使用可能な SQL Server Standard および Enterprise Edition のライセンス[Microsoft ボリューム ライセンス](https://www.microsoft.com/Licensing/licensing-programs/licensing-programs.aspx)です。

- 実稼働 SQL Server のコンテナー イメージをプルする必要があります[Docker ストア](https://store.docker.com)です。 1 つをいない場合は、Docker ストアでアカウントを作成します。

- 実稼働エディションもを実行する、Docker のストアに開発者のコンテナーのイメージを構成できます。 実稼働のエディションを実行するのにには、次の手順を使用します。

   1. 最初に、ログイン、docker id に、コマンドラインからします。

      ```bash
      docker login
      ```

   1. 次に、無料の開発者用 Docker ストアにコンテナーのイメージを取得する必要があります。 移動して[https://store.docker.com/images/mssql-server-linux](https://store.docker.com/images/mssql-server-linux)をクリックして**チェック アウトを続行**、し、指示に従います。

   1. プロシージャを実行し、要件を確認、[クイック スタート チュートリアル](quickstart-install-connect-docker.md)です。 2 つの違いがあります。 イメージをプルする必要があります**ストアまたは microsoft/mssql-サーバー-linux:\<タグ名\>** Docker ストアからです。 実稼働のエディションを指定する必要がありますと、 **MSSQL_PID**環境変数。 次の例では、Enterprise Edition 用の最新の SQL Server 2017 コンテナー イメージを実行する方法を示します。

      ```bash
      docker run --name sqlenterprise \
         -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=<YourStrong!Passw0rd>' \
         -e 'MSSQL_PID=Enterprise' -p 1433:1433 \
         -d store/microsoft/mssql-server-linux:2017-latest
      ```

      ```PowerShell
      docker run --name sqlenterprise `
         -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" `
         -e "MSSQL_PID=Enterprise" -p 1433:1433 `
         -d "store/microsoft/mssql-server-linux:2017-latest"
      ```

      > [!IMPORTANT]
      > 値を渡すことによって**Y**環境変数に**ACCEPT_EULA**にエディションの値と**MSSQL_PID**、有効であり、既存のライセンスがあるかを表す、エディションと使用する SQL Server のバージョン。 Docker コンテナーのイメージで実行されている SQL Server ソフトウェアの使用を SQL Server ライセンスの条項が適用されることにも同意します。

      > [!NOTE]
      > 可能な値の完全な一覧については**MSSQL_PID**を参照してください[Linux 上の環境変数と SQL Server の構成設定](sql-server-linux-configure-environment-variables.md)です。

## <a name="connect-and-query"></a>接続し、クエリ

接続でき、クエリからコンテナー外であるか、または内からコンテナー内の SQL Server のコンテナーです。 次のセクションでは、両方のシナリオについて説明します。 

### <a name="tools-outside-the-container"></a>コンテナーの外部ツール

どの外部 Linux、Windows、または macOS ツールから SQL 接続をサポートする Docker コンピューターに SQL Server インスタンスに接続できます。 いくつかの一般的なツールは次のとおりです。

- [sqlcmd](sql-server-linux-setup-tools.md)
- [Visual Studio Code](sql-server-linux-develop-use-vscode.md)
- [Windows で SQL Server Management Studio (SSMS)](sql-server-linux-develop-use-ssms.md)

次の例で**sqlcmd** Docker コンテナーで実行されている SQL Server に接続します。 接続文字列で IP アドレスは、コンテナーが実行されているホスト コンピューターの IP アドレスです。

```bash
sqlcmd -S 10.3.2.4 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4 -U SA -P "<YourPassword>"
```

既定値でなかったホスト ポートをマップしたかどうか**1433**、接続文字列にそのポートを追加します。 たとえば、指定した`-p 1400:1433`で、`docker run`コマンドを使用し、明示的に接続して 1400 のポートを指定します。

```bash
sqlcmd -S 10.3.2.4,1400 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1400 -U SA -P "<YourPassword>"
```

### <a name="tools-inside-the-container"></a>コンテナー内のツール

SQL Server 2017 CTP 2.0 以降で、 [SQL Server コマンド ライン ツール](sql-server-linux-setup-tools.md)コンテナー イメージに含まれています。 対話型のコマンド プロンプトで、イメージをアタッチする場合は、ツールをローカルで実行することができます。

1. 使用して、`docker exec -it`実行中のコンテナー内の対話型 bash シェルを起動するコマンド。 次の例で`e69e056c702d`コンテナー ID です。

    ```bash
    docker exec -it e69e056c702d "bash"
    ```

    > [!TIP]
    > 常にコンテナー全体の id を指定する必要はありません。だけ、一意に識別するための十分な文字を指定する必要があるとします。 この例で使用するのに十分なする可能性があります`e6`または`e69`完全 id ではなくです。

2. 1 回、コンテナー内の接続ローカル sqlcmd でします。 その sqlcmd がパスにない、既定では、完全なパスを指定する必要があるので注意してください。

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
    ```

3. 終了したら、sqlcmd で、入力`exit`です。

4. 終了したら、対話型のコマンド プロンプトで、入力`exit`です。 コンテナーは、対話型 bash シェルを終了した後に実行を続けます。

## <a name="run-multiple-sql-server-containers"></a>複数の SQL Server のコンテナーを実行します。

Docker は、同じホスト マシンで複数の SQL Server のコンテナーを実行する方法を提供します。 これは、同じホスト上の SQL Server の複数のインスタンスを必要とするシナリオのアプローチです。 各コンテナーは、別のポートで自体を公開する必要があります。

次の例は、次の 2 つの SQL Server のコンテナーを作成し、ポートにマッピング**1401**と**1402**ホスト コンピューターにします。

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d microsoft/mssql-server-linux:2017-latest
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1402:1433 -d microsoft/mssql-server-linux:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d microsoft/mssql-server-linux:2017-latest
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1402:1433 -d microsoft/mssql-server-linux:2017-latest
```

個別のコンテナーで実行されている SQL Server の 2 つのインスタンスがあるようになりました。 クライアントは、コンテナーの Docker ホストとポート番号の IP アドレスを使用して、各 SQL Server インスタンスに接続できます。

```bash
sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
sqlcmd -S 10.3.2.4,1402 -U SA -P '<YourPassword>'
```

```PowerShell
sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
sqlcmd -S 10.3.2.4,1402 -U SA -P "<YourPassword>"
```

## <a id="persist"></a>データを永続化します。

SQL Server 構成の変更とデータベース ファイルに保存されているコンテナーとコンテナーを再起動する場合でも`docker stop`と`docker start`です。 ただしのコンテナーを削除する場合`docker rm`コンテナー内のすべてが削除された、SQL Server や、データベースなどです。 次のセクションを使用する方法について説明**データ ボリューム**に関連付けられているコンテナーが削除された場合でも、データベース ファイルを保持します。

> [!IMPORTANT]
> SQL Server の Docker でのデータの永続性を理解することが重要です。 このセクションの詳細については、に加えて Docker のドキュメントを参照して[Docker コンテナー内のデータを管理する方法](https://docs.docker.com/engine/tutorials/dockervolumes/)です。

### <a name="mount-a-host-directory-as-data-volume"></a>データ ボリュームとホストのディレクトリをマウントします。

最初のオプションは、コンテナー内のデータ ボリュームとしては、ホスト上のディレクトリをマウントすることです。 実行するには、使用、`docker run`コマンドと、`-v <host directory>:/var/opt/mssql`フラグ。 これにより、コンテナーの実行間で復元するデータ。

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

この手法では、共有し、Docker の外部でホスト上のファイルを表示することもできます。

> [!IMPORTANT]
> この時点では、Linux イメージ上の SQL Server で、Mac 上の Docker のホスト ボリュームのマッピングはサポートされていません。 代わりにデータ ボリューム コンテナーを使用します。 この制限に固有の`/var/opt/mssql`ディレクトリ。 マウントされたディレクトリが正しく動作からの読み取り。 たとえば、– v を使用して、Mac のホストのディレクトリをマウントでき、ホスト上にある .bak ファイルからバックアップを復元できます。

### <a name="use-data-volume-containers"></a>データ ボリューム コンテナーを使用してください。

2 番目のオプションでは、データのボリューム コンテナーを使用します。 データ ボリューム コンテナーを作成するにはホスト ディレクトリではなく、ボリューム名を指定することによって、`-v`パラメーター。 次の例では、という名前の共有データ ボリューム**sqlvolume**です。

```bash
docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v sqlvolume:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

```PowerShell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1433:1433 -v sqlvolume:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
```

> [!NOTE]
> Run コマンドでデータ ボリュームを暗黙的に作成するためには、この手法は、Docker の古いバージョンでは機能しません。 その場合は、Docker のドキュメントに記載されている明示的な手順を使用して[の作成とデータ ボリューム コンテナーをマウント](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container)です。

停止して、このコンテナーを削除した場合でも、データ ボリュームを維持します。 表示できます、`docker volume ls`コマンド。

```bash
docker volume ls
```

同じボリュームの名前を持つし、別のコンテナーを作成する場合、新しいコンテナーは、ボリュームに格納されている同じ SQL Server のデータを使用します。

削除するには、データ ボリューム コンテナーを使用して、`docker volume rm`コマンド。

> [!WARNING]
> データ ボリューム コンテナーを削除すると、コンテナー内の任意の SQL Server データが*完全*削除します。

### <a name="backup-and-restore"></a>バックアップと復元

これらのコンテナー手法に加えても標準の SQL Server のバックアップを使用し、手法を復元できます。 データを保護するか、別の SQL Server インスタンスにデータを移動する、バックアップ ファイルを使用できます。 詳細については、次を参照してください。 [Linux に SQL Server がデータベースのバックアップと復元](sql-server-linux-backup-and-restore-database.md)です。

> [!WARNING]
> バックアップを作成する場合は、作成またはコンテナーの外部でのバックアップ ファイルをコピーすることを確認してください。 それ以外の場合、コンテナーが削除された場合、バックアップ ファイルも削除されます。

## <a name="execute-commands-in-a-container"></a>コンテナー内のコマンドを実行します。

実行中のコンテナーを使っている場合は、ターミナル ホストからコンテナー内のコマンドを実行できます。

実行するコンテナーの ID を取得します。

```bash
docker ps
```

コンテナーの実行でターミナル バッシュを開始するには。

```bash
docker exec -ti <Container ID> /bin/bash
```

今すぐ端末、コンテナー内で実行しているかのように、コマンドを実行できます。 終了したら、入力`exit`です。 対話型コマンド セッションで、これが終了したが、コンテナーが実行し続けます。

## <a name="copy-files-from-a-container"></a>コンテナーからファイルをコピー

コンテナからファイルをコピーするには、次のコマンドを使用します。

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

## <a name="run-a-specific-sql-server-container-image"></a>特定の SQL Server のコンテナー イメージを実行します。

ここでたくない最新の SQL Server のコンテナー イメージを使用するシナリオがあります。 特定の SQL Server のコンテナー イメージを実行するには、次の手順を使用します。

1. Docker を識別**タグ**を使用するリリースします。 使用できるタグを表示するを参照してください。 [mssql サーバー linux Docker ハブ ページ](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/)です。

1. タグを持つ SQL Server のコンテナー イメージをプルします。 たとえば、RC1 のイメージをプルする次のように置換します。`<image_tag>`で次のコマンドで`rc1`です。

   ```bash
   docker pull microsoft/mssql-server-linux:<image_tag>
   ```

1. をそのイメージを新しいコンテナーを実行するには、でタグの名前を指定、`docker run`コマンド。 次のコマンドで置き換える`<image_tag>`バージョンを実行するとします。

   ```bash
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
   ```

次の手順は、既存のコンテナーをダウン グレードにも使用できます。 たとえばにロールバックします。 またはトラブルシューティングやテストの実行中のコンテナーをダウン グレードする可能性があります。 実行中のコンテナーをダウン グレードには、データ フォルダーの永続化手法を使用する必要があります。 同じ手順で説明されている、[アップグレード セクション](#upgrade)が、新しいコンテナーを実行すると、古いバージョンのタグ名を指定します。

> [!IMPORTANT]
> アップグレードおよびダウン グレードは、この時点で RC1 と RC2 の間でのみサポートされます。

## <a id="upgrade"></a>コンテナー内の SQL Server をアップグレードします。

Docker でコンテナー イメージをアップグレードするには、まず、リリース アップグレードのためのタグを特定します。 このバージョンを使用してレジストリからプル、`docker pull`コマンド。

```bash
docker pull microsoft/mssql-server-linux:<image_tag>
```

これにより、SQL Server イメージを作成すると、任意の新しいコンテナーの更新しますが、実行中のすべてのコンテナー内の SQL Server は更新されません。 これを行うには、最新の SQL Server のコンテナー イメージを使用新しいコンテナーを作成し、その新しいコンテナーにデータを移行する必要があります。

1. いずれかを使用しているかどうかを確認、[データ永続化手法](#persist)既存の SQL Server のコンテナーにします。 これにより、同じデータで新しいコンテナーを開始できます。

1. SQL Server のコンテナーを停止、`docker stop`コマンド。

1. 新しい SQL Server コンテナーを作成する`docker run`し、マッピングされたホスト ディレクトリまたはデータのボリューム コンテナーのいずれかを指定します。 特定のタグを使用するように、SQL Server のアップグレード。 新しいコンテナーは、今すぐ、既存の SQL Server データを新しいバージョンの SQL Server を使用します。

   > [!IMPORTANT]
   > アップグレードは、この時点で RC1、RC2 では、GA 間でのみサポートされます。

1. データベースと新しいコンテナー内のデータを確認します。

1. 必要に応じて、削除でコンテナーを古い`docker rm`です。

## <a id="troubleshooting"></a>トラブルシューティング

次のセクションでは、SQL Server のコンテナーの実行のトラブルシューティング方法を提供します。

### <a name="docker-command-errors"></a>Docker コマンドのエラー

いずれかのエラーが発生する場合`docker`コマンド、docker サービスが実行されていることを確認してくださいおよび高度な権限で実行してみてください。

たとえば、Linux では、可能性がありますエラーが発生する次の実行時に`docker`コマンド。

```
Cannot connect to the Docker daemon. Is the docker daemon running on this host?
```

Linux にこのエラーを発生する場合で始まる同じコマンドを実行してください。`sudo`です。 失敗した場合は、docker サービスが実行されていると、必要に応じて開始を確認します。

```bash
sudo systemctl status docker
sudo systemctl start docker
```

Windows では、PowerShell、または、管理者としてコマンド プロンプトを起動することを確認します。

### <a name="sql-server-container-startup-errors"></a>SQL Server のコンテナーの起動エラー

実行する、SQL Server のコンテナーが失敗した場合は、次のテストを試してください。

- など、エラーが発生した場合**' をネットワーク ブリッジ エンドポイント CONTAINER_NAME を作成できませんでした。プロキシを開始中にエラー: リッスン tcp 0.0.0.0:1433 バインド: 既に使用されているアドレスです '。**、コンテナーのポート 1433 を既に使用されているポートにマップしようとしています。 これは、ホスト コンピューターに SQL Server をローカルで実行している場合に発生することができます。 また、2 つの SQL Server のコンテナーを開始して、これらの両方を同じホスト ポートにマップしようとした場合も発生することができます。 この場合を使用して、`-p`コンテナー ポート 1433 を別のホストのポートにマップするパラメーターです。 例: 

    ```bash
    docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1400:1433 -d microsoft/mssql-server-linux:2017-latest`.
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1400:1433 -d microsoft/mssql-server-linux:2017-latest`.
    ```

- コンテナーからのエラー メッセージがあるかどうかを確認します。

    ```bash
    docker logs e69e056c702d
    ```

- 指定された最小メモリとディスク要件を満たしていることを確認、[要件](#requirements)このトピックの「します。

- コンテナーの管理ソフトウェアを使用している場合は、ルートとして実行されているコンテナー プロセスをサポートしていることを確認します。 ルートとして、コンテナーに sqlservr プロセスが実行されます。

- 確認、 [SQL Server のセットアップとエラーのログ](#errorlogs)です。

### <a name="enable-dump-captures"></a>ダンプのキャプチャを有効にします。

コンテナー内には、SQL Server プロセスが失敗する場合で新しいコンテナーを作成する必要があります**SYS_PTRACE**有効にします。 例外のダンプ ファイルを作成するために必要なプロセスをトレースする Linux 機能が追加されます。 ダンプ ファイルは、問題のトラブルシューティングに役立つサポートで使用できます。 次の docker run コマンドでは、この機能が有効にします。

```bash
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" --cap-add SYS_PTRACE -p 1401:1433 -d microsoft/mssql-server-linux:2017-latest
```

### <a name="sql-server-connection-failures"></a>SQL Server 接続エラー

コンテナーで実行されている SQL Server インスタンスに接続することはできない場合、は、次のテストを実行します。

- 調べることで、SQL Server のコンテナーが実行されていることを確認してください、**ステータス**の列、`docker ps -a`出力します。 使用していない場合は、`docker start <Container ID>`を開始します。

- 既定ではないホスト ポート (1433 ではない) にマップした場合、接続文字列でポートを指定することを確認します。 ポート マッピングを表示できます、**ポート**の列、`docker ps -a`出力します。 たとえば、次のコマンドは、1401 のポートでリッスンしているコンテナーに sqlcmd を接続します。

    ```bash
    sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
    ```

    ```PowerShell
    sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
    ```

- 使用した場合`docker run`の値を無視している SQL Server で、既存のマップされたデータ量やデータのボリューム コンテナーで`MSSQL_SA_PASSWORD`です。 代わりに、構成済みの SA ユーザー パスワードは、データ ボリューム、またはデータのボリューム コンテナー内の SQL Server データから使用されます。 アタッチしているデータに関連付けられている SA パスワードを使用していることを確認します。

- 確認、 [SQL Server のセットアップとエラーのログ](#errorlogs)です。

### <a name="sql-server-availability-groups"></a>SQL Server 可用性グループ

Docker と SQL Server 可用性グループを使用している場合は、次の 2 つの追加要件があります。

- レプリカ (既定値は 5022) の通信に使用されるポートをマップします。 たとえば、指定`-p 5022:5022`の一部として、`docker run`コマンド。

- コンテナーのホスト名を明示的に設定、`-h YOURHOSTNAME`のパラメーター、`docker run`コマンド。 このホスト名は、可用性グループを構成するときに使用されます。 指定しない場合は`-h`、既定値は、コンテナーの id です。

### <a id="errorlogs"></a>SQL Server のセットアップとエラーのログ

SQL Server セットアップを確認できのエラー ログの**/var/opt/mssql/log**です。 コンテナーが実行されていない場合は、まず、コンテナーを開始します。 対話型のコマンド プロンプトを使用して、ログを検査します。

```bash
docker start e69e056c702d
docker exec -it e69e056c702d "bash"
```

バッシュ セッション、コンテナー内から次のコマンドを実行します。

```bash
cd /var/opt/mssql/log
cat setup*.log
cat errorlog
```

> [!TIP]
> ホストのディレクトリをマウントした場合**/var/opt/mssql**に確認できる代わりに、コンテナーを作成したときに、**ログ**ホスト上のマップされたパスのサブディレクトリ。

## <a name="next-steps"></a>次の手順

経由して Docker でコンテナー イメージの SQL Server 2017 の概要、[クイック スタート チュートリアル](quickstart-install-connect-docker.md)です。

またを参照してください、 [mssql docker GitHub リポジトリ](https://github.com/Microsoft/mssql-docker)リソース、フィードバック、および既知の問題です。
