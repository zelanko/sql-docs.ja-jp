---
title: Kubernetes での SQL Server のビッグ データ クラスターをデプロイする方法 |Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/08/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 02a1aa7299173315e4f4d6a60eae5f166e8fcdfe
ms.sourcegitcommit: ce4b39bf88c9a423ff240a7e3ac840a532c6fcae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48877895"
---
# <a name="how-to-deploy-sql-server-big-data-cluster-on-kubernetes"></a>Kubernetes での SQL Server のビッグ データ クラスターをデプロイする方法

SQL Server のビッグ データ クラスターは、Kubernetes クラスター上の docker コンテナーとしてデプロイできます。 これは、セットアップと構成手順の概要を示します。

- 1 つの vm、Vm のクラスターの Azure Container Service で Kubernetes クラスターのセットアップ
- クラスターの構成ツールをインストール`mssqlctl`クライアント コンピューターに
- Kubernetes クラスターで SQL Server のビッグ データ クラスターをデプロイします。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="prereqs"></a> Kubernetes クラスターの前提条件

SQL Server のビッグ データ クラスターでは、kubernetes では、サーバーとクライアントの両方で、最小 v1.10 バージョンが必要です。 Kubectl クライアントでは、特定のバージョンをインストールするを参照してください。 [kubectl curl を使用してバイナリをインストール](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl)します。  Minikube と AKS の最新バージョンとは、少なくとも 1.10 です。 AKS を使用する必要があります`--kubernetes-version`既定とは異なるバージョンを指定するパラメーター。

> [!NOTE]
> クライアントとサーバーの Kubernetes のバージョンで +1 または-1 のマイナー バージョンがあることに注意してください。 詳細については、次を参照してください。 [Kubernetes がサポートされるのは、リリースと傾斜コンポーネント](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew)します。

## <a id="kubernetes"></a> Kubernetes クラスターのセットアップ

