---
title: R モデルの RevoScaleR チュートリアル - SQL Server Machine Learning の作成します。
description: SQL Server で R 言語を使用して、モデルを構築する方法のチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: ae58ddf27628612200920899d914895d4fea3840
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513179"
---
# <a name="create-r-models-sql-server-and-revoscaler-tutorial"></a>R モデル (SQL Server と RevoScaleR チュートリアル) を作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンの一部である、 [RevoScaleR チュートリアル](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)を使用する方法の[RevoScaleR 関数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

これで、トレーニング データを拡充しました、回帰モデリングを使用してデータを分析する時間を勧めします。 線形モデルは予測分析の世界で重要なツールと**RevoScaleR**パッケージには、ワークロードを分割したり、並列で実行する回帰アルゴリズムが含まれています。

> [!div class="checklist"]
> * 線形回帰モデルを作成する
> * ロジスティック回帰モデルを作成する

## <a name="create-a-linear-regression-model"></a>線形回帰モデルを作成する

この手順で、独立変数としての値を使用して顧客のクレジット_カード残高を推定する単純な線形モデルを作成、*性別*と*creditLine*列。
  
これを行うには、使用、 [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)関数で、リモート コンピューティング コンテキストをサポートします。
  
1. 完成したを格納する R 変数を作成するモデル、および呼び出し**rxLinMod**、適切な数式を渡します。
  
    ```R
    linModObj <- rxLinMod(balance ~ gender + creditLine,  data = sqlFraudDS)
    ```
  
2. 結果の概要を表示する標準の R を呼び出す**概要**モデル オブジェクトに対して関数。
  
     ```R
     summary(linModObj)
     ```

前の手順では、サーバーに対して計算コンテキストを設定したので、この手順で **summary** のような単純な R 関数を利用できることが奇妙に感じられるかもしれませんが、 **rxLinMod** 関数でリモート計算コンテキストを使用してモデルを作成する場合でも、そのモデルを含むオブジェクトがローカル ワークステーションに返され、共有ディレクトリに格納されます。

そのため、"ローカル" コンテキストを使用して作成した場合と同様に、モデルに対して標準の R コマンドを実行することができます。

**結果**

```R
Linear Regression Results for: balance ~ gender + creditLineData: sqlFraudDS (RxSqlServerData Data Source)
Dependent variable(s): balance
Total independent variables: 4 (Including number dropped: 1)
Number of valid observations: 10000
Number of missing observations: 0
Coefficients: (1 not defined because of singularities)

Estimate Std. Error t value Pr(>|t|) (Intercept)
3253.575 71.194 45.700 2.22e-16
gender=Male -88.813 78.360 -1.133 0.257
gender=Female Dropped Dropped Dropped Dropped
creditLine 95.379 3.862 24.694 2.22e-16
Signif. codes: 0  0.001  0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 3812 on 9997 degrees of freedom
Multiple R-squared: 0.05765
Adjusted R-squared: 0.05746
F-statistic: 305.8 on 2 and 9997 DF, p-value: < 2.2e-16
Condition number: 1.0184
```

## <a name="create-a-logistic-regression-model"></a>ロジスティック回帰モデルを作成する

次に、特定の顧客が不正行為のリスクであるかどうかを示すロジスティック回帰モデルを作成します。 使用して、 **RevoScaleR** [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)関数の場合、リモートでロジスティック回帰モデルの計算コンテキスト。

計算コンテキストはそのまま保持します。 同じデータ ソースを使用することも引き続きします。

1. **rxLogit** 関数を呼び出して、モデルの定義に必要な数式を渡します。

    ```R
    logitObj <- rxLogit(fraudRisk ~ state + gender + cardholder + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS, dropFirst = TRUE)
    ```
  
    60 個の独立変数 (破棄される 3 つのダミー変数を含む) を使用する大規模なモデルなので、計算コンテキストからオブジェクトが返されるまでにしばらく時間がかかる場合があります。
    
    このモデルがこのように大きくなるのは、R と **RevoScaleR** パッケージでは、カテゴリ要因変数のすべてのレベルがそれぞれ個別のダミー変数として自動的に処理されるためです。
  
2. 返されるモデルの概要を確認するには、R の **summary** 関数を呼び出します。
  
    ```R
    summary(logitObj)
    ```
  
**結果の一部**

```R
Logistic Regression Results for: fraudRisk ~ state + gender + cardholder + balance + numTrans + numIntlTrans + creditLine
Data: sqlFraudDS (RxSqlServerData Data Source)
Dependent variable(s): fraudRisk
Total independent variables: 60 (Including number dropped: 3)
Number of valid observations: 10000 -2

LogLikelihood: 2032.8699 (Residual deviance on 9943 degrees of freedom)

Coefficients:
Estimate Std. Error z value Pr(>|z|)     (Intercept)
-8.627e+00  1.319e+00  -6.538 6.22e-11
state=AK                Dropped    Dropped Dropped  Dropped
state=AL             -1.043e+00  1.383e+00  -0.754   0.4511

(other states omitted)

gender=Male             Dropped    Dropped Dropped  Dropped
gender=Female         7.226e-01  1.217e-01   5.936 2.92e-09
cardholder=Principal    Dropped    Dropped Dropped  Dropped
cardholder=Secondary  5.635e-01  3.403e-01   1.656   0.0977
balance               3.962e-04  1.564e-05  25.335 2.22e-16
numTrans              4.950e-02  2.202e-03  22.477 2.22e-16
numIntlTrans          3.414e-02  5.318e-03   6.420 1.36e-10
creditLine            1.042e-01  4.705e-03  22.153 2.22e-16

Signif. codes:  0 '\*\*\*' 0.001 '\*\*' 0.01 '\*' 0.05 '.' 0.1 ' ' 1
Condition number of final variance-covariance matrix: 3997.308
Number of iterations: 15
```

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [新しいデータのスコア付け](../../advanced-analytics/tutorials/deepdive-score-new-data.md)