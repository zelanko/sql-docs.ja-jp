---
title: ビッグデータクラスターとは
titleSuffix: SQL Server big data clusters
description: Kubernetes で実行され、リレーショナルデータと HDFS データの両方にスケールアウトオプションを提供する SQL Server 2019 ビッグデータクラスター (プレビュー) について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: overview
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0beb4ea57ba6c2591e5b2c06a7775fc2d7e8b26c
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419498"
---
# <a name="what-are-sql-server-big-data-clusters"></a>SQL Server ビッグ データ クラスターとは

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]以降 SQL Server ビッグデータクラスターを使用すると、Kubernetes で実行されている SQL Server、Spark、および HDFS コンテナーのスケーラブルなクラスターをデプロイできます。 これらのコンポーネントは並行して実行されているため、Transact-sql または Spark からのビッグデータの読み取り、書き込み、処理を行うことができます。これにより、大量のビッグデータを使用して、価値の高いリレーショナルデータを簡単に組み合わせて分析することができます。

最新リリースの新機能と既知の問題の詳細については、[リリースノート](release-notes-big-data-cluster.md)を参照してください。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="scenarios"></a>シナリオ

ビッグデータクラスターを SQL Server と、ビッグデータを柔軟に操作することができます。 外部データソースに対してクエリを実行したり、SQL Server によって管理される HDFS にビッグデータを格納したり、クラスターを介して複数の外部データソースからデータを照会したりすることができます。 その後、AI、machine learning、およびその他の分析タスクにデータを使用できます。 以下のセクションでは、これらのシナリオの詳細について説明します。

### <a name="data-virtualization"></a>データの仮想化

[SQL Server PolyBase](../relational-databases/polybase/polybase-guide.md)SQL Server を利用することで、ビッグデータクラスターはデータを移動またはコピーせずに外部データソースにクエリを実行できます。 [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]では、データソースへの新しいコネクタが導入されています。

![データの仮想化](media/big-data-cluster-overview/data-virtualization.png)

### <a name="data-lake"></a>Data lake

SQL Server ビッグデータクラスターには、スケーラブルな HDFS*記憶域プール*が含まれています。 これは、複数の外部ソースから取り込まれた可能性があるビッグデータを格納するために使用できます。 ビッグデータクラスターの HDFS にビッグデータが格納されると、データを分析してクエリを実行し、リレーショナルデータと組み合わせることができます。

![Data lake](media/big-data-cluster-overview/data-lake.png)

### <a name="scale-out-data-mart"></a>スケールアウトデータマート

ビッグデータクラスター SQL Server は、データの分析のパフォーマンスを向上させるためにスケールアウトコンピューティングとストレージを提供します。 さまざまなソースからのデータを取り込まれたして、さらに分析するためにキャッシュとして*データプール*ノード間で分散することができます。

![データマート](media/big-data-cluster-overview/data-mart.png)

### <a name="integrated-ai-and-machine-learning"></a>AI と Machine Learning の統合

ビッグデータクラスター SQL Server、HDFS ストレージプールとデータプールに格納されているデータに対して AI および機械学習のタスクを有効にします。 SQL Server では、R、Python、スケール a、または Java を使用して、Spark および組み込みの AI ツールを使用できます。

![AI と ML](media/big-data-cluster-overview/ai-ml-spark.png)

### <a name="management-and-monitoring"></a>管理と監視

管理と監視は、コマンドラインツール、Api、ポータル、および動的管理ビューの組み合わせによって提供されます。

Azure Data Studio を使用すると、ビッグデータクラスターでさまざまなタスクを実行できます。 これは、新しい**SQL Server 2019 拡張機能 (プレビュー)** によって有効になります。 この拡張機能は次を提供します。

- 一般的な管理タスク用の組み込みスニペットです。
- HDFS の参照、ファイルのアップロード、ファイルのプレビュー、およびディレクトリの作成を行うことができます。
- Jupyter 互換ノートブックを作成、開いて、実行する機能。
- データ仮想化ウィザード。外部データソースの作成を簡略化します。

