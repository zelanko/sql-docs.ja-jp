---
title: 配置スクリプト
titleSuffix: SQL Server big data clusters
description: Azure Kubernetes Service (AKS) での SQL Server 2019 ビッグデータクラスター (プレビュー) のデプロイについて説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7ff1ec3672fbcf101d98ad30913742186dea574d
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419394"
---
# <a name="deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Azure Kubernetes Service (AKS) に SQL Server ビッグデータクラスターをデプロイする

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このチュートリアルでは、サンプルのデプロイスクリプトを使用して SQL Server 2019 ビッグデータクラスター (プレビュー) を Azure Kubernetes Service (AKS) にデプロイします。 

> [!TIP]
> AKS は、ビッグデータクラスターの Kubernetes をホストするためのオプションの1つにすぎません。 その他の展開オプションと、展開オプションをカスタマイズする方法の詳細については、「 [Kubernetes でビッグデータクラスターを SQL Server デプロイする方法](deployment-guidance.md)」を参照してください。

ここで使用される既定のビッグデータクラスターのデプロイは、SQL マスターインスタンス、1つのコンピューティングプールインスタンス、2つのデータプールインスタンス、2つのストレージプールインスタンスで構成されています。 データは、AKS の既定のストレージクラスを使用する Kubernetes 永続ボリュームを使用して永続化されます。 このチュートリアルで使用する既定の構成は、開発/テスト環境に適しています。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>必須コンポーネント

- Azure サブスクリプション。
- [ビッグデータツール](deploy-big-data-tools.md):
   - **azdata**
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server 2019 拡張機能**
   - **Azure CLI**

## <a name="log-in-to-your-azure-account"></a>Azure アカウントにログインします。

このスクリプトでは、AKS クラスターの作成を自動化するために Azure CLI を使用します。 スクリプトを実行する前に、少なくとも1回は Azure CLI を使用して Azure アカウントにログインする必要があります。 コマンドプロンプトから次のコマンドを実行します。

```
az login
```

## <a name="download-the-deployment-script"></a>デプロイスクリプトをダウンロードする

このチュートリアルでは、python スクリプト**deploy-sql-big-data-aks.py**を使用した AKS でのビッグデータクラスターの作成を自動化します。 **Azdata**用に python を既にインストールしている場合は、このチュートリアルでスクリプトを正常に実行できます。 

Windows PowerShell または Linux bash プロンプトで、次のコマンドを実行して、GitHub からデプロイスクリプトをダウンロードします。

```
curl -o deploy-sql-big-data-aks.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/aks/deploy-sql-big-data-aks.py"
```

## <a name="run-the-deployment-script"></a>配置スクリプトを実行する

