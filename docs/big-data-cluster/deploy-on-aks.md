---
title: Azure Kubernetes サービスを構成します。
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 ビッグ データ クラスター (プレビュー) のデプロイ用 Azure Kubernetes Service (AKS) を構成する方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/10/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d39f62345a539094c585b196c9b6030b673f8e89
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958486"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-big-data-cluster-deployments"></a>SQL Server のビッグ データ クラスター デプロイ用 Azure Kubernetes サービスを構成します。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) のデプロイ用 Azure Kubernetes Service (AKS) を構成する方法について説明します。

AKS によって、作成、構成、およびコンテナー化されたアプリケーションを実行するための Kubernetes クラスターであらかじめ構成されている仮想マシンのクラスターの管理を簡単にできます。 これにより、既存のスキルを使用して、または Microsoft Azure でコンテナー ベースのアプリケーション展開および管理する、コミュニティの専門知識の増加し続けるの本文に描画することができます。

この記事では、Azure CLI を使用して AKS で Kubernetes をデプロイする手順について説明します。 Azure サブスクリプションを持っていない場合は、開始する前に、無料のアカウントを作成します。

> [!TIP] 
> AKS と SQL Server の両方のビッグ データ クラスターをデプロイするサンプル python スクリプトについては、次を参照してください。[クイック スタート。ビッグ データ クラスター Azure Kubernetes Service (AKS) で SQL Server 展開](quickstart-big-data-cluster-deploy.md)します。

## <a name="prerequisites"></a>必須コンポーネント

- [SQL Server 2019 のビッグ データ ツールの展開](deploy-big-data-tools.md):
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server 2019 の拡張機能**
   - **Azure CLI**

- Kubernetes のサーバーの最小 1.10 バージョンです。 For AKS を使用する必要があります。 `--kubernetes-version` 、既定値以外のバージョンを指定するパラメーター。

- AKS での基本的なシナリオの検証中に最適なエクスペリエンスを使用します。
   - すべてのノードで 8 個の Vcpu
   - VM あたりのメモリとして 32 GB
   - すべてのノードで 24 またはアタッチされた複数のディスク

   > [!TIP]
   > Azure インフラストラクチャ Vm のサイズの複数のオプションを参照してください[ここ](https://docs.microsoft.com/azure/virtual-machines/windows/sizes)の展開を計画しているリージョンの選択項目。

## <a name="create-a-resource-group"></a>リソース グループを作成します。

Azure リソース グループは、azure リソースのデプロイし、管理論理グループです。 次の手順では、Azure にサインインし、AKS クラスターのリソース グループを作成します。

1. コマンド プロンプトで次のコマンドを実行し、Azure サブスクリプションへのログインの指示に従います。

    ```azurecli
    az login
    ```

1. 複数のサブスクリプションがある場合は、次のコマンドを実行してすべてのサブスクリプションを表示できます。

   ```azurecli
   az account list
   ```

1. 別のサブスクリプションに変更したい場合は、このコマンドを実行できます。

   ```azurecli
   az account set --subscription <subscription id>
   ```

1. 使用してリソース グループを作成、 **az グループ作成**コマンド。 次の例は、という名前のリソース グループを作成します。`sqlbdcgroup`で、`westus2`場所。

   ```azurecli
   az group create --name sqlbdcgroup --location westus2
   ```

## <a name="verify-available-kubernetes-versions"></a>使用可能な Kubernetes バージョンを確認します。

Kubernetes の最新バージョンを使用します。 最新のバージョンは、クラスターを展開している場所によって異なります。 次のコマンドは、特定の場所で利用可能な Kubernetes バージョンを返します。

コマンドを実行する前に、スクリプトを更新します。 置換`<Azure data center>`クラスターの場所を使用します。

   **Bash**

   ```bash
   az aks get-versions \
   --location <Azure data center> \
   --query orchestrators \
   --o table
   ```

   **PowerShell**

   ```powershell
   az aks get-versions `
   --location <Azure data center> `
   --query orchestrators `
   --o table
   ```

クラスターの最新バージョンを選択します。 バージョン番号を記録します。 次の手順で使用します。

## <a name="create-a-kubernetes-cluster"></a>Kubernetes クラスターを作成します。

1. 使用して AKS で Kubernetes クラスターを作成、 [az aks 作成](https://docs.microsoft.com/cli/azure/aks)コマンド。 次の例では、という名前の Kubernetes クラスターを作成する*kubcluster*サイズの Linux エージェント ノードが 1 つ**Standard_L8s**します。

   スクリプトを実行する前に置き換える`<version number>`前の手順で特定したバージョン番号。

   前のセクションで使用したのと同じリソース グループで、AKS クラスターを作成することを確認します。

   **挑戦:**

   ```bash
   az aks create --name kubcluster \
   --resource-group sqlbdcgroup \
   --generate-ssh-keys \
   --node-vm-size Standard_L8s \
   --node-count 1 \
   --kubernetes-version <version number>
   ```

   **PowerShell:**

   ```powershell
   az aks create --name kubcluster `
   --resource-group sqlbdcgroup `
   --generate-ssh-keys `
   --node-vm-size Standard_L8s `
   --node-count 1 `
   --kubernetes-version <version number>
   ```

   大きくしたり、変更することで Kubernetes エージェント ノードの数を減らす、`--node-count <n>`場所`<n>`を使用するエージェント ノードの数です。 これは、AKS でバック グラウンドで管理されているマスターの Kubernetes ノードには含まれません。 前の例では、のみ、評価の目的で 1 つのノードを使用します。

   数分後、コマンドが完了し、クラスターに関する情報を JSON 形式を返します。

   > [!TIP]
   > Aks クラスターの作成エラーが発生した場合は、次を参照してください。、[トラブルシューティングのセクション](#troubleshoot)に改訂された記事。

1. 後で使用できるは、前のコマンドからの JSON 出力を保存します。

## <a name="connect-to-the-cluster"></a>クラスターに接続します。

1. Kubernetes クラスターに接続するように kubectl を構成するには、実行、 [az aks 資格情報の取得](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials)コマンド。 この手順では、資格情報をダウンロードし、それらを使用する CLI kubectl を構成します。

   ```azurecli
   az aks get-credentials --resource-group=sqlbdcgroup --name kubcluster
   ```

1. クラスターへの接続を確認するため、 [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)コマンドをクラスター ノードの一覧を返します。  次の例は、出力を示しています。 1 つのマスターと 3 つのエージェント ノードがある場合。

   ```bash
   kubectl get nodes
   ```

## <a id="troubleshoot"></a> トラブルシューティング

前のコマンドを使用して Azure Kubernetes サービスを作成するすべての問題がある場合は、次の解決策を試してください。

- インストールされていることを確認、[最新の Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)します。
- 別のリソース グループとクラスター名を使用する手順と同じにしてみてください。

## <a name="next-steps"></a>次の手順

この記事の手順では、AKS で Kubernetes クラスターを構成します。 次の手順では、AKS の Kubernetes クラスター上の SQL Server 2019 ビッグ データ クラスターを展開します。 ビッグ データ クラスターをデプロイする方法の詳細については、次の記事を参照してください。

[Kubernetes での SQL Server のビッグ データ クラスターをデプロイする方法](deployment-guidance.md)
