---
title: SQL Server Machine Learning Services のチュートリアル |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b692b9660c3caec18c689f56ba382f8df194a9cc
ms.sourcegitcommit: b1990ec4491b5a8097c3675334009cb2876673ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2018
ms.locfileid: "49384127"
---
# <a name="tutorials-for-sql-server-machine-learning-services"></a>SQL Server Machine Learning Services のチュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、チュートリアル、デモ、および SQL Server 2016 または SQL Server 2017 での機械学習機能を使用するサンプル アプリケーションの包括的な一覧を示します。 ここで T-SQL から R または Python を実行する方法、リモートとローカル コンピューティング コンテキストを使用する方法、および運用環境の SQL R と Python コードを最適化する方法について説明します。

+ [Python のチュートリアル](../tutorials/sql-server-python-tutorials.md)

+ [R のチュートリアル](../tutorials/sql-server-r-tutorials.md)

要件と設定を取得する方法の詳細については、次を参照してください。[の前提条件](#bkmk_prerequisites)します。

## <a name="samples-and-solutions"></a>サンプルとソリューション

+ [サンプル](#bkmk_samples) 

    SQL Server 開発チームからこれらの実際のシナリオでは、アプリケーションに機械学習を埋め込む方法を示します。 すべてのサンプルには、実稼働環境でのダウンロード、変更、および使用するコードが含まれます。

+ [ソリューション](#bkmk_solutions) 

    Microsoft データ サイエンス チームからのテンプレートはカスタマイズ可能な機械学習をすぐに開始するためです。 各ソリューションは、特定のタスクまたは業界の問題にお応えします。 SQL server、または Azure Machine Learning などのクラウド環境で実行するほとんどのソリューションが設計されています。 他のソリューションは、Microsoft R Server または Machine Learning Server を使用して、または Spark や Hadoop のクラスターで linux を実行できます。

### <a name ="bkmk_samples"></a>SQL Server 製品サンプル

これらのサンプルとデモの SQL Server と R Server 開発チームによって提供されることは、実際のアプリケーションで埋め込み分析を使用する方法を選択します。

| リンク | 説明 | 適用対象 |
|------|-------------|------------|
| [顧客を実行する R と SQL Server を使用してクラスタ リング](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | 売上データに基づき顧客をセグメントの教師なし学習を使用します。 この例では、Microsoft R からスケーラブルな rxKmeans アルゴリズムを使用して、クラスタ リング モデルを構築します。 | SQL Server 2016 または SQL Server 2017 |
| [顧客を実行する Python と SQL Server を使用してクラスタ リング](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | K-平均法アルゴリズムを使用して、顧客の教師なしのクラスタ リングを実行する方法について説明します。 この例では、Python 言語でのデータベースを使用します。| SQL Server 2017 |
| [R と SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | スキー レンタル ビジネスを予測する機械学習、今後のレンタルを今後の需要を満たすためには、ビジネスの計画と人員配置を一層使用方法について説明します。 この例では、Microsoft のアルゴリズムを使用して、ロジスティック回帰、デシジョン ツリー モデルを構築します。 | SQL Server 2016 または SQL Server 2017 |
| [Python と SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | 今後の需要を計画するために、Python を使用して、スキー レンタル分析アプリケーションをビルドします。 この例は、新しい Python ライブラリを使用して**revoscalepy**、線形回帰モデルを作成します。 | SQL Server 2017 |
| [SQL Server Machine Learning Services で Tableau を使用する方法](https://blogs.msdn.microsoft.com/mlserver/2017/12/14/how-to-use-tableau-with-sql-server-machine-learning-services-with-r-and-python/) | ソーシャル メディアを分析し、SQL Server を R. Tableau グラフの作成 | SQL Server 2016 または SQL Server 2017 |

### <a name="bkmk_solutions"></a>ソリューション テンプレート

Microsoft データ サイエンス チームは、一般的なシナリオ ソリューションをすぐに使用できるソリューション テンプレートを提供しています。 すべてのコードは、トレーニングおよび SQL Server のストアド プロシージャを使用してスコア付けのモデルをデプロイする方法の指示と共に提供されます。

+ [不正行為の検出](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [顧客離れ予測](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [予測メンテナンス](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [病院入院を予測します。](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

詳細については、「[Machine Learning Templates with SQL Server 2016 R Services](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/)」 (SQL Server 2016 R Services の機械学習テンプレート) を参照してください。

## <a name="more-resources-and-reading"></a>複数のリソースと読み取り

+ [なぜして開発したことでしょうか。](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/01/10/sql-server-r-services-why-did-we-build-it/)

    R Services の背後にある本当の話を知りたいです。 この記事の開発と配信元と SQL Server R Services の目的を説明する PM チームからご覧ください。

+ [チュートリアルと Microsoft R のサンプル データ](https://docs.microsoft.com/machine-learning-server/r/tutorial-introduction)

    Microsoft R、およびクイック チュートリアルのこのコレクションで、RevoScaleR パッケージで提供されるものについて説明します。 RevoScaleR のデータ ソースとリモート コンピューティング コンテキストを使用して R コードを一度記述して、どこにでもデプロイする方法について説明します。

+ [MicrosoftML を概要します。](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package)

  高度なモデリングおよび複数の計算コンテキスト用に最適化された、スケーラブルなデータ変換の MicrosoftML パッケージで新しいアルゴリズムを使用する方法について説明します。
