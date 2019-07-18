---
title: コンテナーで SQL Server Machine Learning Services を実行する |Microsoft Docs
description: このチュートリアルでは、Docker で実行されている Linux コンテナーで SQL Server Machine Learning Services を使用する方法について説明します。
author: uc-msft
ms.author: umajay
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.collection: linux-container
moniker: '>= sql-server-linux-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: f3d3774adf4bee07269b25c3359b031ca24eb99e
ms.sourcegitcommit: ef7834ed0f38c1712f45737018a0bfe892e894ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2019
ms.locfileid: "68300423"
---
# <a name="run-sql-server-machine-learning-services-in-a-container"></a>コンテナーで SQL Server Machine Learning Services を実行する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このチュートリアルでは、SQL Server Machine Learning Services を使用して Docker コンテナーを構築し、Transact-sql から Machine Learning スクリプトを実行する方法について説明します。

> [!div class="checklist"]
> * Mssql-docker リポジトリを複製します。
> * Machine Learning Services を使用して SQL Server Linux コンテナーイメージをビルドします。
> * Machine Learning Services を使用して SQL Server Linux コンテナーイメージを実行します。
> * Transact-sql ステートメントを使用して R または Python スクリプトを実行します。
> * SQL Server Linux コンテナーを停止して削除します。 

## <a name="prerequisites"></a>必須コンポーネント

* Git コマンドラインインターフェイス。
* サポートされている任意の Linux ディストリビューションの Docker エンジン 1.8 + または Docker for Mac/Windows。 詳細については「[Install Docker](https://docs.docker.com/engine/installation/)」(Docker のインストール) を参照してください。
* 2 GB 以上のディスク領域。
* 2 GB 以上の RAM。
* [SQL Server on Linux のシステム要件](sql-server-linux-setup.md#system)。

## <a name="clone-the-mssql-docker-repository"></a>Mssql-docker リポジトリを複製する

1. Linux/Mac または Windows 上の WSL ターミナルで bash ターミナルを開きます。

1. Mssql-docker リポジトリのコピーをローカルに保持するローカルディレクトリを作成します。
1. Git clone コマンドを実行して、mssql-docker リポジトリを複製します。

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-sql-server-linux-container-image-with-machine-learning-services"></a>Machine Learning Services を使用して Linux コンテナーイメージをビルド SQL Server

1. Mssql-mlservices ディレクトリにディレクトリを変更します。

    ```bash
    cd mssql-docker/linux/preview/examples/mssql-mlservices
    ```

1. Build.sh スクリプトを実行します。

   ```bash
   ./build.sh
   ```

   > [!NOTE]
   > Docker イメージをビルドするには、サイズが数 Gb のパッケージをインストールする必要があります。 このスクリプトは、ネットワーク帯域幅によっては、完了までに最大20分かかる場合があります。

## <a name="run-sql-server-linux-container-image-with-machine-learning-services"></a>Machine Learning Services を使用して SQL Server Linux コンテナーイメージを実行する

1. コンテナーを実行する前に環境変数を設定します。 PATH_TO_MSSQL 環境変数をホストディレクトリに設定します。

   ```bash
    export MSSQL_PID='Developer'
    export ACCEPT_EULA='Y'
    export ACCEPT_EULA_ML='Y'
    export PATH_TO_MSSQL='/home/mssql/'
   ```

1. Run.sh スクリプトを実行します。

   ```bash
   ./run.sh
   ```

   このコマンドは、Developer edition (既定) を使用して Machine Learning Services を持つ SQL Server コンテナーを作成します。 SQL Server ポート**1433**は、ポート**1401**としてホスト上で公開されます。

   > [!NOTE]
   > コンテナーで運用 SQL Server エディションを実行するためのプロセスは若干異なります。 詳細については、「 [Docker で SQL Server コンテナーイメージを構成する](sql-server-linux-configure-docker.md)」を参照してください。 同じコンテナー名とポートを使用する場合でも、このチュートリアルの残りの部分では実稼働コンテナーを使用します。

1. Docker コンテナーを表示するには、 `docker ps` コマンドを使用します。

   ```bash
   sudo docker ps -a
   ```

1. **[STATUS]** 列に **[Up]** の状態が表示されている場合、SQL Server はコンテナーで実行されており、 **[PORTS]** 列に指定されたポートでリッスンしています。 SQL Server コンテナーの **[STATUS]** 列に **[Exited]** と表示されている場合は、[構成ガイドのトラブルシューティングのセクション](sql-server-linux-configure-docker.md#troubleshooting)を参照してください。

   ```bash
   $ sudo docker ps -a
   ```

    Output: 
    
    ```
    CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
    941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour     0.0.0.0:1401->1433/tcp   sql1
    ```

## <a name="change-the-sa-password"></a>SA パスワードを変更する

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="execute-r--python-scripts-from-transact-sql"></a>Transact-sql からの R/Python スクリプトの実行

1. 次の T-sql ステートメントを実行して、コンテナー内の SQL Server に接続し、external script 構成オプションを有効にします。

    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    go
    ```

1. 次の単純な R/Python sp_execute_external_script を実行して Machine Learning Services が機能していることを確認します。

    ```sql
    execute sp_execute_external_script 
    @language = N'R',
    @script = N'
    print("Hello World!")
    print(R.version)
    print(Revo.version)
    OutputDataSet <- InputDataSet', 
    @input_data_1 = N'select 1'
    with result sets((i int));
    go
    ```

    ```sql
    execute sp_execute_external_script 
    @language = N'Python',
    @script = N'
    import sys
    print(sys.version)
    print("Hello World!")
    OutputDataSet = InputDataSet',
    @input_data_1 = N'select 1'
    with result sets((i int));
    go 
    ```

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の操作を実行する方法を学習しました。

> [!div class="checklist"]
> * Mssql-docker リポジトリを複製します。
> * Machine Learning Services を使用して SQL Server Linux コンテナーイメージをビルドします。
> * Machine Learning Services を使用して SQL Server Linux コンテナーイメージを実行します。
> * Transact-sql ステートメントを使用して R または Python スクリプトを実行します。
> * SQL Server Linux コンテナーを停止して削除します。

次に、その他の Docker の構成とトラブルシューティングのシナリオを確認します。

> [!div class="nextstepaction"]
>[Docker での SQL Server の構成ガイド](sql-server-linux-configure-docker.md)
