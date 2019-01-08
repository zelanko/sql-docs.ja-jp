---
title: SQL Server の R と Python のチュートリアル - SQL Server Machine Learning
description: 例と、R と Python の SQL Server Machine Learning Services でのスクリプト作成に関するチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 69009a5a11e7f7985729656ae9df6c60bcba8037
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596933"
---
# <a name="sql-server-machine-learning-tutorials-in-r-and-python"></a>R および Python での SQL Server Machine Learning のチュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では包括的な一連のチュートリアルと、機械学習の機能を示すコード サンプル[SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)または[SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)します。 

+ クイック スタートでは、最小限の労力で高速な探索の組み込みのデータまたはデータのないを使用します。
+ チュートリアルに進むと詳細のタスク、さらに大きなデータセット、および長い説明。
+ サンプルとソリューションは、コードを開始する概念およびサポート技術情報のギャップを埋めるためのレッスンを下位の操作を使用する開発者です。

高パフォーマンスのデータの同じ操作のコンテキスト、実行し、カスタム コードをデプロイするための SQL Server ストアド プロシージャを使用する方法、および Microsoft R を呼び出す方法で常駐のリレーショナル データを R と Python ライブラリと Python ライブラリを使用する方法について説明しますサイエンスと機械学習タスク。

最初の手順としてバックアップする Microsoft の基本概念を確認して SQL Server と R と Python の統合。

## <a name="concepts"></a>概念

データベース内分析は、データベース エンジンへのアドオンとして SQL Server Machine Learning Services または SQL Server 2016 R Services (R の場合のみ) をインストールすると、SQL Server の R と Python のネイティブ サポートを参照します。 R と Python の統合には、基本のオープン ソース ディストリビューションと高パフォーマンスの分析用の Microsoft 固有のライブラリが含まれます。

コードは、アーキテクチャ観点から、データベース エンジンの整合性を保持するために、ボックスに、外部プロセスとして実行されます。 ただし、すべてのデータ アクセスしセキュリティは、SQL Server データベース ロールを介してとアクセス許可は、SQL Server にアクセス権を持つ任意のアプリケーションのことを意味は、ストアド プロシージャとしてデプロイまたはシリアル化し、トレーニング済みモデルを SQL に保存するときに、R と Python スクリプトにアクセスできます。サーバーのデータベースです。

他の Microsoft 製品での同等の言語サポートと SQL Server で R と Python 間の主な相違点をサポートし、サービスが含まれます。

+ ストアド プロシージャまたは二項モデルとして「パッケージ」のコードに機能します。
+ SQL Server プログラム ファイルをローカルにインストールされている Microsoft R と Python ライブラリを呼び出すコードを記述します。
+ SQL Server のデータベースのセキュリティ アーキテクチャを R と Python のソリューションに適用されます。
+ SQL Server インフラストラクチャを活用して、カスタム ソリューションの管理をサポートします。

## <a name="quickstarts"></a>クイック スタート

ここで T-SQL から R または Python を実行する方法と、SQL の運用環境用の R と Python コードを操作する方法について説明します。

+ [Python:T-SQL を使用して Python を実行します。](run-python-using-t-sql.md)
+ [R:R と SQL での hello World](rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [R:入力と出力を処理します。](rtsql-working-with-inputs-and-outputs.md)
+ [R:データ型とオブジェクトを処理します。](rtsql-r-and-sql-data-types-and-data-objects.md)
+ [R:R 関数の使用](rtsql-using-r-functions-with-sql-server-data.md)
+ [R:予測モデルを作成します。](rtsql-create-a-predictive-model-r.md)
+ [R:予測し、プロットをモデルから](rtsql-predict-and-plot-from-model.md)

## <a name="tutorials"></a>チュートリアル

について詳しく見て、マイクロソフトのパッケージとローカルからリモート コンピューティング コンテキストに移行より専門的な操作を実行して、R、Python、T-SQL での最初の経験をビルドします。

+ [Python のチュートリアル](sql-server-python-tutorials.md)
+ [R のチュートリアル](sql-server-r-tutorials.md)

<a name ="bkmk_samples"></a>

## <a name="samples"></a>サンプル

これらのサンプルとデモの SQL Server と R Server 開発チームによって提供されることは、実際のアプリケーションで埋め込み分析を使用する方法を選択します。

| リンク | 説明 | 
|------|-------------|
| [顧客を実行する R と SQL Server を使用してクラスタ リング](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | 売上データに基づき顧客をセグメントの教師なし学習を使用します。 この例では、Microsoft R からスケーラブルな rxKmeans アルゴリズムを使用して、クラスタ リング モデルを構築します。 |
| [顧客を実行する Python と SQL Server を使用してクラスタ リング](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | K-平均法アルゴリズムを使用して、顧客の教師なしのクラスタ リングを実行する方法について説明します。 この例では、Python 言語でのデータベースを使用します。| SQL Server 2017 |
| [R と SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | スキー レンタル ビジネスを予測する機械学習、今後のレンタルを今後の需要を満たすためには、ビジネスの計画と人員配置を一層使用方法について説明します。 この例では、Microsoft のアルゴリズムを使用して、ロジスティック回帰、デシジョン ツリー モデルを構築します。 | 
| [Python と SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | 今後の需要を計画するために、Python を使用して、スキー レンタル分析アプリケーションをビルドします。 この例は、新しい Python ライブラリを使用して**revoscalepy**、線形回帰モデルを作成します。 | 
| [SQL Server Machine Learning Services で Tableau を使用する方法](https://blogs.msdn.microsoft.com/mlserver/2017/12/14/how-to-use-tableau-with-sql-server-machine-learning-services-with-r-and-python/) | ソーシャル メディアを分析し、SQL Server を R. Tableau グラフの作成 | 

<a name="bkmk_solutions"></a>

## <a name="solution-templates"></a>ソリューション テンプレート

Microsoft データ サイエンス チームは、一般的なシナリオ ソリューションをすぐに使用できるカスタマイズ可能なソリューション テンプレートを提供しています。 各ソリューションは、特定のタスクまたは業界の問題にお応えします。 SQL server、または Azure Machine Learning などのクラウド環境で実行するほとんどのソリューションが設計されています。 他のソリューションは、Microsoft R Server または Machine Learning Server を使用して、または Spark や Hadoop のクラスターで linux を実行できます。

すべてのコードは、トレーニングおよび SQL Server のストアド プロシージャを使用してスコア付けのモデルをデプロイする方法の指示と共に提供されます。

+ [不正行為の検出](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [顧客離れ予測](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [予測メンテナンス](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [病院入院を予測します。](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

詳細については、「[Machine Learning Templates with SQL Server 2016 R Services](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/)」 (SQL Server 2016 R Services の機械学習テンプレート) を参照してください。

