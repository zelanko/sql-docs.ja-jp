---
title: 展開のガイダンス
titleSuffix: SQL Server big data clusters
description: Kubernetes での SQL Server 2019 ビッグ データ クラスター (プレビュー) をデプロイする方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 924d026c61275d5bc957ce1157e30381f27ef2d0
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65993984"
---
# <a name="how-to-deploy-sql-server-big-data-clusters-on-kubernetes"></a>Kubernetes での SQL Server のビッグ データ クラスターをデプロイする方法

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

SQL Server のビッグ データ クラスターは、Kubernetes クラスター上の docker コンテナーとしてデプロイされます。 これは、セットアップと構成手順の概要を示します。

- 1 つの VM、Vm、または Azure Kubernetes Service (AKS) クラスター上の Kubernetes クラスターを設定します。
- クラスターの構成ツールをインストール**mssqlctl**クライアント コンピューターにします。
- Kubernetes クラスターで SQL Server のビッグ データ クラスターをデプロイします。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="install-sql-server-2019-big-data-tools"></a>SQL Server 2019 ビッグ データ ツールをインストールします。

まず、SQL Server 2019 ビッグ データ クラスターをデプロイする前に[ビッグ データ ツールをインストール](deploy-big-data-tools.md):

- **mssqlctl**
- **kubectl**
- **Azure Data Studio**
- **SQL Server 2019 の拡張機能**

## <a id="prereqs"></a> Kubernetes の前提条件

ビッグ データの SQL Server クラスターの最小 Kubernetes バージョンが少なくとも必要 v1.10 サーバーおよびクライアント (kubectl) の両方。

> [!NOTE]
> +1 または-1 のマイナー バージョン内でクライアントとサーバーの Kubernetes バージョンがあることに注意してください。 詳細については、次を参照してください。 [Kubernetes がサポートされるのは、リリースと傾斜コンポーネント](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew)します。

### <a id="kubernetes"></a> Kubernetes クラスターのセットアップ

