---
title: "レッスン 5: 簡単なシミュレーションの作成 (データ サイエンスの詳細情報) | Microsoft Docs"
ms.custom: ""
ms.date: "10/03/2016"
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
ms.assetid: f420b816-ddab-4a1a-89b9-c8285a2d33a3
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# レッスン 5: 簡単なシミュレーションの作成 (データ サイエンスの詳細情報)
今までは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とローカル コンピューティング コンテキストの間でデータを移動させるための SQL Server R Services が提供する R 関数を利用していました。 しかしながら、独自のカスタム R 関数を記述し、それをサーバーで実行するにはどうすればよいでしょうか。  
  
*rxExec* 関数を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターで任意の関数を呼び出すことができます。 また、*rxExec* を使用すると、単一サーバー ノードのコア全体で作業を明示的に分散させることもできます。  
  
このレッスンでは、リモート サーバーを利用し、簡単なシミュレーションを作成します。 このシミュレーションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データは必要ありません。この例では、カスタム関数を設計し、*rxExec* を使用してそれを呼び出す方法のみを示します。  
  
より複雑な *rxExec* の使用例については、記事 [http://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html](http://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html) を参照してください。  
  
## 関数を作成する  
一般的なカジノ ゲームでは、一組のサイコロを次のルールで転がします。  
  
-   最初に転がしたとき、7 か 11 になれば、あなたの勝ちです。  
  
-   2、3、12 が出た場合、あなたの負けです。  
  
-   4、5、6、8、9、10 が出た場合、その数があなたのポイントになり、そのポイントを出すか、7 を出すまでサイコロを振り続けます。そのポイントが出たら、あなたの勝ちで、7 が出たら、あなたの負けです。  
  
このゲームは R で簡単にシミュレートできます。カスタム関数を作成し、それを何度も実行します。  
  
1.  次の R コードを使用して、カスタム関数を作成します。  
  
    ```R  
    rollDice <- function()   
    {   
        result <- NULL        
        point <- NULL     
        count <- 1   
            while (is.null(result))   
            {   
                roll <- sum(sample(6, 2, replace=TRUE))   
  
                if (is.null(point))   
                { point <- roll }   
                if (count == 1 && (roll == 7 || roll == 11))   
                {  result <- "Win" }   
                else if (count == 1 && (roll == 2 || roll == 3 || roll == 12))    
                { result <- "Loss" }    
                else if (count > 1 && roll == 7 )   
                { result <- "Loss" }    
                else if (count > 1 && point == roll)   
                { result <- "Win" }    
                else { count <- count + 1 }   
            }   
            result   
    }  
  
    ```  
  
2.  関数を実行すると、サイコロ ゲームが 1 回シミュレートされます。  
  
    ```R  
    rollDice()   
    ```  
  
    あなたの勝ちでしたか。それとも負けでしたか。  
  
次に関数を何度も実行し、勝率の決定に役立つシミュレーションを作成します。  
  
## シミュレーションを作成する  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターで任意の関数を実行するには、*rxExec* 関数を呼び出します。 *rxExec* では、1 つのサーバーのノード全体またはコア全体で関数を並行分散実行できますが、ここではサーバーでカスタム関数を実行するためだけに使用します。  
  
1.  *rxExec* への引数としてカスタム関数を呼び出し、シミュレーションを変更する他のパラメーターを指定します。  
  
    ```R  
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")   
    length(sqlServerExec)   
    ```  
  
    -   *timesToRun* 引数を使用すれば、関数を実行する回数を指示できます。  この場合、20 回サイコロを振ります。  
  
    -   *RNGseed* 引数と *RNGkind* 引数を利用し、乱数の生成を制御できます。 *RNGseed* が **auto** に設定されると、各ワーカーで並行乱数ストリームが初期化されます。  
  
2.  *rxExec* 関数は実行のたびに 1 つの要素で一覧を作成します。ただし、一覧が完了するまで内容はわかりません。 すべての繰り返しが完了すると、`length` から始まる行が値を返します。  
  
    次の手順に進むと、勝敗記録のまとめを取得できます。  
  
3.  R の *unlist* 関数を使用して、返された一覧をベクトルに変換し、*table* 関数を使用して結果をまとめます。  
  
    ```R  
    table(unlist(sqlServerExec))  
    ```  
  
    結果は次のようになります。  
  
     *負け  勝ち*   
     *12  8*  
  
## 結論  
このチュートリアルで、次の作業を習得しました。  
  
-   分析で使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データを取得する  
  
-   R のデータ ソースを作成し、変更する  
  
-   ワークステーションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバーの間でモデル、データ、プロットを渡す  
  
>  [!TIP]
> 
> さらに大きなデータセット (1000 万件の観察結果) で以上の手法を試す場合は、[http://packages.revolutionanalytics.com/datasets](http://packages.revolutionanalytics.com/datasets) からデータ ファイルを入手できます。  
>   
> 大きなデータ ファイルでこのチュートリアルを再利用するには、データをダウンロードし、データ ソースを次のように変更します。   
>  -   新しいデータ ファイルをポイントするように変数の *ccFraudCsv* と *ccScoreCsv* を設定する     
>  -   *sqlFraudTable* で参照されるテーブルの名前を *ccFraud10* に変更する    
>  -   *sqlScoreTable* で参照されるテーブルの名前を *ccFraudScore10* に変更する   
  
## 前の手順  
[SQL Server と XDF ファイルの間でデータを移動させる (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/move-data-between-sql-server-and-xdf-file-data-science-deep-dive.md)  
  
  
  
