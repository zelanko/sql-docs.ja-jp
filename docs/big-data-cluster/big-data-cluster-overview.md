---
title: ビッグ データ クラスターとは
titleSuffix: SQL Server big data clusters
description: Kubernetes で実行して、リレーショナルの両方でスケール アウト オプションおよび HDFS データを提供する SQL Server 2019 ビッグ データ クラスター (プレビュー) について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/07/2018
ms.topic: overview
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: e9e9cdcd63873ade4d9d828309f8b2d4b5b874e0
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860254"
---
# <a name="what-are-sql-server-big-data-clusters"></a>SQL Server ビッグ データ クラスターとは

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

以降で[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]、ビッグ データの SQL Server クラスターでは、Kubernetes で実行されている SQL Server、Spark、および HDFS のコンテナーの拡張性の高いクラスターをデプロイできます。 これらのコンポーネントを使用すると、読み取り、書き込み、および TRANSACT-SQL または Spark からビッグ データの処理、結合および価値の高いリレーショナル データを大量のビッグ データ分析を簡単にすることができますを並行して実行されます。

新機能と最新のリリースの既知の問題の詳細については、次を参照してください。、[リリース ノート](release-notes-big-data-cluster.md)します。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="scenarios"></a>シナリオ

SQL Server のビッグ データ クラスターでは、ビッグ データと対話する方法の柔軟性を提供します。 外部データ ソースのクエリ、SQL Server、またはクラスターを複数の外部データ ソースからデータを照会して管理されている HDFS のビッグ データを格納できます。 AI、機械学習、およびその他の分析タスクに、このデータを使用できます。 次のセクションでは、これらのシナリオに関する詳細を提供します。

### <a name="data-virtualization"></a>データの仮想化

利用して[SQL Server PolyBase](../relational-databases/polybase/polybase-guide.md)、ビッグ データの SQL Server クラスターは移動またはデータをコピーすることがなく外部データ ソースを照会できます。 [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] データ ソースには、新しいコネクタが導入されています。

![データの仮想化](media/big-data-cluster-overview/data-virtualization.png)

### <a name="data-lake"></a>Data lake

SQL Server のビッグ データ クラスターには、スケーラブルな HDFS が含まれています。*記憶域プール*します。 複数の外部ソースから取り込まれる可能性のあるビッグ データを格納するために使用できます。 ビッグ データ クラスターで HDFS のビッグ データが保存されると、分析、データのクエリし、リレーショナル データと組み合わせることとことができます。

![Data lake](media/big-data-cluster-overview/data-lake.png)

### <a name="scale-out-data-mart"></a>スケール アウト データ マート

SQL Server のビッグ データ クラスターは、スケール アウトのコンピューティングとデータの分析のパフォーマンスを向上させるためにストレージを提供します。 さまざまなソースからデータを取り込みし、分散*データ プール*さらに詳しい分析のキャッシュとしてのノード。

![データ マート](media/big-data-cluster-overview/data-mart.png)

### <a name="integrated-ai-and-machine-learning"></a>統合された AI と機械学習

SQL Server のビッグ データ クラスターには、AI と機械学習タスクに HDFS の記憶域プールおよびデータ プールに格納されたデータが有効にします。 R、Python、Scala、または Java を使用して、SQL Server では、組み込みの AI ツールと同様に Spark を使用できます。

![AI と ML](media/big-data-cluster-overview/ai-ml-spark.png)

### <a name="management-and-monitoring"></a>管理と監視

管理と監視は、コマンド ライン ツール、Api、管理者ポータルでは、動的管理ビューの組み合わせを通じて提供されます。

[クラスター管理者ポータル](cluster-admin-portal.md)は、クラスター内のポッドの正常性と状態を表示する web インターフェイスです。 Log analytics と監視ダッシュ ボードの他のダッシュ ボードへのリンクも提供します。

Azure Data Studio を使用して、ビッグ データ クラスター上のさまざまなタスクを実行することができます。 これは、オプションが有効で、新しい**SQL Server 2019 拡張機能 (プレビュー)** します。 この拡張機能を提供します。

- 一般的な管理タスクの組み込みのスニペットです。
- HDFS を参照する機能は、ファイルのアップロード、ファイルをプレビューし、ディレクトリを作成します。
- 機能を作成するには、開くと互換性のある Jupyter notebook を実行します。
- データの仮想化ウィザード外部データ ソースの作成を簡略化します。

## <a id="architecture"></a> アーキテクチャ

