---
title: "マイクロソフトの機械学習のサービス |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 10/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 341e80f5-3b59-4122-bbaa-969d7904297d
caps.latest.revision: 23
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 246ea9f306c7d99b835c933c9feec695850a861b
ms.openlocfilehash: ddc9b3f17afe1f9d4c811e4a5871f48a3a08de7f
ms.contentlocale: ja-jp
ms.lasthandoff: 10/13/2017

---
# <a name="microsoft-machine-learning-services"></a>マイクロソフトの機械学習サービス

Microsoft Machine Learning のサービスの目的は、machine learning のサービスを使用するアプリケーションと機械学習タスクとツールを統合するため、拡張可能な拡張性の高いプラットフォームを提供します。 プラットフォーム必要がありますのニーズを満たすすべてのユーザー データの開発と、分析プロセスに関連するからデータ科学者、アーキテクトやデータベース管理者にします。

主な利点は次のとおりです。

+ スケーラブルな分析
+ 複数のプラットフォームとの「1 回の記述、任意の場所の展開」のソリューションの計算コンテキスト
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
+ **Microsoft Machine Learning Server**遅延 2017 の計画的なサポートされている他のプラットフォームに展開を含む、Windows サーバーで R、Python の展開をサポートします。

### <a name="benefits"></a>利点

Microsoft Machine Learning のサービスは、データベースと同じコンピューター上で実行する R を許可することで、計算をデータに表示されます。 外部で実行する、スタート パッドの信頼されたサービスが含まれている、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を処理し、R または Python ランタイムと安全に通信します。

SQL Server の Machine Learning のサービスを使用して、モデルのトレーニング、プロットを生成、スコアリングを実行して間でデータを簡単に移動[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と R または Python です。

テストとソリューションの開発は、データ サイエンティストは、サーバー上のコードを安全に実行するリモート開発コンピューターからスクリプトを送信できますか、完成したソリューションを SQL ストアド プロシージャにマシン ラーニング コードを埋め込むことで SQL Server に展開できます。

SQL Server の機械学習をインストールするときに、オープン ソース R または Python 言語だけでなく Microsoft によって提供される拡張性の高い R、Python のライブラリの分布を取得します。 SQL Server データベース エンジンには、接続性を強化し、R、Python などの外部の言語でより安全な通信をより速く、ことを確認するように設計の新しいコンポーネントも含まれます。

### <a name="where-to-get-it"></a>入手場所

開始するには、これらのリソースを参照してください。

+ [SQL Server R サービス](sql-server-r-services.md)
+ [SQL Server の Python サービス](../python/sql-server-python-services.md)
+ [機械学習のチュートリアル](../tutorials/machine-learning-services-tutorials.md)

> [!NOTE]
> Python のサポートは、SQL Server 2017 でのみ提供されます。 

## <a name="machine-learning-server-standalone-and-microsoft-r-server-standalone"></a>Machine Learning Server (スタンドアロン) および Microsoft R Server (スタンドアロン)

このスタンドアロン サーバー システムでは、複数のプラットフォームおよび Linux および HD Insight など、複数のエンタープライズ データ ソースを使用して分散型スケーラブル R ソリューションをサポートしています。 SQL Server との統合を必要としない場合は、迅速な開発、デプロイ、し、機械学習ソリューションの使用を有効にする R サーバーをインストールできます。 SQL Server インスタンスに関連付けられた R コンポーネントをアップグレードしは r です。 最新バージョンを取得する R Server のインストーラーを使用することもできます。

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

Azure Machine Learning Studio で独自のワークスペースを作成する場合は、400 を超えるプリロードされている R パッケージへのアクセスがあります。 標準的な CRAN R ディストリビューションまたは Microsoft R Open を使用して R を配置する、R を使用する実験を作成するときにも選択できます。 でも、独自の R パッケージを作成し、カスタム モジュールとして実行する Azure にアップロードできます。

詳細については、次のリソースをご覧ください。

+ [R を使用した実験の拡張](https://docs.microsoft.com/azure/machine-learning/machine-learning-extend-your-experiment-with-r)
+ [Azure Machine Learning でカスタム R モジュールを作成者](https://docs.microsoft.com/azure/machine-learning/machine-learning-custom-r-modules)

Azure ML で提供されるアルゴリズムの多くは今すぐ MicrosoftML パッケージの一部として、Microsoft Machine Learning のサービスに含まれます。 詳細については、次を参照してください。 [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)です。

Azure Machine Learning は、データ サイエンティストと開発者を作成、トレーニング、および Web サービスを使用してモデルを配置する必要があるもう 1 つの便利なプラットフォームです。 ソリューションを発行することができます、 [Machine Learning Marketplace](http://datamarket.azure.com/browse/data?category=machine-learning)です。

### <a name="data-science-virtual-machines"></a>データ サイエンス仮想マシン

Microsoft Azure でプレインストールと構成済みバージョンの [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)] をデプロイできます。これにより、オンプレミスの完全に構成されたシステムをセットアップすることなく、データ探索の開始やクラウドでの即時モデリングが容易になります。

Azure Marketplace には、データ サイエンスをサポートする次のようないくつかの仮想マシンが含まれています。

+ **Microsoft データ サイエンス仮想マシン** には、Microsoft R Server、Python (Anaconda ディストリビューション)、Jupyter ノートブック サーバー、Visual Studio Community エディション、Power BI Desktop、Azure SDK、および SQL Server Express Edition が構成されています。

+ **Microsoft R Server 2016 for Linux** には、最新バージョンの R Server (バージョン 9.0.1) が含まれています。 別の Vm は、CentOS バージョン 7.2 と 16.04 バージョン Ubuntu 利用できます。

+ **R サーバーのみ SQL Server 2016 Enterprise**仮想マシンには、新しいソフトウェアの最新のライフ サイクルのライセンス モデルをサポートする 9.0.1 R Server のスタンドアロン インストーラーが含まれています。

> [!TIP]
> 新しい[データ サイエンス VM の Windows Server 2016](http://aka.ms/dsvm/win2016) GPU のバージョンの CNTK などの一般的な深層学習フレームワークを提供します。 インストール済みのツールには、GPU NVIDIA ドライバー、CUDA Toolkit 8.0、および GPU のワークロードの NVIDIA cuDNN ライブラリが含まれます。 わずか数分間、CPU または CPU と GPU のいずれかで実行できる深層学習モデルを構築するための完全な環境を使用することができます。

## <a name="next-steps"></a>次の手順

[Machine Learning のサービスの概要](getting-started-with-sql-server-r-services.md)

[Machine Learning のサーバーの概要](getting-started-with-microsoft-r-server-standalone.md)

[SQL Server データベース エンジンをインストールします。](../../database-engine/install-windows/install-sql-server-database-engine.md)