上記の前提条件を満たしている Kubernetes クラスターが既にある場合に直接進んで、[配置手順](#deploy)します。 このセクションでは、Kubernetes の概念の基本的な知識を前提とします。  Kubernetes の詳細については、次を参照してください。、 [Kubernetes のドキュメント](https://kubernetes.io/docs/home)します。

3 つの方法のいずれかでの Kubernetes にデプロイすることができます。

| Kubernetes をデプロイします。 | 説明 |
|---|---|
| **Minikube** | VM で単一ノードの Kubernetes クラスター。 |
| **Azure Kubernetes サービス (AKS)** | Azure の managed Kubernetes コンテナー サービスです。 |
| **複数の Vm** | Kubeadm を使用して Vm にデプロイされた Kubernetes クラスター |

SQL Server のビッグ データ クラスターの Kubernetes クラスター オプションのいずれかを構成する方法の詳細については、次の記事のいずれかを参照してください。

   - [Minikube を構成します。](deploy-on-minikube.md)
   - [Azure Kubernetes Service で Kubernetes を構成します。](deploy-on-aks.md)

## <a id="deploy"></a> SQL Server のビッグ データ クラスターをデプロイします。

Kubernetes クラスターを構成した後は、SQL Server のビッグ データ クラスターの配置を続行することができます。 開発/テスト環境のすべての既定の構成でのビッグ データ クラスターを展開するには、この記事の手順に従います。

[クイック スタート: SQL Server のビッグ データは、kubernetes クラスターをデプロイします。](quickstart-big-data-cluster-deploy.md)

ワークロードのニーズに合わせて、ビッグ データ クラスター構成をカスタマイズする場合は、一連の手順に従います。

## <a name="verify-kubernetes-configuration"></a>Kubernetes 構成を確認します。

実行、次の kubectl コマンドをクラスター構成を表示します。 その kubectl が適切なクラスター コンテキストを指すことを確認します。

```bash
kubectl config view
```

## <a name="install-mssqlctl-cli-management-tool-for-sql-server-big-data-cluster"></a>SQL Server のビッグ データ クラスター mssqlctl CLI 管理ツールをインストールします。
`mssqlctl` コマンド ライン ユーティリティは、クラスター管理者は、ブートス トラップし、REST Api を使用してビッグ データ クラスターを管理できるようにする Python で記述されます。 必要な最小の Python バージョン v3.5 です。 必要がある`pip`をダウンロードしてインストールに使用される`mssqlctl`ツール。 Windows クライアントから必要な Python パッケージをダウンロードできます[ https://www.python.org/downloads/](https://www.python.org/downloads/)します。 Python3.5.3 以降、Python をインストールすると、pip3 もインストールします。 インストールするときに、パスに追加 を選択することがありますできません。 Pip3 があるし、パスに手動で追加を見つけることができます。
Linux (たとえば WSL または Ubuntu のクライアント) では、これらのコマンドは Python と pip の 3.5 最新のバージョンをインストールします。

```bash
sudo apt-get update
sudo apt-get install python3
sudo apt-get install python3-pip
sudo pip3 install --upgrade pip
```

> [!NOTE]
Python のインストール環境がない場合、`requests`パッケージをインストールする必要がある`requests`を使用して`python -m pip install requests`。 既にある場合、`requests`パッケージのインストールを実行して最新のバージョンがあるかどうかを確認してください`python -m pip install requests --upgrade`します。

実行、次のコマンドを msqlctl をインストールします。

```bash
pip3 install --index-url https://private-repo.microsoft.com/python/ctp-2.0 mssqlctl
```

## <a name="define-environment-variables"></a>環境変数を定義します。

渡される環境変数のセットを使用して、クラスター構成をカスタマイズすることができます、`mssqlctl create cluster`コマンド。 環境変数のほとんどは、以下に従って avalues を既定ではオプションです。 資格情報をユーザー入力を必要とするように環境変数があることに注意してください。

| 環境変数 | 必須 | 既定値 | 説明 |
|---|---|---|---|
| **ACCEPT_EULA** | はい | なし | SQL Server のライセンス契約 (たとえば、"Y") をそのまま使用します。  |
| **CLUSTER_NAME** | はい | なし | Sql Server のビッグ データ クラスターをデプロイする Kubernetes 名前空間の名前。 |
| **CLUSTER_PLATFORM** | はい | なし | Kubernetes クラスターが展開されているプラットフォームです。 `aks`、 `minikube`、 `kubernetes`|
| **CLUSTER_COMPUTE_POOL_REPLICAS** | いいえ | 1 | 構築するためのコンピューティング プールのレプリカの数。CTP2.0 のみ値が 1 には許可します。 |
| **CLUSTER_DATA_POOL_REPLICAS** | いいえ | 2 | データの数はプールを構築するためのレプリカです。 |
| **CLUSTER_STORAGE_POOL_REPLICAS** | いいえ | 2 | 構築するための記憶域プールのレプリカの数。 |
| **DOCKER_REGISTRY** | はい | TBD | クラスターのデプロイに使用されるイメージが格納されているプライベート レジストリです。 |
| **DOCKER_REPOSITORY** | はい | TBD | イメージを格納、上記のレジストリ内のプライベート リポジトリ。  ゲートのパブリック プレビューの期間が必要です。 |
| **DOCKER_USERNAME** | はい | なし | これらはプライベート リポジトリに格納されている場合に、コンテナー イメージにアクセスするユーザー名。 ゲートのパブリック プレビューの期間が必要です。 |
| **DOCKER_PASSWORD** | はい | なし | 上記のプライベート リポジトリにアクセスするパスワード。 ゲートのパブリック プレビューの期間が必要です。|
| **DOCKER_EMAIL** | はい | なし | 上記のプライベート リポジトリに関連付けられた電子メール アドレス。 ゲートのプライベート プレビューの期間が必要です。 |
| **DOCKER_IMAGE_TAG** | いいえ | 最新 | イメージをタグ付けするために使用するラベル。 |
| **DOCKER_IMAGE_POLICY** | いいえ | 毎回 | イメージのプルは常に強制します。  |
| **DOCKER_PRIVATE_REGISTRY** | はい | 1 | ゲートのパブリック プレビューの期間、この値は 1 に設定するのには。 |
| **CONTROLLER_USERNAME** | はい | なし | クラスター管理者のユーザー名。 |
| **CONTROLLER_PASSWORD** | はい | なし | クラスター管理者のパスワード。 |
| **KNOX_PASSWORD** | はい | なし | Knox ユーザーのパスワード。 |
| **MSSQL_SA_PASSWORD** | はい | なし | SQL のマスター インスタンスの SA ユーザーのパスワード。 |
| **USE_PERSISTENT_VOLUME** | いいえ | true | `true` Kubernetes 永続ボリュームを使用するには、ポッドの記憶域を要求します。  `false` ポッドの記憶域の一時的なホストの記憶域を使用します。 参照してください、[データ永続化](concept-data-persistence.md)詳細についてはトピック。 |
| **STORAGE_CLASS_NAME** | いいえ | 既定値 (default) | 場合`USE_PERSISTENT_VOLUME`は`true`を使用する Kubernetes ストレージ クラスの名前を示します。 参照してください、[データ永続化](concept-data-persistence.md)詳細についてはトピック。 |
| **MASTER_SQL_PORT** | いいえ | 31433 | Master の SQL インスタンスがパブリック ネットワークをリッスンする TCP/IP ポート。 |
| **KNOX_PORT** | いいえ | 30443 | Apache Knox がパブリック ネットワークをリッスンする TCP/IP ポート。 |
| **GRAFANA_PORT** | いいえ | 30888 | アプリケーションの監視 Grafana がパブリック ネットワークをリッスンする TCP/IP ポート。 |
| **KIBANA_PORT** | いいえ | 30999 | Kibana のログ検索アプリケーションがパブリック ネットワークでリッスンする TCP/IP ポート。 |



> [!IMPORTANT]
>1. 制限付きのプライベート プレビューの期間中、プライベート Docker レジストリの資格情報はお客様に提供されるトリアージ時に、 [EAP 登録](https://aka.ms/eapsignup)します。
>1. Kubeadm、環境変数の値で構築された、オンプレミス クラスター`CLUSTER_PLATFORM`は`kubernetes`します。 また、USE_PERSISTENT_STORAGE = true の場合、Kubernetes ストレージ クラスの事前プロビジョニングして、STORAGE_CLASS_NAME を使用して通過する必要があります。
>1. 特殊文字が含まれている場合、二重引用符で囲まれた、パスワードをラップすることを確認します。 MSSQL_SA_PASSWORD を任意に設定できますが必ず、十分に複雑な使用しないでください、 `!`、`&`または`‘`文字。 コマンドの bash でのみ二重引用符区切り記号の動作に注意してください。
>1. クラスターの名前は小文字英数字文字、空白のみである必要があります。 すべての Kubernetes ・ アーティファクト (コンテナー、ポッド、ステートフルのセット、サービスなど)、クラスターのクラスターと同じ名前を持つ名前空間に作成されます名を指定します。
>1. **SA**アカウントは、システム管理者は、セットアップ中に作成される SQL Server マスター インスタンス。 実行して探索可能なは、MSSQL_SA_PASSWORD 環境変数を指定した、SQL Server のコンテナーを作成した後は、コンテナー内の $MSSQL_SA_PASSWORD をエコーします。 セキュリティのために、文書化のベスト プラクティスに従って、SA のパスワードを変更する[ここ](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password)します。

クラスターは、Aris を展開するために必要な環境変数を設定するため、Windows または Linux クライアントを使用しているかどうかによって異なります。  使用しているオペレーティング システムに応じて次の手順を選択します。

次の環境変数を初期化、クラスターをデプロイに必要な場合。

### <a name="windows"></a>Windows

コマンド ウィンドウ (PowerShell ではなく) を使用して、次の環境変数を構成します。

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=<minikube or aks or kubernetes>

SET CONTROLLER_USERNAME=<controller_admin_name – can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
SET MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instances>

SET DOCKER_REGISTRY=private-repo.microsoft.com
SET DOCKER_REPOSITORY=mssql-private-preview
SET DOCKER_USERNAME=<your username>
SET DOCKER_PASSWORD=<your password>
SET DOCKER_EMAIL=<your Docker email, use same as username provided>
SET DOCKER_PRIVATE_REGISTRY="1"
```

### <a name="linux"></a>Linux

次の環境変数を初期化します。

```bash
export ACCEPT_EULA=Y
export CLUSTER_PLATFORM=<minikube or aks or kubernetes>

export CONTROLLER_USERNAME=<controller_admin_name – can be anything>
export CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
export KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
export MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instances>

export DOCKER_REGISTRY=private-repo.microsoft.com
export DOCKER_REPOSITORY=mssql-private-preview
export DOCKER_USERNAME=<your username>
export DOCKER_PASSWORD=<your password>
export DOCKER_EMAIL=<your Docker email, use same as username provided>
export DOCKER_PRIVATE_REGISTRY="1"
```

## <a name="deploy-sql-server-big-data-cluster"></a>SQL Server のビッグ データ クラスターをデプロイします。

Kubernetes 名前空間を初期化して、名前空間にすべてのアプリケーション ポッドをデプロイする作成クラスター API が使用されます。 Kubernetes クラスターで SQL Server のビッグ データ クラスターをデプロイするには、次のコマンドを実行します。

```bash
mssqlctl create cluster <name of your cluster>
```

クラスターのブートス トラップ中にクライアントのコマンド ウィンドウは出力をデプロイの状態になります。 別のコマンド ウィンドウでこれらのコマンドを実行してデプロイの状態をチェックすることもできます。

```bash
kubectl get all -n <name of your cluster>
kubectl get pods -n <name of your cluster>
kubectl get svc -n <name of your cluster>
```

実行してより詳細な状態と各ポッドの構成を確認できます。
```bash
kubectl describe pod <pod name> -n <name of your cluster>
```

コント ローラーのポッドが実行されている展開の監視、クラスターの管理ポータルの [展開] タブを利用できます。

## <a id="masterip"></a> SQL Server マスター インスタンスと SQL Server のビッグ データ クラスター IP アドレスを取得します。

配置スクリプトが正常に完了したら、次の手順を使用して、SQL Server マスター インスタンスの IP アドレスを取得できます。 この IP アドレスとポート番号 31433 master の SQL Server インスタンスへの接続に使用する (例:  **\<ip アドレス\>31433、**)。 同様に、SQL Server のビッグ データのクラスターの IP を実行します。 クラスターの管理ポータルもサービス エンドポイント タブでは、クラスターのすべてのエンドポイントが記載されています。 クラスターの管理ポータルを使用すると、展開を監視します。 外部 IP アドレスとポート番号を使用してポータルにアクセスすることができます、 `service-proxy-lb` (例: **https://\<ip アドレス\>: 30777**)。 値の管理ポータルにアクセスするための資格情報`CONTROLLER_USERNAME`と`CONTROLLER_PASSWORD`上で指定した環境変数。

### <a name="aks"></a>AKS

AKS を使用している場合、Azure は、Azure ロード バランサーのサービスを提供します。 次のコマンドを実行します。

```bash
kubectl get svc service-master-pool-lb -n <name of your cluster>
kubectl get svc service-security-lb -n <name of your cluster>
kubectl get svc service-proxy-lb -n <name of your cluster>
```

探して、 **EXTERNAL-IP**サービスに割り当てられている値。 ポート 31433 で IP アドレスを使用して、SQL Server マスター インスタンスに接続し、(例:  **\<ip アドレス\>31433、**) と SQL Server のビッグ データ クラスターの外部 ip アドレスを使用してエンドポイント`service-security-lb`サービス。 

### <a name="minikube"></a>Minikube

Minikube を使用している場合に接続する必要がある IP アドレスを取得する次のコマンドを実行する必要があります。 だけでなく、IP への接続に必要なエンドポイントのポートを指定します。 すべてのサービス エンドポイントを取得するには 

```bash
minikube ip
```

プラットフォームに関係なく、Kubernetes クラスターを実行するクラスター、次のコマンド用にデプロイされたすべてのサービス エンドポイントを取得する、実行されます。
```bash
kubectl get svc -n <name of your cluster>
```

## <a name="next-steps"></a>次の手順

SQL Server のビッグ データを正常に展開した後、クラスター、Kubernetes を[ビッグ データ ツールをインストール](deploy-big-data-tools.md)について説明し、新機能の一部を試して[SQL Server 2019 プレビューで notebook を使用する方法](notebooks-guidance.md)。
