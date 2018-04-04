---
title: R Services - データの最適化のパフォーマンス |Microsoft ドキュメント
ms.custom: ''
ms.date: 07/12/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 6b320357d8978a97878d31943b48accee8898f9f
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="performance-for-r-services---data-optimization"></a>R Services - データの最適化のパフォーマンス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、次の 2 つのケース スタディに基づいて R Services のパフォーマンスの最適化について説明するシリーズの 3 番目です。 R のパフォーマンス最適化機能について説明、または Python スクリプトの SQL Server で実行されています。 パフォーマンスを向上して、既知の問題を回避する、R コードを更新するのに使用できるメソッドについても説明します。

## <a name="choosing-a-compute-context"></a>コンピューティング コンテキストを選択します。

SQL Server 2016 および 2017 で、いずれかを使用できる、**ローカル**または**SQL** R または Python スクリプトを実行するときにコンテキストを計算します。

使用する場合、**ローカル**コンピューターおよびサーバーではなくコンピューティング コンテキスト、分析を実行します。 そのため、コード内で使用する SQL Server からデータを取得する場合、ネットワーク経由でデータをフェッチする必要があります。 このネットワーク転送によるパフォーマンスの低下は、転送されるデータのサイズ、ネットワークの速度、および同時に発生しているその他のネットワーク転送によって異なります。

使用する場合、 **SQL Server の計算コンテキスト**コードは、サーバーで実行されます。 SQL Server からデータを取得する場合は、データは、分析を実行しているサーバーにローカルにする必要があり、ネットワークのオーバーヘッドが発生しないためです。 その他のソースからデータをインポートする必要がある場合は、ETL をあらかじめ配置を検討してください。

大規模なデータ セットを操作する場合は、常に SQL 計算コンテキストを使用してください。

## <a name="factors"></a>因子

