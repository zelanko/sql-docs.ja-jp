---
title: デプロイ クイック スタート
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 ビッグ データ クラスター (プレビュー) Azure Kubernetes Service (AKS) でのデプロイのチュートリアルです。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/27/2018
ms.topic: quickstart
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 7b8abf65b5c2e7abf8823ce98aede22bba14caad
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860529"
---
# <a name="quickstart-deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>クイック スタート: SQL Server のビッグ データ クラスター Azure Kubernetes Service (AKS) でのデプロイします。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このクイック スタートでは、サンプル デプロイ スクリプトを使用して Azure Kubernetes Service (AKS) を SQL Server 2019 ビッグ データ クラスター (プレビュー) をデプロイします。 

> [!TIP]
> AKS は、ビッグ データ クラスターの Kubernetes をホストするためのオプションを 1 つだけです。 オプションの展開をカスタマイズする方法についても、その他の展開オプションについては、[ビッグ データの SQL Server をデプロイする方法を Kubernetes クラスターの](deployment-guidance.md)を参照してください。

ここで使用する既定のビッグ データ クラスター展開は、SQL のマスター インスタンス、プールのインスタンスを 1 つのコンピューティング、2 つのデータ プール インスタンス、および記憶域プールの 2 つのインスタンスで構成されます。 AKS の既定のストレージ クラスを使用する Kubernetes 永続ボリュームを使用してデータが保持されます。 このクイック スタートで使用される既定の構成は、開発/テスト環境に適しています。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>前提条件

- Azure サブスクリプション。
- [ビッグ データ ツール](deploy-big-data-tools.md):
   - **mssqlctl**
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server 2019 の拡張機能**
   - **Azure CLI**

## <a name="log-in-to-your-azure-account"></a>Azure アカウントにログインします。

スクリプトでは、Azure CLI を使用して AKS クラスターの作成を自動化します。 スクリプトを実行する前にログインして Azure CLI を使用した Azure アカウントに少なくとも 1 回。 コマンド プロンプトから次のコマンドを実行します。

```
az login
```

## <a name="download-the-deployment-script"></a>配置スクリプトをダウンロードします。

このクイック スタートは、python スクリプトを使用して AKS でのビッグ データ クラスターの作成を自動化**展開-sql-ビッグ-データ-aks.py**します。 用の python が既にインストールされている場合**mssqlctl**、このクイック スタートでは、スクリプトが正常に実行できる必要があります。 

Windows PowerShell または Linux の bash プロンプトには、GitHub からデプロイ スクリプトをダウンロードするには、次のコマンドを実行します。

```
curl -o deploy-sql-big-data-aks.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/aks/deploy-sql-big-data-aks.py"
```

## <a name="run-the-deployment-script"></a>デプロイメント スクリプトを実行します。

