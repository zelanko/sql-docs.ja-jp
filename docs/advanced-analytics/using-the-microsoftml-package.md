---
title: SQL Server での MicrosoftML パッケージの使用 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 51ffa33bef7ab880704c9c1391a69feb3e194202
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38984564"
---
# <a name="using-the-microsoftml-package-with-sql-server"></a>SQL Server での MicrosoftML パッケージを使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[ **MicrosoftML** ](https://msdn.microsoft.com/microsoft-r/microsoftml-introduction) Microsoft R Server と SQL Server 2017 に付属しているパッケージには、複数の機械学習アルゴリズムが含まれています。 これらの Api は、内部の machine learning のアプリケーション、Microsoft によって開発され、が改良されてビッグ データで高パフォーマンスをサポートするために長年にわたってマルチコア処理と高速データ ストリーミングを使用します。 MicrosoftML には、テキストとイメージの処理のためのさまざまな変換も含まれています。

SQL Server 2017 CTP 2.0 で、Python 言語のサポートが追加されました。 **Microsoftml**パッケージに Python には、R 向けの MicrosoftML パッケージものと同等の関数が含まれています 

+ **R 用の MicrosoftML**

    概要とパッケージの参照: [MicrosoftML: machine learning R アルゴリズム](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)

    R は大文字であるため、パッケージを読み込むときに正しく名を参照することを確認します。

+ **Python 用の microsoftml**

    概要とパッケージの参照: [microsoftml (Python 用の関数ライブラリ)](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)します。 

## <a name="whats-in-microsoftml"></a>MicrosoftML の新機能

MicrosoftML には、さまざまな機械学習アルゴリズムやパフォーマンスの最適化されている変換が含まれています。

### <a name="machine-learning-algorithms"></a>機械学習アルゴリズム

-  線形モデル:`rxFastLinear`線形学習器に基づいて確率的双対座標二項分類または回帰のために使用できます。 このモデルでは、L1 と L2 の規則化がサポートされています。

- デシジョン ツリーとデシジョン フォレスト モデル:`rxFastTree`は Bing で使用するために開発された、以前は FastRank と呼ばれて、ブースト デシジョン ツリー アルゴリズムです。 最も速く最も人気のあるラーナーの 1 つです。 二項分類と回帰をサポートしています。

  `rxFastForest` ロジスティック回帰モデルは、ランダム フォレスト方法に基づいています。 RevoScaleR の `rxLogit` 関数に似ていますが、L1 と L2 の規則化がサポートされています。 二項分類と回帰をサポートしています。

- ロジスティック回帰:`rxLogisticRegression`は、ロジスティック回帰モデルに似ています、 `rxLogit` L1 と L2 の正則化のサポートを追加で、revoscaler 関数。 バイナリまたは多クラス分類をサポートしています。

- ニューラル ネットワーク:`rxNeuralNet`関数を二項分類、多クラス分類、およびニューラル ネットワークを使用して回帰をサポートしています。 1 つの GPU を使用して、GPU アクセラレータで畳み込みネットワークをカスタマイズおよびサポートしています。

- 異常検出します。  `rxOneClassSvm`関数は、SVM メソッドに基づきますが、不均衡データ セットの二項分類に適しています。

### <a name="transformation-functions"></a>変換関数

MicrosoftML には、データの変換と特徴を抽出するのに役立つ多数の特殊な関数が含まれています。

- テキスト処理機能が含まれます、`featurizeText`と`getSentiment`関数。 N グラムのカウント、使用すると、言語検出、またはテキストの正規化を実行できます。 一般的なテキストのクリーニング ストップ ワードの削除などの操作を実行したり、テキストからハッシュまたはカウント ベースの特徴を生成できます。

- 機能の選択および変換機能、機能のなど`selectFeatures`または`getSentiment`データを分析およびモデリングの最も便利な機能を作成します。

- などを使用して、カテゴリ変数を扱う`categorical`または`categoricalHash`、パフォーマンス向上のためのインデックス付き配列にカテゴリ値を変換します。

- など、イメージ処理や分析に固有の関数`extractPixels`または`featurizeImage`イメージの最大限の情報を取得し、画像を高速に処理します。

詳細については、[MicrosoftML 関数](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml)に関するページをご覧ください。

## <a name="how-to-use-microsoftml"></a>MicrosoftML を使用する方法

このセクションでは、検索して、R と Python のコードでパッケージを読み込む方法について説明します。

+ R の MicrosoftML パッケージは、Microsoft R Server 9.1.0 および SQL Server 2017 では既定でインストールされます。

    インストーラーを使用して、Microsoft R Server の説明に従ってここで、インスタンスの R コンポーネントをアップグレードする場合は、SQL Server 2016 で使用できるようにも:[バインドを使用して SQL Server のインスタンスをアップグレード](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

+ **Microsoftml** for SQL Server 2017 では既定で Python がインストールされているパッケージ 

   このパッケージを使用するには、Release Candidate 2 以降をアップグレードすることをお勧めします。 RC1 で初期のバージョンがリリースされていますが、ライブラリはかなりリビジョン、関数名の変更などが行われました。 

ただし、R と Python の両方のパッケージが読み込まれていない、既定でそのため、パッケージには、その関数を使用するコードの一部として明示的に読み込む必要があります。

### <a name="calling-microsoftml-functions-from-r-in-sql-server"></a>SQL Server で R から MicrosoftML 関数を呼び出す

R コードで MicrosoftML パッケージを読み込むし、他のパッケージのように、その関数を呼び出します。

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

**注**

+ MicrosoftML パッケージは、RevoScaleR パッケージで提供されるデータ処理パイプラインに完全に統合します。 したがって、machine learning の拡張機能が有効になっているが SQL Server のインスタンスを含む、任意の Windows ベースのコンピューティング コンテキストの MicrosoftML パッケージを使用することができます。

    ただし、MicrosoftML は、計算コンテキストの RevoScaleR とリモートを使用するのには、その関数への参照が必要です。

### <a name="calling-microsoftml-functions-from-python-in-sql-server"></a>SQL Server での Python から microsoftml 関数を呼び出す

パッケージ、Python コードから関数を呼び出すには、インポート、 **microsoftml**パッケージ化、およびインポート**revoscalepy**リモート コンピューティング コンテキストまたは関連する接続またはデータ ソースを使用する必要がある場合オブジェクト。 次に、必要がある個々 の関数を参照します。

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

**注**

+ SQL Server 2017 で**microsoftml** Python35 と互換性のあるモジュールです。 

+ 関数は、 **microsoftml**でサポートされているコンピューティング コンテキストとデータ ソースと統合された**revoscalepy**します。 したがって、使用することができます、 **microsoftml** Python パッケージを machine learning の拡張機能を持つ SQL Server のインスタンスを含む、任意の Windows ベースのコンピューティング コンテキストではモデルからスコアを作成します。 有効になります。

    ただし、 **microsoftml** Python への参照を必要があります**revoscalepy**リモートを使用するには、その関数の計算コンテキストとします。

Revoscalepy の詳細についてを参照してください。

+ [Revoscalepy とは](python/what-is-revoscalepy.md)

+ [revoscalepy 関数ライブラリ](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) 
