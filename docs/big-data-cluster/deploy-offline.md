---
title: オフライン デプロイします。
titleSuffix: SQL Server big data clusters
description: ビッグ データの SQL Server クラスターをオフラインで展開を実行する方法について説明します。
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
manager: jroth
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1300c375903eb8692b8da6dce4e74a41e91d80c0
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728924"
---
# <a name="perform-an-offline-deployment-of-a-sql-server-big-data-cluster"></a>ビッグ データの SQL Server クラスターのデプロイのオフライン実行します。

この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) のオフラインの展開を実行する方法について説明します。 ビッグ データ クラスターは、コンテナー イメージをプルする元にある Docker リポジトリにアクセスする必要があります。 オフライン インストールは 1 つのプライベート Docker リポジトリに必要なイメージを配置する場所です。 プライベート リポジトリは、新しいデプロイのイメージ ソースとして使用されます。

## <a name="prerequisites"></a>必須コンポーネント

- サポートされている任意の Linux ディストリビューションの Docker エンジン 1.8 + または Docker for Mac/Windows。 詳細については「[Install Docker](https://docs.docker.com/engine/installation/)」(Docker のインストール) を参照してください。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="load-images-into-a-private-repository"></a>プライベート リポジトリにイメージを読み込む

次の手順では、Microsoft リポジトリからビッグ データ クラスター コンテナー イメージをプルし、し、それらをプライベート リポジトリにプッシュする方法について説明します。

> [!TIP]
> 次の手順では、プロセスについて説明します。 ただし、タスクを簡素化する際、[自動スクリプト](#automated)手動でこれらのコマンドを実行する代わりにします。

1. Microsoft の Docker レジストリに最初に、ログイン、 **docker ログイン**コマンド。 Microsoft Early Adoption Program の一部として提供されるユーザー名とパスワードを使用します。

   ```PowerShell
   docker login private-repo.microsoft.com -u  <SOURCE_DOCKER_USERNAME> -p <SOURCE_DOCKER_PASSWORD>
   ```

   > [!TIP]
   > これらのコマンドは、例として、PowerShell を使用しますが、cmd、bash、または docker を実行できる任意のコマンド シェルから実行することができます。 Linux では、次のように追加します。`sudo`各コマンドにします。

1. 次のコマンドを繰り返すことにより、ビッグ データ クラスターにコンテナー イメージをプルします。 置換`<SOURCE_IMAGE_NAME>`各[イメージ名](#images)します。 置換`<SOURCE_DOCKER_TAG>`などクラスター リリースでは、ビッグ データのタグを持つ**ctp3.1**します。  

   ```PowerShell
   docker pull private-repo.microsoft.com/mssql-private-preview/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG>
   ```

1. Docker レジストリにターゲット プライベートにログインします。

   ```PowerShell
   docker login <TARGET_DOCKER_REGISTRY> -u <TARGET_DOCKER_USERNAME> -p <TARGET_DOCKER_PASSWORD>
   ```

1. イメージごとに次のコマンドでローカル イメージをタグ付けには。

   ```PowerShell
   docker tag private-repo.microsoft.com/mssql-private-preview/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG> <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

1. プライベート Docker リポジトリをローカルのイメージをプッシュします。

   ```PowerShell
   docker push <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

### <a id="images"></a> ビッグ データ クラスターのコンテナー イメージ

次のビッグ データ クラスターのコンテナー イメージは、オフライン インストールの必要があります。

 - **mssql-appdeploy-init**
 - **mssql-monitor-fluentbit**
 - **mssql-monitor-collectd**
 - **mssql-server-data**
 - **mssql-hadoop**
 - **mssql-java**
 - **mssql-mlservices-pythonserver**
 - **mssql-mlservices-rserver**
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
  

## <a id="automated"></a> 自動化されたスクリプト

自動的にすべての必要なコンテナー イメージをプルし、それらをプライベート リポジトリにプッシュする自動化された python スクリプトを使用することができます。

> [!NOTE]
> Python は、スクリプトを使用するための前提条件です。 Python をインストールする方法の詳細については、次を参照してください。、 [Python のドキュメント](https://wiki.python.org/moin/BeginnersGuide/Download)します。

1. Bash または PowerShell でスクリプトをダウンロード**curl**:

   ```PowerShell
   curl -o push-bdc-images-to-custom-private-repo.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/offline/push-bdc-images-to-custom-private-repo.py"
   ```

1. 次のコマンドのいずれかのスクリプトを実行します。

   **Windows:**

   ```PowerShell
   python deploy-sql-big-data-aks.py
   ```

   **Linux の場合:**

   ```bash
   sudo python deploy-sql-big-data-aks.py
   ```

1. Microsoft リポジトリとプライベート リポジトリ情報を入力するための指示に従います。 スクリプトが完了すると、必要なすべてのプライベート リポジトリでイメージを配置する必要があります。

## <a name="install-tools-offline"></a>オフライン ツールをインストールします。

ビッグ データ クラスターのデプロイなど、いくつかのツールを必要と**Python**、 **mssqlctl**、および**kubectl**します。 サーバーがオフラインにこれらのツールをインストールするのにには、次の手順を使用します。

### <a id="python"></a> オフラインの python をインストールします。

1. インターネットにアクセスできるコンピューターには、1 つの Python を含む次の圧縮されたファイルをダウンロードします。

   | オペレーティング システム | ダウンロード |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OS X     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. ターゲット コンピューターに圧縮されたファイルをコピーし、任意のフォルダーに抽出します。

1. Windows でのみ、実行`installLocalPythonPackages.bat`フォルダーから、パラメーターと同じフォルダーのパスの完全なパス。

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

### <a id="mssqlctl"></a> Mssqlctl オフラインのインストールします。

1. インターネットにアクセスできるマシン上および[Python](https://wiki.python.org/moin/BeginnersGuide/Download)、すべてをダウンロードするには、次のコマンドを実行、 **mssqlctl**現在のフォルダーにパッケージします。

   ```PowerShell
   pip download -r https://private-repo.microsoft.com/python/ctp-2.3/mssqlctl/requirements.txt
   ```

1. ダウンロード、 **requirements.txt**ファイル。

   ```PowerShell
   curl -o requirements.txt "https://private-repo.microsoft.com/python/ctp-2.3/mssqlctl/requirements.txt"
   ```

1. ダウンロードしたパッケージをコピーし、 **requirements.txt**ターゲット コンピューターにファイル。

1. ターゲット コンピューターに以前のファイルをコピーしたフォルダーを指定するには、次のコマンドを実行します。

   ```PowerShell
   pip install --no-index --find-links <path-to-packages> -r <path-to-requirements.txt>
   ```

### <a id="kubectl"></a> オフラインの kubectl をインストールします。

インストールする**kubectl**オフラインのマシンに、次の手順を使用します。

1. 使用**curl**をダウンロードする**kubectl**任意のフォルダーにします。 詳細については、次を参照してください。 [curl を使用して kubectl バイナリをインストール](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl)します。

1. ターゲット コンピューターに、フォルダーをコピーします。

## <a name="deploy-from-private-repository"></a>プライベート リポジトリからデプロイします。

プライベート リポジトリからを展開するには、記載された手順を使用、[展開ガイド](deployment-guidance.md)が、プライベート Docker リポジトリ情報を指定するカスタムの展開構成ファイルを使用します。 次**mssqlctl**コマンドは、という名前のカスタム展開構成ファイルで Docker の設定を変更する方法を示します**custom.json**:

```bash
mssqlctl bdc config section set --config-profile custom -j "$.spec.controlPlane.spec.docker.repository=<your-docker-repository>"
mssqlctl bdc config section set --config-profile custom -j "$.spec.controlPlane.spec.docker.registry=<your-docker-registry>"
mssqlctl bdc config section set --config-profile custom -j "$.spec.controlPlane.spec.docker.imageTag=<your-docker-image-tag>"
```

展開が、docker のユーザー名とパスワードを求めまたはで指定することができます、 **DOCKER_USERNAME**と**DOCKER_PASSWORD**環境変数。

## <a name="next-steps"></a>次の手順

ビッグ データ クラスターのデプロイの詳細については、次を参照してください。[ビッグ データの SQL Server をデプロイする方法を Kubernetes クラスターの](deployment-guidance.md)します。
