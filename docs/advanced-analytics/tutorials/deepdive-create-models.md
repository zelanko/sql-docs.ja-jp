---
title: "R モデル (SQL と R deep dive) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: a195d5e2-72e2-4dd6-bf43-947312e4a52a
caps.latest.revision: "14"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 3a769169c90faf6a3ad552de28ea2cbc632e4b1c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="create-r-models-sql-and-r-deep-dive"></a>R モデル (SQL と R deep dive) を作成します。

この記事の内容を使用する方法について、データ サイエンス Deep Dive のチュートリアルの一部である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) SQL Server とします。

トレーニング データの強化が終了したので、次に線形回帰を使用してデータを分析します。 予測分析の世界で線形モデルは重要なツールです。 **の** RevoScaleR [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] パッケージには、高パフォーマンスのスケーラブルなアルゴリズムが含まれています。

## <a name="create-a-linear-regression-model"></a>線形回帰モデルを作成する

内の値を独立変数として使用して、顧客のクレジット_カード残高を推定する単純な線形モデルを作成するこの手順で、*性別*と*creditLine*列です。
  
これを行うを使用して、 [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)関数で、リモート計算コンテキストをサポートしています。
  
1. 完成したを格納する R 変数を作成モデル、および呼び出し**rxLinMod**、該当する式を渡すことです。
  
    ```R
    linModObj <- rxLinMod(balance ~ gender + creditLine,  data = sqlFraudDS)
    ```
  
2. 結果の概要を表示する標準的な R を呼び出す`summary`モデル オブジェクトに対して関数。
  
     ```R
     summary(linModObj)
     ```

特殊なプレーンな R 関数のように考える可能性があります`summary`はここでは、前の手順でサーバーに、計算コンテキストを設定するため機能します。 **rxLinMod** 関数でリモート計算コンテキストを使用してモデルを作成する場合でも、そのモデルを含むオブジェクトがローカル ワークステーションに返され、共有ディレクトリに格納されます。

そのため、"ローカル" コンテキストを使用して作成した場合と同様に、モデルに対して標準の R コマンドを実行することができます。

**結果**

```
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
Signif. codes: 0  0.001  0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 3812 on 9997 degrees of freedom
Multiple R-squared: 0.05765
Adjusted R-squared: 0.05746
F-statistic: 305.8 on 2 and 9997 DF, p-value: < 2.2e-16
Condition number: 1.0184
```

## <a name="create-a-logistic-regression-model"></a>ロジスティック回帰モデルを作成する

次に、特定の顧客が不正行為リスクであるかどうかを示すロジスティック回帰モデルを作成します。 使用して、 **RevoScaleR** [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)関数の場合、計算コンテキストをリモートでロジスティック回帰モデルの場合は、どのサポート調整します。

1.  計算コンテキストはそのまま保持します。 データ ソースも引き続き同じものを使用します。

2.  **rxLogit** 関数を呼び出して、モデルの定義に必要な数式を渡します。

    ```R
    logitObj <- rxLogit(fraudRisk ~ state + gender + cardholder + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS, dropFirst = TRUE)
    ```
  
    60 個の独立変数 (破棄される 3 つのダミー変数を含む) を使用する大規模なモデルなので、計算コンテキストからオブジェクトが返されるまでにしばらく時間がかかる場合があります。
    
    このモデルがこのように大きくなるのは、R と **RevoScaleR** パッケージでは、カテゴリ要因変数のすべてのレベルがそれぞれ個別のダミー変数として自動的に処理されるためです。
  
3.  返されたモデルの概要を表示する、R を呼び出す`summary`関数。
  
    ```R
    summary(logitObj)
    ```
  
**結果の一部**

```
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

Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1
Condition number of final variance-covariance matrix: 3997.308
Number of iterations: 15
```

## <a name="next-step"></a>次の手順

[新しいデータのスコア](../../advanced-analytics/tutorials/deepdive-score-new-data.md)

## <a name="previous-step"></a>前の手順

[R を使用して SQL Server のデータを表示する](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)
