---
title: SQL Server machine learning でのネイティブ スコアリング |Microsoft Docs
description: SQL Server で R または Python で記述された事前トレーニング済みモデルに対して dta 入力のスコアリング、T-SQL の予測関数を使用して予測を生成します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bf8f9a6362b72efddccbf5c2b0e54096c6e86aa7
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2018
ms.locfileid: "40392444"
---
# <a name="native-scoring-using-the-predict-t-sql-function"></a>T-SQL の予測関数を使用して、ネイティブのスコアリング
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

事前トレーニング済みモデルを作成したら、予測値を生成する関数に新しい入力データを渡すことができますか*スコア*します。 SQL Server 2017 Windows または Linux、または Azure SQL Database では、ネイティブ スコアリングをサポートするのに TRANSACT-SQL の PREDICT 関数を使用できます。 T-SQL を使用して呼び出すことができますが、既にトレーニング済みモデルがあることが必要のみです。 

+ ネイティブ スコアリング リアルタイム スコアリングとは
+ しくみ
+ サポートされているプラットフォームと要件

## <a name="what-is-native-scoring-and-how-is-it-different-from-real-time-scoring"></a>ネイティブ スコアリングとは何ですし、リアルタイムのスコア付けの違いがあるでしょうか。

SQL Server 2016 では、Microsoft は、T-SQL から実行する R スクリプトを可能にする機能拡張フレームワークを作成します。 このフレームワークは、単純な関数から複雑な機械学習モデルをトレーニングに至るまで、R で実行するすべての操作をサポートします。 ただし、デュアル プロセス アーキテクチャでは、操作の複雑さに関係なく、すべての呼び出しの外部の R プロセスを呼び出す必要があります。 テーブルと SQL Server の既存のデータにスコアを付けることから、事前トレーニング済みモデルを読み込む場合、外部の R プロセスの呼び出しのオーバーヘッドは、不要なパフォーマンス コストを表します。

_スコア付け_は 2 段階のプロセスです。 最初に、テーブルからの読み込みに事前トレーニング済みモデルを指定します。 次に、新しいパスの入力データを予測値を生成する関数に (または_スコア_)。 入力には、表形式または 1 つのいずれかの行を指定できます。 確率を表す 1 つの列の値を出力するか信頼区間、エラー、またはその他の便利なを補完する、予測サービスなど、いくつかの値を出力する可能性があります。

入力には、多くのデータ行が含まれているときにこれは通常高速化、スコア付けプロセスの一環として、テーブルに、予測値を挿入します。  1 つのスコアを生成するはするフォームまたはユーザーの要求からの入力値を取得し、クライアント アプリケーションにスコアを返すシナリオではより一般的です。 パフォーマンスを向上させるには、連続するスコアを生成するときにメモリに再読み込みできるように、SQL Server は、モデルをキャッシュする可能性があります。

SQL Server Machine Learning サービス (および Microsoft Machine Learning Server) は、高速のスコア付けをサポートするには、R または T-SQL を動作する組み込みのスコア付けライブラリを提供します。 あるバージョンに応じて異なるオプションがあります。

**ネイティブのスコアリング**

+ TRANSACT-SQL の PREDICT 関数をサポートしています_ネイティブ スコアリング_で SQL Server 2017 の任意のインスタンス。 T-SQL を使用して呼び出すことができますが、既にトレーニング済みモデルがあることが必要のみです。 T-SQL を使用して、ネイティブのスコアリングと、これらの利点があります。

    + 追加の構成は必要ありません。
    + R ランタイムは呼び出されません。 R. をインストールする必要はありません。

**リアルタイム スコアリング**

+ **sp_rxPredict**ストアド プロシージャは、R ランタイムを呼び出さずに、任意のサポートされているモデル型からスコアを生成に使用できるリアルタイムのスコアリングします。

  このストアド プロシージャも Microsoft R Server のスタンドアロン インストーラーを使用して R コンポーネントをアップグレードする場合は、SQL Server 2016 で使用できます。 sp_rxPredict は、SQL Server 2017 でもサポートされます。 そのため、PREDICT 関数でサポートされていないモデルの種類のスコアを生成するときに、この関数を使用する場合があります。

