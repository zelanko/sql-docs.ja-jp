---
title: SQL Server Machine Learning サービスをコンテナーの実行 |Microsoft Docs
description: このチュートリアルでは、Docker で実行される Linux コンテナーで SQL Server Machine Learning Services を使用する方法を示します。
author: uc-msft
ms.author: umajay
manager: craigg
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.collection: linux-container
moniker: '>= sql-server-linux-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: 3e654e29d6c49d3bf68cdfe7c4e3b479b47a973c
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67840471"
---
# <a name="run-sql-server-machine-learning-services-in-a-container"></a>SQL Server Machine Learning サービスをコンテナーの実行します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このチュートリアルでは、SQL Server Machine Learning Services での Docker コンテナーを構築し、TRANSACT-SQL から Machine Learning スクリプトを実行する方法について説明します。

> [!div class="checklist"]
> * Mssql docker リポジトリを複製します。
> * Machine Learning サービスでの SQL Server Linux コンテナー イメージをビルドします。
> * Machine Learning サービスでは、SQL Server Linux コンテナー イメージを実行します。
> * TRANSACT-SQL ステートメントを使用して、R または Python のスクリプトを実行します。
> * 停止し、SQL Server Linux コンテナーを削除します。 

## <a name="prerequisites"></a>必須コンポーネント

* Git コマンド ライン インターフェイス。
* サポートされている任意の Linux ディストリビューションの Docker エンジン 1.8 + または Docker for Mac/Windows。 詳細については「[Install Docker](https://docs.docker.com/engine/installation/)」(Docker のインストール) を参照してください。
* 2 GB のディスク領域の最小値。
* 2 GB の RAM の最小値。
* [SQL Server on Linux のシステム要件](sql-server-linux-setup.md#system)。

## <a name="clone-the-mssql-docker-repository"></a>Mssql docker リポジトリを複製します。

1. Windows 上の Linux または Mac または WSL ターミナルでバッシュ ターミナルを開きます。

1. Mssql docker リポジトリのコピーをローカルに保持するためにローカル ディレクトリを作成します。
1. Mssql docker リポジトリを複製する git clone コマンドを実行します。

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-sql-server-linux-container-image-with-machine-learning-services"></a>Machine Learning サービスでの SQL Server Linux コンテナー イメージをビルドします。

1. Mssql mlservices ディレクトリにディレクトリを変更します。

    ```bash
    cd mssql-docker/linux/preview/examples/mssql-mlservices
    ```

1. Build.sh スクリプトを実行します。

   ```bash
   ./build.sh
   ```

   > [!NOTE]
   > Docker イメージを構築するには、数 Gb のサイズであるパッケージをインストールする必要があります。 スクリプトは、ネットワーク帯域幅によっては完了までに最大 20 分かかります。

## <a name="run-sql-server-linux-container-image-with-machine-learning-services"></a>Machine Learning サービスで SQL Server Linux コンテナー イメージを実行します。

1. コンテナーを実行する前に環境変数を設定します。 ホスト ディレクトリに PATH_TO_MSSQL 環境変数を設定します。

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

   このコマンドは、Developer edition (既定値)、Machine Learning サービスと SQL Server のコンテナーを作成します。 SQL Server ポート**1433**ポートとホスト上で公開される**1401**します。

   > [!NOTE]
   > コンテナーで実稼働 SQL Server のエディションを実行するためのプロセスは若干異なります。 詳細については 「[実稼働環境のコンテナー イメージを実行する](sql-server-linux-configure-docker.md#production)」を参照してください。 同じコンテナー名とポートを使用する場合、このチュートリアルの残りの部分は、実稼働のコンテナーで引き続き動作します。

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

## <a name="execute-r--python-scripts-from-transact-sql"></a>R を実行する TRANSACT-SQL からの Python スクリプト/

1. コンテナー内の SQL Server に接続し、次の T-SQL ステートメントを実行して外部スクリプトの構成オプションを有効にします。

    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    go
    ```

1. Machine Learning サービスが次の単純な R および Python sp_execute_external_script を実行して動作を確認します。

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

このチュートリアルでは、次のことについて学習しました。

> [!div class="checklist"]
> * Mssql docker リポジトリを複製します。
> * Machine Learning サービスでの SQL Server Linux コンテナー イメージをビルドします。
> * Machine Learning サービスでは、SQL Server Linux コンテナー イメージを実行します。
> * TRANSACT-SQL ステートメントを使用して、R または Python のスクリプトを実行します。
> * 停止し、SQL Server Linux コンテナーを削除します。

次に、その他の Docker の構成とトラブルシューティングのシナリオを確認します。

> [!div class="nextstepaction"]
>[Docker 上の SQL Server の構成ガイド](sql-server-linux-configure-docker.md)
