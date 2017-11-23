---
title: "R を使用して SQL Server のデータを表示する (データ サイエンスの詳細情報) | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 10def0b3-9b09-4df9-b8aa-69516f7d7659
caps.latest.revision: "14"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a67480daf011a021002e1688b006a1f0593f8e5f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="visualize-sql-server-data-using-r"></a>R を使用して SQL Server のデータを表示する

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の強化されたパッケージには、スケーラビリティと並列処理に最適化された複数の関数が含まれます。 通常、これらの関数の名前の前には *rx* または *Rx*付いています。

このチュートリアルでは、 **rxHistogram** 関数を使用して、 _creditLine_ 列の値の分布を男女別に表示します。

## <a name="visualize-data-using-rxhistogram"></a>RxHistogram を使用してデータを視覚化します。

1. RxHistogram 関数を呼び出すし、数式とデータ ソースを渡すには、次の R コードを使用します。 ローカルで最初にこの操作を実行することで、予想される結果と、所要時間を確認できます。
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    内部的に含まれている rxCube 関数を呼び出し、rxHistogram、 **RevoScaleR**パッケージです。 RxCube 関数は、さらに、カウント列の数式で指定された各変数に対して 1 つの列を含む、1 つのリスト (またはデータ フレーム) を出力します。
    
2. ここで、リモートの SQL Server コンピューターに、計算コンテキストを設定し、rxHistogram をもう一度実行します。
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
 
3. 同じデータ ソースを使用しているため、結果はまったく同じです。ただし、計算は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターで実行されます。  結果は、表示のためにローカル ワークステーションに返されます。
   
![ヒストグラム結果](media/rsql-sue-histogramresults.jpg "ヒストグラム結果")

4. RxCube 関数を呼び出すし、R プロット関数に結果を渡すことができますも。  たとえば、次の例 rxCube の平均を計算する*fraudRisk*の組み合わせごとに*numTrans*と*numIntlTrans*:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    グループの平均の計算に使用するグループを指定するには、 `F()` 表記を使用します。 この例では、 `F(numTrans):F(numIntlTrans)` は、変数 _numTrans_ と _numIntlTrans_ の整数を各整数値をレベルとするカテゴリ変数として処理する必要があることを示します。
  
    低レベルと高レベルは ( *colInfo* パラメーターを使用して) データ ソース *sqlFraudDS* に既に追加されているので、レベルはヒストグラムで自動的に使用されます。
  
5. RxCube の戻り値が既定では、 *rxCube オブジェクト*、クロス集計を表します。 ただし、 **rxResultsDF** 関数を使用して、R の標準プロット関数のいずれかで簡単に使用できるデータ フレームに、結果を変換できます。
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    > [!TIP]
    > 
    > 注 rxCube 関数に、省略可能な引数が含まれている*returnDataFrame* = TRUE、結果をデータ フレームに直接変換に使用することでした。 例:
    >   
    > `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
    >   
    > ただし、rxResultsDF の出力はクリーンで、ソース列の名前を保持します。
  
6. 最後に、次のコードを使用して、ヒート マップの作成を実行、`levelplot`から機能、**格子**パッケージは、すべての R ディストリビューションに含まれています。
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **[結果]**
  
    ![散布図の結果](media/rsql-sue-scatterplotresults.jpg "散布図の結果")
  
この簡単な分析からでも、トランザクションの数および国際的トランザクションの数の両方に伴って不正行為のリスクが高くなることがわかります。

一般的なクロス集計と rxCube 関数に関する詳細については、次を参照してください。[データ サマリ](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-summaries)です。

## <a name="next-step"></a>次の手順

[モデルを作成します。](../../advanced-analytics/tutorials/deepdive-create-models.md)

## <a name="previous-step"></a>前の手順

[レッスン 2: R スクリプトの作成と実行](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)


