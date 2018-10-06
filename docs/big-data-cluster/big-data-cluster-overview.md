---
title: SQL Server 2019 ビッグ データ クラスターとは何ですか。 | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: overview
ms.prod: sql
ms.openlocfilehash: cf13ea198a5a40a5d67d41fea2f8f9b9b3b5434d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796416"
---
# <a name="what-is-sql-server-2019-big-data-clusters"></a>SQL Server 2019 ビッグ データ クラスターとは何ですか。

以降で[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]、ビッグ データの SQL Server クラスターでは、Kubernetes で実行されている SQL Server、Spark、および HDFS の Docker コンテナーの拡張性の高いクラスターをデプロイできます。 これらのコンポーネントを使用すると、読み取り、書き込み、および TRANSACT-SQL または Spark からビッグ データの処理に並行して実行されます。 ビッグ データの SQL Server クラスターを使用すると、簡単に結合し、価値の高い大規模のビッグ データをリレーショナル データを分析できます。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="scenarios"></a>シナリオ

SQL Server のビッグ データ クラスターでは、ビッグ データと対話する方法の柔軟性を提供します。 外部データ ソースのクエリ、SQL Server、または複数のデータ ソースからデータをプルによって管理されるクラスターに HDFS のビッグ データを格納できます。 AI、機械学習、およびその他の分析タスクに、このデータを使用できます。 次のセクションでは、これらのシナリオに関する詳細を提供します。

### <a name="data-virtualization"></a>データの仮想化

利用して[SQL Server PolyBase](../relational-databases/polybase/polybase-guide.md)、ビッグ データの SQL Server クラスターは、データをインポートせずに外部データ ソースを照会できます。 [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] データ ソースには、新しいコネクタが導入されています。

![データの仮想化](media/big-data-cluster-overview/data-virtualization.png)

### <a name="data-lake"></a>Data lake

SQL Server のビッグ データ クラスターには、スケーラブルな HDFS が含まれています。*記憶域プール*します。 これは、直接可能性のある複数の外部ソースから取り込まれたビッグ データの格納に使用できます。 ビッグ データ クラスターに 1 回分析しデータを照会して、価値の高いリレーショナル データと結合できます。

![Data lake](media/big-data-cluster-overview/data-lake.png)

### <a name="scale-out-data-mart"></a>スケール アウト データ マート

SQL Server のビッグ データ クラスターは、スケール アウトのコンピューティングとデータの分析のパフォーマンスを向上させるためにストレージを提供します。 さまざまなソースからデータを取り込みし、分散*データ プール*ノードをさらに詳しく分析します。

![データ マート](media/big-data-cluster-overview/data-mart.png)

### <a name="integrated-ai-and-machine-learning"></a>統合された AI と機械学習

SQL Server のビッグ データ クラスターには、AI と機械学習データ記憶域プールの HDFS とのデータ プールに格納されたデータでのタスクが有効にします。 R、Python、または Java を使用して、SQL Server では、組み込みの AI ツールと同様に Spark を使用できます。

![AI と ML](media/big-data-cluster-overview/ai-ml-spark.png)

### <a name="management-and-monitoring"></a>管理と監視

管理と監視は、オープン ソース コンポーネント、SQL Server ツール、および動的管理ビューの組み合わせを通じて提供されます。

[クラスター管理ポータル](cluster-admin-portal.md)は、クラスター内のポッドの正常性と状態を表示する web インターフェイスです。 Grafana と Kibana によって提供される他のダッシュ ボードへのリンクも提供します。

Azure Data Studio を使用して、ビッグ データ クラスター上のさまざまなタスクを実行することができます。 これは、オプションが有効で、新しい**SQL Server 2019 拡張機能 (プレビュー)** します。 この拡張機能を提供します。

- 一般的な管理タスクの組み込みのスニペットです。
- コンピューティング プールの数とジョブの実行の状態についてレポートします。
- HDFS と Spark ジョブの状態についてレポートします。
- HDFS を参照する機能は、ファイルのアップロード、ファイルをプレビューし、ディレクトリを作成します。
- 機能を作成するには、開くと互換性のある Jupyter notebook を実行します。
- データの仮想化ウィザード外部データ ソースの作成を簡略化します。

