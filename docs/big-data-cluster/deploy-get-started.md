---
title: 作業開始
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 ビッグデータクラスター (プレビュー) をデプロイするための手順とリソースについて説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 41dd39c7aa613083f8ff47824ed6238b6f3c61b9
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419424"
---
# <a name="get-started-with-sql-server-big-data-clusters"></a>SQL Server ビッグデータクラスターの概要

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、 [SQL Server 2019 ビッグデータクラスター (プレビュー)](big-data-cluster-overview.md)をデプロイする方法の概要について説明します。 概念を説明し、このセクションの他のデプロイに関する記事を理解するためのフレームワークを提供することを目的としています。 特定の展開手順は、クライアントとサーバーのプラットフォームの選択によって異なります。

## <a id="tools"></a>クライアントツール

ビッグデータクラスターには、特定のクライアントツールのセットが必要です。 Kubernetes にビッグデータクラスターを展開する前に、次のツールをインストールする必要があります。

| ツール | 説明 |
|---|---|
| **azdata** | ビッグデータクラスターをデプロイおよび管理します。 |
| **kubectl** | 基になる Kubernetes クラスターを作成して管理します。 |
| **Azure Data Studio** | ビッグデータクラスターを使用するためのグラフィカルインターフェイス。 |
| **SQL Server 2019 拡張機能** | ビッグデータクラスター機能を有効にする Azure Data Studio 拡張機能。 |

その他のツールは、さまざまなシナリオで必要になります。 各記事で、特定のタスクを実行するための前提条件となるツールについて説明します。 ツールとインストールリンクの完全な一覧については、「 [Install SQL Server 2019 big data tools](deploy-big-data-tools.md)」を参照してください。

## <a name="kubernetes"></a>Kubernetes

ビッグデータクラスターは、 [Kubernetes](https://kubernetes.io/docs/home)で管理される一連の相互に関連するコンテナーとしてデプロイされます。 Kubernetes はさまざまな方法でホストできます。 既存の Kubernetes 環境が既に存在する場合でも、ビッグデータクラスターの関連要件を確認する必要があります。

- **Azure Kubernetes サービス (AKS)** :AKS を使用すると、Azure で管理された Kubernetes クラスターをデプロイできます。 エージェントノードの管理と管理のみを行います。 AKS では、クラスター用に独自のハードウェアをプロビジョニングする必要はありません。 ビッグデータクラスター[デプロイスクリプト](quickstart-big-data-cluster-deploy.md)を使用すると、AKS クラスターを作成し、1つの手順でビッグデータクラスターをデプロイすることも簡単にできます。 ビッグデータクラスターでの AKS の使用の詳細については、「 [Configure Azure Kubernetes Service for SQL Server 2019 ビッグ data cluster (preview) デプロイメント](deploy-on-aks.md)」を参照してください。

- **複数のコンピューター**:Kubernetes は、物理サーバーまたは仮想マシンとして、複数の Linux マシンにデプロイすることもできます。 [Kubeadm](https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/)ツールを使用すると、Kubernetes クラスターを作成できます。 この方法は、ビッグデータクラスターに使用する既存のインフラストラクチャが既に存在する場合に適しています。 ビッグデータクラスターでの**kubeadm**デプロイの使用の詳細については、「 [SQL Server 2019 ビッグデータクラスター (プレビュー) のデプロイのために複数のコンピューターで Kubernetes を構成](deploy-with-kubeadm.md)する」を参照してください。

- **Minikube**:Minikube を使用すると、1台のサーバーで Kubernetes をローカルで実行できます。 ビッグデータクラスターを試す場合や、テストまたは開発シナリオで使用する必要がある場合は、このオプションを選択することをお勧めします。 Minikube の使用方法の詳細については、 [Minikube のドキュメント](https://kubernetes.io/docs/setup/minikube/)を参照してください。 ビッグデータクラスターで Minikube を使用するための特定の要件については、「 [Configure Minikube for SQL Server 2019 ビッグデータクラスターのデプロイ](deploy-on-minikube.md)」を参照してください。

## <a name="deploy-a-big-data-cluster"></a>ビッグ データ クラスターをデプロイする

Kubernetes を構成した後、 `azdata bdc create`コマンドを使用してビッグデータクラスターをデプロイします。 を展開するときに、いくつかの異なる方法を使用できます。

- 開発/テスト環境にデプロイする場合は、 **azdata**によって提供される[既定の構成](deployment-guidance.md#deploy)のいずれかを使用することを選択できます。

- 配置をカスタマイズするには、独自の[配置構成ファイル](deployment-guidance.md#configfile)を作成して使用します。

- 完全無人インストールの場合は、環境変数に他のすべての設定を渡すことができます。 詳細については、「[無人展開](deployment-guidance.md#unattended)」を参照してください。

## <a name="deployment-scripts"></a>展開スクリプト

配置スクリプトは、Kubernetes とビッグデータクラスターの両方を1回の手順で展開するのに役立ちます。 また、多くの場合、ビッグデータクラスター設定の既定値を提供します。 Azure Kubernetes Service (AKS) のビッグデータクラスターのデプロイスクリプトの例については、次の記事を参照してください。

[デプロイスクリプト (AKS) を使用して SQL Server 2019 ビッグデータクラスターをデプロイ](quickstart-big-data-cluster-deploy.md)します。

ビッグデータクラスター環境変数を異なる方法で構成する独自のバージョンを作成することにより、配置スクリプトをカスタマイズできます。

[Azure Data Studio notebook を使用して SQL Server 2019 ビッグデータクラスターをデプロイ](deploy-notebooks.md)します。

## <a name="next-steps"></a>次の手順

ビッグデータクラスターを正常にデプロイしたら、[クラスターに接続](connect-to-big-data-cluster.md)し、いくつかのチュートリアルで使用する[サンプルデータの読み込み](tutorial-load-sample-data.md)を検討します。