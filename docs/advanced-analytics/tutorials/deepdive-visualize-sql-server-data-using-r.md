---
title: R (SQL と R の詳細情報) を使用した SQL Server データの視覚化 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 0d34ece68c421dbb7aabd845e117c9f07e00d013
ms.sourcegitcommit: 2420c57d2952add3697dbe0467ee1d755c5c2ee5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2018
ms.locfileid: "47217517"
---
#  <a name="visualize-sql-server-data-using-r-sql-and-r-deep-dive"></a>R (SQL と R の詳細情報) を使用した SQL Server のデータを視覚化します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、データ サイエンスの詳細情報を使用する方法のチュートリアルの一部[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の強化されたパッケージには、スケーラビリティと並列処理に最適化された複数の関数が含まれます。 通常、これらの関数の名前の前には **rx** または **Rx**付いています。

このチュートリアルで使用する、 **rxHistogram**関数内の値の分布を表示、 _creditLine_性別による列。

## <a name="visualize-data-using-rxhistogram"></a>RxHistogram を使用してデータを視覚化します。

1. 次の R コードを使用して [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) 関数を呼び出し、式とデータ ソースを渡します。 ローカルで最初にこの操作を実行することで、予想される結果と、所要時間を確認できます。
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    内部的には、 **rxHistogram** は、 [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) パッケージに含まれる **rxCube** 関数を呼び出します。 **rxCube**とカウント列、式で指定された各変数の 1 つの列を含む、1 つのリスト (またはデータ フレーム) を出力します。
    
2. ここで、リモートの SQL Server コンピューターに、コンピューティング コンテキストを設定し、実行**rxHistogram**もう一度です。
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
 
3. 同じデータ ソースを使用しているため、結果はまったく同じです。ただし、計算は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターで実行されます。  結果は、表示のためにローカル ワークステーションに返されます。
   
![ヒストグラム結果](media/rsql-sue-histogramresults.jpg "ヒストグラム結果")

4. 呼び出すことも、 **rxCube**機能し、結果を R プロット関数に渡します。  たとえば、次の例では **rxCube** を使用して、 *numTrans* と *numIntlTrans* のすべての組み合わせに対する *fraudRisk*の平均を計算します。
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    グループの平均の計算に使用するグループを指定するには、 `F()` 表記を使用します。 この例で`F(numTrans):F(numIntlTrans)`ことを示します整数変数を`numTrans`と`numIntlTrans`レベルには、各整数値、カテゴリ変数として処理する必要があります。
  
    下限と上限のレベルは、データ ソースに既に追加されているため`sqlFraudDS`(を使用して、`colInfo`パラメーター)、レベルはヒストグラムで自動的に使用します。
  
5. 既定の戻り値の**rxCube**は、 *rxCube オブジェクト*、クロス集計を表します。 ただし、 [rxResultsDF](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) 関数を使用して、R の標準プロット関数のいずれかで簡単に使用できるデータ フレームに、結果を変換できます。
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    **RxCube**関数には、オプションの引数が含まれています。 *returnDataFrame* = **TRUE**、結果をデータ フレームに直接変換を使用できますが、します。 以下に例を示します。
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    ただし、 **rxResultsDF** の出力の方がはるかに簡潔であり、ソース列の名前が保持されます。
  
6. 最後に、次のコードを使用して、ヒート マップの作成を実行、`levelplot`関数を**格子**パッケージは、すべての R ディストリビューションに含まれています。
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **結果**
  
    ![散布図の結果](media/rsql-sue-scatterplotresults.jpg "散布図の結果")
  
この簡単な分析からでも、トランザクションの数および国際的トランザクションの数の両方に伴って不正行為のリスクが高くなることがわかります。

詳細については、 **rxCube**関数およびクロス集計表が一般に、表示[RevoScaleR を使用してデータを集計](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries)します。

## <a name="next-step"></a>次の手順

[SQL Server のデータを使用して R モデルを作成します。](../../advanced-analytics/tutorials/deepdive-create-models.md)

## <a name="previous-step"></a>前の手順

[R スクリプトの作成と実行](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