## <a id="architecture"></a> アーキテクチャ

SQL Server ビッグデータクラスターは、 [Kubernetes](https://kubernetes.io/docs/concepts/)によって調整された Linux コンテナーのクラスターです。

### <a name="kubernetes-concepts"></a>Kubernetes の概念

Kubernetes はオープンソースのコンテナー orchestrator であり、必要に応じてコンテナーのデプロイを拡張できます。 次の表では、重要な Kubernetes 用語をいくつか定義します。

|||
|:--|:--|
| **Cluster** | Kubernetes クラスターは、ノードと呼ばれる一連のコンピューターです。 1つのノードがクラスターを制御し、マスターノードとして指定されます。残りのノードは worker ノードです。 Kubernetes マスターは、ワーカー間で作業を分散し、クラスターの正常性を監視する役割を担います。 |
| **[Node]** | ノードは、コンテナー化されたアプリケーションを実行します。 物理マシンまたは仮想マシンのいずれかを指定できます。 Kubernetes クラスターには、物理マシンと仮想マシンの両方のノードを含めることができます。 |
| **ポッド** | ポッドは、Kubernetes のアトミックデプロイ単位です。 ポッドは、アプリケーションを実行するために必要な1つ以上のコンテナーと関連リソースの論理グループです。 各ポッドはノード上で実行されます。ノードは、1つまたは複数のポッドを実行できます。 Kubernetes マスターは、クラスター内のノードにポッドを自動的に割り当てます。 |
| &nbsp; ||

SQL Server ビッグデータクラスターでは、Kubernetes は SQL Server ビッグデータクラスターの状態を担います。Kubernetes は、クラスターノードの構築と構成を行い、ポッドをノードに割り当て、クラスターの正常性を監視します。

### <a name="big-data-clusters-architecture"></a>ビッグデータクラスターのアーキテクチャ

次の図は、SQL Server 用のビッグデータクラスターのコンポーネントを示しています。

![アーキテクチャの概要](media/big-data-cluster-overview/architecture-diagram-overview.png)

### <a id="controlplane"></a>コントロール

コントローラーは、クラスターの管理とセキュリティを提供します。 これには、cntrol サービス、構成ストア、およびその他のクラスターレベルサービス (Kibana、Grafana、エラスティック検索など) が含まれています。

### <a id="computeplane"></a>コンピューティングプール

コンピューティングプールは、クラスターにコンピューティングリソースを提供します。 SQL Server on Linux ポッドを実行するノードが含まれています。 コンピューティングプール内のポッドは、特定の処理タスクのために*SQL コンピューティングインスタンス*に分割されます。 

### <a id="dataplane"></a>データプール

データプールは、データの永続化とキャッシュに使用されます。 データプールは、SQL Server on Linux を実行している1つ以上のポッドで構成されます。 これは、SQL クエリまたは Spark ジョブからデータを取り込むために使用されます。 SQL Server ビッグデータクラスターのデータマートは、データプールに保持されます。 

### <a name="storage-pool"></a>記憶域プール

記憶域プールは、SQL Server on Linux、Spark、および HDFS で構成される記憶域プールポッドで構成されます。 SQL Server ビッグデータクラスター内のすべての記憶域ノードは、HDFS クラスターのメンバーです。

> [!TIP]
> ビッグデータクラスターのアーキテクチャとインストールの詳細については、「 [ワークショップ:ビッグデータクラスターのアーキテクチャ](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)を Microsoft SQL Server します。

## <a name="next-steps"></a>次のステップ

SQL Server ビッグデータクラスターは、SQL Server 2019 早期導入プログラムを通じて、限られたパブリックプレビューとして最初に利用できます。 アクセスを要求するには、[ここ](https://aka.ms/eapsignup)に登録し、ビッグデータクラスターを試すための関心を指定します。 Microsoft は、すべての要求をトリアージし、できるだけ早く対応します。
