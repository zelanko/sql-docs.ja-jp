---
title: 展開のガイダンス
titleSuffix: SQL Server big data clusters
description: Kubernetes で SQL Server 2019 ビッグデータクラスター (プレビュー) をデプロイする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e6f2eefd37c45753e3051722448b80d88712df26
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419422"
---
# <a name="how-to-deploy-sql-server-big-data-clusters-on-kubernetes"></a>Kubernetes にビッグデータクラスター SQL Server デプロイする方法

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

SQL Server ビッグデータクラスターは、Kubernetes クラスター上の docker コンテナーとしてデプロイされます。 ここでは、セットアップと構成の手順の概要を説明します。

- 1つの VM、Vm のクラスター、または Azure Kubernetes Service (AKS) で、Kubernetes クラスターを設定します。
- クライアントコンピューターにクラスター構成ツールの**azdata**をインストールします。
- Kubernetes クラスターに SQL Server ビッグデータクラスターをデプロイします。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="install-sql-server-2019-big-data-tools"></a>SQL Server 2019 ビッグデータツールのインストール

SQL Server 2019 ビッグデータクラスターをデプロイする前に、まず[ビッグデータツールをインストール](deploy-big-data-tools.md)します。

- **azdata**
- **kubectl**
- **Azure Data Studio**
- **SQL Server 2019 拡張機能**

## <a id="prereqs"></a>Kubernetes の前提条件

ビッグデータクラスター SQL Server は、サーバーとクライアント (kubectl) の両方に対して、少なくとも v 1.10 の最小 Kubernetes バージョンが必要です。

> [!NOTE]
> クライアントとサーバーの Kubernetes のバージョンは、+ 1 または-1 のマイナーバージョンの範囲内である必要があることに注意してください。 詳細については、「 [Kubernetes release note and version SKEW SKU policy](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew)」を参照してください。

### <a id="kubernetes"></a>クラスターセットアップの Kubernetes

