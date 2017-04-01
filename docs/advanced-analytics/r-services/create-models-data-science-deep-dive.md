---
title: "モデルの作成 (データ サイエンスの詳細情報) | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: a195d5e2-72e2-4dd6-bf43-947312e4a52a
caps.latest.revision: 14
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# モデルの作成 (データ サイエンスの詳細情報)
トレーニング データの強化が終了したので、次に線形回帰を使用してデータを分析します。 予測分析の世界で線形モデルは重要なツールです。[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の **RevoScaleR** パッケージには、高パフォーマンスのスケーラブルなアルゴリズムが含まれています。  
  
## 線形回帰モデルを作成する  
独立変数として *gender* 列と *creditLine* 列の値を使用して、顧客のクレジット カード残高を推定する単純な線形モデルを作成します。  
  
そのためには、リモートの計算コンテキストをサポートする *rxLinMod* 関数を使用します。  
  
1.  完成したモデルを格納する R 変数を作成し、*rxLinMod* 関数を呼び出して適切な数式を渡します。  
  
    ```R  
    linModObj <- rxLinMod(balance ~ gender + creditLine,  data = sqlFraudDS)   
    ```  
  
2.   結果の概要を確認するには、モデル オブジェクトに対して標準の R 関数 *summary* を呼び出します。  
  
     ```R  
     summary(linModObj)   
     ```  

前の手順では、サーバーに対して計算コンテキストを設定したので、この手順で **summary** のような単純な R 関数を利用できることが奇妙に感じられるかもしれませんが、 **rxLinMod** 関数でリモート計算コンテキストを使用してモデルを作成する場合でも、そのモデルを含むオブジェクトがローカル ワークステーションに返され、共有ディレクトリに格納されます。

そのため、"ローカル" コンテキストを使用して作成した場合と同様に、モデルに対して標準の R コマンドを実行することができます。
  
**[結果]**  
  
*Linear Regression Results for: balance ~ gender + creditLineData: sqlFraudDS (RxSqlServerData Data Source)*  
*Dependent variable(s): balance*  
*Total independent variables: 4 (Including number dropped: 1)*  
*Number of valid observations: 10000*  
*Number of missing observations: 0*    
*Coefficients: (1 not defined because of singularities)*      
*Estimate Std. Error t value Pr(>|t|) (Intercept)*   
*3253.575 71.194 45.700 2.22e-16*   
*gender=Male -88.813 78.360 -1.133 0.257*   
*gender=Female Dropped Dropped Dropped Dropped*   
*creditLine 95.379 3.862 24.694 2.22e-16*   
*Signif. codes: 0  0.001  0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1*  
  
*Residual standard error: 3812 on 9997 degrees of freedom*  
*Multiple R-squared: 0.05765*   
*Adjusted R-squared: 0.05746*   
*F-statistic: 305.8 on 2 and 9997 DF, p-value: < 2.2e-16*  
*Condition number: 1.0184*  
  
## ロジスティック回帰モデルを作成する  
次に、特定の顧客に不正使用の危険があるかどうかを示すロジスティック回帰モデルを作成します。  
  
ロジスティック回帰をリモートの計算コンテキストに収めることができる *rxLogit* 関数 (**RevoScaleR** パッケージに入っている) を使用します。  
  
1.  計算コンテキストはそのまま保持します。 データ ソースも引き続き同じものを使用します。  
  
2.  *rxLogit* 関数を呼び出して、モデルの定義に必要な数式を渡します。  
  
    ```R  
    logitObj <- rxLogit(fraudRisk ~ state + gender + cardholder + balance +      numTrans + numIntlTrans + creditLine, data = sqlFraudDS,      dropFirst = TRUE)   
    ```  
  
    60 個の独立変数 (破棄される 3 つのダミー変数を含む) を使用する大規模なモデルなので、計算コンテキストからオブジェクトが返されるまでにしばらく時間がかかる場合があります。  
    
    このモデルがこのように大きくなるのは、R と **RevoScaleR** パッケージでは、カテゴリ要因変数のすべてのレベルがそれぞれ個別のダミー変数として自動的に処理されるためです。  
  
3.  返されるモデルの概要を確認するには、R の *summary* 関数を呼び出します。  
  
    ```R  
    summary(logitObj)  
    ```  
  
**結果の一部**  
  
*Logistic Regression Results for: fraudRisk ~ state + gender +     cardholder + balance + numTrans + numIntlTrans + creditLine*   
*Data: sqlFraudDS (RxSqlServerData Data Source)*   
*Dependent variable(s): fraudRisk*   
*Total independent variables: 60 (Including number dropped: 3)*   
*Number of valid observations: 10000 -2\*  
*LogLikelihood: 2032.8699 (Residual deviance on 9943 degrees of freedom)*  
*Coefficients:*   
*Estimate Std. Error z value Pr(>|z|)     (Intercept)*  
*-8.627e+00  1.319e+00  -6.538 6.22e-11 \*\*\*   
state=AK                Dropped    Dropped Dropped  Dropped       
state=AL             -1.043e+00  1.383e+00  -0.754   0.4511* (other states omitted) *gender=Male             Dropped    Dropped Dropped  Dropped*  
*gender=Female         7.226e-01  1.217e-01   5.936 2.92e-09 \*\*\**  
*cardholder=Principal    Dropped    Dropped Dropped  Dropped*       
*cardholder=Secondary  5.635e-01  3.403e-01   1.656   0.0977 .*     
*balance               3.962e-04  1.564e-05  25.335 2.22e-16 \*\*\**  
*numTrans              4.950e-02  2.202e-03  22.477 2.22e-16 \*\*\**  
*numIntlTrans          3.414e-02  5.318e-03   6.420 1.36e-10 \*\*\**  
*creditLine            1.042e-01  4.705e-03  22.153 2.22e-16 \*\*\**   
*---*   
*Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1*   
*Condition number of final variance-covariance matrix: 3997.308*   
*Number of iterations: 15*  
  
## 次の手順  
[新しいデータのスコア付け (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/score-new-data-data-science-deep-dive.md)  
  
## 前の手順  
[R を使用して SQL Server データを視覚化する (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/visualize-sql-server-data-using-r-data-science-deep-dive.md)  
  
## 参照  
[データ サイエンスの詳細: RevoScaleR パッケージの使用](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
