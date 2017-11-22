---
title: "SQL Server で MicrosoftML パッケージの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/23/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 1c377717-e281-431e-8171-3924dcce1cdd
caps.latest.revision: "132"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5d4e4081ba4722f2c7aa468cf70f3a3238d6e9ee
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="using-the-microsoftml-package-with-sql-server"></a>SQL Server で MicrosoftML パッケージの使用

[ **MicrosoftML** ](https://msdn.microsoft.com/microsoft-r/microsoftml-introduction) Microsoft R Server と SQL Server 2017 に用意されているパッケージに複数の機械学習アルゴリズムが含まれています。 これらの Api の内部の機械学習のアプリケーション、Microsoft によって開発されたれているし、洗練されたビッグ データは、高パフォーマンスをサポートするために長年にわたってマルチコア処理と高速なデータのストリーミングを使用します。 MicrosoftML には、テキストとイメージの処理のためのさまざまな変換も含まれています。

SQL Server 2017 CTP 2.0 では、Python 言語のサポートが追加されました。 **Microsoftml**パッケージの Python には R. の MicrosoftML パッケージ内のものと同等の関数が含まれています 

+ **R の MicrosoftML**

    概要とパッケージの参照: [MicrosoftML: コンピューターの R の学習アルゴリズム](https://docs.microsoft.com/en-us/r-server/r-reference/microsoftml/microsoftml-package)

    R は大文字であるために、パッケージを読み込むときに正しく名を参照することを確認します。

+ **Python の microsoftml**

    概要とパッケージの参照: [microsoftml (Python の関数ライブラリ)](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)です。 

## <a name="whats-in-microsoftml"></a>MicrosoftML には

MicrosoftML には、さまざまな機械学習アルゴリズムとパフォーマンスの最適化されている変換が含まれています。

### <a name="machine-learning-algorithms"></a>機械学習アルゴリズム

-  線形モデル:`rxFastLinear`線形学習器に基づいてストキャスティクスのデュアル座標アセント二項分類または回帰に使用できます。 このモデルでは、L1 と L2 の規則化がサポートされています。

- デシジョン ツリーとデシジョン フォレスト モデル: `rxFastTree` Bing で使用するために開発された FastRank と呼ばれる最初のブースト デシジョン ツリー アルゴリズムは、します。 最も速く最も人気のあるラーナーの 1 つです。 二項分類と回帰をサポートしています。

  `rxFastForest`ロジスティック回帰モデルは、ランダム フォレスト メソッドに基づいています。 RevoScaleR の `rxLogit` 関数に似ていますが、L1 と L2 の規則化がサポートされています。 二項分類と回帰をサポートしています。

- ロジスティック回帰:`rxLogisticRegression`ロジスティック回帰モデルをに似ていますが、 `rxLogit` L1 と L2 の正則化の追加サポートと共に、RevoScaleR 関数。 バイナリまたは多クラス分類をサポートしています。

- ニューラル ネットワーク:`rxNeuralNet`関数は、二項分類、多クラス分類、およびニューラル ネットワークを使用した回帰をサポートしています。 GPU アクセラレータ、単一の GPU を使用して複雑なネットワークをカスタマイズおよびサポートしています。

- 異常検出します。  `rxOneClassSvm`関数が SVM メソッドに基づきますが不均衡のデータ セットで二項分類に適しています。

### <a name="transformation-functions"></a>変換関数

MicrosoftML には、データを変換して、機能を抽出するのに便利な多数の特別な関数が含まれています。

- テキスト処理機能では、`featurizeText`と`getSentiment`関数。 N-gram の数、使用する言語を検出したり、テキストの正規化を実行できます。 一般的なテキストがストップ ワードの削除などの操作のクリーンアップを実行したり、テキストからハッシュまたはカウント ベースの機能を生成できます。

- 機能の選択と、変換関数をなど機能`selectFeatures`または`getSentiment`データを分析およびモデリングの最も便利な機能を作成します。

- などを使用して、カテゴリ変数を扱う`categorical`または`categoricalHash`、パフォーマンス向上のためのインデックスの配列にカテゴリ値を変換します。

- などイメージ処理と分析に固有の関数`extractPixels`または`featurizeImage`では、イメージのほとんどの情報を取得し、画像を高速に処理します。

詳細については、[MicrosoftML 関数](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml)に関するページをご覧ください。

## <a name="how-to-use-microsoftml"></a>MicrosoftML を使用する方法

このセクションを探して、R、Python コード内のパッケージを読み込む方法について説明します。

+ R の MicrosoftML パッケージは、SQL Server 2017 および Microsoft R Server 9.1.0 で既定でインストールされます。

    インストーラーを使用して、Microsoft R Server の説明に従ってここで、インスタンスの R コンポーネントをアップグレードする場合は、SQL Server 2016 で使用可能なも:[バインディングを使用して SQL Server のインスタンスをアップグレード](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

+ **Microsoftml** Python が既定では、SQL Server 2017 インストール用のパッケージ 

   このパッケージを使用するのには、Release Candidate 2 以降をアップグレードすることお勧めします。 RC1 と、以前のバージョンがリリースされましたが、ライブラリの関数名の変更など、かなりのリビジョンがされました。 

ただし、R と Python の両方で、パッケージが読み込まれていません。 既定ではしたがって、パッケージには、その関数を使用して、コードの一部として明示的に読み込む必要があります。

### <a name="calling-microsoftml-functions-from-r-in-sql-server"></a>SQL Server で R から MicrosoftML 関数の呼び出し

R コードで MicrosoftML パッケージの読み込みし、他のパッケージと同様に、その関数を呼び出します。

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

**注**

+ MicrosoftML パッケージは、RevoScaleR パッケージによって提供されるデータ処理のパイプラインと完全に統合されています。 したがって、machine learning extensions が有効である SQL Server のインスタンスを含む、任意の Windows ベースのコンピューティング コンテキストで MicrosoftML パッケージを使用することができます。

    ただし、MicrosoftML は RevoScaleR とリモートを使用するのには、その関数への参照の計算コンテキストが必要です。

### <a name="calling-microsoftml-functions-from-python-in-sql-server"></a>SQL Server での Python から microsoftml 関数の呼び出し

Python コード内のパッケージから関数を呼び出すには、インポート、 **microsoftml**パッケージ化、およびインポート**revoscalepy**リモート計算コンテキストまたは関連する接続またはデータ ソースを使用する必要がある場合オブジェクト。 次に、必要がある個々 の関数を参照します。

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

**注**

+ SQL Server の 2017 で**microsoftml** Python35 と互換性のあるモジュールです。 

+ 内の関数**microsoftml**は、計算コンテキストとデータ ソースでサポートされていると統合される**revoscalepy**です。 したがって、使用することができます、 **microsoftml** Python パッケージを作成し、マシン学習の拡張機能を持つ SQL Server のインスタンスを含む、任意の Windows ベースのコンピューティング コンテキストでのモデルからスコア付けします。 有効になります。

    ただし、 **microsoftml** Python への参照を必要する**revoscalepy**リモートを使用するのには、その関数の計算コンテキストとします。

Revoscalepy の詳細についてを参照してください。

+ [Revoscalepy とは](python/what-is-revoscalepy.md)

+ [revoscalepy 関数ライブラリ](https://docs.microsoft.com/en-us/r-server/python-reference/revoscalepy/revoscalepy-package) 
