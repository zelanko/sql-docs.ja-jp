---
title: "マイクロソフトの機械学習のサービス |Microsoft ドキュメント"
ms.date: 11/09/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 341e80f5-3b59-4122-bbaa-969d7904297d
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 40c76cba27559c8fcc314ce4c9761ee42edacac0
ms.sourcegitcommit: 657d18fc805512c9574b2fe7451310601b9d78cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="microsoft-machine-learning-services"></a>Microsoft Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Microsoft Machine Learning のサービスの目的は、machine learning のサービスを使用するアプリケーションと機械学習タスクとツールを統合するため、拡張可能な拡張性の高いプラットフォームを提供します。 プラットフォーム必要がありますのニーズを満たすすべてのユーザー データの開発と、分析プロセスに関連するからデータ科学者、アーキテクトやデータベース管理者にします。

主な利点は次のとおりです。

+ スケーラブルな分析
+ 複数のプラットフォームとの「1 回のコードは、任意の場所の展開」のソリューションの計算コンテキスト
+ データを分析することでデータの移動やデータのリスクを回避できます。
+ データ サイエンティストは、独自のツールと言語を選択できます。
+ Microsoft のエンタープライズ用機能とオープン ソースの優れた機能を統合し、します。
+ 管理の簡略化
+ 簡単に展開し、予測モデルを使用します。

## <a name="in-database-analytics-with-sql-server"></a>データベース内の SQL Server での分析

SQL Server 2016 では、Microsoft は、一般的なオープン ソース R 言語をビジネス アプリケーションと統合するための 2 つのサーバー プラットフォームを起動しました。

+ **との統合用の**SQL Server R Services (データベース内) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
+ **Microsoft R Server**、Windows および Linux サーバーでエンタープライズ レベルの R のデプロイの

SQL Server の 2017 でよく使われる Python 言語のサポートを反映するように名前が変更されました。

+ **SQL Server マシン ラーニング Services (In-database)**データベース内の分析のため、R、Python の両方をサポートしています。
+ **Microsoft Machine Learning Server** Windows、Linux、および HDInsight Spark Hadoop クラスターで R、Python の展開をサポートします。

### <a name="benefits"></a>利点

Microsoft Machine Learning のサービスは、データベースと同じコンピューター上で実行する R を許可することで、計算をデータに表示されます。 外部で実行する、スタート パッド サービスが含まれている、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を処理し、R または Python ランタイムと安全に通信します。

