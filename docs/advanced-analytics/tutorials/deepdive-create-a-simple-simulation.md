---
title: (SQL と R の詳細情報) の簡単なシミュレーションの作成 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b0db5fdfd177f1303432659f7a96b0fbf111c000
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51698240"
---
# <a name="create-a-simple-simulation-sql-and-r-deep-dive"></a>(SQL と R の詳細情報) の簡単なシミュレーションを作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、最後の手順をチュートリアルでは、データ サイエンスの詳細情報、使用する方法の[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

これまで使用したように設計された R 関数の間でデータを移動するには、具体的には[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]とローカル コンピューティング コンテキスト。 しかしながら、独自のカスタム R 関数を記述し、それをサーバーで実行するにはどうすればよいでしょうか。

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rxExec [関数を使用して、](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) コンピューターで任意の関数を呼び出すことができます。 使用することも**rxExec**を明示的に作業を 1 つのサーバー コアに分散します。

このレッスンでは、リモート サーバーを使用する簡単なシミュレーションを作成します。 このシミュレーションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データは必要ありません。この例では、カスタム関数を設計し、 **rxExec** を使用してそれを呼び出す方法のみを示します。

使用するより複雑な例については**rxExec**、この記事を参照してください: [foreach と rxExec 粒度が粗い並列処理](https://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)

## <a name="create-the-custom-function"></a>カスタム関数を作成します。

一般的なカジノ ゲームでは、一組のサイコロを次のルールで転がします。

- 最初に転がしたとき、7 か 11 になれば、あなたの勝ちです。
- 2、3、12 が出た場合、あなたの負けです。
- 4、5、6、8、9、10 が出た場合、その数があなたのポイントになり、そのポイントを出すか、7 を出すまでサイコロを振り続けます。そのポイントが出たら、あなたの勝ちで、7 が出たら、あなたの負けです。

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
                { result \<- "Loss" }
                else if (count > 1 && roll == 7 )
                { result \<- "Loss" }
                else if (count > 1 && point == roll)
                { result <- "Win" }
                else { count <- count + 1 }
            }
            result
    }
    ```
  
2.  1 つのサイコロ ゲームをシミュレートするには、関数を実行します。
  
    ```R
    rollDice()
    ```
  
    あなたの勝ちでしたか。それとも負けでしたか。
  
今すぐ使用する方法を見てみましょう**rxExec**関数を複数回実行する、成功の確率を特定するのに役立つシミュレーションを作成します。

## <a name="create-the-simulation"></a>シミュレーションを作成します。

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターで任意の関数を実行するには、 **rxExec** 関数を呼び出します。 **RxExec**も並列ノード間で、関数の実行の分散をサポートしているか、コア サーバーのコンテキストは、ここで、SQL Server コンピューターで、カスタム関数を実行します。

1. 引数としてカスタム関数を呼び出す**rxExec**をシミュレーションを変更するその他のパラメーターを使用します。
  
    ```R
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")
    length(sqlServerExec)
    ```
  
    - *timesToRun* 引数を使用すれば、関数を実行する回数を指示できます。  この場合、20 回サイコロを振ります。
  
    - *RNGseed* 引数と *RNGkind* 引数を利用し、乱数の生成を制御できます。 *RNGseed* が **auto**に設定されると、各ワーカーで並行乱数ストリームが初期化されます。
  
2. **rxExec** 関数は実行のたびに 1 つの要素で一覧を作成します。ただし、一覧が完了するまで内容はわかりません。 すべての繰り返しが完了すると、 `length` から始まる行が値を返します。
  
    次の手順に進むと、勝敗記録のまとめを取得できます。
  
3. R の `unlist` 関数を使用して、返された一覧をベクトルに変換し、 `table` コンピューターで任意の関数を呼び出すことができます。
  
    ```R
    table(unlist(sqlServerExec))
    ```
  
    結果は次のようになります。
  
     *負け勝ち* *12 8*

## <a name="conclusions"></a>結論

このチュートリアルで、次の作業を習得しました。
  
-   分析で使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データを取得する
  
-   R のデータ ソースを作成し、変更する
  
-   ワークステーションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバーの間でモデル、データ、プロットを渡す
  

Revolution analytics web サイトからデータ ファイルは 1,000万の所見の大規模なデータセットを使用してこれらの手法を実験したい場合:[データセットのインデックス](https://packages.revolutionanalytics.com/datasets)

大きなデータ ファイルでこのチュートリアルを再利用するには、データをダウンロードし、各データ ソースの次のように変更します。

1. 変数の変更`ccFraudCsv`と`ccScoreCsv`新しいデータ ファイルを指定するには
2. 参照されるテーブルの名前を変更*sqlFraudTable*に `ccFraud10`
3. 参照されるテーブルの名前を変更*sqlScoreTable*に `ccFraudScore10`

## <a name="additional-samples"></a>その他のサンプル

コンピューティング コンテキストを渡すし、データ変換の RevoScaler 関数の使用を習得したので、これでは、これらのチュートリアルをご覧ください。

[Machine Learning Services の R のチュートリアル](machine-learning-services-tutorials.md)
## <a name="previous-step"></a>前の手順

[SQL Server と XDF ファイル間のデータの移動](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
