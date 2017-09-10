---
title: "レッスン 5: 簡単なシミュレーションの作成 (データ サイエンスの詳細情報) | Microsoft Docs"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: f420b816-ddab-4a1a-89b9-c8285a2d33a3
caps.latest.revision: 16
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e5bbd69bba01da2aacd3b8912aebac6b4e1c28a1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-simple-simulation"></a>単純なシミュレーションを作成します。

これまで使用したように設計された R 関数の間でデータを移動するには、具体的には[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]およびローカル コンピューティング コンテキスト。 しかしながら、独自のカスタム R 関数を記述し、それをサーバーで実行するにはどうすればよいでしょうか。

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rxExec **関数を使用して、** コンピューターで任意の関数を呼び出すことができます。 また、明示的に作業を単一のサーバー ノード内のコアに分散させる rxExec を使用することができます。

このレッスンでは、リモート サーバーを利用し、簡単なシミュレーションを作成します。 シミュレーションのいずれかで必要としない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データの例では、カスタム関数を設計し、rxExec 関数を使用してを呼び出す方法についてのみ説明します。

RxExec を使用するより複雑な例は、この記事を参照してください: [foreach と rxExec 粒度が粗い並列処理](http://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)

## <a name="create-the-function"></a>関数を作成する

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
  
2.  関数を実行すると、サイコロ ゲームが 1 回シミュレートされます。
  
    ```R
    rollDice()
    ```
  
    あなたの勝ちでしたか。それとも負けでしたか。
  
次に関数を何度も実行し、勝率の決定に役立つシミュレーションを作成します。

## <a name="create-the-simulation"></a>シミュレーションを作成する

コンテキストで任意の関数を実行する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rxExec 関数を呼び出すコンピューター。 RxExec もサポートしていますが、関数の実行の分散並列でノードまたはコア サーバーのコンテキスト内で、ここに使用することのみ、サーバーで、ユーザー定義関数を実行します。

1. シミュレーションを変更するその他のいくつかのパラメーターと共に、rxExec への引数としてユーザー定義関数を呼び出します。
  
    ```R
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")
    length(sqlServerExec)
    ```
  
    - *timesToRun* 引数を使用すれば、関数を実行する回数を指示できます。  この場合、20 回サイコロを振ります。
  
    - *RNGseed* 引数と *RNGkind* 引数を利用し、乱数の生成を制御できます。 *RNGseed* が **auto**に設定されると、各ワーカーで並行乱数ストリームが初期化されます。
  
2. RxExec 関数は、それぞれの実行に 1 つの要素を持つリストを作成します。ただし、多く発生している一覧が完了するまでは表示されません。 すべての繰り返しが完了すると、 `length` から始まる行が値を返します。
  
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
  
>  [!TIP]
> 
> 1,000万観測の大規模なデータセットを使用してこれらの手法をテストする場合は、データ ファイルは、Revolution analytics の web サイトから:[データセットのインデックス](http://packages.revolutionanalytics.com/datasets)
>   
> 大きなデータ ファイルのこのチュートリアルを再利用するには、データをダウンロードして各データ ソースの次のように変更します。
>  - 新しいデータ ファイルをポイントするように変数の *ccFraudCsv* と *ccScoreCsv* を設定する
>  - *sqlFraudTable* で参照されるテーブルの名前を *ccFraud10*に変更する
>  - *sqlScoreTable* で参照されるテーブルの名前を *ccFraudScore10*に変更する

## <a name="previous-step"></a>前の手順

[SQL Server と XDF ファイル間でデータを移動します。](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)



