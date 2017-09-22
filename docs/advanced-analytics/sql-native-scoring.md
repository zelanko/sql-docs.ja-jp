---
title: "ネイティブ スコアリング |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/19/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: fe571e3e432d6445c76133c4c2a9c56f2f67eff0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---

# <a name="native-scoring"></a>ネイティブのスコアリング

このトピックでは、SQL Server 2017 でほぼリアルタイムで機械学習モデルのスコアを提供する機能について説明します。

+ ネイティブのリアルタイムのスコアリングとスコア付けとは
+ しくみ
+ サポートされているプラットフォームと要件

## <a name="what-is-native-scoring-and-how-is-it-different-from-realtime-scoring"></a>新機能はネイティブ スコア付けとは異なるリアルタイム スコア付けしますか。

SQL Server 2016 では、マイクロソフトは、T-SQL を実行する R スクリプトを可能にする拡張機能フレームワークを作成します。 このフレームワークは、R、複雑な機械学習モデルをトレーニングする単純な関数の範囲で必要なすべての操作をサポートします。 ただし、デュアル プロセス アーキテクチャでは、操作の複雑さに関係なく、すべての呼び出しの外部 R プロセスを呼び出す必要があります。 テーブルとそれに対して SQL Server の既存のデータをスコア付けから事前トレーニング済みモデルを読み込む場合、R の外部プロセスの呼び出しのオーバーヘッドは、不要なパフォーマンス コストを表します。

_スコア付け_は、2 段階のプロセスです。 まず、テーブルからの読み込みに事前トレーニング済みモデルを指定します。 2 番目、新しいパスの入力、予測値を生成する関数へのデータ (または_スコア_)。 入力には、表形式または 1 つの行を指定できます。 確率を表す 1 つの列値を出力するか信頼区間、エラー、またはその他の便利ビットごとの補数、予測するなど、いくつかの値を出力する可能性があります。

入力には、多くのデータ行が含まれている場合、これは通常高速スコア付けプロセスの一部として、テーブルに、予測値を挿入します。  1 つのスコアを生成するは、フォームまたはユーザーの要求から入力値を取得し、クライアント アプリケーションにスコアを返すシナリオではより一般的です。 パフォーマンスを向上させるには、一連のスコアを生成するときにメモリに再読み込みすることができるように、SQL Server は、モデルをキャッシュする可能性があります。

SQL Server マシン ラーニング サービス (および Microsoft Machine Learning サーバー) は、高速のスコア付けをサポートするには、T-SQL または R で使用する組み込みのスコアリング ライブラリを提供します。 あるバージョンに応じて異なるオプションがあります。

**ネイティブのスコアリング**

+ TRANSACT-SQL で予測関数をサポートしている_ネイティブ スコアリング_SQL Server 2017 の任意のインスタンスにします。 T-SQL を使用して呼び出すことができるモデルのトレーニングを既にがあることが必要のみです。 T-SQL を使用してネイティブ スコア付けすると、これらの利点があります。

    + 追加の構成は必要ありません。
    + R ランタイムは呼び出されません。 R. をインストールする必要はありません。

**リアルタイムのスコアリング**

+ **sp_rxPredict**ストアド プロシージャをリアルタイムをスコア付けを使用して、R ランタイムを呼び出さずに、サポートされているモデルの種類からスコアを生成します。

  このストアド プロシージャも Microsoft R Server のスタンドアロン インストーラーを使用して、R コンポーネントをアップグレードする場合は、SQL Server 2016 で使用できます。 sp_rxPredict は SQL Server 2017 でもサポートされます。 そのため、予測関数でサポートされていないモデルの種類にスコアを生成するときに、この関数を使用する場合があります。

+ RxPredict 関数は、高速のスコア付け R コード内で使用できます。

これらすべてのスコアリング方法、サポートされている RevoScaleR または MicrosoftML アルゴリズムのいずれかを使用してトレーニングが行われたモデルを使用する必要があります。

アクションのスコアリング リアルタイムの例は、次を参照してください[エンド ツー エンド ローン ChargeOff 予測ビルドを使用して Azure HDInsight Spark クラスターと SQL Server 2016 R サービス。](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

## <a name="how-native-scoring-works"></a>ネイティブのスコア付け動作

特殊なバイナリ形式のモデルの読み取りおよびスコアを生成できる Microsoft からのネイティブの C++ ライブラリを使用してネイティブのスコア付けします。 モデルをパブリッシュして、R インタープリターを呼び出さずにスコアリングのために使用できることができます、ために、複数のプロセスの対話処理のオーバーヘッドが減ります。 そのため、ネイティブのスコアリングと、エンタープライズの実稼働のシナリオで予測のパフォーマンスを向上させる多くをサポートします。

このライブラリを使用してスコアを生成するには、スコア付け関数を呼び出すし、次の必須の入力を渡します。

+ 互換性のあるモデルです。 参照してください、[要件](#Requirements)詳細セクションです。
+ 通常、SQL クエリとして定義、入力データ

この関数は、通過するソース データの列と共に、入力データの予測を返します。

と共に、必要なバイナリ形式でモデルを準備する方法を説明のコード サンプルは、この記事を参照してください。

+ [リアルタイムのスコアリングを実行する方法](r/how-to-do-realtime-scoring.md)

ネイティブのスコアを含む完全なソリューションは、SQL Server 開発チームのこれらのサンプルを参照してください。

+ ML スクリプトの展開: [Python モデルを使用します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ ML スクリプトの展開: [R モデルを使用します。](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)

## <a name="requirements"></a>必要条件

サポートされるプラットフォームは次のとおりです。

+ SQL Server 2017 Machine Learning Services (Microsoft R Server 9.1.0 が含まれています)
    
    予測を使用してネイティブ スコア付けには、SQL Server 2017 が必要です。
    Linux を含む、SQL Server 2017 の任意のバージョンで動作します。

    リアルタイムを使用してスコア付けを実行することも sp_rxPredict します。 このストアド プロシージャを使用するには、有効にすることが必要[SQL Server の CLR 統合](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration)です。

+ SQL Server 2016

   リアルタイム sp_rxPredict を使用してスコア付けは、SQL Server 2016 で実行できる Microsoft R Server を実行することもできます。 このオプションは、SQLCLR が有効にして、Microsoft R Server のアップグレードをインストールすることが必要です。
   詳細については、次を参照してください[リアルタイムのスコアリング。](Real-time-scoring.md)

### <a name="model-preparation"></a>モデルの準備

+ 事前に、サポートされているのいずれかを使用して、モデルをトレーニングする必要があります**rx**アルゴリズムです。 詳細については、「[アルゴリズムがサポートされている](#bkmk_native_supported_algos)です。
+ Microsoft R Server 9.1.0 で提供される新しいシリアル化の関数を使用して、モデルを保存する必要があります。 シリアル化の関数は、高速のスコア付けをサポートするために最適化されます。

### <a name="bkmk_native_supported_algos"></a>ネイティブのスコア付けをサポートするアルゴリズム

+ RevoScaleR モデル

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

MicrosoftML からモデルを使用する必要がある場合は、リアルタイム sp_rxPredict スコアリングを使用します。

### <a name="restrictions"></a>制限

次の種類のモデルがサポートされていません。

+ サポートされていない、他の種類の R の変換を含むモデル
+ 使用してモデル化、`rxGlm`または`rxNaiveBayes`RevoScaleR 内のアルゴリズム
+ PMML モデル
+ CRAN または他のリポジトリから他の R ライブラリを使用して作成されたモデル
+ その他のすべての R 変換を含むモデル