R 言語には、「要素」は、カテゴリ データに対する特別な変数は、の概念があります。 データ サイエンティストは、多くの場合、式で係数変数を使用でデータを確実要因としてのカテゴリの変数を処理するためは、machine learning 関数によって正しく処理です。 詳細については、次を参照してください。 [ダミーの R: 係数変数] (http://www.dummies.com/programming/r/how-to-look-at-the-structure-of-a-factor-in-r/)です。

仕様では、整数とストレージや処理用にもう一度、文字列から、係数の変数を変換します。 R`data.frame`関数は、係数の変数とすべての文字列を処理しない限り、引数*stringsAsFactors*に設定されている**False**です。 これは意味は文字列が自動的には、処理に整数に変換され、その後、元の文字列にマップします。

整数としての要素のソース データが格納されている場合、パフォーマンスが低下、R が係数の整数を実行時に文字列に変換し、独自の内部文字列に整数変換を実行するためです。

このような実行時変換を避けるためには、SQL Server テーブルに整数値として値を格納および使用を検討してください、 _colInfo_要素として使用される列のレベルを指定する引数。 RevoScaleR のほとんどのデータ ソース オブジェクトは、パラメーターを受け取る_colInfo_です。 このパラメーターを使用するには、データ ソースによって使用される変数の名前と、その型を指定、列の値に変数レベルまたは変換を定義します。

たとえば、次の R 関数の呼び出しは、テーブルから 1、2、および 3 の整数を取得、レベル"apple"を持つ要素の値、「オレンジ」および「バナナ」をマッピングします。

```R
c("fruit" = c(type = "factor", levels=as.character(c(1:3)), newLevels=c("apple", "orange", "banana")))
```

基になる列に文字列が含まれている場合は常に詳細を使用して前のレベルを指定すると効率、 _colInfo_パラメーター。 たとえば、次の R コードは、読み取られるとして、要素として文字列を処理します。

```R
c("fruit" = c(type = "factor", levels= c("apple", "orange", "banana")))
```

モデルの生成のセマンティックの相違点がない場合は、後者の方法は、パフォーマンスが向上する可能性があります。

## <a name="data-transformations"></a>データ変換

多くの場合、データ サイエンティストは、分析の一部として R で記述された変換関数を使用します。 変換関数は、テーブルから取得した行ごとに適用されます。 SQL Server では、このような変換は、R インタープリターと分析エンジン間の通信を必要とするバッチで取得されるすべての行に適用されます。 変換を実行するため、データは SQL から分析エンジンに移動し、その後 R インタープリターで処理されて戻ってきます。

このため、R コードの一部として変換を使用して関連するデータの量によって、アルゴリズムのパフォーマンスに悪影響が重要なことができます。

テーブルまたはビューの分析を実行する前にすべての必要な列があり、計算中に変換を回避するのにはより効率的です。 既存のテーブルに列を追加できない場合は、変換後の列を含む別のテーブルまたはビューを作成し、適切なクエリを使用してデータを取得することを検討してください。

## <a name="batch-row-reads"></a>バッチの行を読み取ります

SQL Server データ ソースを使用する場合 (`RxSqlServerData`)、コードのことをお勧めするパラメーターを使用して_rowsPerRead_バッチ サイズを指定します。 このパラメーターは、クエリを実行され、外部のスクリプトに送信して処理される行の数を定義します。 アルゴリズムでは、実行時に、各バッチ内の行の指定された数だけが表示されます。

一度に処理されるデータの量を制御する機能は、解決または問題を回避するのに役立ちます。 たとえば、入力データセットが非常に広い場合 (多くの列を持つ) メモリ不足データのページングを回避するためのバッチ サイズを減らすことができます (フリー テキスト) など、いくつかの大きな列がデータセットに存在、または。

既定では、このパラメーターの値はメモリが不足しているマシン上であっても適切なパフォーマンスを得るため、50000 に設定します。 サーバーに十分なメモリがある場合は、500,000 個以上, 000 にさらにこの値を増やすと、特に大規模テーブルのパフォーマンスを向上できます。

バッチ サイズを増やすことの利点は、複数のプロセスで実行できるタスクと、大きなデータ セットで明らかになります。 ただし、この値を増やすことが常に結果が得られないベストです。 データと、最適な値を特定するアルゴリズムを試すことをお勧めします。

## <a name="parallel-processing"></a>並列処理

パフォーマンスを向上させる**rx**分析関数は、サーバー コンピューターで使用可能なコアを使用して並列にタスクを実行する SQL Server の機能を活用することができます。

これには SQL Server での R の並列化を実現するために 2 つの方法があります。

-   **使用して\@並列です。** `sp_execute_external_script` ストアド プロシージャを使用して R スクリプトを実行する場合は、`@parallel` パラメーターを `1` に設定します。 これは、R スクリプトでは、場合に最適な方法**されません**処理のためには、その他のメカニズムである必要が RevoScaleR 関数を使用します。 場合、スクリプトは、RevoScaleR 関数 (通常、プレフィックス"rx") を使用して、並列処理は自動的に実行を明示的に設定する必要はありません`@parallel`に`1`です。

    R スクリプトを並列に処理でき、SQL クエリを並列化できる場合は、データベース エンジンは複数の並列処理を作成します。 作成できるプロセスの最大数と等しい、**並列処理の次数の最大**インスタンス (MAXDOP) 設定します。 すべてのプロセスは、同じスクリプトを実行しがデータの一部のみを受信します。
    
    したがって、このメソッドはない場合など、すべてのデータを表示する必要がありますスクリプトで、モデルをトレーニングします。 ただし、バッチ予測などのタスクを並列で実行する場合は便利です。 並列処理を使用する方法についての`sp_execute_external_script`を参照してください、**ヒントの詳細: 並列処理**のセクション[TRANSACT-SQL での R コードを使用して](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)です。

-   **NumTasks を使用して 1 を = です。** 使用する場合**rx** SQL Server のコンピューティング コンテキストで関数の値の設定、 _numTasks_パラメーターを作成するにはプロセスの数。 作成されたプロセスの数にすることはできません以上**MAXDOP**です。 ただし、データベース エンジンによって作成されたプロセスの実際の数が決定されます、するよりも小さいを要求できます。

    R スクリプトを並列に処理でき、SQL クエリを並列化できる場合は rx 関数の実行時に SQL Server によって複数の並列処理に作成されます。 作成されるプロセスの実際の数は、さまざまなリソース管理などの要因によって、リソース、その他のセッション、および R スクリプトで使用されるクエリのクエリ実行プランの現在の使用量によって異なります。

## <a name="query-parallelization"></a>クエリの並列処理

Microsoft R では、RxSqlServerData データ ソース オブジェクトと、データを定義することで SQL Server データ ソースを操作できます。

全体のテーブルまたはビューに基づくデータ ソースを作成します。

```R
RxSqlServerData(table= "airline", connectionString = sqlConnString)
```

SQL クエリに基づくデータ ソースを作成します。

```R
RxSqlServerData(sqlQuery= "SELECT [ArrDelay],[CRSDepTime],[DayOfWeek] FROM  airlineWithIndex WHERE rowNum <= 100000", connectionString = sqlConnString)
```

> [!NOTE]
> R Services が、テーブルからフェッチするために必要な列を決定する内部ヒューリスティックを使用して、テーブルがクエリではなく、データ ソースで指定されている場合ただし、この方法では、並列実行で発生する可能性はありません。

データを並列で分析できるためには、データベース エンジンが、並列クエリ プランを作成できるようにデータを取得するためのクエリを囲む必要があります。 コードまたはアルゴリズムは、大量のデータを使用している場合、以下のことを確認する指定されたクエリ`RxSqlServerData`並列実行に適しています。 並列実行プランにならないクエリは、計算の 1 つのプロセスになる可能性があります。

大規模なデータセットを使用する必要がある場合は、Management Studio や、R コードを実行する前に別の SQL クエリ アナライザーを使用して、実行プランを分析します。 クエリのパフォーマンスを向上させるためにすべての推奨手順を実行します。 たとえば、テーブルのインデックス不足は、クエリの実行時間に影響する可能性があります。 詳細については、次を参照してください。[パフォーマンスの監視とチューニング](../../relational-databases/performance/monitor-and-tune-for-performance.md)です。

パフォーマンスに影響する他のよくある間違いは、クエリが必要な数より多い列を取得します。 たとえば、数式は、3 つだけの列に基づいていますが、ソース テーブル内の 30 個の列が場合、データを不必要に移動します。

 + 使用しないでください`SELECT *`!
 + データセット内の列を確認し、分析に必要なものだけを識別する時間がかかる
 + GUID および rowguids などの R コードと互換性がないデータ型を含むすべての列に、クエリから削除します。
 + サポートされていない日付と時刻の形式の確認
 + テーブルを読み込むではなく特定の値を選択または変換エラーを回避する列をキャストするビューを作成します。

## <a name="optimizing-the-machine-learning-algorithm"></a>機械学習アルゴリズムを最適化します。

このセクションではその他のヒントと RevoScaleR と Microsoft R. に他のオプションに固有のリソース

> [!TIP]
> R の最適化の一般的なディスカッションでは、この記事の範囲外です。 ただし、コードに高速化するため必要がある場合をお勧め、人気のある記事[、R Inferno](http://www.burns-stat.com/pages/Tutor/R_inferno.pdf)です。 R でのプログラミング構成要素と鮮明な言語と詳細のよくある落とし穴について説明し、R プログラミング手法の多くの具体例を提供します。

### <a name="optimizations-for-revoscaler"></a>RevoScaleR 用の最適化

RevoScaleR アルゴリズムの多くは、トレーニング済みモデルを生成する方法を制御するパラメーターをサポートします。 精度とモデルの正確性は重要ですが、アルゴリズムのパフォーマンスが等しく重要な場合があります。 精度とトレーニングの時間のバランスを取得するには、および多くの場合、計算の速度を上げるため、正確性や正確性を減らさずにパフォーマンスが向上するパラメーターを変更できます。

+ [rxDTree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)

    `rxDTree` サポートしている、`maxDepth`パラメーターで、デシジョン ツリーの深さを制御します。 として`maxDepth`は大きくしても、パフォーマンスが低下、ため、パフォーマンスの低下と深さを増やすことの利点を分析することが重要です。

    などのパラメーターを調整することで時間の複雑さと予測の精度のバランスを制御することもできます。 `maxNumBins`、 `maxDepth`、 `maxComplete`、および`maxSurrogate`です。 深さを 10 または 15 を超えた値に増やすと、計算が非常に不経済になる可能性があります。

+ [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)

    使用してみて、`cube`引数の式の最初の依存する変数が要素変数の場合。
    
    ときに`cube`に設定されている`TRUE`、処理が速くなる場合があり、標準の回帰の計算よりも少ないメモリを使用するパーティションの逆関数を使用して、回帰を実行します。 数式に大量の変数がある場合は、パフォーマンスが大幅に向上する可能性があります。

+ [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)

    使用して、`cube`引数の最初の従属変数が要素変数の場合。
    
    ときに`cube`に設定されている`TRUE`アルゴリズムで処理が速くなる場合がありますより少ないメモリを使用してパーティションの逆関数を使用します。 数式に大量の変数がある場合は、パフォーマンスが大幅に向上する可能性があります。

RevoScaleR の最適化に関する追加のガイダンスについては、次の記事を参照してください。

+ サポートの記事:[パフォーマンス チューニング rxDForest および rxDTree オプション](https://support.microsoft.com/kb/3104235)

+ ブースト ツリー モデルでモデルを制御するためのメソッドと一致:[の推定モデルを使用して確率的勾配ブースティング](https://docs.microsoft.com/r-server/r/how-to-revoscaler-boosting)

+ RevoScaleR の移動やデータの処理の方法の概要: [ScaleR でカスタムのチャンク アルゴリズムを記述します。](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ RevoScaleR のプログラミング モデル: [RevoScaleR でスレッドを管理します。](https://docs.microsoft.com/r-server/r/how-to-developer-manage-threads)

+ 関数の参照[rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

+ 関数の参照[rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)

### <a name="use-microsoftml"></a>MicrosoftML を使用します。

また、新しいを調査することをお勧め**MicrosoftML**パッケージで、計算コンテキストと RevoScaleR によって提供される変換に使用できるスケーラブルな機械学習アルゴリズムを提供します。

+ [MicrosoftML を概要します。](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)

+ [MicrosoftML アルゴリズムを選択する方法](https://docs.microsoft.com/r-server/r/how-to-choose-microsoftml-algorithms-cheatsheet)

### <a name="operationalize-a-solution-using-microsoft-r-server"></a>Microsoft R Server を使用してソリューションを運用します。

シナリオでは、保存されたモデルを使用して予測を高速または機械学習をアプリケーションに統合することができますを使用する場合、[操作運用](https://docs.microsoft.com/r-server/what-is-operationalization)(旧称 DeployR) Microsoft R Server の機能です。

+ として、**データ サイエンティスト**を使用して、 [mrsdeploy パッケージ](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package)を他のコンピューターと R コードを共有し、web、デスクトップ、モバイル、およびダッシュ ボード アプリケーション内で R の分析の統合:[を公開する方法R Server で R web サービスおよび管理](https://docs.microsoft.com/r-server/operationalize/how-to-deploy-web-service-publish-manage-in-r)

+ として、**管理者**、パッケージの管理、web のノードを監視する方法について説明し、コンピューティング ノード、および R ジョブのセキュリティを制御します[とやり取りして、R での web サービスを使用する方法。](https://docs.microsoft.com/r-server/operationalize/how-to-consume-web-service-interact-in-r)

## <a name="articles-in-this-series"></a>この系列内のアーティクル

[パフォーマンス – R のチューニングの概要](sql-server-r-services-performance-tuning.md)

[R - SQL Server の構成のパフォーマンスの調整](sql-server-configuration-r-services.md)

[R の R のパフォーマンスの調整コードとデータの最適化](r-and-data-optimization-r-services.md)

[パフォーマンスのチューニングのケース スタディ結果](performance-case-study-r-services.md)
