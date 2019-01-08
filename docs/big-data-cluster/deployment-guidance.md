---
title: デプロイする方法
titleSuffix: SQL Server 2019 big data clusters
description: Kubernetes での SQL Server 2019 ビッグ データ クラスター (プレビュー) をデプロイする方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/07/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: 9c1f2fbb750dcdf8e5d78ddcfd5004a32c0cc209
ms.sourcegitcommit: edf7372cb674179f03a330de5e674824a8b4118f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53246751"
---
# <a name="how-to-deploy-sql-server-big-data-clusters-on-kubernetes"></a>Kubernetes での SQL Server のビッグ データ クラスターをデプロイする方法

SQL Server のビッグ データ クラスターは、Kubernetes クラスター上の docker コンテナーとしてデプロイできます。 これは、セットアップと構成手順の概要を示します。

- 1 つの VM、Vm、または Azure Kubernetes Service (AKS) クラスター上の Kubernetes クラスターを設定します。
- クラスターの構成ツールをインストール**mssqlctl**クライアント コンピューターにします。
- Kubernetes クラスターで SQL Server のビッグ データ クラスターをデプロイします。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="prereqs"></a> Kubernetes クラスターの前提条件

ビッグ データの SQL Server クラスターの最小 Kubernetes バージョンが少なくとも必要 v1.10 サーバーおよびクライアント (kubectl) の両方。

> [!NOTE]
> クライアントとサーバーの Kubernetes のバージョンで +1 または-1 のマイナー バージョンがあることに注意してください。 詳細については、次を参照してください。 [Kubernetes がサポートされるのは、リリースと傾斜コンポーネント](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew)します。

## <a id="kubernetes"></a> Kubernetes クラスターのセットアップ

