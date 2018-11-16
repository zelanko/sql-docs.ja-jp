---
title: SQL Server のビッグ データ クラスターのデプロイ |Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: quickstart
ms.prod: sql
ms.openlocfilehash: c25474a30ace6ed6e1ab0560f1b3746a071690ef
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51697040"
---
# <a name="quickstart-deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>クイック スタート: Azure Kubernetes Service (AKS) での SQL Server のビッグ データ クラスターをデプロイします。

AKS での開発/テスト環境に適した既定の構成でのビッグ データの SQL Server クラスターをインストールします。 SQL マスター インスタンスに加えて、クラスターには、プールのインスタンスを 1 つのコンピューティング、1 つのデータ プール インスタンス、および記憶域プールの 2 つのインスタンスが含まれています。 AKS の既定のストレージ クラスを使用する Kubernetes 永続ボリュームを使用してデータが保持されます。 さらに、構成をカスタマイズで環境変数を参照してください。[デプロイ ガイダンス](deployment-guidance.md)します。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>前提条件

このクイック スタートでは、v1.10 の最小バージョンと、AKS クラスターが既に構成されている必要があります。 詳細については、次を参照してください。、 [AKS にデプロイ](deploy-on-aks.md)ガイド。

SQL Server のビッグ データ クラスターをインストールするコマンドを実行しているコンピューターにインストール[kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)します。 SQL Server のビッグ データ クラスターでは、kubernetes では、サーバーとクライアント (kubectl) の両方で、最小の 1.10 バージョンが必要です。 Kubectl をインストールするを参照してください。 [kubectl のインストール](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl)します。 

インストールする、 **mssqlctl** SQL Server のビッグ データを管理するための CLI ツールは、クライアント コンピューターのクラスター、最初にインストールする必要があります[Python](https://www.python.org/downloads/) v3.0 の最小バージョンと[pip3](https://pip.pypa.io/en/stable/installing/)します。 `pip` ダウンロードした 3.4 以上での Python バージョンを使用している場合に既にインストールされて[python.org](https://www.python.org/)します。

## <a name="verify-aks-configuration"></a>AKS の構成を確認します。

実行することができます、AKS クラスターをデプロイした後、次の kubectl コマンドをクラスター構成を表示します。 その kubectl が適切なクラスター コンテキストを指すことを確認します。

```bash
kubectl config view
```

## <a name="install-mssqlctl-cli-management-tool"></a>Mssqlctl CLI 管理ツールをインストールします。

次のコマンドをインストールする実行**mssqlctl**クライアント コンピューターにツール。 このコマンドは、Windows と Linux クライアントの両方から機能しますが、Windows で管理者特権で実行されているコマンド ウィンドウから実行しているかどうかを確認またはプレフィックス`sudo`on Linux:

```
pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.1 mssqlctl  
```

> [!IMPORTANT]
> 以前のリリースをインストールした場合は、クラスターを削除する必要があります*する前に*アップグレード**mssqlctl**と新しいリリースをインストールします。 詳細については、次を参照してください。[新しいリリースにアップグレードする](deployment-guidance.md#upgrade)します。

> [!TIP]
> 場合**mssqlctl**が正常にインストール、記事の前提条件の手順を確認しない[mssqlctl インストール](deployment-guidance.md#mssqlctl)。

## <a name="define-environment-variables"></a>環境変数を定義します。

少しビッグ データ クラスターをデプロイするために必要な環境変数の設定は、Windows または Linux と macOS のクライアントを使用しているかどうかによって異なります。  使用しているオペレーティング システムに応じて次の手順を選択します。

続行する前に、次の重要なガイドラインに注意してください。

- [コマンド ウィンドウ](https://docs.microsoft.com/visualstudio/ide/reference/command-window)、環境変数に引用符が含まれます。 パスワードをラップする引用符を使用する場合は、パスワードに、引用符が含まれます。
- Bash では、引用符は、変数に含まれていません。 この例は、二重引用符を使用`"`します。
- 任意に、パスワード、環境変数を設定できますが必ず、十分に複雑な使用しないでください、 `!`、 `&`、または`'`文字。
- CTP 2.1 のリリースでは、既定のポートを変更できません。
- `sa`アカウントは、システム管理者は、セットアップ中に作成される SQL Server マスター インスタンス。 SQL Server のコンテナーを作成した後、そのコンテナーで `echo $MSSQL_SA_PASSWORD` を実行すると、指定した環境変数 `MSSQL_SA_PASSWORD` が検索できるようになります。 セキュリティのため、変更、`sa`記載されているベスト プラクティスに従ってパスワード[ここ](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password)します。

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
export ACCEPT_EULA="Y"
export CLUSTER_PLATFORM="aks"

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

> [!NOTE]
> 限定のパブリック プレビュー中に SQL Server のビッグ データ クラスターのイメージをダウンロードする Docker の資格情報は、Microsoft によって各顧客に提供されます。 アクセス権を要求するには、登録[ここ](https://aka.ms/eapsignup)、ビッグ データの SQL Server クラスターに関心を指定します。

## <a name="deploy-a-big-data-cluster"></a>ビッグ データ クラスターをデプロイします。

Kubernetes クラスター上の SQL Server 2019 CTP 2.1 ビッグ データ クラスターをデプロイするには、次のコマンドを実行します。

```bash
mssqlctl create cluster <name of your cluster>
```

> [!NOTE]
> クラスターの名前は、小文字、英数字文字、スペースなしのみにする必要があります。 クラスターと同じ名前を持つ名前空間に、ビッグ データ クラスターのすべての Kubernetes の成果物を作成します。 指定された名前。


コマンド ウィンドウまたはシェルは、展開ステータスを返します。 別のコマンド ウィンドウでこれらのコマンドを実行してデプロイの状態をチェックすることもできます。

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
 

## <a name="connect-to-the-big-data-cluster"></a>ビッグ データ クラスターへの接続します。

配置スクリプトが正常に完了したら後、は、SQL Server のマスター インスタンスと、次の手順を使用して Spark/HDFS 終点の IP アドレスを取得できます。 簡単に参照のほか、クラスター管理ポータルでサービス エンドポイント セクションでは、クラスターのすべてのエンドポイントが表示されます。

Azure では、AKS の Azure ロード バランサーのサービスを提供します。 次のコマンドを cmd でを実行するか、bash ウィンドウ。

```bash
kubectl get svc service-master-pool-lb -n <name of your cluster>
kubectl get svc service-security-lb -n <name of your cluster>
```

探して、 **EXTERNAL-IP**サービスに割り当てられている値。 IP アドレスを使用して、SQL Server マスター インスタンスへの接続、`service-master-pool-lb`ポート 31433 で (例:  **\<ip アドレス\>31433、**) との外部 ip アドレスを使用して SQL Server のビッグ データ クラスター エンドポイントに、`service-security-lb`サービス。   ビッグ データ クラスター エンドポイントのことは、HDFS との対話し、Knox を介した Spark ジョブを送信できます。

## <a name="sample-deployment-script"></a>配置スクリプトのサンプル

AKS と SQL Server の両方のビッグ データ クラスターをデプロイするサンプル python スクリプトについては、次を参照してください。[ビッグ データ クラスター Azure Kubernetes Service (AKS) で SQL Server 展開](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks)します。

## <a name="next-steps"></a>次の手順

これで、SQL Server のビッグ データ クラスターをデプロイするは、いくつかの新しい機能を試してください。

> [!div class="nextstepaction"]
> [SQL Server 2019 プレビューで notebook を使用する方法](notebooks-guidance.md)