デプロイスクリプトを実行するには、次の手順に従います。 このスクリプトは、Azure で AKS サービスを作成し、AKS に SQL Server 2019 ビッグデータクラスターをデプロイします。 スクリプトを他の[環境変数](deployment-guidance.md#configfile)で変更して、カスタムデプロイを作成することもできます。

1. 次のコマンドを使用してスクリプトを実行します。

   ```
   python deploy-sql-big-data-aks.py
   ```

   > [!NOTE]
   > クライアントコンピューターとパスの両方に python3 と python2 の両方がある場合は、python3: `python3 deploy-sql-big-data-aks.py`を使用してコマンドを実行する必要があります。

1. プロンプトが表示されたら、次の情報を入力します。

   | 値 | 説明 |
   |---|---|
   | **Azure サブスクリプション ID** | AKS に使用する Azure サブスクリプション ID。 別のコマンドラインからを実行`az account list`して、すべてのサブスクリプションとその id を一覧表示できます。 |
   | **Azure リソースグループ** | AKS クラスター用に作成する Azure リソースグループの名前。 |
   | **Azure リージョン** | 新しい AKS クラスター用の Azure リージョン (既定の**westus**)。 |
   | **マシンサイズ** | AKS クラスター内のノードに使用する[マシンのサイズ](https://docs.microsoft.com/azure/virtual-machines/windows/sizes)(既定の**Standard_L8s**)。 |
   | **ワーカーノード** | AKS クラスター内のワーカーノードの数 (既定値は**1**)。 |
   | **クラスター名** | AKS クラスターとビッグデータクラスターの両方の名前。 ビッグデータクラスターの名前は、小文字の英数字のみを使用し、スペースは使用しないようにする必要があります。 (既定の**sqlbigdata**)。 |
   | **Password** | コントローラー、HDFS/Spark ゲートウェイ、およびマスターインスタンスのパスワード (既定の**MySQLBigData2019**)。 |
   | **コントローラーユーザー** | コントローラーユーザーのユーザー名 (既定値: **admin**)。 |

SQL Server 2019 ビッグデータクラスターの早期導入プログラムの参加者には、次のパラメーターが必要でした。**Docker ユーザー名**と**docker パスワード**。 CTP 3.2 の時点では、必須ではなくなりました。

   > [!IMPORTANT]
   > 既定の**Standard_L8s**マシンサイズは、すべての Azure リージョンで使用できるとは限りません。 別のマシンサイズを選択する場合は、クラスター内のノード間で接続できるディスクの合計数が24以上であることを確認してください。 クラスター内の各永続ボリューム要求には、接続されたディスクが必要です。 現在、ビッグデータクラスターには24個の永続的なボリューム要求が必要です。 たとえば、 [Standard_L8s](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-storage#lsv2-series)マシンのサイズでは、32の接続ディスクがサポートされているため、このマシンサイズの1つのノードでビッグデータクラスターを評価することができます。

   > [!NOTE]
   > `sa`アカウントは、セットアップ中に作成される SQL Server マスターインスタンスのシステム管理者です。 デプロイを`MSSQL_SA_PASSWORD`作成した後は、master インスタンスコンテナー `echo $MSSQL_SA_PASSWORD`でを実行することで、環境変数を検出できます。 セキュリティ上の理由から、 `sa`デプロイ後に master インスタンスのパスワードを変更します。 詳細については、「 [SA パスワードの変更](../linux/quickstart-install-connect-docker.md#sapassword)」を参照してください。

1. スクリプトは、指定したパラメーターを使用して AKS クラスターを作成することによって開始されます。 この手順には数分かかります。

   <img src="./media/quickstart-big-data-cluster-deploy/script-parameters.png" width="800px" alt="Script parameters and AKS cluster creation"/>

## <a name="monitor-the-status"></a>状態を監視する

スクリプトによって AKS クラスターが作成されると、前に指定した設定で必要な環境変数の設定に進みます。 次に、 **azdata**を呼び出して、AKS にビッグデータクラスターをデプロイします。

クライアントのコマンドウィンドウに、展開の状態が出力されます。 デプロイプロセス中に、コントローラーポッドを待機している一連のメッセージが表示されます。

```output
2018-11-15 15:42:02.0209 UTC | INFO | Waiting for controller pod to be up...
```

10 ~ 20 分後に、コントローラーポッドが実行されていることが通知されます。

```output
2018-11-15 15:50:50.0300 UTC | INFO | Controller pod is running.
2018-11-15 15:50:50.0585 UTC | INFO | Controller Endpoint: https://111.111.111.111:30080
```

> [!IMPORTANT]
> ビッグデータクラスターのコンポーネントのコンテナーイメージをダウンロードするために必要な時間によって、デプロイ全体に時間がかかることがあります。 ただし、数時間かかることはありません。 デプロイで問題が発生した場合は、「 [SQL Server ビッグデータクラスターの監視とトラブルシューティング](cluster-troubleshooting-commands.md)」を参照してください。

## <a name="inspect-the-cluster"></a>クラスターを検査する

デプロイ中はいつでも、 **kubectl**または**azdata**を使用して、実行中のビッグデータクラスターの状態と詳細を調べることができます。

### <a name="use-kubectl"></a>Kubectl を使用する

デプロイプロセス中に**kubectl**を使用する新しいコマンドウィンドウを開きます。

1. 次のコマンドを実行して、クラスター全体の状態の概要を取得します。

   ```
   kubectl get all -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > ビッグデータクラスター名を変更しなかった場合、スクリプトは既定で**sqlbigdata**に設定されます。

1. 次の**kubectl**コマンドを使用して、kubernetes services とその内部および外部エンドポイントを調べます。

   ```
   kubectl get svc -n <your-big-data-cluster-name>
   ```

1. 次のコマンドを使用して、kubernetes ポッドの状態を調べることもできます。

   ```
   kubectl get pods -n <your-big-data-cluster-name>
   ```

1. 次のコマンドを使用して、特定のポッドに関する詳細情報を確認します。

   ```
   kubectl describe pod <pod name> -n <your-big-data-cluster-name>
   ```

> [!TIP]
> デプロイの監視とトラブルシューティングの方法の詳細については、「 [SQL Server ビッグデータクラスターの監視とトラブルシューティング](cluster-troubleshooting-commands.md)」を参照してください。

## <a name="connect-to-the-cluster"></a>クラスターに接続する

配置スクリプトが完了すると、次のような結果が通知されます。

```output
2018-11-15 16:10:25.0583 UTC | INFO | Cluster state: Ready
2018-11-15 16:10:25.0583 UTC | INFO | Cluster deployed successfully.
```

SQL Server ビッグデータクラスターが AKS に配置されるようになりました。 これで、Azure Data Studio を使用してクラスターに接続できるようになりました。 詳細については、「Azure Data Studio を使用した[SQL Server ビッグデータクラスターへの接続](connect-to-big-data-cluster.md)」を参照してください。

## <a name="clean-up"></a>クリーンアップ

Azure で SQL Server ビッグデータクラスターをテストしている場合は、予期しない料金が発生しないように、完了時に AKS クラスターを削除する必要があります。 クラスターを引き続き使用する場合は、削除しないでください。

> [!WARNING]
> 次の手順では、SQL Server ビッグデータクラスターも削除する AKS クラスターを破棄します。 保持するデータベースまたは HDFS データがある場合は、クラスターを削除する前にそのデータをバックアップします。

次の Azure CLI コマンドを実行して、Azure のビッグデータクラスターと AKS サービスを削除`<resource group name>`します (をデプロイスクリプトで指定した**azure リソースグループ**に置き換えます)。

```azurecli
az group delete -n <resource group name>
```

## <a name="next-steps"></a>次のステップ

デプロイスクリプトでは、Azure Kubernetes サービスを構成し、SQL Server 2019 ビッグデータクラスターをデプロイしました。 また、手動インストールを使用して、将来の展開をカスタマイズすることもできます。 ビッグデータクラスターのデプロイ方法とデプロイをカスタマイズする方法の詳細については、「 [Kubernetes でビッグデータクラスターを SQL Server デプロイする方法](deployment-guidance.md)」を参照してください。

ビッグデータクラスター SQL Server がデプロイされたので、サンプルデータを読み込んで、チュートリアルを調べることができます。

> [!div class="nextstepaction"]
> [チュートリアル: SQL Server 2019 ビッグデータクラスターへのサンプルデータの読み込み](tutorial-load-sample-data.md)