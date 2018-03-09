---
title: "単純なシミュレーション (SQL と R deep dive) を作成 |Microsoft ドキュメント"
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
dev_langs:
- R
ms.assetid: f420b816-ddab-4a1a-89b9-c8285a2d33a3
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: cc613d303fa3200c3460face71399223e00272e6
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="create-a-simple-simulation-sql-and-r-deep-dive"></a>単純なシミュレーション (SQL と R deep dive) の作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事は、最後の手順を使用する方法について、データ サイエンス Deep Dive のチュートリアルで[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) SQL Server とします。

これまで使用したように設計された R 関数の間でデータを移動するには、具体的には[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]およびローカル コンピューティング コンテキスト。 しかしながら、独自のカスタム R 関数を記述し、それをサーバーで実行するにはどうすればよいでしょうか。

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rxExec [関数を使用して、](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) コンピューターで任意の関数を呼び出すことができます。 使用することも**rxExec**明示的に作業を 1 つのサーバーのコアに分散させる。

このレッスンでは、リモート サーバーを使用する単純なシミュレーションを作成します。 このシミュレーションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データは必要ありません。この例では、カスタム関数を設計し、 **rxExec** を使用してそれを呼び出す方法のみを示します。

使用するより複雑な例については**rxExec**、この記事を参照してください: [foreach と rxExec 粒度が粗い並列処理](http://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)

## <a name="create-the-custom-function"></a>ユーザー定義関数を作成します。

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
  
2.  さいころの 1 つのゲームをシミュレートするには、関数を実行します。
  
    ```R
    rollDice()
    ```
  
    あなたの勝ちでしたか。それとも負けでしたか。
  
今すぐを使用する方法を見て**rxExec**関数を複数回実行する、成功の確率を特定するのに役立つシミュレーションを作成します。

## <a name="create-the-simulation"></a>シミュレーションを作成します。

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターで任意の関数を実行するには、 **rxExec** 関数を呼び出します。 **RxExec**も並列でノード間での関数の実行の分散をサポートしているまたはコアのコンテキストでは、サーバー、ここで、SQL Server コンピューターで、カスタム関数を実行します。

1. カスタム関数に渡す引数として呼び出す**rxExec**シミュレーションを変更するその他のパラメーターと連携して、します。
  
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
  
     *損失 Win* *12 8*

## <a name="conclusions"></a>結論

このチュートリアルで、次の作業を習得しました。
  
-   分析で使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データを取得する
  
-   R のデータ ソースを作成し、変更する
  
-   ワークステーションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバーの間でモデル、データ、プロットを渡す
  

1,000万観測の大規模なデータセットを使用してこれらの手法をテストする場合は、データ ファイルは、Revolution analytics の web サイトから:[データセットのインデックス](http://packages.revolutionanalytics.com/datasets)

大きなデータ ファイルのこのチュートリアルを再利用するには、データをダウンロードして各データ ソースの次のように変更します。

1. 変数の変更`ccFraudCsv`と`ccScoreCsv`新しいデータ ファイルを指定するには
2. 参照されるテーブルの名前を変更*sqlFraudTable*に`ccFraud10`
3. 参照されるテーブルの名前を変更*sqlScoreTable*に`ccFraudScore10`

## <a name="additional-samples"></a>その他のサンプル

計算コンテキストと RevoScaler 関数に渡すし、データ変換の使用を習得すれば、これでは、このチュートリアルを確認します。

[Machine Learning のサービスの R のチュートリアル](machine-learning-services-tutorials.md)
## <a name="previous-step"></a>前の手順

[SQL Server と XDF ファイル間のデータの移動](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