上記の前提条件を満たす Kubernetes クラスターを既にお持ちの場合は、[デプロイの手順](#deploy)に直接進むことができます。 このセクションでは、Kubernetes の概念についての基本的な理解を前提としています。  Kubernetes の詳細については、 [Kubernetes のドキュメント](https://kubernetes.io/docs/home)を参照してください。

次の3つの方法のいずれかで Kubernetes を展開することを選択できます。

| Kubernetes を展開する: | 説明 | リンク |
|---|---|---|
| **Azure Kubernetes Services (AKS)** | Azure の管理された Kubernetes container service。 | [マニュアル](deploy-on-aks.md) |
| **複数のコンピューター (kubeadm)** | **Kubeadm**を使用して物理マシンまたは仮想マシンにデプロイされた Kubernetes クラスター | [マニュアル](deploy-with-kubeadm.md) |
| **Minikube** | VM 内の単一ノード Kubernetes クラスター。 | [マニュアル](deploy-on-minikube.md) |

> [!TIP]
> AKS と SQL Server ビッグデータクラスターの両方を1回の手順でデプロイするサンプル python スクリプトに[ついては、「クイックスタート:SQL Server ビッグデータクラスターを Azure Kubernetes Service (AKS)](quickstart-big-data-cluster-deploy.md)にデプロイします。

### <a name="verify-kubernetes-configuration"></a>Kubernetes の構成を確認する

クラスター構成を表示するには、 **kubectl**コマンドを実行します。 Kubectl が正しいクラスターコンテキストを指していることを確認します。

```bash
kubectl config view
```

Kubernetes クラスターを構成したら、新しい SQL Server ビッグデータクラスターのデプロイに進むことができます。 以前のリリースからアップグレードする場合は、「[ビッグデータクラスター SQL Server アップグレードする方法](deployment-upgrade.md)」を参照してください。

## <a id="deploy"></a>展開の概要

ビッグデータクラスターのほとんどの設定は、JSON 展開構成ファイルで定義されています。 AKS、 `kubeadm`、また`minikube`はの既定の展開プロファイルを使用することも、セットアップ中に使用する独自の展開構成ファイルをカスタマイズすることもできます。 セキュリティ上の理由から、認証設定は環境変数を介して渡されます。

次のセクションでは、ビッグデータクラスターの展開を構成する方法と、一般的なカスタマイズの例について詳しく説明します。 また、VS Code などのエディターを使用して、カスタムデプロイ構成ファイルをいつでも編集できます。

## <a id="configfile"></a>既定の構成

ビッグデータクラスターのデプロイオプションは、JSON 構成ファイルで定義されています。 開発/テスト環境の既定の設定では、3つの標準デプロイプロファイルがあります。

| 展開プロファイル | Kubernetes 環境 |
|---|---|
| **aks** | Azure Kubernetes サービス (AKS) |
| **kubeadm** | 複数のコンピューター (kubeadm) |
| **minikube-dev-test** | Minikube |

ビッグデータクラスターをデプロイするには、 **azdata bdc create**を実行します。 これにより、既定の構成のいずれかを選択するよう求められます。その後、展開を順を追って説明します。

を初めて実行`azdata`するときは、使用許諾契約書 (EULA) に同意するためにを含める`--accept-eula`必要があります。

```bash
azdata bdc create --accept-eula
```

このシナリオでは、パスワードなど、既定の構成の一部ではない設定を入力するように求められます。 

> [!NOTE]
> SQL Server 2019 CTP 3.2 以降では、ビッグデータクラスターのプレビューリリースを体験するために、SQL Server 2019[早期導入プログラム](https://aka.ms/eapsignup)に対するメンバーではなくなりました。

> [!IMPORTANT]
> ビッグデータクラスターの既定の名前は**mssql-cluster**です。 このことは、 `-n`パラメーターを使用して Kubernetes 名前空間を指定する**kubectl**コマンドを実行するために重要です。

## <a id="customconfig"></a>カスタム構成

また、独自の展開構成プロファイルをカスタマイズすることもできます。 これを行うには、次の手順を実行します。

1. Kubernetes 環境に一致する標準の展開プロファイルの1つを使用して開始します。 **Azdata bdc の [構成リスト**] コマンドを使用して、これらの一覧を表示できます。

   ```bash
   azdata bdc config list
   ```

1. デプロイをカスタマイズするには、 **azdata bdc config init**コマンドを使用して、デプロイプロファイルのコピーを作成します。 たとえば、次のコマンドは、 **aks**展開構成ファイルのコピーをという名前`custom`のターゲットディレクトリに作成します。

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

   azdata
   > は`--target` 、 `--source`パラメーターに基づいて、構成ファイル ( **cluster. json**と**control. json**) を含むディレクトリを指定します。

1. 展開構成プロファイルの設定をカスタマイズするには、VS Code などの JSON ファイルの編集に適したツールで展開構成ファイルを編集します。 スクリプト化された自動化では、 **azdata bdc config**コマンドを使用してカスタムデプロイプロファイルを編集することもできます。 たとえば、次のコマンドは、デプロイされたクラスターの名前を既定 (**mssql クラスター**) から**テストクラスター**に変更するために、カスタムデプロイプロファイルを変更します。  

   ```bash
   azdata bdc config replace --config-file custom/cluster.json --json-values "metadata.name=test-cluster"
   ```

   > JSON パスを検索するための便利なツールは、 [Jsonpath Online エバリュエーター](https://jsonpath.com/)です。

   キーと値のペアを渡すだけでなく、インライン JSON 値を指定したり、JSON 修正プログラムファイルを渡したりすることもできます。 詳細については、「[ビッグデータクラスターの展開設定を構成する](deployment-custom-configuration.md)」を参照してください。

1. 次に、カスタム構成ファイルを**azdata bdc create**に渡します。 必要な[環境変数](#env)を設定する必要があることに注意してください。そうしないと、値の入力を求められます。

   ```bash
   azdata bdc create --config-profile custom --accept-eula yes
   ```

> 展開構成ファイルの構造の詳細については、「[展開構成ファイルのリファレンス](reference-deployment-config.md)」を参照してください。 構成例の詳細については、「[ビッグデータクラスターの展開設定を構成する](deployment-custom-configuration.md)」を参照してください。

## <a id="env"></a>環境変数

次の環境変数は、展開構成ファイルに格納されていないセキュリティ設定に使用されます。 資格情報以外の Docker 設定は、構成ファイルで設定できることに注意してください。

| 環境変数 | 要件 |説明 |
|---|---|---|
| **CONTROLLER_USERNAME** | 必須 |クラスター管理者のユーザー名。 |
| **CONTROLLER_PASSWORD** | 必須 |クラスター管理者のパスワード。 |
| **MSSQL_SA_PASSWORD** | 必須 |SQL master インスタンスの SA ユーザーのパスワード。 |
| **KNOX_PASSWORD** | 必須 |Knox ユーザーのパスワード。 |
| **ACCEPT_EULA**| 最初の使用に必要`azdata`| 値は必要ありません。 環境変数として設定すると、SQL Server と`azdata`の両方に EULA が適用されます。 環境変数として設定されてい`--accept-eula`ない場合は、コマンド`azdata`の最初の使用にを含めることができます。|
| **DOCKER_USERNAME** | 省略可 | プライベートリポジトリに格納されている場合に、コンテナーイメージにアクセスするためのユーザー名。 ビッグデータクラスターの展開にプライベート Docker リポジトリを使用する方法の詳細については、「[オフライン展開](deploy-offline.md)」を参照してください。|
| **DOCKER_PASSWORD** | Optional |上記のプライベートリポジトリにアクセスするためのパスワード。 |

**Azdata bdc create**を呼び出す前に、これらの環境変数を設定する必要があります。 変数が設定されていない場合は、そのことを求めるメッセージが表示されます。

次の例は、Linux (bash) と Windows (PowerShell) の環境変数を設定する方法を示しています。

```bash
export CONTROLLER_USERNAME=admin
export CONTROLLER_PASSWORD=<password>
export MSSQL_SA_PASSWORD=<password>
export KNOX_PASSWORD=<password>
```

```PowerShell
SET CONTROLLER_USERNAME=admin
SET CONTROLLER_PASSWORD=<password>
SET MSSQL_SA_PASSWORD=<password>
SET KNOX_PASSWORD=<password>
```

環境変数を設定したら、を実行`azdata bdc create`して配置をトリガーする必要があります。 この例では、上記で作成したクラスター構成プロファイルを使用します。

```bash
azdata bdc create --config-profile custom --accept-eula yes
```

次のガイドラインに注意してください。

- 特殊文字が含まれている場合は、パスワードを二重引用符で囲む必要があります。 **MSSQL_SA_PASSWORD**は自由に設定できますが、パスワードが十分に複雑で`!`、、、 `&`または`'`文字を使用しないようにしてください。 二重引用符の区切り記号は bash コマンドでのみ機能することに注意してください。
- **SA**ログインは、セットアップ中に作成される SQL Server master インスタンスのシステム管理者です。 SQL Server コンテナーを作成した後は、コンテナーでを実行`echo $MSSQL_SA_PASSWORD`することで、指定した MSSQL_SA_PASSWORD 環境変数を検出できます。 セキュリティ上の理由から、[ここ](../linux/quickstart-install-connect-docker.md#sapassword)に記載されているベストプラクティスに従って、SA パスワードを変更してください。

## <a id="unattended"></a>無人インストール

無人展開の場合は、必要なすべての環境変数を設定し、構成ファイルを使用`azdata bdc create`して、 `--accept-eula yes`パラメーターを指定して command を呼び出す必要があります。 前のセクションの例では、無人インストールの構文を示します。

## <a id="monitor"></a>展開を監視する

クラスターのブートストラップ中に、クライアントのコマンドウィンドウによって展開の状態が出力されます。 デプロイプロセス中に、コントローラーポッドを待機している一連のメッセージが表示されます。

```output
Waiting for cluster controller to start.
```

15 ~ 30 分で、コントローラーポッドが実行されていることが通知されます。

```output
Cluster controller endpoint is available at 11.111.111.11:30080.
Cluster control plane is ready.
```

> [!IMPORTANT]
> ビッグデータクラスターのコンポーネントのコンテナーイメージをダウンロードするために必要な時間によって、デプロイ全体に時間がかかることがあります。 ただし、数時間かかることはありません。 デプロイで問題が発生した場合は、「 [SQL Server ビッグデータクラスターの監視とトラブルシューティング](cluster-troubleshooting-commands.md)」を参照してください。

デプロイが完了すると、出力は成功したことを通知します。

```output
Cluster deployed successfully.
```

> [!TIP]
> デプロイされたビッグデータクラスターの既定の`mssql-cluster`名前は、カスタム構成によって変更された場合を除きます。

## <a id="endpoints"></a>エンドポイントを取得する

デプロイスクリプトが正常に完了したら、次の手順に従って、ビッグデータクラスターの外部エンドポイントの IP アドレスを取得できます。

1. デプロイ後、デプロイの標準出力から、または次の**kubectl**コマンドの外部 ip 出力を見て、コントローラーエンドポイントの ip アドレスを検索します。

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > デプロイ中に既定の名前を変更しなかった場合`-n mssql-cluster`は、前のコマンドでを使用します。 " **mssql クラスター** " は、ビッグデータクラスターの既定の名前です。

1. [Azdata ログイン](reference-azdata.md)を使用してビッグデータクラスターにログインします。 **--Controller-endpoint**パラメーターをコントローラーエンドポイントの外部 IP アドレスに設定します。

   ```bash
   azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   デプロイ中にコントローラー (CONTROLLER_USERNAME と CONTROLLER_PASSWORD) に対して構成したユーザー名とパスワードを指定します。

1. [Azdata bdc エンドポイントリスト](reference-azdata-bdc-endpoint.md)を実行して、各エンドポイントの説明とそれに対応する IP アドレスとポート値を一覧表示します。 

   ```bash
   azdata bdc endpoint list -o table
   ```

   次の一覧に、このコマンドからの出力例を示します。

   ```output
   Description                                             Endpoint                                                   Ip              Name               Port    Protocol
   ------------------------------------------------------  ---------------------------------------------------------  --------------  -----------------  ------  ----------
   Gateway to access HDFS files, Spark                     https://11.111.111.111:30443                               11.111.111.111  gateway            30443   https
   Spark Jobs Management and Monitoring Dashboard          https://11.111.111.111:30443/gateway/default/sparkhistory  11.111.111.111  spark-history      30443   https
   Spark Diagnostics and Monitoring Dashboard              https://11.111.111.111:30443/gateway/default/yarn          11.111.111.111  yarn-ui            30443   https
   Application Proxy                                       https://11.111.111.111:30778                               11.111.111.111  app-proxy          30778   https
   Management Proxy                                        https://11.111.111.111:30777                               11.111.111.111  mgmtproxy          30777   https
   Log Search Dashboard                                    https://11.111.111.111:30777/kibana                        11.111.111.111  logsui             30777   https
   Metrics Dashboard                                       https://11.111.111.111:30777/grafana                       11.111.111.111  metricsui          30777   https
   Cluster Management Service                              https://11.111.111.111:30080                               11.111.111.111  controller         30080   https
   SQL Server Master Instance Front-End                    11.111.111.111,31433                                       11.111.111.111  sql-server-master  31433   tcp
   HDFS File System Proxy                                  https://11.111.111.111:30443/gateway/default/webhdfs/v1    11.111.111.111  webhdfs            30443   https
   Proxy for running Spark statements, jobs, applications  https://11.111.111.111:30443/gateway/default/livy/v1       11.111.111.111  livy               30443   https
   ```

次の**kubectl**コマンドを実行して、クラスターにデプロイされているすべてのサービスエンドポイントを取得することもできます。

```bash
kubectl get svc -n <your-big-data-cluster-name>
```

### <a name="minikube"></a>Minikube

Minikube を使用している場合は、次のコマンドを実行して、接続に必要な IP アドレスを取得する必要があります。 IP に加えて、接続に必要なエンドポイントのポートを指定します。

```bash
minikube ip
```

## <a id="status"></a>クラスターの状態を確認する

デプロイ後、 [azdata bdc status show](reference-azdata-bdc-status.md)コマンドを使用して、クラスターの状態を確認できます。

```bash
azdata bdc status show -o table
```

> [!TIP]
> Status コマンドを実行するには、最初に、前の「エンドポイント」セクションで示した**azdata login**コマンドを使用してログインする必要があります。

このコマンドからの出力例を次に示します。

```output
Kind     Name           State
-------  -------------  -------
BDC      mssql-cluster  Ready
Control  default        Ready
Master   default        Ready
Compute  default        Ready
Data     default        Ready
Storage  default        Ready
```

この概要ステータスには、次のコマンドを使用して詳細な状態を取得することもできます。

- [azdata bdc コントロールの状態](reference-azdata-bdc-control-status.md)
- [azdata bdc プールの状態](reference-azdata-bdc-pool-status.md)

これらのコマンドからの出力には、より詳細な分析を行うための Kibana および Grafana ダッシュボードへの Url が含まれています。

**Azdata**を使用するだけでなく、Azure Data Studio を使用してエンドポイントとステータス情報の両方を検索することもできます。 **Azdata**および Azure Data Studio でクラスターの状態を表示する方法の詳細については、「[ビッグデータクラスターの状態を表示する方法](view-cluster-status.md)」を参照してください。

## <a id="connect"></a>クラスターに接続する

ビッグデータクラスターに接続する方法の詳細については、「Azure Data Studio を使用した[SQL Server ビッグデータクラスターへの接続](connect-to-big-data-cluster.md)」を参照してください。

## <a name="next-steps"></a>次の手順

ビッグデータクラスターの展開の詳細については、次のリソースを参照してください。

- [ビッグデータクラスターの展開設定を構成する](deployment-custom-configuration.md)
- [SQL Server ビッグデータクラスターのオフライン展開を実行する](deploy-offline.md)
- [ワークショップビッグデータクラスターのアーキテクチャの Microsoft SQL Server](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
