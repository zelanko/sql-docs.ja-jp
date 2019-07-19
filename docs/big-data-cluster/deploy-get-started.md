---
title: 作業開始
titleSuffix: SQL Server big data clusters
description: 手順と SQL Server 2019 ビッグ データ クラスター (プレビュー) を展開するためのリソースについて説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8583610606e5d554f039a69688af3ddff8dc8bb3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958530"
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

- **Azure Kubernetes Service (AKS)** :AKS で Azure の managed Kubernetes クラスターをデプロイすることができます。 管理し、エージェント ノードのメンテナンスだけです。 Aks を使うと、クラスター用ハードウェアをプロビジョニングする必要はありません。 簡単にビッグ データ クラスターを使用しても[配置スクリプト](quickstart-big-data-cluster-deploy.md)AKS クラスターを作成し、1 つの手順でビッグ データ クラスターをデプロイします。 ビッグ データ クラスターを AKS を使用する方法の詳細については、次を参照してください。 [Azure Kubernetes サービスの構成の SQL Server 2019 ビッグ データ クラスター (プレビュー) のデプロイ](deploy-on-aks.md)します。

- **複数のマシン**:Kubernetes を複数の Linux マシン、物理サーバーまたは仮想マシンにデプロイすることもできます。 [Kubeadm](https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/)ツールは、Kubernetes クラスターを作成するために使用できます。 このメソッドは、ビッグ データ クラスターに使用する既存のインフラストラクチャが既にある場合にも動作します。 使用しての詳細については**kubeadm**ビッグ データのクラスターでのデプロイを参照してください[複数のコンピューターの SQL Server 2019 ビッグ データ クラスター (プレビュー) のデプロイでの Kubernetes の構成](deploy-with-kubeadm.md)します。

- **Minikube**:Minikube を使用すると、1 台のサーバーで Kubernetes をローカルに実行できます。 ビッグ データ クラスターをテストするか、またはテストまたは開発のシナリオで使用する必要がある場合、有効な選択肢になります。 詳細については、Minikube を使用して、次を参照してください。、 [Minikube ドキュメント](https://kubernetes.io/docs/setup/minikube/)します。 ビッグ データ クラスターを Minikube を使用するため、特定の要件を参照してください。 [minikube の SQL Server 2019 ビッグ データ クラスターのデプロイを構成する](deploy-on-minikube.md)します。

## <a name="deploy-a-big-data-cluster"></a>ビッグ データ クラスターをデプロイする

ビッグ データ クラスターをデプロイする Kubernetes を構成した後、`mssqlctl bdc create`コマンド。 を展開する場合は、いくつかの方法を実行できます。

- 開発/テスト環境に展開する場合は、いずれかを使用することもできます、[既定の構成](deployment-guidance.md#deploy)によって提供される**mssqlctl**します。

- デプロイをカスタマイズする作成し、使用、独自[展開構成ファイル](deployment-guidance.md#configfile)します。

- 完全に無人インストールでは、環境変数にその他のすべての設定を渡すことができます。 詳細については、次を参照してください。[無人展開](deployment-guidance.md#unattended)します。

## <a name="deployment-scripts"></a>展開スクリプト

配置スクリプトは、Kubernetes と 1 つのステップでのビッグ データ クラスターの両方を展開できます。 多くの場合もビッグ データ クラスター設定の既定値を指定します。 Azure Kubernetes Service (AKS) でのビッグ データ クラスターのデプロイ スクリプトの例は、次の記事を参照してください。

[ビッグ データ クラスターのデプロイ スクリプト (AKS) で SQL Server 2019 展開](quickstart-big-data-cluster-deploy.md)します。

任意の配置スクリプトをカスタマイズするには、ビッグ データ クラスター環境変数が異なる方法で構成される、独自のバージョンを作成します。

## <a name="next-steps"></a>次の手順

ビッグ データ クラスターを正常に展開した後[クラスターに接続する](connect-to-big-data-cluster.md)を検討してください[サンプル データの読み込み](tutorial-load-sample-data.md)いくつかのチュートリアルで使用するためです。