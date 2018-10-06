---
title: SQL Server のビッグ データ クラスターのデプロイ |Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: quickstart
ms.prod: sql
ms.openlocfilehash: e44e6588cb58148c1474bc9e5ddda7527737ebba
ms.sourcegitcommit: 8aecafdaaee615b4cd0a9889f5721b1c7b13e160
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2018
ms.locfileid: "48817990"
---
# <a name="quickstart-deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>クイック スタート: Azure Kubernetes Service (AKS) での SQL Server のビッグ データ クラスターをデプロイします。

このクイック スタートでは、開発/テスト環境に適した既定の構成で AKS でビッグ データの SQL Server クラスターをインストールします。 SQL マスター インスタンスに加えてプール インスタンスを 1 つのコンピューティング、プールのインスタンスを 1 つのデータおよび記憶域プールの 2 つのインスタンスには、クラスターが含まれます。 AKS の既定のストレージ クラスの上にプロビジョニングされている Kubernetes 永続ボリュームを使用してデータを永続化されます。 [デプロイ ガイダンス](deployment-guidance.md)トピックをさらに、構成をカスタマイズに使用できる環境変数のセットを見つけることができます。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>前提条件

このクイック スタートでは、v1.10 の最小バージョンと、AKS クラスターが既に構成されている必要があります。 詳細については、次を参照してください。、 [AKS にデプロイ](deploy-on-aks.md)ガイド。

SQL Server のビッグ データ クラスターをインストールするコマンドを実行しているコンピューターにインストールする必要があります。 [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)します。 SQL Server のビッグ データ クラスターでは、kubernetes では、サーバーとクライアント (kubectl) の両方で、最小の 1.10 バージョンが必要です。 Kubectl をインストールするを参照してください。 [kubectl のインストール](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl)します。 