SQL Server のビッグ データ クラスターはクラスターによって調整される Linux コンテナーの場合、 [Kubernetes](https://kubernetes.io/docs/concepts/)します。

### <a name="kubernetes-concepts"></a>Kubernetes の概念

Kubernetes は、ニーズに合わせてコンテナーのデプロイでスケールできる、オープン ソース コンテナー オーケストレーターです。 次の表では、Kubernetes の重要な用語を定義します。

|||
|:--|:--|
| **Cluster** | Kubernetes クラスターは、一連のノードと呼ばれるマシンです。 1 つのノードがクラスターを制御し、マスター ノードが指定されます。残りのノードは、ワーカー ノードです。 Kubernetes マスターは、ワーカー間の作業を配布して、クラスターの正常性を監視します。 |
| **[Node]** | ノードには、コンテナー化されたアプリケーションが実行されます。 物理マシンまたは仮想マシンのいずれかを指定できます。 Kubernetes クラスターには、物理マシンと仮想マシン ノードの組み合わせを含めることができます。 |
| **pod 型** | ポッドは、Kubernetes のデプロイのアトミック単位です。 ポッドは、1 つまたは複数のコンテナーの論理グループ-リソース必要なアプリケーションの実行に関連付けられているとします。 それぞれのポッドが; ノードで実行します。ノードには、1 つまたは複数のポッドを実行できます。 Kubernetes マスターは、クラスター内のノードにポッドを自動的に割り当てます。 |
| &nbsp; ||

ビッグ データの SQL Server クラスター、Kubernetes は SQL Server のビッグ データ クラスター; の状態を担当Kubernetes で、ビルド、クラスター ノードを構成およびノードにポッドを割り当てます、および、クラスターの正常性を監視します。

### <a name="big-data-clusters-architecture"></a>ビッグ データ クラスターのアーキテクチャ

クラスター内のノードが 3 つの論理面に配置されます: コントロール プレーン、コンピューティング、プレーンとデータ プレーンです。 各プレーンでは、クラスターにさまざまな役割を持っています。 SQL Server のビッグ データ クラスター内のすべての Kubernetes ノードが少なくとも 1 つの平面のコンポーネントのポッドをホストしています。

![アーキテクチャの概要](media/big-data-cluster-overview/architecture-diagram-planes.png)

### <a id="controlplane"></a> コントロール プレーン

コントロール プレーンでは、管理とクラスターのセキュリティを提供します。 Kubernetes マスターが含まれている、*マスター インスタンスの SQL Server*、および Hive メタストアと Spark ドライバーなどの他のクラスター レベル サービス。

### <a id="computeplane"></a> 平面を計算します。

コンピューティングの面では、クラスターにコンピューティング リソースを提供します。 SQL Server を Linux のポッドで実行されるノードが含まれています。 コンピューティング平面のポッドが分割*プールのコンピューティング*特定のタスクを処理します。 コンピューティング プールが果たすことができる、 [PolyBase](../relational-databases/polybase/polybase-guide.md)ソースなどさまざまなデータとして HDFS、Oracle、MongoDB、または Teradata に対する分散クエリのスケール アウト グループ。

### <a id="dataplane"></a> データ プレーン

データ プレーンは、データの永続化とキャッシュに使用されます。 SQL データのプールと記憶域プールが含まれています。  SQL のデータ プールは、Linux 上の SQL Server を実行している 1 つまたは複数のポッドで構成されます。 SQL クエリまたは Spark ジョブからデータを取り込むために使用されます。 ビッグ データの SQL Server クラスターのデータ マートは、データのプールに保存されます。 記憶域プールは、Linux、Spark、および HDFS 上の SQL Server から成る記憶域プールのポッドで構成されます。 SQL Server のビッグ データ クラスター内のすべての記憶域ノードは、HDFS クラスターのメンバーです。

> [!TIP]
> ビッグ データ クラスターのアーキテクチャとインストールの詳細については、次を参照してください。[ワーク ショップ。Microsoft SQL Server のビッグ データ クラスター アーキテクチャ](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)します。

## <a name="next-steps"></a>次のステップ

SQL Server のビッグ データ クラスターは、SQL Server 2019 Early Adoption Program を通じて限定パブリック プレビューとして利用可能なは first です。 アクセス権を要求するには、登録[ここ](https://aka.ms/eapsignup)、ビッグ データ クラスターに関心を指定します。 Microsoft はすべての要求をトリアージし、できるだけ早く対応します。