上記の前提条件を満たしている Kubernetes クラスターが既にある場合に直接進んで、[配置手順](#deploy)します。 このセクションでは、Kubernetes の概念の基本的な知識を前提とします。  Kubernetes の詳細については、次を参照してください。、 [Kubernetes のドキュメント](https://kubernetes.io/docs/home)します。

3 つの方法のいずれかでの Kubernetes にデプロイすることができます。

| Kubernetes をデプロイします。 | 説明 | リンク |
|---|---|---|
| **Azure Kubernetes サービス (AKS)** | Azure の managed Kubernetes コンテナー サービスです。 | [手順](deploy-on-aks.md) |
| **複数のマシン (kubeadm)** | 物理マシンまたはを使用して仮想マシンにデプロイされる Kubernetes クラスター **kubeadm** | [手順](deploy-with-kubeadm.md) |
| **Minikube** | VM で単一ノードの Kubernetes クラスター。 | [手順](deploy-on-minikube.md) |

> [!TIP]
> AKS とビッグ データ クラスターの 1 つの手順で SQL Server の両方をデプロイするサンプル python スクリプトについては、次を参照してください。[クイック スタート。ビッグ データ クラスター Azure Kubernetes Service (AKS) で SQL Server 展開](quickstart-big-data-cluster-deploy.md)します。

### <a name="verify-kubernetes-configuration"></a>Kubernetes 構成を確認します。

実行、 **kubectl**クラスター構成を表示するコマンド。 その kubectl が適切なクラスター コンテキストを指すことを確認します。

```bash
kubectl config view
```

Kubernetes クラスターを構成した後、新しい SQL Server のビッグ データ クラスターの展開を進めることができます。 以前のリリースからアップグレードする場合を参照してください[ビッグ データの SQL Server クラスターをアップグレードする方法](deployment-upgrade.md)します。

## <a id="deploy"></a> 展開の概要

CTP 2.5 以降、ほとんどのビッグ データ クラスター設定は、JSON の展開構成ファイルで定義されます。 AKS、kubeadm の展開の既定のプロファイルを使用することができますか、minikube またはするには、セットアップ時に使用する独自の展開構成ファイルをカスタマイズできます。 セキュリティ上の理由から、認証の設定は環境変数を使用して渡されます。

次のセクションでは、ビッグ データを構成する方法の詳細についてはクラスターの展開と一般的なカスタマイズの例を提供します。 また、たとえば、VSCode などのエディターを使用してカスタムの展開構成ファイルを常に編集できます。

## <a id="configfile"></a> 既定の構成

ビッグ データ クラスターのデプロイ オプションは、JSON 構成ファイルで定義されます。 開発/テスト環境の既定の設定で 3 つの標準の展開プロファイルがあります。

| デプロイ プロファイル | Kubernetes 環境 |
|---|---|
| **aks-dev-test.json** | Azure Kubernetes Service (AKS) |
| **kubeadm-dev-test.json** | 複数のマシン (kubeadm) |
| **minikube-dev-test.json** | Minikube |

実行して、ビッグ データ クラスターを展開する**mssqlctl クラスター作成**です。 これは、既定の構成のいずれかを選択するように求められますされ、展開支援いたします。

```bash
mssqlctl cluster create
```

> [!TIP]
> この例では、パスワードなどの既定の構成の一部ではないすべての設定を求められます。 Docker 情報が提供する Microsoft SQL Server の 2019 の一部として注[Early Adoption Program](https://aka.ms/eapsignup)します。

## <a id="customconfig"></a> カスタム構成

独自の展開構成ファイルをカスタマイズすることもできます。 次の手順で、これを行うことができます。

1. Kubernetes 環境に合った標準的なデプロイ プロファイルのいずれかで開始します。 使用することができます、 **mssqlctl クラスター構成一覧**それらを一覧表示するコマンド。

   ```bash
   mssqlctl cluster config list
   ```

1. デプロイをカスタマイズすると、デプロイ プロファイルのコピーを作成、 **mssqlctl クラスター構成の init**コマンド。 次のコマンドでのコピーを作成するなど、 **aks の開発-test.json**現在のディレクトリに展開構成ファイル。

   ```bash
   mssqlctl cluster config init --src aks-dev-test.json --target custom.json
   ```

1. デプロイの構成ファイルで設定をカスタマイズするには、VS Code のような json ドキュメントを編集するための適切なツールで編集できます。 スクリプト化された automation の場合、カスタム構成を使用してファイルを編集できます**mssqlctl クラスター構成セクション セット**コマンド。 次のコマンドが既定値からデプロイしたクラスターの名前を変更するカスタム構成ファイルを変更するなど、(**mssql クラスター**) に**テスト クラスター**:  

   ```bash
   mssqlctl cluster config section set --config-file custom.json --json-values "metadata.name=test-cluster"
   ```

   > [!TIP]
   > JSON のパスを検索するための便利なツールは、 [JSONPath オンライン エバリュエーター](https://jsonpath.com/)します。

   キー/値ペアを渡すだけでなくも JSON 値をインラインで指定したり、JSON の修正プログラム ファイルを渡すできます。 詳細については、次を参照してください。[ビッグ データ クラスターのデプロイ設定を構成する](deployment-custom-configuration.md)します。

1. カスタム構成ファイルを渡します**mssqlctl クラスター作成**です。 必要な設定する必要がありますに注意してください。[環境変数](#env)、それ以外の場合を求める値。

   ```bash
   mssqlctl cluster create --config-file custom.json --accept-eula yes
   ```

> [!TIP]
> 展開構成ファイルの構造の詳細については、次を参照してください。、[展開構成ファイル リファレンス](reference-deployment-config.md)します。 構成例については、次を参照してください。[ビッグ データ クラスターのデプロイ設定を構成する](deployment-custom-configuration.md)します。

## <a id="env"></a> 環境変数

次の環境変数は、展開の構成ファイルに格納されていないセキュリティ設定に使用されます。 資格情報を除く、Docker の設定を構成ファイルで設定できることに注意してください。

| 環境変数 | 説明 |
|---|---|---|---|
| **DOCKER_USERNAME** | これらはプライベート リポジトリに格納されている場合に、コンテナー イメージにアクセスするユーザー名。 |
| **DOCKER_PASSWORD** | 上記のプライベート リポジトリにアクセスするパスワード。 |
| **CONTROLLER_USERNAME** | クラスター管理者のユーザー名。 |
| **CONTROLLER_PASSWORD** | クラスター管理者のパスワード。 |
| **KNOX_PASSWORD** | Knox ユーザーのパスワード。 |
| **MSSQL_SA_PASSWORD** | SQL のマスター インスタンスの SA ユーザーのパスワードです。 |

これらの環境変数を呼び出す前に設定する必要があります**mssqlctl クラスター作成**です。 任意の変数が設定されていないことを求められます。

次の例では、Linux (bash) および Windows (PowerShell) の環境変数を設定する方法を示します。

```bash
export CONTROLLER_USERNAME=admin
export CONTROLLER_PASSWORD=<password>
export MSSQL_SA_PASSWORD=<password>
export KNOX_PASSWORD=<password>
export DOCKER_USERNAME=<docker-username>
export DOCKER_PASSWORD=<docker-password>
```

```PowerShell
SET CONTROLLER_USERNAME=admin
SET CONTROLLER_PASSWORD=<password>
SET MSSQL_SA_PASSWORD=<password>
SET KNOX_PASSWORD=<password>
SET DOCKER_USERNAME=<docker-username>
SET DOCKER_PASSWORD=<docker-password>
```

環境変数を設定したときに実行する必要があります`mssqlctl cluster create`デプロイを開始します。 この例では、上記で作成したクラスターの構成ファイルを使用します。

```
mssqlctl cluster create --config-file custom.json --accept-eula yes
```

次のガイドラインに注意してください。

- 現時点では、プライベート Docker レジストリの資格情報はお客様に提供されるトリアージすると、 [Early Adoption Program 登録](https://aka.ms/eapsignup)します。 ビッグ データの SQL Server クラスターをテストするには、Adoption Program の初期登録が必要です。
- 特殊文字が含まれている場合、二重引用符で囲まれた、パスワードをラップすることを確認します。 設定することができます、 **MSSQL_SA_PASSWORD**に内容が、パスワードが十分に複雑になっていることを確認し、使用しないでください、 `!`、`&`または`'`文字。 コマンドの bash でのみ二重引用符区切り記号の動作に注意してください。
- **SA**ログインがシステム管理者は、セットアップ時に作成される SQL Server のマスター インスタンス。 SQL Server のコンテナーを作成した後、 **MSSQL_SA_PASSWORD**を実行して、指定した環境変数が探索可能なコンテナーで $MSSQL_SA_PASSWORD をエコーします。 セキュリティのために、文書化のベスト プラクティスに従って、SA のパスワードを変更する[ここ](../linux/quickstart-install-connect-docker.md#sapassword)します。

## <a id="unattended"></a> 無人インストール

無人展開は、すべての必要な環境変数、構成ファイルを使用および呼び出しを設定する必要があります`mssqlctl cluster create`コマンドと、`--accept-eula yes`パラメーター。 前のセクションの例では、無人インストールの構文を示します。

## <a id="monitor"></a> 展開を監視します。

クラスターのブートス トラップ中には、クライアントのコマンド ウィンドウが展開ステータスを出力します。 展開プロセス中には、コント ローラーのポッドの待機中は、一連のメッセージ表示されます。

```output
2019-04-12 14:40:10.0129 UTC | INFO | Waiting for controller pod to be up...
```

、15 ~ 30 分未満では、コント ローラーのポッドが実行されていることが通知する必要があります。

```output
2019-04-12 15:01:10.0809 UTC | INFO | Waiting for controller pod to be up. Checkthe mssqlctl.log file for more details.
2019-04-12 15:01:40.0861 UTC | INFO | Controller pod is running.
2019-04-12 15:01:40.0884 UTC | INFO | Controller Endpoint: https://<ip-address>:30080
```

> [!IMPORTANT]
> デプロイ全体のビッグ データ クラスター コンポーネントのコンテナー イメージをダウンロードするために必要な時間のため時間がかかることができます。 ただし、いくつかの時間はなりません。 デプロイに関する問題が発生する場合は、次を参照してください。[監視とビッグ データの SQL Server クラスターのトラブルシューティングを行う](cluster-troubleshooting-commands.md)します。

デプロイが完了したら、出力では、成功のにより通知されます。

```output
2019-04-12 15:37:18.0271 UTC | INFO | Monitor and track your cluster at the Portal Endpoint: https://<ip-address>:30777/portal/
2019-04-12 15:37:18.0271 UTC | INFO | Cluster deployed successfully.
```

URL に注意してください、**ポータル エンドポイント**で、次のセクションで使用するため、前の出力。

> [!TIP]
> デプロイされたビッグ データ クラスターの既定の名前は`mssql-cluster`カスタム構成を変更しない限り、します。

## <a id="endpoints"></a> エンドポイントを取得します。

配置スクリプトが正常に完了したら、次の手順を使用してビッグ データ クラスターの外部エンドポイントの IP アドレスを取得できます。

1. デプロイ後、次の外部 IP の出力を調べることでコント ローラー エンドポイントの IP アドレスを見つける**kubectl**コマンド。

   ```bash
   kubectl get svc controller-svc-external -n <your-cluster-name>
   ```

1. 使用して、ビッグ データ クラスターにログイン**mssqlctl ログイン**します。 設定、 **-コント ローラー エンドポイント**コント ローラーのエンドポイントの外部 IP アドレスへのパラメーター。

   ```bash
   mssqlctl login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   デプロイ時にユーザー名とコント ローラー (CONTROLLER_USERNAME および CONTROLLER_PASSWORD) 用に構成したパスワードを指定します。

1. 実行**mssqlctl クラスター エンドポイント リスト**の各エンドポイントと対応する IP アドレスとポート値の説明の一覧を取得します。 

   ```bash
   mssqlctl cluster endpoint list
   ```

   このコマンドからの出力例を次に示します。

   ```output
   Name               Description                                             Endpoint                                                   Ip              Port    Protocol
   -----------------  ------------------------------------------------------  ---------------------------------------------------------  --------------  ------  ----------
   gateway            Gateway to access HDFS files, Spark                     https://11.111.111.111:30443                               11.111.111.111  30443   https
   spark-history      Spark Jobs Management and Monitoring Dashboard          https://11.111.111.111:30443/gateway/default/sparkhistory  11.111.111.111  30443   https
   yarn-ui            Spark Diagnostics and Monitoring Dashboard              https://11.111.111.111:30443/gateway/default/yarn          11.111.111.111  30443   https
   app-proxy          Application Proxy                                       https://11.111.111.111:30778                               11.111.111.111  30778   https
   management-proxy   Management Proxy                                        https://11.111.111.111:30777                               11.111.111.111  30777   https
   portal             Management Portal                                       https://11.111.111.111:30777/portal                        11.111.111.111  30777   https
   log-search-ui      Log Search Dashboard                                    https://11.111.111.111:30777/kibana                        11.111.111.111  30777   https
   metrics-ui         Metrics Dashboard                                       https://11.111.111.111:30777/grafana                       11.111.111.111  30777   https
   controller         Cluster Management Service                              https://11.111.111.111:30080                               11.111.111.111  30080   https
   sql-server-master  SQL Server Master Instance Front-End                    11.111.111.111,31433                                       11.111.111.111  31433   tcp
   webhdfs            HDFS File System Proxy                                  https://11.111.111.111:30443/gateway/default/webhdfs/v1    11.111.111.111  30443   https
   livy               Proxy for running Spark statements, jobs, applications  https://11.111.111.111:30443/gateway/default/livy/v1       11.111.111.111  30443   https
   ```

### <a name="minikube"></a>Minikube

Minikube を使用している場合に接続する必要がある IP アドレスを取得する次のコマンドを実行する必要があります。 だけでなく、IP への接続に必要なエンドポイントのポートを指定します。

```bash
minikube ip
```

プラットフォームに関係なく、Kubernetes クラスターを実行するクラスター、次のコマンド用にデプロイされたすべてのサービス エンドポイントを取得する、実行されます。

```bash
kubectl get svc -n <your-cluster-name>
```

## <a id="connect"></a> クラスターに接続します。

ビッグ データ クラスターに接続する方法の詳細については、次を参照してください。 [Azure データ Studio を使用した SQL Server クラスターのビッグ データへの接続](connect-to-big-data-cluster.md)します。

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターのデプロイに関する詳細については、次のリソースを参照してください。

- [ビッグ データ クラスターのデプロイ設定を構成します。](deployment-custom-configuration.md)
- [ビッグ データの SQL Server クラスターのデプロイのオフライン実行します。](deploy-offline.md)
- [ワーク ショップ:Microsoft SQL Server のビッグ データ クラスターのアーキテクチャ](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
