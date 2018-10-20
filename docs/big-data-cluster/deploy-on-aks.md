---
title: SQL Server 2019 CTP 2.0 の展開用の Azure Kubernetes サービスの構成 |Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: ee1faae6d43cbf2cc6c8a23086600241ad15e061
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2018
ms.locfileid: "49460897"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-2019-ctp-20"></a>SQL Server 2019 CTP 2.0 用 Azure Kubernetes サービスの構成します。

Azure Kubernetes Service (AKS) によって、作成、構成、およびコンテナー化されたアプリケーションを実行するための Kubernetes クラスターであらかじめ構成されている仮想マシンのクラスターの管理を簡単にできます。 

これにより、既存のスキルを使用して、または Microsoft Azure でコンテナー ベースのアプリケーション展開および管理する、コミュニティの専門知識の増加し続けるの本文に描画することができます。

この記事では、Azure CLI を使用して AKS で Kubernetes をデプロイする手順について説明します。 Azure サブスクリプションを持っていない場合は、開始する前に、無料のアカウントを作成します。

> [!TIP] 
> AKS と SQL Server の両方のビッグ データ クラスターをデプロイするサンプル python スクリプトについては、次を参照してください。[ビッグ データ クラスター Azure Kubernetes Service (AKS) で SQL Server 展開](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks)します。

## <a name="prerequisites"></a>前提条件

- AKS 環境では、VM の最小要件は (マスターへの追加) での最小サイズの少なくとも 2 つのエージェント Vm [Standard_DS3_v2](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-general#dsv2-series)します。 VM ごとに必要な最小リソースとは、4 つの Cpu、14 GB のメモリです。
  
   > [!NOTE]
   > 最小サイズは、ビッグ データ ジョブまたは複数の Spark アプリケーションを実行する場合は、 [Standard_D8_v3](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-general#dv3-series-sup1sup)、VM ごとに必要な最小リソースは、8 個の Cpu およびメモリとして 32 GB とします。

- このセクションでは、ことが必要です実行、Azure CLI バージョン 2.0.4 以降。 インストールまたはアップグレードを表示する必要がある場合[Azure CLI 2.0 のインストール](https://docs.microsoft.com/cli/azure/install-azure-cli)します。 実行`az --version`必要な場合は、バージョンを確認します。

- インストール[kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)します。 SQL Server のビッグ データ クラスターでは、kubernetes では、サーバーおよびクライアントの両方に 1.10 バージョンの範囲内のすべてのマイナー バージョンが必要です。 Kubectl クライアントでは、特定のバージョンをインストールするを参照してください。 [kubectl curl を使用してバイナリをインストール](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl)します。 AKS を使用する必要があります`--kubernetes-version`既定とは異なるバージョンを指定するパラメーター。 CTP2.0 リリース タイム フレームで AKS のみをサポートしている 1.10.7 および 1.10.8 バージョンに注意してください。 


> [!NOTE]
クライアント/サーバーのバージョンのスキューされていることは、1 のマイナー バージョンの +/-サポートされています。 Kubernetes のドキュメントの状態を"が、クライアント、マスターから複数の傾斜のマイナー バージョンにする必要がありますに 1 つのマイナー バージョンによって、マスターがあります。 たとえば、v1.3 マスター v1.1、バージョン 1.2、および v1.3 のノードを使用する必要があり、v1.2、v1.3、v1.4 クライアントを操作する必要があります。" 詳細については、次を参照してください。 [Kubernetes がサポートされるのは、リリースと傾斜コンポーネント](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew)します。

また、`az aks kubernetes install-cli`バージョンで kubectl クライアントをインストールを下げる必要 1.10 します。 手順については、適切なバージョンの kubectl クライアントをインストールする前に従います。

## <a name="create-a-resource-group"></a>リソース グループを作成します。

Azure リソース グループは、azure リソースのデプロイし、管理論理グループです。 次の手順では、Azure にサインインし、AKS クラスターのリソース グループを作成します。

> [!TIP]
> Windows を使用している場合は、PowerShell を使用して、残りの手順を実行します。

1. コマンド プロンプトで次のコマンドを実行し、Azure サブスクリプションへのログインの指示に従います。

    ```bash
    az login
    ```

1. 複数のサブスクリプションがある場合は、次のコマンドを実行してすべてのサブスクリプションを表示できます。

   ```bash
   az account list
   ```

1. 別のサブスクリプションに変更したい場合は、このコマンドを実行できます。

   ```bash
   az account set --subscription <subscription id>
   ```

1. 使用してリソース グループを作成、 **az グループ作成**コマンド。 次の例は、という名前のリソース グループを作成します。`sqlbigdatagroup`で、`westus2`場所。

   ```bash
   az group create --name sqlbigdatagroup --location westus2
   ```

## <a name="create-a-kubernetes-cluster"></a>Kubernetes クラスターを作成します。

1. 使用して AKS で Kubernetes クラスターを作成、 [az aks 作成](https://docs.microsoft.com/cli/azure/aks)コマンド。 次の例では、という名前の Kubernetes クラスターを作成する*kubcluster* 1 つの Linux マスター ノードと 2 つの Linux エージェント ノード。 前のセクションで使用したのと同じリソース グループで、AKS クラスターを作成することを確認します。

    ```bash
   az aks create --name kubcluster \
    --resource-group sqlbigdatagroup \
    --generate-ssh-keys \
    --node-vm-size Standard_DS3_v2 \
    --node-count 2 \
    --kubernetes-version 1.10.7
    ```

    増やすことも変更することで、既定のエージェント数を減らす、`--node-count <n>`場所`<n>`たいエージェント ノードの数です。

    数分後、コマンドが完了し、クラスターに関する情報を JSON 形式を返します。

1. 後で使用できるは、前のコマンドからの JSON 出力を保存します。

## <a name="connect-to-the-cluster"></a>クラスターに接続します。

1. Kubernetes クラスターに接続するように kubectl を構成するには、実行、 [az aks 資格情報の取得](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials)コマンド。 この手順では、資格情報をダウンロードし、それらを使用する CLI kubectl を構成します。

   ```bash
   az aks get-credentials --resource-group=sqlbigdatagroup --name kubcluster
   ```

1. クラスターへの接続を確認するため、 [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)コマンドをクラスター ノードの一覧を返します。  次の例は、出力を示しています。 1 つのマスターと 3 つのエージェント ノードがある場合。

   ```bash
   kubectl get nodes
   ```

## <a name="next-steps"></a>次の手順

この記事の手順では、AKS で Kubernetes クラスターを構成します。 次の手順では、SQL Server 2019 のビッグ データ クラスターをデプロイします。

[Kubernetes での SQL Server 2019 のビッグ データ クラスターをデプロイします。](quickstart-big-data-cluster-deploy.md)
