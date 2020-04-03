---
title: Docker にインストールする
titleSuffix: SQL Server Machine Learning Services
description: Docker に SQL Server Machine Learning Services (Python と R) をインストールする方法を説明します。
author: cawrites
ms.author: chadam
ms.reviewer: davidph
manager: cgronlun
ms.date: 03/23/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e5a53419aba5515a9a60817ec0cc2a9de5a648d2
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2020
ms.locfileid: "80228343"
---
# <a name="install-sql-server-machine-learning-services-python-and-r-on-docker"></a>Docker に SQL Server Machine Learning Services (Python と R) をインストールする

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Docker に SQL Server Machine Learning Services をインストールする方法について説明します。 Machine Learning Services を使用して、データベース内で Python または R スクリプトを実行できます。 Machine Learning Services には、事前に構築されたコンテナーは用意されていません。 [GitHub で入手できるテンプレートの例](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices)使用して、SQL Server コンテナーから作成できます。

## <a name="prerequisites"></a>前提条件

- Git のコマンド ライン インターフェイス。

- サポートされているいずれかの Linux ディストリビューションの Docker エンジン 1.8 以降 または Mac/Windows 用 Docker。 詳細については、「[Get Docker](https://docs.docker.com/get-docker/)」を参照してください。

- 「[SQL Server on Linux のシステム要件](sql-server-linux-setup.md#system)」も参照してください。

## <a name="clone-the-mssql-docker-repository"></a>mssql-docker リポジトリをクローンする

次のコマンドによって `mssql-docker` git リポジトリがローカル ディレクトリにクローンされます。

1. Linux または Mac で Bash ターミナルを開くか、または Windows で Linux 用 Windows サブシステム ターミナルを開きます。

2. mssql-docker リポジトリのローカル コピーを保持するディレクトリを作成します。

3. git clone コマンドを実行して、mssql-docker リポジトリを複製します。

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-a-sql-server-linux-container-image"></a>SQL Server の Linux コンテナー イメージをビルドする

次の手順で Docker イメージをビルドします。

1. ディレクトリを mssql-mlservices ディレクトリに変更します。

2. 同じディレクトリで、次のコマンドを実行します。

    ```bash
    docker builds -t mssql-server-mlservices
    ```

3. 次のコマンドを実行します。

    ```bash
    docker runs -d -e MSSQL_PID=Developer -e ACCEPT_EULA=Y -e ACCEPT_EULA_ML=Y -e SA_PASSWORD=<your_sa_password> -v OS>:/var/opt/mssql -p 1433:1433 mssql-server-mlservices
    ```

    `SA_PASSWORD=<your_sa_password>` で `<your_sa_password>` を変更し、`-v` パスを変更します。 

4. 次のコマンドを実行して確認します。

    ```bash
    docker ps -a
    ```

   > [!NOTE]
   > Docker イメージをビルドするには、サイズが数 GB のパッケージをいくつかインストールする必要があります。 このスクリプトは、ネットワークの帯域幅によっては完了までに時間がかかることがあります。

## <a name="run-the-sql-server-linux-container-image"></a>SQL Server Linux コンテナー イメージを実行する

1. コンテナーを実行する前に環境変数を設定します。 PATH_TO_MSSQL 環境変数をホスト ディレクトリに設定します。

   ```bash
   export MSSQL_PID='Developer'
   export ACCEPT_EULA='Y'
   export ACCEPT_EULA_ML='Y'
   export PATH_TO_MSSQL='/home/mssql/'
   ```

2. run.sh スクリプトを実行します。

   ```bash
   ./run.sh
   ```

   このコマンドでは、Developer エディション (既定) を使用して、Machine Learning Services を含む SQL Server コンテナーが作成されます。 SQL Server のポート **1433** は、ホスト上ではポート **1401** として公開されています。

   > [!NOTE]
   > SQL Server の実稼働エディションをコンテナーで実行するプロセスは、若干異なります。 詳細については、「[Docker で SQL Server コンテナーイメージを構成する](sql-server-linux-configure-docker.md)」を参照してください。 同じコンテナー名とポートを使う場合でも、このチュートリアルの残りの部分を引き続き実稼働のコンテナーに適用できます。

3. Docker コンテナーを表示するには、`docker ps` コマンドを実行します。

   ```bash
   sudo docker ps -a
   ```

4. **[STATUS]** 列に表示されている状態が **[Up]** の場合、SQL Server はコンテナーで実行されており、 **[PORTS]** 列で指定されているポートでリッスンしています。 SQL Server コンテナーの **[STATUS]** 列に **[Exited]** と表示されている場合は、[構成ガイドのトラブルシューティングのセクション](sql-server-linux-configure-docker.md#troubleshooting)を参照してください。

   ```bash
   $ sudo docker ps -a
   ```

    出力:

    ```
    CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
    941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour     0.0.0.0:1401->1433/tcp   sql1
    ```

## <a name="enable-machine-learning-services"></a>Machine Learning Services を有効にする

Machine Learning Services を有効にするには、SQL Server インスタンスに接続し、次の T-SQL ステートメントを実行します。

```sql
EXEC sp_configure  'external scripts enabled', 1;
RECONFIGURE WITH OVERRIDE
```

## <a name="next-steps"></a>次のステップ

Python 開発者は、次のチュートリアルに従って、SQL Server で Python を使用する方法を学習できます。

+ [Python のチュートリアル:SQL Server Machine Learning Services での線形回帰を使用したスキー レンタルの予測](../advanced-analytics/tutorials/python-ski-rental-linear-regression.md)
+ [チュートリアル:SQL Server Machine Learning Services と K-Means クラスタリングを使用して顧客を分類する](../advanced-analytics/tutorials/python-clustering-model.md)

R 開発者はいくつかの簡単な例を試して、SQL Server での R の動作方法の基本を確認できます。 次の手順については、以下のリンクを参照してください。

+ [チュートリアル:T-SQL での R の実行](../advanced-analytics/tutorials/quickstart-r-create-script.md)
+ [チュートリアル:R 開発者向けのデータベース内分析](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)
