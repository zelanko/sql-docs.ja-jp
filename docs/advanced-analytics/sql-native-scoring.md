---
title: "ネイティブ スコアリング |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-server-2016
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
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e1cb06223e5274c1fa439eb9f7d82a005e93a47d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---

# <a name="native-scoring"></a>ネイティブのスコアリング

このトピックでは、SQL Server 2017 でほぼリアルタイムで機械学習モデルのスコアを提供する機能について説明します。

+ ネイティブのリアルタイムのスコアリングとスコア付けとは
+ しくみ
+ サポートされているプラットフォームと要件

## <a name="what-is-native-scoring-and-how-is-it-different-from-realtime-scoring"></a>新機能はネイティブ スコア付けとは異なるリアルタイム スコア付けしますか。

SQL Server 2016 では、マイクロソフトは、T-SQL を実行する R スクリプトを可能にする拡張機能フレームワークを作成します。 このフレームワークは、R、複雑な機械学習モデルをトレーニングする単純な関数の範囲で必要なすべての操作をサポートします。 ただし、SQL Server で R のペアをデュアル プロセス アーキテクチャは、操作の複雑さに関係なく、すべての呼び出しの外部 R のプロセスを呼び出す必要がありますを意味します。 テーブルとそれに対して SQL Server の既存のデータをスコア付けから事前トレーニング済みモデルを読み込む場合、R の外部プロセスの呼び出しのオーバーヘッドは、不要なパフォーマンス コストを表します。

_スコア付け_は、2 段階のプロセス: 事前トレーニング済みモデルは、テーブルから読み込まれ、新しい値を生成すると、モデルに新しい入力データを表形式または 1 つの行が渡される (または_スコア_)。 出力には、1 つの列を表す、確率または信頼区間、エラー、または、その予測に役立ちます他の補数を含めて、いくつかの値があります。

多くの行のデータをスコア付けに新しい値は通常、スコア付けの手順の一部としてテーブルに挿入されます。  ただし、同時にリアルタイムで 1 つのスコアを取得することもできます。 連続する入力のスコアリング、高速のメモリに再読み込みすることができるように、このモデルをキャッシュ可能性があります。

SQL Server マシン ラーニング サービス (および Microsoft Machine Learning サーバー) は、高速のスコア付けをサポートするには、T-SQL または R で使用する組み込みのスコアリング ライブラリを提供します。 あるバージョンに応じて異なるオプションがあります。

**ネイティブのスコアリング**

+ TRANSACT-SQL で予測関数を使用できます_ネイティブ スコアリング_SQL Server 2017 の任意のインスタンスから。 既にトレーニングし、テーブルに保存されたモデルがあること必要のみか、T-SQL を使用して呼び出すことができます。 これはネイティブの T-SQL で関数を使用する、リアルタイムのスコアの種類追加構成は必要ありません。

   R ランタイムは呼び出されません. をインストールする必要はありません。

**リアルタイムのスコアリング**

+ **sp_rxPredict**ストアド プロシージャをリアルタイムをスコア付けを使用して、R ランタイムを呼び出さずに、サポートされているモデルの種類からスコアを生成します。

  リアルタイムのスコア付けを使用する場合にも Microsoft R Server のスタンドアロン インストーラーを使用して、R コンポーネントをアップグレードする場合は、SQL Server 2016 で使用できます。 sp_rxPredict は、SQL Server の 2017 でもサポートされてし、予測関数でサポートされていないモデルの種類のスコア付けしている場合、適切なオプションがあります。

+ RxPredict 関数は、高速のスコア付け R コード内で使用できます。

これらすべてのスコアリング方法、サポートされている RevoScaleR または MicrosoftML アルゴリズムのいずれかを使用してトレーニングが行われたモデルを使用する必要があります。

アクションのスコアリング リアルタイムの例は、次を参照してください[エンド ツー エンド ローン ChargeOff 予測ビルドを使用して Azure HDInsight Spark クラスターと SQL Server 2016 R サービス。](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

## <a name="how-native-scoring-works"></a>ネイティブのスコア付け動作

特殊なバイナリ形式のモデルの読み取りおよびスコアを生成できる Microsoft からのネイティブの C++ ライブラリを使用してネイティブのスコア付けします。 モデルをパブリッシュして、R インタープリターを呼び出さずにスコアリングのために使用できることができます、ために、複数のプロセスの対話処理のオーバーヘッドが減ります。 これは、エンタープライズの実稼働のシナリオで予測のパフォーマンスを向上させる多くをサポートします。

このライブラリを使用してスコアを生成するには、スコア付け関数を呼び出すし、次の必須の入力を渡します。

+ 互換性のあるモデルです。 参照してください、[要件](#Requirements)詳細セクションです。
+ 通常、SQL クエリとして定義、入力データ

この関数は、通過するソース データの列と共に、入力データの予測を返します。

と共に、必要なバイナリ形式でモデルを準備する方法を説明のコード サンプルは、この記事を参照してください。

+ [リアルタイムのスコアリングを実行する方法](r/how-to-do-realtime-scoring.md)

## <a name="requirements"></a>必要条件

サポートされるプラットフォームは次のとおりです。

+ SQL Server 2017 Machine Learning Services (Microsoft R Server 9.1.0 が含まれています)
    
    予測を使用してネイティブ スコア付けには、SQL Server 2017 が必要です。
    Linux を含む、SQL Server 2017 の任意のバージョンで動作します。

    リアルタイムを使用してスコア付けを実行することも、sp_rxPredict SQL CLR を有効にする必要があります。

+ SQL Server 2016

   使用してスコア付けリアルタイム sp_rxPredict は、SQL Server 2016 では可能では、および Microsoft R Server を実行することもできます。 このオプションは、SQLCLR が有効にして、Microsoft R Server のアップグレードをインストールすることが必要です。
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
  + [rxdForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

MicrosoftML からモデルを使用する必要がある場合は、リアルタイム sp_rxPredict スコアリングを使用します。

### <a name="restrictions"></a>制限

次の種類のモデルがサポートされていません。

+ サポートされていない、他の種類の R の変換を含むモデル
+ 使用してモデル化、`rxGlm`または`rxNaiveBayes`RevoScaleR 内のアルゴリズム
+ PMML モデル
+ CRAN または他のリポジトリから他の R ライブラリを使用して作成されたモデル
+ 他の R の変換を含むモデル

