---
title: "R を使用して SQL Server のデータを表示する (データ サイエンスの詳細情報) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
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
ms.assetid: 10def0b3-9b09-4df9-b8aa-69516f7d7659
caps.latest.revision: 14
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# R を使用して SQL Server のデータを表示する (データ サイエンスの詳細情報)
[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の強化されたパッケージには、スケーラビリティと並列処理に最適化された複数の関数が含まれます。 通常、これらの関数の名前の前には *rx* または *Rx* 付いています。  
  
このチュートリアルでは、*rxHistogram* 関数を使用して、_creditLine_ 列の値の分布を男女別に表示します。  
  
## RxHistogram と rxCube を使用してデータを表示する  
  
1.  次の R コードを使用して *rxHistogram* 関数を呼び出し、式とデータ ソースを渡します。 ローカルで最初にこの操作を実行することで、予想される結果と、所要時間を確認できます。
  
    ```R  
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")   
    ```  
 
    内部的には、*rxHistogram* は、**RevoScaleR** パッケージに含まれる *rxCube* 関数を呼び出します。 *rxCube* 関数は、式で指定された各変数の 1 つの列を含む 1 つのリスト (またはデータ フレーム) とカウント列を出力します。
    
2. ここで、リモート SQL Server コンピューターにコンピューター コンテキストを設定し、*rxHistogram* を再度実行します。
  
    ```R  
    rxSetComputeContext(sqlCompute)  
    ```  
 
3.    同じデータ ソースを使用しているため、結果はまったく同じです。ただし、計算は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターで実行されます。  結果は、表示のためにローカル ワークステーションに返されます。  
   
![histogram results](../../advanced-analytics/r-services/media/rsql-sue-histogramresults.jpg "histogram results")  

  
4.  *rxCube* 関数を呼び出して、結果を R のプロット関数に渡すこともできます。  たとえば、次の例では *rxCube* を使用して、*numTrans* と *numIntlTrans* のすべての組み合わせに対する *fraudRisk* の平均を計算します。  
  
    ```R  
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)   
    ```  
  
    グループの平均の計算に使用するグループを指定するには、`F()` 表記を使用します。 この例では、`F(numTrans):F(numIntlTrans)` は、変数 _numTrans_ と _numIntlTrans_ の整数を各整数値をレベルとするカテゴリ変数として処理する必要があることを示します。  
  
    低レベルと高レベルは (*colInfo* パラメーターを使用して) データ ソース *sqlFraudDS* に既に追加されているので、レベルはヒストグラムで自動的に使用されます。  
  
5.  *rxCube* の既定の戻り値は、クロス集計を表す *rxCube object* です。 ただし、*rxResultsDF* 関数を使用して、R の標準プロット関数のいずれかで簡単に使用できるデータ フレームに、結果を変換できます。  
  
    ```R  
    cubePlot <- rxResultsDF(cube1)   
    ```  
  
    > [!TIP]  
    > *rxCube* 関数のオプションの引数 *returnDataFrame* = TRUE に注意してください。これを使うと、結果をデータ フレームに直接変換できます。 例:  
    >   
    > `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`  
    >   
    > ただし、*rxResultsDF* の出力の方がはるかに簡潔であり、ソース列の名前が保持されます。  
  
6.  最後に、次のコードを実行し、すべての R ディストリビューションに含まれる **lattice** パッケージの *levelplot* 関数を使用して、ヒート マップを作成します。  
  
    ```R  
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)   
    ```  
  
    **[結果]**  
  
    ![scatterplot results](../../advanced-analytics/r-services/media/rsql-sue-scatterplotresults.jpg "scatterplot results")  
  
この簡単な分析からでも、トランザクションの数および国際的トランザクションの数の両方に伴って不正行為のリスクが高くなることがわかります。

一般的な *rxCube* 関数およびクロス集計表の詳細については、「[Data Summaries](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-summaries)」 (データの概要) を参照してください。  
  
## 次の手順  
[モデルの作成 (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/create-models-data-science-deep-dive.md)  
  
## 前の手順  
[レッスン 2: R スクリプトの作成と実行 (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/lesson-2-create-and-run-r-scripts-data-science-deep-dive.md)  
  
## 参照  
[データ サイエンスの詳細: RevoScaleR パッケージの使用](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