次の手順を使用して、デプロイ スクリプトを実行します。 このスクリプトは Azure での AKS サービスを作成し、AKS の SQL Server 2019 のビッグ データ クラスターをデプロイします。 他のスクリプトを変更することもできます。[環境変数](deployment-guidance.md#env)カスタムの展開を作成します。

1. 次のコマンドを使用して、スクリプトを実行します。

   ```
   python deploy-sql-big-data-aks.py
   ```

   > [!NOTE]
   > Python3 を使用してコマンドを実行する必要がある場合 python3 と python2 パスとクライアント コンピューターで、:`python3 deploy-sql-big-data-aks.py`します。

1. 入力を求められたら、次の情報を入力します。

   | 値 | 説明 |
   |---|---|
   | **Azure サブスクリプション ID** | AKS を使用する Azure サブスクリプション ID。 実行して、すべてのサブスクリプションとその Id を一覧表示できます`az account list`から別のコマンドライン。 |
   | **Azure リソース グループ** | AKS クラスターを作成する Azure リソース グループ名。 |
   | **Docker のユーザー名** | 限定パブリック プレビューの一部として提供されている Docker のユーザー名。 |
   | **Docker のパスワード** | 限定パブリック プレビューの一部として提供されている Docker のパスワードです。 |
   | **Azure リージョン** | 新しい AKS クラスターの Azure リージョン (既定**westus**)。 |
   | **マシンのサイズ** | [マシンのサイズ](https://docs.microsoft.com/azure/virtual-machines/windows/sizes)AKS クラスター内のノードを使用する (既定**Standard_L8s**)。 |
   | **ワーカー ノード** | AKS クラスター内の worker ノードの数 (既定**1**)。 |
   | **クラスター名** | AKS クラスターとビッグ データ クラスターの両方の名前。 クラスターの名前は、小文字の英数字文字のみとスペースなしである必要があります。 (既定**sqlbigdata**)。 |
   | **パスワード** | コント ローラー、HDFS/Spark ゲートウェイ、およびマスター インスタンスのパスワード (デフォルト**MySQLBigData2019**)。 |
   | **コント ローラーのユーザー** | コント ローラーのユーザーのユーザー名 (既定:**管理者**)。 |

   > [!IMPORTANT]
   > 既定の**Standard_L8s**マシンのサイズはすべての Azure リージョンでは使用できません。 別のマシン サイズを選択した場合、クラスター内のノード間で接続できるディスクの合計数が 24 以上であることを確認します。 クラスター内各永続ボリューム要求は、接続されたディスクが必要です。 現時点では、ビッグ データ クラスターには、24 の永続ボリューム要求が必要です。 たとえば、 [Standard_L8s](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-storage#ls-series)マシンのサイズは、このマシンのサイズの 1 つのノードでのビッグ データ クラスターを評価することのできる、32 個のアタッチされたディスクをサポートしています。

   > [!NOTE]
   > `sa`アカウントは、システム管理者は、セットアップ時に作成される SQL Server のマスター インスタンス。 展開を作成した後、`MSSQL_SA_PASSWORD`を実行して環境変数が探索可能な`echo $MSSQL_SA_PASSWORD`マスター インスタンス コンテナーにします。 セキュリティのため、変更、`sa`デプロイ後に、マスター インスタンス上のパスワード。 詳細については、[SA パスワードの変更](../linux/quickstart-install-connect-docker.md#sapassword)を参照してください。

1. 指定したパラメーターを使用して AKS クラスターを作成して、スクリプトが開始されます。 この手順では、数分をかかります。

   <img src="./media/quickstart-big-data-cluster-deploy/script-parameters.png" width="800px" alt="Script parameters and AKS cluster creation"/>

## <a name="monitor-the-status"></a>状態を監視します

スクリプトでは、AKS クラスターを作成する前に指定した設定で必要な環境変数の設定に進みます。 呼び出して**mssqlctl** AKS でのビッグ データ クラスターをデプロイします。

クライアントのコマンド ウィンドウでは、デプロイの状態を出力します。 展開プロセス中には、コント ローラーのポッドの待機中は、一連のメッセージ表示されます。

```output
2018-11-15 15:42:02.0209 UTC | INFO | Waiting for controller pod to be up...
```

10 ~ 20 分後に、コント ローラーのポッドが実行されていることが通知する必要があります。

```output
2018-11-15 15:50:50.0300 UTC | INFO | Controller pod is running.
2018-11-15 15:50:50.0585 UTC | INFO | Controller Endpoint: https://111.111.111.111:30080
```

> [!IMPORTANT]
> デプロイ全体のビッグ データ クラスター コンポーネントのコンテナー イメージをダウンロードするために必要な時間のため時間がかかることができます。 ただし、いくつかの時間はなりません。 デプロイに関する問題が発生する場合を参照してください、[展開のトラブルシューティング](deployment-guidance.md#troubleshoot)展開ガイダンスの記事のセクション。

## <a name="inspect-the-cluster"></a>クラスターを検査します。

デプロイ中にいつでも状態と、実行されているビッグ データ クラスターに関する詳細を検査するのにには、kubectl またはクラスターの管理ポータルを使用できます。

### <a name="use-kubectl"></a>Kubectl を使用します。

使用して、新しいコマンド ウィンドウを開いて**kubectl**展開プロセス中にします。

1. クラスター全体の状態の概要を取得する次のコマンドを実行します。

   ```
   kubectl get all -n <your-cluster-name>
   ```

1. Kubernetes サービスと、次に、内部および外部エンドポイントを検査**kubectl**コマンド。

   ```
   kubectl get svc -n <your-cluster-name>
   ```

1. 次のコマンドを使用して kubernetes ポッドの状態を調べることもできます。

   ```
   kubectl get pods -n <your-cluster-name>
   ```

1. 次のコマンドで特定のポッドの詳細を確認します。

   ```
   kubectl describe pod <pod name> -n <your-cluster-name>
   ```

> [!TIP]
> 監視し、デプロイのトラブルシューティング方法の詳細については、次を参照してください。、[展開のトラブルシューティング](deployment-guidance.md#troubleshoot)展開ガイダンスの記事のセクション。

### <a name="use-the-cluster-administration-portal"></a>クラスターの管理ポータルを使用してください。

コント ローラーのポッドが実行されている場合は、展開の監視、クラスターの管理ポータルを使用することもできます。 外部 IP アドレスとポート番号を使用してポータルにアクセスすることができます、 `endpoint-service-proxy` (例: **https://\<ip アドレス\>: 30777/ポータル**)。 ポータルにログインするために使用する資格情報の値と一致する**コント ローラーのユーザー**と**パスワード**配置スクリプトで指定されています。

IP アドレスを取得することができます、**エンドポイント サービスのプロキシ**bash または cmd ウィンドウでこのコマンドを実行してサービス。

```bash
kubectl get svc endpoint-service-proxy -n <your-cluster-name>
```

> [!NOTE]
> CTP 2.4、表示されますセキュリティの警告を web ページにアクセスするときにビッグ データ クラスターが現在使用して SSL 証明書の自動生成されるためです。

## <a name="connect-to-the-cluster"></a>クラスターに接続します。

配置スクリプトが完了したらは、成功の出力が通知されます。

```output
2018-11-15 16:10:25.0583 UTC | INFO | Cluster state: Ready
2018-11-15 16:10:25.0583 UTC | INFO | Cluster deployed successfully.
```

SQL Server は、ビッグ データ クラスターが AKS にデプロイします。 クラスターに接続する Azure Data Studio を使用できます。 詳細については、[Azure データ Studio を使用した SQL Server クラスターのビッグ データへの接続](connect-to-big-data-cluster.md)を参照してください。

## <a name="clean-up"></a>クリーンアップします。

ビッグ データの SQL Server クラスターを Azure でテストする場合は、予期しない課金を回避するために完了すると、AKS クラスターを削除する必要があります。 使用を継続する場合は、クラスターを削除しないでください。

> [!WARNING]
> 次の手順も、SQL Server ビッグ データ クラスターが削除され、AKS クラスターを廃棄します。 任意のデータベースまたは保持する HDFS データがある場合は、クラスターを削除する前にそのデータをバックアップします。

Azure でビッグ データ クラスターおよび AKS サービスを削除する次の Azure CLI コマンドを実行します (置換`<resource group name>`で、 **Azure リソース グループ**配置スクリプトで指定した)。

```azurecli
az group delete -n <resource group name>
```

## <a name="next-steps"></a>次のステップ

配置スクリプトでは、Azure Kubernetes サービスが構成されているし、SQL Server 2019 のビッグ データ クラスターをデプロイすることもできます。 手動によるインストールを将来のデプロイをカスタマイズすることもできます。 どのビッグ データについてクラスターは、デプロイおよびデプロイをカスタマイズする方法については、[ビッグ データの SQL Server をデプロイする方法を Kubernetes クラスターの](deployment-guidance.md)を参照してください。

これで、SQL Server のビッグ データ クラスターをデプロイすると、サンプル データを読み込むし、チュートリアルの確認できます。

> [!div class="nextstepaction"]
> [チュートリアル:SQL Server 2019 のビッグ データ クラスターにサンプル データを読み込む](tutorial-load-sample-data.md)