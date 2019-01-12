---
title: Azure Kubernetes サービスを構成します。
titleSuffix: SQL Server 2019 big data clusters
description: SQL Server 2019 ビッグ データ クラスター (プレビュー) のデプロイ用 Azure Kubernetes Service (AKS) を構成する方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 8e6e91836b3daf0392da082df1f4ec806e9faf94
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241243"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-2019-big-data-cluster-preview-deployments"></a>SQL Server 2019 ビッグ データ クラスター (プレビュー) のデプロイ用 Azure Kubernetes サービスを構成します。

この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) のデプロイ用 Azure Kubernetes Service (AKS) を構成する方法について説明します。

AKS によって、作成、構成、およびコンテナー化されたアプリケーションを実行するための Kubernetes クラスターであらかじめ構成されている仮想マシンのクラスターの管理を簡単にできます。 これにより、既存のスキルを使用して、または Microsoft Azure でコンテナー ベースのアプリケーション展開および管理する、コミュニティの専門知識の増加し続けるの本文に描画することができます。

この記事では、Azure CLI を使用して AKS で Kubernetes をデプロイする手順について説明します。 Azure サブスクリプションを持っていない場合は、開始する前に、無料のアカウントを作成します。

> [!TIP] 
> AKS と SQL Server の両方のビッグ データ クラスターをデプロイするサンプル python スクリプトについては、次を参照してください。[ビッグ データ クラスター Azure Kubernetes Service (AKS) で SQL Server 展開](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks)します。

## <a name="prerequisites"></a>前提条件

- [SQL Server 2019 のビッグ データ ツールの展開](deploy-big-data-tools.md):
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server 2019 の拡張機能**
   - **Azure CLI**

- Kubernetes のサーバーの最小 1.10 バージョンです。 For AKS を使用する必要があります。 `--kubernetes-version` 、既定値以外のバージョンを指定するパラメーター。

- 基本的なシナリオの検証中に最適なエクスペリエンスのため、AKS の環境で少なくとも 4 つの Vcpu を持つ、少なくとも 3 つのエージェント Vm、および 32 GB のメモリが各お勧めします。 Azure インフラストラクチャ Vm のサイズの複数のオプションを参照してください[ここ](https://docs.microsoft.com/azure/virtual-machines/windows/sizes)の展開を計画しているリージョンの選択項目。

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

1. 使用して AKS で Kubernetes クラスターを作成、 [az aks 作成](https://docs.microsoft.com/cli/azure/aks)コマンド。 次の例では、という名前の Kubernetes クラスターを作成する*kubcluster* 3 つの Linux エージェント ノードを使用します。 前のセクションで使用したのと同じリソース グループで、AKS クラスターを作成することを確認します。

    ```bash
   az aks create --name kubcluster \
    --resource-group sqlbigdatagroup \
    --generate-ssh-keys \
    --node-vm-size Standard_L4s \
    --node-count 3 \
    --kubernetes-version 1.10.8
    ```

   大きくしたり、変更することで Kubernetes エージェント ノードの数を減らす、`--node-count <n>`場所`<n>`を使用するエージェント ノードの数です。 これは、AKS でバック グラウンドで管理されているマスターの Kubernetes ノードには含まれません。 上記の例では、 **3**サイズの Vm **Standard_L4s** AKS クラスターのエージェント ノードに使用します。

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

この記事の手順では、AKS で Kubernetes クラスターを構成します。 次の手順では、SQL Server 2019 ビッグ データ クラスターをデプロイします。

[クイック スタート:SQL Server のビッグ データ クラスター Azure Kubernetes Service (AKS) でのデプロイします。](quickstart-big-data-cluster-deploy.md)
