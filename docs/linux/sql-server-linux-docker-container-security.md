---
title: SQL Server Docker コンテナーをセキュリティで保護する
description: SQL Server Docker コンテナーをセキュリティで保護するさまざまな方法と、ホストでルート以外の別のユーザーとしてコンテナーを実行する方法について説明します
author: vin-yu
ms.author: vinsonyu
ms.reviewer: vanto
ms.custom: contperfq1
ms.date: 09/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
moniker: '>= sql-server-linux-2017 || >= sql-server-2017 || =sqlallproducts-allversions'
ms.openlocfilehash: 10d2eb061a4ee6d9ff9c8d0594561667dd882dc9
ms.sourcegitcommit: 678f513b0c4846797ba82a3f921ac95f7a5ac863
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2020
ms.locfileid: "89511590"
---
# <a name="secure-sql-server-docker-containers"></a>SQL Server Docker コンテナーをセキュリティで保護する

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

既定で SQL Server 2017 のコンテナーは、ルート ユーザーとして起動されます。 これにより、セキュリティ上の問題が発生することがあります。 この記事では SQL Server Docker コンテナーを実行するときのセキュリティ オプションと、ルート以外のユーザーとして SQL Server コンテナーを構築する方法について説明します。

## <a name="build-and-run-non-root-sql-server-2017-containers"></a><a id="buildnonrootcontainer"></a>非ルート SQL Server 2017 コンテナーを作成して実行する

次の手順に従って、`mssql` (非ルート) ユーザーとして起動する SQL Server 2017 コンテナーを作成します。

> [!NOTE]
> SQL Server 2019 コンテナーは自動的に非ルートとして起動するため、次の手順は、既定でルートとして起動する SQL Server 2017 コンテナーにのみ適用されます。

1. [非ルート SQL Server コンテナー用のサンプル dockerfile](https://raw.githubusercontent.com/microsoft/mssql-docker/master/linux/preview/examples/mssql-server-linux-non-root/Dockerfile) をダウンロードし、`dockerfile` として保存します。

2. dockerfile ディレクトリのコンテキストで次のコマンドを実行して、非ルート SQL Server コンテナーを作成します。

    ```bash
    cd <path to dockerfile>
    docker build -t 2017-latest-non-root .
    ```

3. コンテナーを開始します。

    ```bash
    docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword@" --cap-add SYS_PTRACE --name sql1 -p 1433:1433 -d 2017-latest-non-root
    ```

    > [!NOTE]
    > 非ルート SQL Server コンテナーによってトラブルシューティング用のダンプが生成されるようにするには、`--cap-add SYS_PTRACE` フラグが必要です。

4. コンテナーが非ルート ユーザーとして実行されていることを確認します。

    ```bash
    docker exec -it sql1 bash
    ```

    `whoami` を実行します。これにより、コンテナーで実行されているユーザーが返されます。
    
    ```bash
    whoami
    ```

## <a name="run-container-as-a-different-non-root-user-on-the-host"></a><a id="nonrootuser"></a> ホスト上で別の非ルート ユーザーとしてコンテナーを実行する

SQL Server コンテナーを別の非ルート ユーザーとして実行するには、-u フラグを docker run コマンドに追加します。 非ルート コンテナーには、非ルート ユーザーがアクセスできる `/var/opt/mssql` にボリュームがマウントされていない限り、ルート グループの一部として実行される必要がある制限があります。 ルート グループから非ルート ユーザーに対して追加のルート アクセス許可は付与されません。

#### <a name="run-as-a-user-with-a-uid-4000"></a>UID 4000 を持つユーザーとして実行する

カスタム UID を使用して SQL Server を開始できます。 たとえば、次のコマンドでは UID 4000 を使用して SQL Server が開始されます。

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u 4000:0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

> [!Warning]
> SQL Server コンテナーに 'mssql' や 'root' などの名前付きユーザーが含まれていることを確認してください。そうしないと、コンテナー内で SQLCMD を実行できません。 SQL Server コンテナーが名前付きユーザーとして実行されているかどうかは、コンテナー内で `whoami` を実行することで確認できます。

#### <a name="run-the-non-root-container-as-the-root-user"></a>非ルート コンテナーをルート ユーザーとして実行する

必要に応じて、非ルート コンテナーをルート ユーザーとして実行できます。 これでは、より高いアクセス許可があるため、ファイルに対するすべてのアクセス許可もコンテナーに自動的に付与されます。

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" -u 0:0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

#### <a name="run-as-a-user-on-your-host-machine"></a>ご利用のホスト コンピューター上のユーザーとして実行する

次のコマンドを使用すれば、ホスト コンピューター上の既存のユーザーで SQL Server を開始できます。
```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u $(id -u myusername):0 -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

#### <a name="run-as-a-different-user-and-group"></a>別のユーザーおよびグループとして実行する

カスタムのユーザーおよびグループで SQL Server を開始できます。 この例では、マウントされたボリュームには、ホスト コンピューター上のユーザーまたはグループ用に構成されたアクセス許可があります。

```bash
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyStrongPassword" --cap-add SYS_PTRACE -u (id -u myusername):(id -g myusername) -v /path/to/mssql:/var/opt/mssql -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest
```

## <a name="configure-persistent-storage-permissions-for-non-root-containers"></a><a id="storagepermissions"></a> 非ルート コンテナーに対して永続的なストレージ アクセス許可を構成する

マウントされたボリューム上にあるデータベース ファイルへのアクセスを非ルート ユーザーに許可するには、コンテナーを実行するユーザーまたはグループが永続的なファイル ストレージを読み書きできるようにします。  

次のコマンドを使用すれば、データベース ファイルの現在の所有権を取得できます。

```bash
ls -ll <database file dir>
```

永続化されたデータベース ファイルへのアクセス権が SQL Server にない場合は、次のいずれかのコマンドを実行します。

#### <a name="grant-the-root-group-rw-access-to-the-db-files"></a>DB ファイルへの R/W アクセス権をルート グループに付与する

非ルート SQL Server コンテナーがデータベース ファイルにアクセスできるように、次のディレクトリへのアクセス許可をルート グループに付与します。

```bash
chgrp -R 0 <database file dir>
chmod -R g=u <database file dir>
```

#### <a name="set-the-non-root-user-as-the-owner-of-the-files"></a>非ルート ユーザーをファイルの所有者として設定する

これは、既定の非ルート ユーザーとすることも、その他の任意の非ルート ユーザーを指定することもできます。 この例では、UID 10001 を非ルート ユーザーとして設定します。

```bash
chown -R 10001:0 <database file dir>
```

## <a name="next-steps"></a>次のステップ

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

- [クイックスタート](quickstart-install-connect-docker.md?view=sql-server-2017)に従って、Docker 上で SQL Server 2017 のコンテナー イメージを開始する

::: moniker-end

<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

- [クイックスタート](quickstart-install-connect-docker.md?view=sql-server-ver15)に従って、Docker 上で SQL Server 2019 のコンテナー イメージを開始する

::: moniker-end

- [SQL Server Docker コンテナーをデプロイして接続する](sql-server-linux-docker-container-deployment.md)

- [Docker コンテナーに追加できる構成とカスタマイズを確認する](sql-server-linux-docker-container-configure.md)

- [SQL Server Docker コンテナーのトラブルシューティング](sql-server-linux-docker-container-troubleshooting.md)