上記の前提条件を満たしている Kubernetes クラスターが既にある場合に直接進んで、[配置手順](#deploy)します。 このセクションでは、Kubernetes の概念の基本的な知識を前提とします。  Kubernetes の詳細については、次を参照してください。、 [Kubernetes のドキュメント](https://kubernetes.io/docs/home)します。

3 つの方法のいずれかでの Kubernetes にデプロイすることができます。

| Kubernetes をデプロイします。 | 説明 | リンク |
|---|---|---|
| **Minikube** | VM で単一ノードの Kubernetes クラスター。 | [手順](deploy-on-minikube.md) |
| **Azure Kubernetes サービス (AKS)** | Azure の managed Kubernetes コンテナー サービスです。 | [手順](deploy-on-aks.md) |
| **複数のマシン** | 物理マシンまたはを使用して仮想マシンにデプロイされる Kubernetes クラスター **kubeadm** | [手順](deploy-with-kubeadm.md) |
  
> [!TIP]
> AKS と SQL Server の両方のビッグ データ クラスターをデプロイするサンプル python スクリプトについては、次を参照してください。[ビッグ データ クラスター Azure Kubernetes Service (AKS) で SQL Server 展開](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks)します。

## <a name="deploy-sql-server-2019-big-data-tools"></a>SQL Server 2019 ビッグ データ ツールを展開します。

まず、SQL Server 2019 ビッグ データ クラスターをデプロイする前に[ビッグ データ ツールをインストール](deploy-big-data-tools.md):
- **mssqlctl**
- **kubectl**
- **Azure Data Studio**
- **SQL Server 2019 の拡張機能**

## <a id="deploy"></a> SQL Server のビッグ データ クラスターをデプロイします。

Kubernetes クラスターを構成した後は、SQL Server のビッグ データ クラスターの配置を続行することができます。 

> [!NOTE]
> 以前のリリースからアップグレードする場合を参照してください、[この記事の「アップグレード](#upgrade)します。

開発/テスト環境のすべての既定の構成で Azure でビッグ データ クラスターをデプロイするには、この記事の手順に従います。

[クイック スタート:Kubernetes での SQL Server ビッグ データ クラスターをデプロイします。](quickstart-big-data-cluster-deploy.md)

場合、ワークロードに合わせて、ビッグ データ クラスターの展開をカスタマイズする必要が、この記事の残りの指示に従います。

## <a name="verify-kubernetes-configuration"></a>Kubernetes 構成を確認します。

実行、 **kubectl**クラスター構成を表示するコマンド。 その kubectl が適切なクラスター コンテキストを指すことを確認します。

```bash
kubectl config view
```

## <a name="define-environment-variables"></a>環境変数を定義します。

渡される環境変数のセットを使用して、クラスター構成をカスタマイズすることができます、`mssqlctl create cluster`コマンド。 環境変数のほとんどは、以下に従って既定値を持つ省略可能です。 資格情報をユーザー入力を必要とするように環境変数があることに注意してください。

| 環境変数 | 必須 | 既定値 | 説明 |
|---|---|---|---|
| **ACCEPT_EULA** | はい | なし | SQL Server のライセンス契約 (たとえば、"Y") をそのまま使用します。  |
| **CLUSTER_NAME** | はい | なし | SQLServer にビッグ データのクラスターをデプロイする Kubernetes 名前空間の名前。 |
| **CLUSTER_PLATFORM** | はい | なし | Kubernetes クラスターが展開されているプラットフォームです。 `aks`、 `minikube`、 `kubernetes`|
| **CLUSTER_COMPUTE_POOL_REPLICAS** | いいえ | 1 | 構築するためのコンピューティング プールのレプリカの数。CTP 2.2 の値のみが許可されている、1 です。 |
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
>1. 特殊文字が含まれている場合、二重引用符で囲まれた、パスワードをラップすることを確認します。 MSSQL_SA_PASSWORD を任意に設定できますが必ず、十分に複雑な使用しないでください、 `!`、`&`または`'`文字。 コマンドの bash でのみ二重引用符区切り記号の動作に注意してください。
>1. クラスターの名前は小文字英数字文字、空白のみである必要があります。 すべての Kubernetes ・ アーティファクト (コンテナー、ポッド、ステートフルのセット、サービスなど)、クラスターのクラスターと同じ名前を持つ名前空間に作成されます名を指定します。
>1. **SA**アカウントは、システム管理者は、セットアップ中に作成される SQL Server マスター インスタンス。 実行して探索可能なは、MSSQL_SA_PASSWORD 環境変数を指定した、SQL Server のコンテナーを作成した後は、コンテナー内の $MSSQL_SA_PASSWORD をエコーします。 セキュリティのために、文書化のベスト プラクティスに従って、SA のパスワードを変更する[ここ](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password)します。

ビッグ データ クラスターを展開するために必要な環境変数の設定は、Windows または Linux クライアントを使用しているかどうかによって異なります。  使用しているオペレーティング システムに応じて次の手順を選択します。

次の環境変数を初期化、クラスターをデプロイに必要な場合。

### <a name="windows"></a>Windows

コマンド ウィンドウ (PowerShell ではなく) を使用して、次の環境変数を構成します。 値を囲む引用符は使用しないでください。

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=<minikube or aks or kubernetes>

SET CONTROLLER_USERNAME=<controller_admin_name - can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password - can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password - can be anything, password complexity compliant>
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

export CONTROLLER_USERNAME="<controller_admin_name - can be anything>"
export CONTROLLER_PASSWORD="<controller_admin_password - can be anything, password complexity compliant>"
export KNOX_PASSWORD="<knox_password - can be anything, password complexity compliant>"
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
mssqlctl create cluster <your-cluster-name>
```

クラスターのブートス トラップ中には、クライアントのコマンド ウィンドウが展開ステータスを出力します。 展開プロセス中には、コント ローラーのポッドの待機中は、一連のメッセージ表示されます。

```output
2018-11-15 15:42:02.0209 UTC | INFO | Waiting for controller pod to be up...
```

10 ~ 20 分後に、コント ローラーのポッドが実行されていることが通知する必要があります。

```output
2018-11-15 15:50:50.0300 UTC | INFO | Controller pod is running.
2018-11-15 15:50:50.0585 UTC | INFO | Controller Endpoint: https://111.222.222.222:30080
```

> [!IMPORTANT]
> デプロイ全体のビッグ データ クラスター コンポーネントのコンテナー イメージをダウンロードするために必要な時間のため時間がかかることができます。 ただし、いくつかの時間はなりません。 デプロイに関する問題が発生する場合を参照してください、[トラブルシューティング](#troubleshoot)を監視して、展開を検査する方法については、この記事の「します。

デプロイが完了したら、出力では、成功のにより通知されます。

```output
2018-11-15 16:10:25.0583 UTC | INFO | Cluster state: Ready
2018-11-15 16:10:25.0583 UTC | INFO | Cluster deployed successfully.
```

## <a id="masterip"></a> SQL Server マスター インスタンスと SQL Server のビッグ データ クラスター IP アドレスを取得します。

配置スクリプトが正常に完了したら、次の手順を使用して、SQL Server マスター インスタンスの IP アドレスを取得できます。 この IP アドレスとポート番号 31433 master の SQL Server インスタンスへの接続に使用する (例:  **\<ip アドレス\>31433、**)。 同様に、SQL Server のビッグ データ クラスターの IP を実行します。 クラスターの管理ポータルもサービス エンドポイント タブでは、クラスターのすべてのエンドポイントが記載されています。 クラスターの管理ポータルを使用すると、展開を監視します。 外部 IP アドレスとポート番号を使用してポータルにアクセスすることができます、 `service-proxy-lb` (例: **https://\<ip アドレス\>: 30777/ポータル**)。 値の管理ポータルにアクセスするための資格情報`CONTROLLER_USERNAME`と`CONTROLLER_PASSWORD`上で指定した環境変数。

### <a name="aks"></a>AKS

AKS を使用している場合、Azure は、Azure ロード バランサーのサービスを提供します。 次のコマンドを実行します。

```bash
kubectl get svc endpoint-master-pool -n <your-cluster-name>
kubectl get svc service-security-lb -n <your-cluster-name>
kubectl get svc service-proxy-lb -n <your-cluster-name>
```

探して、 **EXTERNAL-IP**サービスに割り当てられている値。 ポート 31433 で IP アドレスを使用して、SQL Server マスター インスタンスに接続し (例:  **\<ip アドレス\>31433、**) との外部 ip アドレスを使用して SQL Server ビッグ データ クラスター エンドポイントに`service-security-lb`サービス。 

### <a name="minikube"></a>Minikube

Minikube を使用している場合に接続する必要がある IP アドレスを取得する次のコマンドを実行する必要があります。 だけでなく、IP への接続に必要なエンドポイントのポートを指定します。 すべてのサービス エンドポイントを取得するには 

```bash
minikube ip
```

プラットフォームに関係なく、Kubernetes クラスターを実行するクラスター、次のコマンド用にデプロイされたすべてのサービス エンドポイントを取得する、実行されます。
```bash
kubectl get svc -n <your-cluster-name>
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
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.2 mssqlctl
   ```

   > [!IMPORTANT]
   > 各リリースへのパス**mssqlctl**変更します。 以前にインストールした場合でも**mssqlctl**、新しいクラスターを作成する前に最新のパスから再インストールする必要があります。

1. 」の手順に従って、最新リリースをインストール、[セクションを展開](#deploy)に改訂された記事。 

## <a id="troubleshoot"></a> 監視とトラブルシューティング

デプロイのトラブルシューティングまたは監視を使用**kubectl**クラスターの状態を検査し、潜在的な問題を検出します。 デプロイ中にいつでも次のテストを実行する別のコマンド ウィンドウを開くことができます。

1. クラスターのポッドの状態を検査します。

   ```cmd
   kubectl get pods -n <your-cluster-name>
   ```

   ポッド数、展開中に、**状態**の**ContainerCreating**も起動します。 何らかの理由で、展開がハングした場合このことができますが理解できる問題があります。 見ても、**準備**列。 これは、コンテナーの数が、pod で開始します。 展開が、構成とネットワークによって 30 分以上かかることができることに注意してください。 この時間の大半はさまざまなコンポーネントのコンテナー イメージのダウンロードに費やされました。 次の表では、デプロイ中に 2 つのコンテナーの編集の例の出力を示します。

   ```output
   PS C:\> kubectl get pods -n sbdc8
   NAME                                     READY   STATUS              RESTARTS   AGE
   mssql-controller-h79ft                   4/4     Running             0          13m
   mssql-storage-pool-default-0             0/7     ContainerCreating   0          6m
   ```

1. 詳細については、個々 のポッドをについて説明します。 次のコマンドを検査、 `mssql-storage-pool-default-0` pod です。

   ```cmd
   kubectl describe pod mssql-storage-pool-default-0 -n <your-cluster-name>
   ```

   これにより、最近のイベントを含む、ポッドに関する詳細情報が出力されます。 エラーが発生した場合は、ここでエラーがあることができます。

1. あるポッドで実行されているコンテナーのログを取得します。 次のコマンドは、という名前のポッドで実行されているすべてのコンテナーのログを取得`mssql-storage-pool-default-0`名前のファイルに出力して`pod-logs.txt`:

   ```cmd
   kubectl logs mssql-storage-pool-default-0 --all-containers=true -n <your-cluster-name> > pod-logs.txt
   ```

1. 次のコマンドを使用した展開の前後には、クラスター サービスを確認します。

   ```cmd
   kubectl get svc -n <your-cluster-name>
   ```

   これらのサービスでは、ビッグ データ クラスターへの内部および外部接続をサポートします。 外部接続は、次のサービスが使用されます。

   | サービス | 説明 |
   |---|---|
   | **エンドポイントでマスター-プール** | マスター インスタンスへのアクセスを提供します。<br/>(**EXTERNAL-IP、31433**と**SA**ユーザー) |
   | **サービス mssql コント ローラー lb**<br/>**サービス mssql コント ローラー nodeport** | ツールと、クラスターを管理するクライアントをサポートしています。 |
   | **サービス プロキシ-lb**<br/>**サービスのプロキシ-nodeport** | アクセスできるように、[クラスター管理ポータル](cluster-admin-portal.md)します。<br/>(https://**EXTERNAL-IP**: 30777/ポータル)|
   | **サービス-セキュリティ-lb**<br/>**サービス-セキュリティ-nodeport** | HDFS/Spark ゲートウェイへのアクセスを提供します。<br/>(**EXTERNAL-IP**と**ルート**ユーザー) |

   > [!NOTE]
   > サービス名は、Kubernetes 環境によって異なります。 Azure Kubernetes Service (AKS) をデプロイするときに、サービス名が終わる**lb**します。サービス名が終わる minikube と kubeadm 展開で **- nodeport**します。

1. 使用して、[クラスター管理ポータル](cluster-admin-portal.md)で展開を監視するため、**展開**タブ。待機しなければ、**サービス プロキシ-lb**展開の開始時に利用できないようにするために、このポータルにアクセスする前に開始するサービス。

> [!TIP]
> クラスターのトラブルシューティングの詳細については、次を参照してください。[監視とトラブルシューティングのビッグ データの SQL Server クラスターの Kubectl コマンド](cluster-troubleshooting-commands.md)します。

## <a name="next-steps"></a>次の手順

新しい機能のいくつかごお試しください[SQL Server 2019 プレビューで notebook を使用する方法](notebooks-guidance.md)します。