インストールする、 `mssqlctl` SQL Server のビッグ データを管理するための CLI ツールは、クライアント コンピューターのクラスター、最初にインストールする必要があります[Python](https://www.python.org/downloads/) v3.0 の最小バージョンと[pip3](https://pip.pypa.io/en/stable/installing/)します。 ダウンロードした 3.4 以上での Python バージョンを使用している場合、pip が既にインストールされているに注意してください。 [python.org](https://www.python.org/)します。

Python のインストール環境がない場合、`requests`パッケージをインストールする必要がある`requests`を使用して`python -m pip install requests`。 既にある場合、`requests`パッケージが最新バージョンを使用するアップグレード`python -m pip install requests --upgrade`します。

## <a name="verify-aks-configuration"></a>AKS の構成を確認します。

実行することができます、AKS クラスターをデプロイした後、次の kubectl コマンドをクラスター構成を表示します。 その kubectl が適切なクラスター コンテキストを指すことを確認します。

```bash
kubectl config view
```

## <a name="install-mssqlctl-cli-management-tool"></a>Mssqlctl CLI 管理ツールをインストールします。

次のコマンドをインストールする実行`mssqlctl`クライアント コンピューターにツール。 Windows と Linux クライアントの両方からのコマンドが Windows で管理者権限で実行されているコマンド ウィンドウから実行しているか、先頭に使用するかどうかを必ず同じ`sudo`on Linux:

```
pip3 install --index-url https://private-repo.microsoft.com/python/ctp-2.0 mssqlctl  
```

## <a name="define-environment-variables"></a>環境変数を定義します。

少しビッグ データ クラスターをデプロイするために必要な環境変数の設定は、Windows または Linux と macOS のクライアントを使用しているかどうかによって異なります。  使用しているオペレーティング システムに応じて次の手順を選択します。

> [!IMPORTANT]
> 特殊文字が含まれている場合、二重引用符で囲まれた、パスワードをラップすることを確認します。 コマンドの bash でのみ二重引用符区切り記号の動作に注意してください。
>
> 任意に、パスワード、環境変数を設定できますが必ず、十分に複雑な使用しないでください、 `!`、 `&`、または`‘`文字。

[!IMPORTANT]
**SA**アカウントは、システム管理者は、セットアップ中に作成される SQL Server マスター インスタンス。 実行して探索可能なは、MSSQL_SA_PASSWORD 環境変数を指定した、SQL Server のコンテナーを作成した後は、コンテナー内の $MSSQL_SA_PASSWORD をエコーします。 セキュリティのために、文書化のベスト プラクティスに従って、SA のパスワードを変更する[ここ](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password)します。


> [!NOTE]
> CTP 2.0 のリリースでは、既定のポートは変更されません。

次の環境変数を初期化します。  ビッグ データ クラスターのデプロイに必要な。

### <a name="windows"></a>Windows

コマンド ウィンドウ (PowerShell ではなく) を使用して、次の環境変数を構成します。

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=aks

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

### <a name="linuxmacos"></a>Linux と macOS

次の環境変数を初期化します。

```bash
export ACCEPT_EULA=Y
export CLUSTER_PLATFORM=aks

export CONTROLLER_USERNAME=<controller_admin_name – can be anything>
export CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
export KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
export MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

export DOCKER_REGISTRY=private-repo.microsoft.com
export DOCKER_REPOSITORY=mssql-private-preview
export DOCKER_USERNAME=<your username, credentials provided by Microsoft>
export DOCKER_PASSWORD=<your password, credentials provided by Microsoft>
export DOCKER_EMAIL=<your Docker email, use the username provided by Microsoft>
export DOCKER_PRIVATE_REGISTRY="1"
```

> [!NOTE]
> 限定のパブリック プレビュー中に SQL Server のビッグ データ クラスターのイメージをダウンロードする Docker の資格情報は、Microsoft によって各顧客に提供されます。 アクセス権を要求するには、登録[ここ](https://aka.ms/eapsignup)、ビッグ データの SQL Server クラスターに関心を指定します。

## <a name="deploy-sql-server-big-data-cluster"></a>SQL Server のビッグ データ クラスターをデプロイします。

Kubernetes クラスターで SQL Server 2019 CTP 2.0 のビッグ データ クラスターをデプロイするには、次のコマンドを実行します。

```bash
mssqlctl create cluster <name of your cluster>
```

> [!NOTE]
> クラスターの名前は、小文字、英数字文字、スペースなしのみにする必要があります。 クラスターと同じ名前を持つ名前空間に、ビッグ データ クラスターのすべての Kubernetes の成果物を作成します。 指定された名前。


コマンド ウィンドウでは、デプロイの状態を出力します。 別のコマンド ウィンドウでこれらのコマンドを実行してデプロイの状態をチェックすることもできます。

```bash
kubectl get all -n <name of your cluster>
kubectl get pods -n <name of your cluster>
kubectl get svc -n <name of your cluster>
```

実行してより詳細な状態と各ポッドの構成を確認できます。
```bash
kubectl describe pod <pod name> -n <name of your cluster>
```

コント ローラーのポッドが実行されている展開の監視、クラスターの管理ポータルを使用できます。 外部 IP アドレスとポート番号を使用してポータルにアクセスすることができます、 `service-proxy-lb` (例: **https://\<ip アドレス\>: 30777**)。 値の管理ポータルにアクセスするための資格情報`CONTROLLER_USERNAME`と`CONTROLLER_PASSWORD`上で指定した環境変数。

Bash または cmd ウィンドウでこのコマンドを実行してサービス プロキシ-lb サービスの IP アドレスを取得できます。

```bash
kubectl get svc service-proxy-lb -n <name of your cluster>
```

> [!NOTE]
> 自動生成された SSL 証明書を使用しているため、web ページにアクセスするとき、セキュリティ警告が表示されます。 将来のリリースは、独自の署名証明書を提供する機能。
 

## <a name="connect-to-sql-server-master-instance-and-sql-server-big-data-cluster-hdfsspark-end-points"></a>SQL Server のマスター インスタンスと SQL Server ビッグ データ クラスターの HDFS/Spark 終了点への接続します。

配置スクリプトが正常に完了したら後、は、SQL Server のマスター インスタンスと、次の手順を使用して Spark/HDFS 終点の IP アドレスを取得できます。 簡単に参照のほか、クラスター管理ポータルでサービス エンドポイント セクションでは、クラスターのすべてのエンドポイントが表示されます。

Azure では、AKS の Azure ロード バランサーのサービスを提供します。 次のコマンドを cmd でを実行するか、bash ウィンドウ。

```bash
kubectl get svc service-master-pool-lb -n <name of your cluster>
kubectl get svc service-security-lb -n <name of your cluster>
```

探して、 **EXTERNAL-IP**サービスに割り当てられている値。 IP アドレスを使用して、SQL Server マスター インスタンスへの接続、`service-master-pool-lb`ポート 31433 で (例:  **\<ip アドレス\>31433、**) との外部 ip アドレスを使用して SQL Server のビッグ データ クラスター エンドポイントに、`service-security-lb`サービス。   ビッグ データ クラスター エンドポイントのことは、Knox をジョブの HDFS との対話して Spark を送信する場所です。

# <a name="next-steps"></a>次の手順

これで、SQL Server のビッグ データ クラスターをデプロイするは、いくつかの新しい機能を試してください。

> [!div class="nextstepaction"]
> [SQL Server 2019 プレビューで notebook を使用する方法](notebooks-guidance.md)