## <a id="architecture"></a> アーキテクチャ

SQL Server のビッグ データ クラスターによって調整される Linux ノードのクラスターは、 [Kubernetes](https://kubernetes.io/docs/concepts/)します。

### <a name="kubernetes-concepts"></a>Kubernetes の概念

Kubernetes は、ニーズに合わせてコンテナーのデプロイでスケールできる、オープン ソース コンテナー オーケストレーターです。 次の表では、Kubernetes の重要な用語を定義します。

|||
|--|--|
| **Cluster** | Kubernetes クラスターは、一連のノードと呼ばれるマシンです。 1 つのノードがクラスターを制御し、マスター ノードが指定されます。残りのノードは、ワーカー ノードです。 Kubernetes マスターは、ワーカー間の作業を配布して、クラスターの正常性を監視します。 |
| **[Node]** | ノードには、コンテナー化されたアプリケーションが実行されます。 物理マシンまたは仮想マシンのいずれかを指定できます。 Kubernetes クラスターには、物理マシンと仮想マシン ノードの組み合わせを含めることができます。 |
| **Pod 型** | ポッドは、Kubernetes のアトミック単位です。 ポッドは、1 つまたは複数のコンテナーの論理グループ- と関連リソース: アプリケーションを実行するために必要です。 それぞれのポッドが; ノードで実行します。ノードには、1 つまたは複数のポッドを実行できます。 Kubernetes マスターは、クラスター内のノードにポッドを自動的に割り当てます。 |

ビッグ データの SQL Server クラスター、Kubernetes は SQL Server のビッグ データ クラスター; の状態を担当Kubernetes で、ビルド、クラスター ノードを構成およびノードにポッドを割り当てます、および、クラスターの正常性を監視します。

### <a name="big-data-clusters-architecture"></a>ビッグ データ クラスターのアーキテクチャ

クラスター内のノードが 3 つの論理面に配置されます: コントロール プレーン、計算ウィンドウ、およびデータ プレーンです。 各プレーンでは、クラスターにさまざまな役割を持っています。 SQL Server のビッグ データ クラスター内のすべての Kubernetes ノードは、少なくとも 1 つの平面のメンバーです。

![アーキテクチャの概要](media/big-data-cluster-overview/architecture-diagram-planes.png)

### <a id="controlplane"></a> コントロール プレーン

コントロール プレーンでは、管理とクラスターのセキュリティを提供します。 Kubernetes マスターが含まれている、*マスター インスタンスの SQL Server*、および Hive メタストアと Spark ドライバーなどの他のクラスター レベル サービス。

### <a id="computeplane"></a> 平面を計算します。

コンピューティングの面では、クラスターにコンピューティング リソースを提供します。 SQL Server を Linux のポッドで実行されるノードが含まれています。 コンピューティング平面のポッドが分割*プールのコンピューティング*特定のタスクを処理します。 コンピューティング プールが果たすことができる、 [PolyBase](../relational-databases/polybase/polybase-guide.md)さまざまなデータ ソースに対する分散クエリのスケール アウト グループ: HDFS、Oracle、MongoDB、Teradata など。

### <a id="dataplane"></a> データ プレーン

データ プレーンは、データの永続化とキャッシュに使用されます。 SQL データのプールと記憶域ノードが含まれています。  SQL のデータ プールは、Linux 上の SQL Server を実行している 1 つまたは複数のノードで構成されます。 SQL クエリまたは Spark ジョブからデータを取り込むために使用されます。 ビッグ データの SQL Server クラスターのデータ マートは、データのプールに保存されます。 記憶域プールは、記憶域ノードから成る Linux、Spark、および HDFS 上の SQL Server で構成されます。 SQL Server のビッグ データ クラスター内のすべての記憶域ノードは、HDFS クラスターのメンバーです。

## <a name="next-steps"></a>次の手順

SQL Server のビッグ データ クラスターは、SQL Server 2019 Early Adoption Program を通じて限定パブリック プレビューとして利用可能なは first です。 アクセス権を要求するには、登録[ここ](https://aka.ms/eapsignup)、ビッグ データ クラスターに関心を指定します。 Microsoft はすべての要求をトリアージし、できるだけ早く対応します。