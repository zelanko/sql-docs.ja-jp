---
title: Kubernetes でのクラスターのビッグ データの SQL Server をデプロイする方法 |Microsoft Docs
description: Kubernetes での SQL Server 2019 ビッグ データ クラスター (プレビュー) をデプロイする方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 70d8b07caf618cb5f1629fc80f0ca1db8b73ad3c
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269865"
---
# <a name="how-to-deploy-sql-server-big-data-cluster-on-kubernetes"></a>SQL Server のビッグ データは、kubernetes クラスターをデプロイする方法

SQL Server のビッグ データ クラスターは、Kubernetes クラスター上の docker コンテナーとしてデプロイできます。 これは、セットアップと構成手順の概要を示します。

- 1 つの VM、Vm、または Azure Kubernetes Service (AKS) クラスター上の Kubernetes クラスターを設定します。
- クラスターの構成ツールをインストール**mssqlctl**クライアント コンピューターにします。
- Kubernetes クラスターで SQL Server のビッグ データ クラスターをデプロイします。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="prereqs"></a> Kubernetes クラスターの前提条件

SQL Server のビッグ データのクラスターでは、kubernetes では、サーバーおよびクライアントの両方に v1.10 の最小バージョンが必要です。 Kubectl クライアントでは、特定のバージョンをインストールするを参照してください。 [kubectl curl を使用してバイナリをインストール](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl)します。 Minikube と AKS の最新バージョンとは、少なくとも 1.10 です。 For AKS を使用する必要があります`--kubernetes-version`既定とは異なるバージョンを指定するパラメーター。

> [!NOTE]
> クライアントとサーバーの Kubernetes のバージョンで +1 または-1 のマイナー バージョンがあることに注意してください。 詳細については、次を参照してください。 [Kubernetes がサポートされるのは、リリースと傾斜コンポーネント](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew)します。

## <a id="kubernetes"></a> Kubernetes クラスターのセットアップ