+ RxPredict 関数は、高速のスコア付け R コード内で使用できます。

これらのスコアリング方法のすべてのサポートされている RevoScaleR または MicrosoftML アルゴリズムのいずれかを使用してトレーニングされたモデルを使用する必要があります。

リアルタイムのスコア付けの動作の例は、次を参照してください[エンド ツー エンド ローン償却予測ビルドを使用して Azure HDInsight Spark クラスターと SQL Server 2016 R サービス。](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

## <a name="how-native-scoring-works"></a>ネイティブのスコアリング動作

ネイティブ スコアリングは、特別なバイナリ形式から、モデルを読み取ることができ、スコアを生成する、Microsoft のネイティブの C++ ライブラリを使用します。 モデルをパブリッシュして、R インタープリターを呼び出さずにスコア付けに使用できる、ため、複数のプロセスの対話処理のオーバーヘッドが減少します。 そのため、ネイティブ スコアリングと、運用環境のエンタープライズ シナリオで予測パフォーマンスを向上させる多くをサポートします。

このライブラリを使用してスコアを生成するには、スコア付けの関数を呼び出すし、次の必須の入力を渡します。

+ 互換性のあるモデル。 参照してください、[要件](#Requirements)については、セクション。
+ 入力データ、通常、SQL クエリとして定義されます。

関数は、通過するソース データの列と共に、入力データの予測を返します。

と共に、必要なバイナリ形式でモデルを準備する方法を説明のコード サンプルは、この記事を参照してください。

+ [リアルタイム スコアリングを実行する方法](r/how-to-do-realtime-scoring.md)

ネイティブ スコアリングを含む完全なソリューションでは、SQL Server 開発チームからこれらのサンプルを参照してください。

+ ML スクリプトのデプロイ: [Python モデルを使用します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ ML スクリプトのデプロイ: [R モデルを使用します。](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)

## <a name="requirements"></a>要件

サポートされているプラットフォームは次のとおりです。

+ SQL Server 2017 Machine Learning Services (Microsoft R Server 9.1.0 を含む)
    
    ネイティブ スコアリング PREDICT を使用するには、SQL Server 2017 が必要です。
    Linux を含む、SQL Server 2017 の任意のバージョンで動作します。

    リアルタイムのスコアリング sp_rxPredict を使用して実行することもできます。 このストアド プロシージャを使用するには、有効にすることが必要[SQL Server の CLR 統合](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration)します。

+ SQL Server 2016

   リアルタイムのスコアリングを使用して sp_rxPredict は、SQL Server 2016 では、Microsoft R Server を実行することもできます。 このオプションは、SQLCLR が有効にして、Microsoft R Server のアップグレードをインストールすることが必要です。
   詳細については、次を参照してください[リアルタイム スコアリング。](Real-time-scoring.md)

### <a name="model-preparation"></a>モデルの準備

+ 事前に、サポートされているのいずれかを使用してモデルをトレーニングする必要があります**rx**アルゴリズム。 詳細については、次を参照してください。[アルゴリズムがサポートされている](#bkmk_native_supported_algos)します。
+ Microsoft R Server 9.1.0 で提供される新しいシリアル化関数を使用して、モデルを保存する必要があります。 シリアル化の関数は、高速のスコア付けをサポートするために最適化されています。

### <a name="bkmk_native_supported_algos"></a> ネイティブ スコアリングをサポートするアルゴリズム

+ RevoScaleR のモデル

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

MicrosoftML からモデルを使用する必要がある場合は、sp_rxPredict でリアルタイムのスコアリングを使用します。

### <a name="restrictions"></a>制限

モデルの種類がサポートされていません。

+ サポートされていない、他の種類の R の変換を含むモデル
+ モデルを使用して、`rxGlm`または`rxNaiveBayes`revoscaler アルゴリズム
+ PMML モデル
+ CRAN またはその他のリポジトリから他の R ライブラリを使用して作成されたモデル
+ その他のすべての R 変換を含むモデル

## <a name="see-also"></a>参照

[リアルタイムの SQL Server machine learning でのスコアリング ](real-time-scoring.md)