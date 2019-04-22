---
title: 作業開始
titleSuffix: SQL Server big data clusters
description: 手順と SQL Server 2019 ビッグ データ クラスター (プレビュー) を展開するためのリソースについて説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/18/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 69b5d9b69536243d371cb45c1c46620f5194657d
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860433"
---
# <a name="get-started-with-sql-server-big-data-clusters"></a>ビッグ データの SQL Server クラスターを概要します。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、デプロイする方法の概要を示します、 [SQL Server 2019 ビッグ データ クラスター (プレビュー)](big-data-cluster-overview.md)します。 概念を理解し、このセクションでは、その他のデプロイに関する記事を理解するためのフレームワークを提供するものです。 特定の展開手順は、クライアントとサーバー向けプラットフォームの選択によって異なります。

## <a id="tools"></a> クライアント ツール

ビッグ データ クラスターには、特定のクライアント ツールのセットが必要です。 ビッグ データ クラスターを Kubernetes にデプロイする前に、次のツールをインストールする必要があります。

| ツール | 説明 |
|---|---|
| **mssqlctl** | 展開して、ビッグ データ クラスターを管理します。 |
| **kubectl** | 作成し、基になる Kubernetes クラスターを管理します。 |
| **Azure Data Studio** | ビッグ データ クラスターを使用するためのグラフィカル インターフェイスです。 |
| **SQL Server 2019 の拡張機能** | ビッグ データ クラスター機能を有効にする azure Data Studio 拡張子。 |

その他のツールは、さまざまなシナリオの必要があります。 各記事では、特定のタスクを実行するための前提条件となるツールを説明します。 ツールとインストールのリンクの一覧については、次を参照してください。[ビッグ データ ツールのインストールの SQL Server 2019](deploy-big-data-tools.md)します。

## <a name="kubernetes"></a>Kubernetes

ビッグ データ クラスターは、一連の相互に関連するコンテナーで管理されているデプロイ[Kubernetes](https://kubernetes.io/docs/home)します。 さまざまな方法で Kubernetes をホストすることができます。 既存の Kubernetes 環境を既に存在する場合でも、ビッグ データ クラスターの場合、関連する要件を確認してください。

- **Azure Kubernetes Service (AKS)**:AKS で Azure の managed Kubernetes クラスターをデプロイすることができます。 管理し、エージェント ノードのメンテナンスだけです。 Aks を使うと、クラスター用ハードウェアをプロビジョニングする必要はありません。 簡単にビッグ データ クラスターを使用しても[配置スクリプト](quickstart-big-data-cluster-deploy.md)AKS クラスターを作成し、1 つの手順でビッグ データ クラスターをデプロイします。 ビッグ データ クラスターを AKS を使用する方法の詳細については、次を参照してください。 [Azure Kubernetes サービスの構成の SQL Server 2019 ビッグ データ クラスター (プレビュー) のデプロイ](deploy-on-aks.md)します。

- **複数のマシン**:Kubernetes を複数の Linux マシン、物理サーバーまたは仮想マシンにデプロイすることもできます。 [Kubeadm](https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/)ツールは、Kubernetes クラスターを作成するために使用できます。 このメソッドは、ビッグ データ クラスターに使用する既存のインフラストラクチャが既にある場合にも動作します。 使用しての詳細については**kubeadm**ビッグ データのクラスターでのデプロイを参照してください[複数のコンピューターの SQL Server 2019 ビッグ データ クラスター (プレビュー) のデプロイでの Kubernetes の構成](deploy-with-kubeadm.md)します。

- **Minikube**:Minikube を使用すると、1 台のサーバーで Kubernetes をローカルに実行できます。 ビッグ データ クラスターをテストするか、またはテストまたは開発のシナリオで使用する必要がある場合、有効な選択肢になります。 詳細については、Minikube を使用して、次を参照してください。、 [Minikube ドキュメント](https://kubernetes.io/docs/setup/minikube/)します。 ビッグ データ クラスターを Minikube を使用するため、特定の要件を参照してください。 [minikube の SQL Server 2019 ビッグ データ クラスターのデプロイを構成する](deploy-on-minikube.md)します。

## <a name="deployment-scripts"></a>展開スクリプト

配置スクリプトは、Kubernetes と 1 つのステップでのビッグ データ クラスターの両方を展開できます。 多くの場合も、必要な環境変数の既定値を指定します。 Azure Kubernetes Service (AKS) でのビッグ データ クラスターのデプロイ スクリプトの例は、次を参照してください。[デプロイ クラスター デプロイ スクリプト (AKS) でのビッグ データ、SQL Server 2019](quickstart-big-data-cluster-deploy.md)します。

任意の配置スクリプトをカスタマイズするには、ビッグ データ クラスター環境変数が異なる方法で構成される、独自のバージョンを作成します。

## <a name="deploy-a-big-data-cluster"></a>ビッグ データ クラスターをデプロイする

1 つのスクリプトを使用して、AKS の Kubernetes とビッグ データ クラスターを展開するには、次の例を参照してください。

- [デプロイ スクリプト (AKS) で SQL Server 2019 ビッグ データ クラスターをデプロイします。](quickstart-big-data-cluster-deploy.md)

AKS、kubeadm、MiniKube を使用してビッグ データ クラスターの展開の展開の詳細については、次の記事を参照してください。

- [Kubernetes での SQL Server のビッグ データ クラスターをデプロイする方法](deployment-guidance.md)

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターを正常に展開した後[クラスターに接続する](connect-to-big-data-cluster.md)を検討してください[サンプル データの読み込み](tutorial-load-sample-data.md)いくつかのチュートリアルで使用するためです。