上記の前提条件を満たしている Kubernetes クラスターが既にある場合に直接進んで、[配置手順](#deploy)します。 このセクションでは、Kubernetes の概念の基本的な知識を前提とします。  Kubernetes の詳細については、次を参照してください。、 [Kubernetes のドキュメント](https://kubernetes.io/docs/home)します。

3 つの方法のいずれかでの Kubernetes にデプロイすることができます。

| Kubernetes をデプロイします。 | 説明 |
|---|---|
| **Minikube** | VM で単一ノードの Kubernetes クラスター。 |
| **Azure Kubernetes サービス (AKS)** | Azure の managed Kubernetes コンテナー サービスです。 |
| **複数のマシン** | 物理マシンまたはを使用して仮想マシンにデプロイされる Kubernetes クラスター **kubeadm** |

ビッグ データの SQL Server クラスターの Kubernetes クラスター オプションのいずれかを構成する方法の詳細については、次の記事のいずれかを参照してください。

   - [Minikube を構成します。](deploy-on-minikube.md)
   - [Azure Kubernetes Service で Kubernetes を構成します。](deploy-on-aks.md)
   - [Kubeadm で複数のコンピューターでの Kubernetes を構成します。](deploy-with-kubeadm.md)
   
> [!TIP]
> AKS と SQL Server の両方のビッグ データ クラスターをデプロイするサンプル python スクリプトについては、次を参照してください。[ビッグ データ クラスター Azure Kubernetes Service (AKS) で SQL Server 展開](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks)します。

## <a id="deploy"></a> SQL Server のビッグ データ クラスターをデプロイします。

Kubernetes クラスターを構成した後は、SQL Server のビッグ データ クラスターの配置を続行することができます。 

> [!NOTE]
> 以前のリリースからアップグレードする場合を参照してください、[この記事の「アップグレード](#upgrade)します。

開発/テスト環境のすべての既定の構成で Azure でビッグ データ クラスターをデプロイするには、この記事の手順に従います。

[クイック スタート: Kubernetes 上の SQL Server のビッグ データ クラスターをデプロイします。](quickstart-big-data-cluster-deploy.md)

ワークロードのニーズに従って、ビッグ データ クラスター構成をカスタマイズする場合は、一連の手順に従います。

## <a name="verify-kubernetes-configuration"></a>Kubernetes 構成を確認します。

実行、 **kubectl**クラスター構成を表示するコマンド。 その kubectl が適切なクラスター コンテキストを指すことを確認します。

```bash
kubectl config view
```

## <a id="mssqlctl"></a> Mssqlctl をインストールします。

**mssqlctl**は Python で記述された、により、クラスター管理者のブートス トラップし、REST Api を使用してビッグ データ クラスターを管理するコマンド ライン ユーティリティです。 必要な最小の Python バージョン v3.5 です。 必要がある`pip`をダウンロードしてインストールに使用される**mssqlctl**ツール。 

> [!IMPORTANT]
> 以前のリリースをインストールした場合は、クラスターを削除する必要があります*する前に*アップグレード**mssqlctl**と新しいリリースをインストールします。 詳細については、次を参照してください。[新しいリリースにアップグレードする](deployment-guidance.md#upgrade)します。

### <a name="windows-mssqlctl-installation"></a>Windows mssqlctl インストール

1. Windows クライアントでは、上から必要な Python パッケージをダウンロード[ https://www.python.org/downloads/](https://www.python.org/downloads/)します。 Python3.5.3 以降、Python をインストールすると、pip3 もインストールします。 

   > [!TIP] 
   > Python3 でインストールする場合は、Python のパスを追加選択します。 そうでない場合は、pip3 がある場所を後で検索し、パスに手動で追加できます。

1. 最新であることを確認**要求**パッケージ。

   ```cmd
   python -m pip install requests
   python -m pip install requests --upgrade
   ```

1. インストール**mssqlctl**次のコマンドを使用します。

   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.1 mssqlctl
   ```

### <a name="linux-mssqlctl-installation"></a>Linux mssqlctl のインストール

Linux では、インストールする必要があります、 **python3**と**python3 pip**パッケージ化し、実行`sudo pip3 install --upgrade pip`します。 3.5 最新の Python と pip がインストールされます。 Ubuntu のこれらのコマンドのしくみは次の例を示しています (別のプラットフォームを使用している場合、コマンドの変更、パッケージ マネージャー)。

1. 必要な Python パッケージをインストールします。

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip && /
   sudo -H pip3 install --upgrade pip
   ```

1. インストール**mssqlctl**次のコマンドを使用します。

   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.1 mssqlctl
   ```

## <a name="define-environment-variables"></a>環境変数を定義します。

渡される環境変数のセットを使用して、クラスター構成をカスタマイズすることができます、`mssqlctl create cluster`コマンド。 環境変数のほとんどは、以下に従って既定値を持つ省略可能です。 資格情報をユーザー入力を必要とするように環境変数があることに注意してください。

| 環境変数 | 必須 | 既定値 | 説明 |
|---|---|---|---|
| **ACCEPT_EULA** | はい | なし | SQL Server のライセンス契約 (たとえば、"Y") をそのまま使用します。  |
| **CLUSTER_NAME** | はい | なし | SQLServer にビッグ データのクラスターをデプロイする Kubernetes 名前空間の名前。 |
| **CLUSTER_PLATFORM** | はい | なし | Kubernetes クラスターが展開されているプラットフォームです。 `aks`、 `minikube`、 `kubernetes`|
| **CLUSTER_COMPUTE_POOL_REPLICAS** | いいえ | 1 | 構築するためのコンピューティング プールのレプリカの数。CTP2.0 のみ値が 1 には許可します。 |
| **CLUSTER_DATA_POOL_REPLICAS** | いいえ | 2 | データの数はプールを構築するためのレプリカです。 |
| **CLUSTER_STORAGE_POOL_REPLICAS** | いいえ | 2 | 構築するための記憶域プールのレプリカの数。 |
| **DOCKER_REGISTRY** | はい | TBD | クラスターのデプロイに使用されるイメージが格納されているプライベート レジストリです。 |
| **DOCKER_REPOSITORY** | はい | TBD | イメージを格納、上記のレジストリ内のプライベート リポジトリ。  ゲートのパブリック プレビューの期間が必要です。 |
| **DOCKER_USERNAME** | はい | なし | これらはプライベート リポジトリに格納されている場合に、コンテナー イメージにアクセスするユーザー名。 ゲートのパブリック プレビューの期間が必要です。 |
| **DOCKER_PASSWORD** | はい | なし | 上記のプライベート リポジトリにアクセスするパスワード。 ゲートのパブリック プレビューの期間が必要です。|
| **DOCKER_EMAIL** | はい | なし | 上記のプライベート リポジトリに関連付けられた電子メール アドレス。 ゲートのプライベート プレビューの期間が必要です。 |
| **DOCKER_IMAGE_TAG** | いいえ | 最新 | イメージにタグ付けに使用されるラベル。 |
| **DOCKER_IMAGE_POLICY** | いいえ | 毎回 | イメージのプルは常に強制します。  |
| **DOCKER_PRIVATE_REGISTRY** | はい | 1 | ゲートのパブリック プレビューの期間、この値は 1 に設定するのには。 |
| **CONTROLLER_USERNAME** | はい | なし | クラスター管理者のユーザー名。 |
| **CONTROLLER_PASSWORD** | はい | なし | クラスター管理者のパスワード。 |
| **KNOX_PASSWORD** | はい | なし | Knox ユーザーのパスワード。 |
| **MSSQL_SA_PASSWORD** | はい | なし | SQL のマスター インスタンスの SA ユーザーのパスワードです。 |
| **USE_PERSISTENT_VOLUME** | いいえ | true | `true` Kubernetes 永続ボリュームを使用するには、ポッドの記憶域を要求します。  `false` ポッドの記憶域の一時的なホストの記憶域を使用します。 参照してください、[データ永続化](concept-data-persistence.md)詳細については資料。 SQL Server が minikube 上でビッグ データ クラスターおよび USE_PERSISTENT_VOLUME 展開する場合は、= true に設定する必要があります値を設定するの`STORAGE_CLASS_NAME=standard`します。 |
| **STORAGE_CLASS_NAME** | いいえ | 既定値 (default) | 場合`USE_PERSISTENT_VOLUME`は`true`を使用する Kubernetes ストレージ クラスの名前を示します。 参照してください、[データ永続化](concept-data-persistence.md)詳細については資料。 SQL Server が minikube 上でビッグ データ クラスターをデプロイする場合、既定のストレージ クラス名が異なると設定をオーバーライドする必要があります`STORAGE_CLASS_NAME=standard`します。 |
| **MASTER_SQL_PORT** | いいえ | 31433 | Master の SQL インスタンスがパブリック ネットワークをリッスンする TCP/IP ポート。 |
| **KNOX_PORT** | いいえ | 30443 | Apache Knox がパブリック ネットワークをリッスンする TCP/IP ポート。 |
| **GRAFANA_PORT** | いいえ | 30888 | アプリケーションの監視 Grafana がパブリック ネットワークをリッスンする TCP/IP ポート。 |
| **KIBANA_PORT** | いいえ | 30999 | Kibana のログ検索アプリケーションがパブリック ネットワークでリッスンする TCP/IP ポート。 |

> [!IMPORTANT]
>1. 制限付きのプライベート プレビューの期間中、プライベート Docker レジストリの資格情報はお客様に提供されるトリアージ時に、 [EAP 登録](https://aka.ms/eapsignup)します。
>1. 構築された、オンプレミスのクラスターの**kubeadm**、環境変数の値は、`CLUSTER_PLATFORM`は`kubernetes`します。 また、 `USE_PERSISTENT_VOLUME=true`、Kubernetes ストレージ クラスに事前に準備しを使用して通過する必要があります、`STORAGE_CLASS_NAME`します。
>1. 特殊文字が含まれている場合、二重引用符で囲まれた、パスワードをラップすることを確認します。 MSSQL_SA_PASSWORD を任意に設定できますが必ず、十分に複雑な使用しないでください、 `!`、`&`または`‘`文字。 コマンドの bash でのみ二重引用符区切り記号の動作に注意してください。
>1. クラスターの名前は小文字英数字文字、空白のみである必要があります。 すべての Kubernetes ・ アーティファクト (コンテナー、ポッド、ステートフルのセット、サービスなど)、クラスターのクラスターと同じ名前を持つ名前空間に作成されます名を指定します。
>1. **SA**アカウントは、システム管理者は、セットアップ中に作成される SQL Server マスター インスタンス。 実行して探索可能なは、MSSQL_SA_PASSWORD 環境変数を指定した、SQL Server のコンテナーを作成した後は、コンテナー内の $MSSQL_SA_PASSWORD をエコーします。 セキュリティのために、文書化のベスト プラクティスに従って、SA のパスワードを変更する[ここ](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password)します。

ビッグ データ クラスターを展開するために必要な環境変数の設定は、Windows または Linux クライアントを使用しているかどうかによって異なります。  使用しているオペレーティング システムに応じて次の手順を選択します。

次の環境変数を初期化、クラスターをデプロイに必要な場合。

### <a name="windows"></a>Windows

コマンド ウィンドウ (PowerShell ではなく) を使用して、次の環境変数を構成します。 値を囲む引用符は使用しないでください。

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=<minikube or aks or kubernetes>

SET CONTROLLER_USERNAME=<controller_admin_name – can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
SET MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

SET DOCKER_REGISTRY=private-repo.microsoft.com
SET DOCKER_REPOSITORY=mssql-private-preview
SET DOCKER_USERNAME=<your username, credentials provided by Microsoft>
SET DOCKER_PASSWORD=<your password, credentials provided by Microsoft>
SET DOCKER_EMAIL=<your Docker email, use the username provided by Microsoft>
SET DOCKER_PRIVATE_REGISTRY="1"
```

### <a name="linux"></a>Linux

次の環境変数を初期化します。 Bash では、各値を囲む引用符を使用できます。

```bash
export ACCEPT_EULA=Y
export CLUSTER_PLATFORM=<minikube or aks or kubernetes>

export CONTROLLER_USERNAME="<controller_admin_name – can be anything>"
export CONTROLLER_PASSWORD="<controller_admin_password – can be anything, password complexity compliant>"
export KNOX_PASSWORD="<knox_password – can be anything, password complexity compliant>"
export MSSQL_SA_PASSWORD="<sa_password_of_master_sql_instance, password complexity compliant>"

export DOCKER_REGISTRY="private-repo.microsoft.com"
export DOCKER_REPOSITORY="mssql-private-preview"
export DOCKER_USERNAME="<your username, credentials provided by Microsoft>"
export DOCKER_PASSWORD="<your password, credentials provided by Microsoft>"
export DOCKER_EMAIL="<your Docker email, use the username provided by Microsoft>"
export DOCKER_PRIVATE_REGISTRY="1"
```

### <a name="minikube-settings"></a>Minikube 設定

Minikube を展開する場合と`USE_PERSISTENT_VOLUME=true`(既定値) の既定値もオーバーライドする必要があります`STORAGE_CLASS_NAME`環境変数。

Minikube 展開の Windows で、次のコマンドを使用します。

```cmd
SET STORAGE_CLASS_NAME=standard
```

Linux 上の次のコマンドを使用して、minikube 展開。

```bash
export STORAGE_CLASS_NAME=standard
```

永続ボリュームを設定して minikube を使用してを抑制する代わりに、`USE_PERSISTENT_VOLUME=false`します。

### <a name="kubadm-settings"></a>Kubadm 設定

Kubernetes ストレージ クラスの事前プロビジョニングし、を使用して通過する必要があります、独自の物理または仮想マシンに kubeadm を展開している場合、`STORAGE_CLASS_NAME`します。 永続ボリュームを使用して設定を抑制する代わりに、`USE_PERSISTENT_VOLUME=false`します。 永続的なストレージの詳細については、次を参照してください。[を Kubernetes クラスターのビッグ データ、SQL Server でのデータ永続化](concept-data-persistence.md)します。

## <a name="deploy-sql-server-big-data-cluster"></a>SQL Server ビッグ データ クラスターを展開する

Kubernetes 名前空間を初期化して、名前空間にすべてのアプリケーション ポッドをデプロイする作成クラスター API が使用されます。 Kubernetes クラスターで SQL Server のビッグ データ クラスターをデプロイするには、次のコマンドを実行します。

```bash
mssqlctl create cluster <name of your cluster>
```

クラスターのブートス トラップ中には、クライアントのコマンド ウィンドウが展開ステータスを出力します。 別のコマンド ウィンドウでこれらのコマンドを実行してデプロイの状態をチェックすることもできます。

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

配置スクリプトが正常に完了したら、次の手順を使用して、SQL Server マスター インスタンスの IP アドレスを取得できます。 この IP アドレスとポート番号 31433 master の SQL Server インスタンスへの接続に使用する (例:  **\<ip アドレス\>31433、**)。 同様に、SQL Server のビッグ データ クラスターの IP を実行します。 クラスターの管理ポータルもサービス エンドポイント タブでは、クラスターのすべてのエンドポイントが記載されています。 クラスターの管理ポータルを使用すると、展開を監視します。 外部 IP アドレスとポート番号を使用してポータルにアクセスすることができます、 `service-proxy-lb` (例: **https://\<ip アドレス\>: 30777**)。 値の管理ポータルにアクセスするための資格情報`CONTROLLER_USERNAME`と`CONTROLLER_PASSWORD`上で指定した環境変数。

### <a name="aks"></a>AKS

AKS を使用している場合、Azure は、Azure ロード バランサーのサービスを提供します。 次のコマンドを実行します。

```bash
kubectl get svc service-master-pool-lb -n <name of your cluster>
kubectl get svc service-security-lb -n <name of your cluster>
kubectl get svc service-proxy-lb -n <name of your cluster>
```

探して、 **EXTERNAL-IP**サービスに割り当てられている値。 ポート 31433 で IP アドレスを使用して、SQL Server マスター インスタンスに接続し (例:  **\<ip アドレス\>31433、**) との外部 ip アドレスを使用して SQL Server ビッグ データ クラスター エンドポイントに`service-security-lb`サービス。 

### <a name="minikube"></a>Minikube

Minikube を使用している場合に接続する必要がある IP アドレスを取得する次のコマンドを実行する必要があります。 だけでなく、IP への接続に必要なエンドポイントのポートを指定します。 すべてのサービス エンドポイントを取得するには 

```bash
minikube ip
```

プラットフォームに関係なく、Kubernetes クラスターを実行するクラスター、次のコマンド用にデプロイされたすべてのサービス エンドポイントを取得する、実行されます。
```bash
kubectl get svc -n <name of your cluster>
```

## <a id="upgrade"></a> 新しいリリースにアップグレードします。

現時点では、ビッグ データ クラスターを新しいリリースにアップグレードする唯一の方法は、手動で削除してクラスターを再作成します。 各リリースでは、一意のバージョンの**mssqlctl**ですが、以前のバージョンと互換性がありません。 また、古いクラスターを新しいノードにイメージをダウンロードする場合は、最新のイメージ可能性がありますと互換性がない、クラスター上で古いイメージ。 最新のリリースにアップグレードするには、次の手順を使用します。

1. 以前のクラスターを削除する前に、HDFS と SQL Server のマスター インスタンスにデータをバックアップします。 使用することができます、SQL Server のマスター インスタンスの[SQL Server のバックアップと復元](data-ingestion-restore-databse.md)します。 HDFS のする[で、データをコピーできます**curl**](data-ingestion-curl.md)します。

1. 以前のクラスターを削除、`mssqlctl delete cluster`コマンド。

   ```bash
    mssqlctl delete cluster <old-cluster-name>
   ```

1. 最新バージョンのインストール**mssqlctl**します。
   
   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.1 mssqlctl
   ```

   > [!IMPORTANT]
   > 各リリースへのパス**mssqlctl**変更します。 以前にインストールした場合でも**mssqlctl**、新しいクラスターを作成する前に最新のパスから再インストールする必要があります。

1. 」の手順に従って、最新リリースをインストール、[セクションを展開](#deploy)に改訂された記事。 

## <a name="next-steps"></a>次の手順

ビッグ データ クラスター Kubernetes では、SQL Server を正常に展開した後[ビッグ データ ツールをインストール](deploy-big-data-tools.md)について説明し、新機能の一部を試して[SQL Server 2019 プレビューで notebook を使用する方法](notebooks-guidance.md)します。