SQL Server の Machine Learning のサービスを使用して、モデルのトレーニング、プロットを生成、スコアリングを実行して間でデータを安全に移動[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と R または Python です。

データ サイエンティストは、テスト、およびソリューションの開発では、リモート開発コンピューターからスクリプトを送信でき、データを移動せず、サーバーで、コードを実行することができます。 開発者は、SQL ストアド プロシージャにマシン ラーニング コードを埋め込むことで、SQL Server に完成したソリューションを展開できます。

SQL Server の機械学習をインストールするときに、オープン ソース R または Python 言語だけでなく Microsoft によって提供される拡張性の高い R、Python のライブラリの分布を取得します。 SQL Server データベース エンジンには、接続性を強化し、R、Python などの外部の言語でより安全な通信をより速く、ことを確認するように設計の新しいコンポーネントも含まれます。

### <a name="where-to-get-it"></a>入手場所

開始するには、これらのリソースを参照してください。

+ [SQL Server R サービス](sql-server-r-services.md)
+ [SQL Server Python Services](../python/sql-server-python-services.md)
+ [機械学習のチュートリアル](../tutorials/machine-learning-services-tutorials.md)

> [!NOTE]
> Python のサポートは、SQL Server 2017 でのみ提供されます。 

## <a name="machine-learning-server-standalone-and-microsoft-r-server-standalone"></a>Machine Learning Server (スタンドアロン) および Microsoft R Server (スタンドアロン)

このスタンドアロン サーバー システムでは、複数のプラットフォームおよび Linux および HDInsight など、複数のエンタープライズ データ ソースを使用して分散型スケーラブル R ソリューションをサポートしています。 SQL Server との統合を必要としない場合は、迅速な開発、デプロイ、し、機械学習ソリューションの使用を有効にする R サーバーをインストールできます。 SQL Server インスタンスに関連付けられた R コンポーネントをアップグレードしは r です。 最新バージョンを取得する R Server のインストーラーを使用することもできます。

SQL Server 2017 セットアップを使用して Microsoft Machine Learning サーバーをインストールする場合も展開でき、Python アプリケーションを使用します。

詳細については、次を参照してください。 [Microsoft Machine Learning Server](https://docs.microsoft.com/r-server/index)です。

## <a name="related-technologies"></a>関連テクノロジ

Microsoft は、machine learning エコシステム、ツール、プロバイダー、拡張 R パッケージと Python パッケージ、クラウド開発およびサービス プラットフォームでは、統合開発環境などの広範なサポートを提供します。

### <a name="r-tools-for-visual-studio"></a>R Tools for Visual Studio

Visual Studio では、R 言語用の完全な開発環境が提供されます。 プラグインには、エディター、対話型のウィンドウ、プロット、デバッガーなどが含まれます。 R から .NET 言語を使用したり、R.NET や rClr などのオープン ソース ライブラリを介して .NET から R を呼び出したりすることができます。

Visual Studio では、優れた Python 開発環境もあります。 SQL データベース開発ツールにアクセスして活用しつつ、machine learning の言語を使用する簡単な方法はありません。

詳細については、以下をご覧ください。

+ [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)
+ [Python - Visual Studio](https://www.visualstudio.com/vs/python/)

### <a name="azure-machine-learning"></a>Azure Machine Learning

Azure Machine Learning Studio で独自のワークスペースを作成する場合は、400 を超えるプリロードされている R パッケージへのアクセスを取得します。 標準的な CRAN R ディストリビューションまたは Microsoft R Open を使用して R を配置する、R を使用する実験を作成するときにも選択できます。 でも、独自の R パッケージを作成し、カスタム モジュールとして実行する Azure にアップロードできます。

Azure ML で提供されるアルゴリズムの多くは今すぐ MicrosoftML パッケージの一部として、Microsoft Machine Learning のサービスに含まれます。 詳細については、次を参照してください。 [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)です。

Azure Machine Learning は、データ サイエンティストと開発者を作成、トレーニング、および Web サービスを使用してモデルを配置する必要があるもう 1 つの便利なプラットフォームです。 ソリューションを発行することができます、 [Machine Learning Marketplace](http://datamarket.azure.com/browse/data?category=machine-learning)です。

Azure Machine Learning サービスで魅力的な変更の詳細については、専門的なデータ サイエンティストをサポートするためにこれらのリソース参照してください。

+ [Azure Machine Learning とは何ですか。](https://docs.microsoft.com/azure/machine-learning/preview/overview-what-is-azure-ml)
+ [モデルの管理機能](https://docs.microsoft.com/azure/machine-learning/preview/model-management-overview)

### <a name="data-science-virtual-machines"></a>データ サイエンス仮想マシン

Microsoft Azure でプレインストールと構成済みバージョンの [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)] をデプロイできます。これにより、オンプレミスの完全に構成されたシステムをセットアップすることなく、データ探索の開始やクラウドでの即時モデリングが容易になります。

Azure Marketplace には、データ サイエンスをサポートしているいくつかのバーチャル マシンが含まれています。

+ **Microsoft データ サイエンス仮想マシン**としても、Python (Anaconda ディストリビューション)、Jupyter ノートブック サーバー、Visual Studio Community エディション、Power BI Desktop、Azure SDK、および SQL Machine Learning のサーバーで構成サーバー。

    新しい[データ サイエンス VM の Windows Server 2016](http://aka.ms/dsvm/win2016) GPU のバージョンの CNTK などの一般的な深層学習フレームワークを提供します。 インストール済みのツールには、GPU NVIDIA ドライバー、CUDA Toolkit 8.0、および GPU のワークロードの NVIDIA cuDNN ライブラリが含まれます。 わずか数分間、CPU または CPU と GPU のいずれかで実行できる深層学習モデルを構築するための完全な環境を使用することができます。

+ R Server または Machine Learning のサーバーの場合は、for Linux または Windows server の 2016 Microsoft Machine Learning サーバー 2017 を勧めします。

+ SQL Server の機械学習で Azure のイメージを取得することをお勧めが含まれている仮想マシン サービスのいずれかの**SQL Server 2017**です。 イメージを選択すると追加の推奨事項に従って層とサービスのレベルは、VM が machine learning のワークロードをサポートできることを確認してください。

## <a name="next-steps"></a>次の手順

[Machine Learning のサービスの概要](getting-started-with-sql-server-r-services.md)

[Machine Learning のサーバーの概要](getting-started-with-microsoft-r-server-standalone.md)

[SQL Server データベース エンジンをインストールします。](../../database-engine/install-windows/install-sql-server-database-engine.md)
