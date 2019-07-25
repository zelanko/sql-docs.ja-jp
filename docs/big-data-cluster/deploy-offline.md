---
title: オフラインでの展開
titleSuffix: SQL Server big data clusters
description: SQL Server ビッグデータクラスターのオフライン展開を実行する方法について説明します。
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cd8b3128fc11037a5ade494813611d473c995f8f
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419368"
---
# <a name="perform-an-offline-deployment-of-a-sql-server-big-data-cluster"></a>SQL Server ビッグデータクラスターのオフライン展開を実行する

この記事では、SQL Server 2019 ビッグデータクラスター (プレビュー) のオフライン展開を実行する方法について説明します。 ビッグデータクラスターは、コンテナーイメージをプルする Docker リポジトリへのアクセス権を持っている必要があります。 オフラインインストールとは、必要なイメージがプライベート Docker リポジトリに配置されるものです。 そのプライベートリポジトリは、新しい展開のイメージソースとして使用されます。

## <a name="prerequisites"></a>必須コンポーネント

- サポートされている任意の Linux ディストリビューションの Docker エンジン 1.8 + または Docker for Mac/Windows。 詳細については「[Install Docker](https://docs.docker.com/engine/installation/)」(Docker のインストール) を参照してください。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="load-images-into-a-private-repository"></a>プライベートリポジトリにイメージを読み込む

次の手順では、ビッグデータクラスターコンテナーイメージを Microsoft リポジトリからプルし、プライベートリポジトリにプッシュする方法について説明します。

> [!TIP]
> 次の手順では、このプロセスについて説明します。 ただし、タスクを簡略化するために、これらのコマンドを手動で実行するのではなく、[自動スクリプト](#automated)を使用できます。

1. 次のコマンドを繰り返して、ビッグデータクラスターコンテナーイメージをプルします。 各`<SOURCE_IMAGE_NAME>` [イメージ名](#images)で置き換えます。 `<SOURCE_DOCKER_TAG>` **2019-ctp 3.2-ubuntu**など、ビッグデータクラスターのリリースのタグで置き換えます。  

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/bdc/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG>
   ```

1. ターゲットプライベート Docker レジストリにログインします。

   ```PowerShell
   docker login <TARGET_DOCKER_REGISTRY> -u <TARGET_DOCKER_USERNAME> -p <TARGET_DOCKER_PASSWORD>
   ```

1. 各イメージに対して次のコマンドを使用して、ローカルイメージにタグを付けます。

   ```PowerShell
   docker tag mcr.microsoft.com/mssql/bdc/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG> <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

1. ローカルイメージをプライベート Docker リポジトリにプッシュします。

   ```PowerShell
   docker push <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

### <a id="images"></a>ビッグデータクラスターコンテナーイメージ

オフラインインストールには、次のビッグデータクラスターコンテナーイメージが必要です。

 - **mssql-appdeploy-init**
 - **mssql-monitor-fluentbit**
 - **mssql-monitor-collectd**
 - **mssql-server-data**
 - **mssql-hadoop**
 - **mssql-monitor-elasticsearch**
 - **mssql-monitor-influxdb**
 - **mssql-security-knox**
 - **mssql-mlserver-r-runtime**
 - **mssql-mlserver-py-runtime**
 - **mssql-controller**
 - **mssql-server-controller**
 - **mssql-monitor-grafana**
 - **mssql-monitor-kibana**
 - **mssql-service-proxy**
 - **mssql-app-service-proxy**
 - **mssql-ssis-app-runtime**
 - **mssql-monitor-telegraf**
 - **mssql-mleap-serving-runtime**
 - **mssql-セキュリティ-サポート**

## <a id="automated"></a>自動スクリプト

自動的にすべての必要なコンテナーイメージをプルし、プライベートリポジトリにプッシュする自動化された python スクリプトを使用できます。

> [!NOTE]
> Python は、スクリプトを使用するための前提条件です。 Python をインストールする方法の詳細については、 [python のドキュメント](https://wiki.python.org/moin/BeginnersGuide/Download)を参照してください。

1. Bash または PowerShell から、 **curl**を使用してスクリプトをダウンロードします。

   ```PowerShell
   curl -o push-bdc-images-to-custom-private-repo.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/offline/push-bdc-images-to-custom-private-repo.py"
   ```

1. その後、次のいずれかのコマンドを使用してスクリプトを実行します。

   **ウィンドウ**

   ```PowerShell
   python deploy-sql-big-data-aks.py
   ```

   **マシン**

   ```bash
   sudo python deploy-sql-big-data-aks.py
   ```

1. 画面の指示に従って、Microsoft リポジトリとプライベートリポジトリの情報を入力します。 スクリプトが完了したら、必要なすべてのイメージがプライベートリポジトリに配置される必要があります。

## <a name="install-tools-offline"></a>ツールをオフラインでインストールする

ビッグデータクラスターのデプロイには、 **Python**、 **azdata**、 **kubectl**など、いくつかのツールが必要です。 これらのツールをオフラインサーバーにインストールするには、次の手順に従います。

### <a id="python"></a>Python をオフラインでインストールする

1. インターネットにアクセスできるコンピューターで、次のいずれかの Python を含む圧縮ファイルをダウンロードします。

   | オペレーティング システム | ダウンロード |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. 圧縮されたファイルをターゲットコンピューターにコピーし、任意のフォルダーに抽出します。

1. Windows の場合のみ、 `installLocalPythonPackages.bat`そのフォルダーからを実行し、パラメーターと同じフォルダーに完全なパスを渡します。

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

### <a id="azdata"></a>Azdata をオフラインでインストールする

1. インターネットアクセスと[Python](https://wiki.python.org/moin/BeginnersGuide/Download)が搭載されたコンピューターで、次のコマンドを実行して、すべての**azdata**パッケージを現在のフォルダーにダウンロードします。

   ```PowerShell
   pip download -r https://aka.ms/azdata
   ```

1. ダウンロードしたパッケージと**必要な .txt**ファイルをターゲットコンピューターにコピーします。

1. ターゲットコンピューターで、前のファイルをコピーしたフォルダーを指定して次のコマンドを実行します。

   ```PowerShell
   pip install --no-index --find-links <path-to-packages> -r <path-to-requirements.txt>
   ```

### <a id="kubectl"></a>Kubectl をオフラインでインストールする

オフラインコンピューターに**kubectl**をインストールするには、次の手順を実行します。

1. **Curl**を使用して、選択したフォルダーに**kubectl**をダウンロードします。 詳細については、「 [curl を使用して kubectl binary をインストールする](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl)」を参照してください。

1. フォルダーをターゲットコンピューターにコピーします。

## <a name="deploy-from-private-repository"></a>プライベートリポジトリからのデプロイ

プライベートリポジトリからデプロイするには、[展開ガイド](deployment-guidance.md)で説明されている手順を使用しますが、プライベート Docker リポジトリ情報を指定するカスタムの展開構成ファイルを使用します。 次の**azdata**コマンドは、 **control. json**という名前のカスタムデプロイ構成ファイルの Docker 設定を変更する方法を示しています。

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.repository=<your-docker-repository>"
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.registry=<your-docker-registry>"
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.imageTag=<your-docker-image-tag>"
```

デプロイによって、docker のユーザー名とパスワードの入力が求められます。または、 **DOCKER_USERNAME**環境変数と**DOCKER_PASSWORD**環境変数で指定することもできます。

## <a name="next-steps"></a>次の手順

ビッグデータクラスターの展開の詳細については、「 [How to deploy SQL Server big data cluster On Kubernetes](deployment-guidance.md)」を参照してください。
