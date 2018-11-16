---
title: SQL Server R Services - データの最適化のパフォーマンス |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3fda560aedb7a0e1119a0524ffefe42a476c4aed
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51699510"
---
# <a name="performance-for-r-services---data-optimization"></a>R Services - データの最適化のパフォーマンス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、2 つのケース スタディに基づく R Services のパフォーマンスの最適化を説明するシリーズの 3 つ目です。 この記事では、R のパフォーマンスの最適化をについて説明します。 または、Python スクリプトの SQL Server で実行されています。 パフォーマンスを向上し、既知の問題を回避するために、R コードを更新するための方法も説明します。

## <a name="choosing-a-compute-context"></a>コンピューティング コンテキストを選択します。

SQL Server 2016 および 2017 で、いずれかを使用できる、**ローカル**または**SQL** R または Python スクリプトを実行するときに、コンピューティング コンテキスト。

使用する場合、**ローカル**コンピューターおよびサーバーではなく、分析、コンピューティング コンテキストを実行します。 そのため、コードで使用する SQL Server からデータを取得する場合、データをネットワーク経由でフェッチする必要があります。 このネットワーク転送によるパフォーマンスの低下は、転送されるデータのサイズ、ネットワークの速度、および同時に発生しているその他のネットワーク転送によって異なります。

使用する場合、 **SQL Server 計算コンテキスト**コードは、サーバーで実行されます。 SQL Server からデータを取得する場合は、データは、分析を実行するサーバーにローカルにする必要があり、ネットワークのオーバーヘッドが発生しないためです。 他のソースからデータをインポートする必要がある場合は、ETL を事前に配置することを検討します。

大規模なデータ セットを操作する場合は、常に SQL 計算コンテキストを使用してください。

## <a name="factors"></a>因子

R 言語の概念には*要因*、カテゴリ データの特殊な変数であります。 データ サイエンティストは多くの場合、数式で因子変数を使用して、データを確実要因としてのカテゴリの変数を処理するためは、machine learning の関数によって正しく処理します。 詳細については、次を参照してください。[ダミーの R: 因子変数](https://www.dummies.com/programming/r/how-to-look-at-the-structure-of-a-factor-in-r/)します。

仕様では、整数と保管または処理用にもう一度因子変数文字列から変換できます。 R`data.frame`場合を除き、関数が要素の変数としてすべての文字列を処理、引数*stringsAsFactors*に設定されている**False**します。 これにより、処理するために整数に変換され、元の文字列にマップされ、文字列が自動的には。

要素のソース データが、整数として格納されている場合パフォーマンスが低下、R 係数の整数を実行時に文字列に変換し、独自の内部文字列から整数型に変換を実行するためです。

このような実行時変換を回避するには、として、SQL Server テーブル内の整数値を格納して、使用を検討してください、 _colInfo_要素として使用する列のレベルを指定する引数。 RevoScaleR のほとんどのデータ ソース オブジェクトは、パラメーターを受け取る_colInfo_します。 データ ソースで使用される変数の名前で、型を指定して、列の値で変数のレベルや変換を定義するには、このパラメーターを使用します。

たとえば、次の R 関数の呼び出しはテーブルから 1、2、および 3 の整数を取得します。、"apple"レベルの要素の値、「オレンジ」および"banana"をマッピングします。

```R
c("fruit" = c(type = "factor", levels=as.character(c(1:3)), newLevels=c("apple", "orange", "banana")))
```

基になる列に文字列が含まれている場合は常に詳細を使用して、事前にレベルを指定する効率的な_colInfo_パラメーター。 たとえば、次の R コードは、読み取られるとして、要因として、文字列を処理します。

```R
c("fruit" = c(type = "factor", levels= c("apple", "orange", "banana")))
```

モデルの生成でセマンティックな相違点がない場合は、後者のアプローチはパフォーマンスが向上するつながることができます。

## <a name="data-transformations"></a>データ変換

多くの場合、データ サイエンティストは、分析の一部として R で記述された変換関数を使用します。 変換関数は、テーブルから取得した各行に適用されます。 SQL Server では、このような変換は、R インタープリターと分析エンジン間の通信を必要とする、バッチで取得したすべての行に適用されます。 変換を実行するため、データは SQL から分析エンジンに移動し、その後 R インタープリターで処理されて戻ってきます。

このため、R コードの一部として変換を使用して関連するデータの量によって、アルゴリズムのパフォーマンスに悪影響が重要なことができます。

テーブルまたはビュー、分析を実行する前にすべての必要な列があり、計算中に変換を回避する方が効率的になります。 既存のテーブルに列を追加できない場合は、変換後の列を含む別のテーブルまたはビューを作成し、適切なクエリを使用してデータを取得することを検討してください。

## <a name="batch-row-reads"></a>バッチの行を読み取ります

SQL Server のデータ ソースを使用する場合 (`RxSqlServerData`) で、コードをお勧め、パラメーターを使用して試してみること_rowsPerRead_バッチ サイズを指定します。 このパラメーターは、クエリを実行し、外部のスクリプトに送信して処理を行の数を定義します。 アルゴリズムでは、実行時に指定した各バッチ内の行の数のみが表示されます。

一度に処理されるデータの量を制御する機能は、解決または問題を回避するのに役立ちます。 たとえば、入力データセットが非常に広い場合 (多数の列がある)、またはデータセットにフリー テキスト) など、いくつかの大きな列がある場合は、メモリ不足データのページングを回避するためにバッチ サイズを小さくことができます。

既定では、このパラメーターの値は低いメモリ マシン上であっても適切なパフォーマンスを確保、50000 に設定されます。 サーバーに十分なメモリがある場合は、500,000 または 1,000,000 にこの値を増やすと、特に大規模なテーブルのパフォーマンスを向上できます。

バッチ サイズを増やすことの利点は、複数のプロセスで実行できるタスクと大規模なデータ セットでは、明らかになります。 ただし、この値を増やすことが常になければ、最適な結果です。 お客様のデータと、最適な値を特定するアルゴリズムを試すことをお勧めします。

## <a name="parallel-processing"></a>並列処理

パフォーマンスを向上させる**rx**分析関数は、サーバー コンピューターで使用可能なコアを使用して並列でタスクを実行する SQL Server の機能を活用することができます。

SQL Server で R を使用した並列化を実現するために 2 つの方法はあります。

-   **使用\@並列です。** `sp_execute_external_script` ストアド プロシージャを使用して R スクリプトを実行する場合は、`@parallel` パラメーターを `1` に設定します。 最適な方法は、R スクリプトの場合これは**いない**処理のためには、その他のメカニズムがあるは、RevoScaleR 関数を使用します。 スクリプト (一般的に rx が付く"")、RevoScaleR 関数を使用する場合は、並列処理が自動的に実行を明示的に設定する必要はありません`@parallel`に`1`します。

    R スクリプトを並列に処理でき、SQL クエリを並列化できる場合は、データベース エンジンは複数の並列プロセスを作成します。 作成できるプロセスの最大数が等しく、**並列処理の最大限度**インスタンスの (MAXDOP) 設定します。 すべてのプロセスは、同じスクリプトを実行しが、データの一部のみが表示されます。
    
    したがって、このメソッドは場合など、すべてのデータを確認する必要がありますスクリプトでは有用モデルをトレーニングします。 ただし、バッチ予測などのタスクを並列で実行する場合は便利です。 並列化を使用しての詳細については`sp_execute_external_script`を参照してください、**ヒントの詳細: 並列処理**の[TRANSACT-SQL での R コードを使用して](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)します。

-   **NumTasks を使用して、1 を = です。** 使用する場合**rx**で SQL Server 計算コンテキストでは、関数の値の設定、 _numTasks_パラメーターを作成するにはプロセスの数。 作成されたプロセスの数にすることはできません以上**MAXDOP**。 ただし、データベース エンジンによって作成されたプロセスの実際の数が決定されます、要求することがよりも簡単です。

    R スクリプトを並列に処理でき、SQL クエリを並列化できる場合は、rx 関数を実行している場合に SQL Server によって複数の並列プロセスに作成されます。 作成されたプロセスの実際の数は、さまざまなリソース ガバナンスなどの要因、リソース、他のセッション、および R スクリプトで使用されるクエリのクエリ実行プランの現在の使用量に依存します。

## <a name="query-parallelization"></a>クエリの並列処理

Microsoft R では、RxSqlServerData データ ソース オブジェクトとしてデータを定義して SQL Server データ ソースを操作できます。

全体のテーブルまたはビューをに基づいてデータ ソースを作成します。

```R
RxSqlServerData(table= "airline", connectionString = sqlConnString)
```

SQL クエリに基づくデータ ソースを作成します。

```R
RxSqlServerData(sqlQuery= "SELECT [ArrDelay],[CRSDepTime],[DayOfWeek] FROM  airlineWithIndex WHERE rowNum <= 100000", connectionString = sqlConnString)
```

> [!NOTE]
> R Services が内部のヒューリスティックを使用して、テーブルから取得するために必要な列を決定する場合は、クエリではなく、データ ソースにテーブルを指定すると、ただし、この方法では、並列実行で発生する可能性はありません。

確実に並列でデータを分析することができます、データベース エンジンが並列クエリ プランを作成できるように、データを取得するためのクエリを構成する必要があります。 コードやアルゴリズムは、大量のデータを使用している場合、以下のことを確認する指定されたクエリ`RxSqlServerData`は並列実行用に最適化されています。 並列実行プランにならないクエリは、計算の 1 つのプロセスになる可能性があります。

大規模なデータセットを使用する必要がある場合は、Management Studio または R コードを実行する前に、別の SQL クエリ アナライザーを使用して、実行プランを分析します。 クエリのパフォーマンスを向上させるために推奨される手順を実行し、します。 たとえば、テーブルのインデックス不足は、クエリの実行時間に影響する可能性があります。 詳細については、次を参照してください。[パフォーマンスの監視とチューニング](../../relational-databases/performance/monitor-and-tune-for-performance.md)します。

パフォーマンスに影響を与えるもう 1 つのよくある間違いは、クエリが必要な数より多い列を取得します。 たとえば、数式は、3 つだけの列に基づいていますが、ソース テーブル内の 30 個の列が、移動する場合はデータが不必要にします。

 + 使用しないでください`SELECT *`!
 + データセット内の列を確認し、分析のために必要なもののみを識別する時間がかかる
 + GUID や更新などの R コードと互換性があるデータ型を含むすべての列に、クエリから削除します。
 + サポートされていない日付と時刻の形式の確認
 + テーブルを読み込むのではなく特定の値を選択するか、変換エラーを回避するために列をキャストするビューを作成します。

## <a name="optimizing-the-machine-learning-algorithm"></a>機械学習アルゴリズムを最適化します。

このセクションでは、その他のヒントと RevoScaleR と Microsoft R での他のオプションに固有のリソースを提供します。

> [!TIP]
> R の最適化の概要については、この記事の範囲外です。 ただし、コードを速く必要がある場合をお勧め、人気のある情報の記事[、R Inferno](https://www.burns-stat.com/pages/Tutor/R_inferno.pdf)します。 R でのプログラミング構成要素と鮮明な言語と詳細のよくある落とし穴について説明し、R プログラミング技法の多くの具体例を提供します。

### <a name="optimizations-for-revoscaler"></a>RevoScaleR の最適化

RevoScaleR アルゴリズムの多くは、トレーニング済みモデルを生成する方法を制御するパラメーターをサポートします。 精度とモデルの正確性は重要ですが、アルゴリズムのパフォーマンスが同じくらい重要な場合があります。 精度とトレーニングの時間のバランスを取得すると多くの場合、計算速度を上げるため、精度と正確性を損なうことがなくパフォーマンスを向上するパラメーターを変更することができます。

+ [rxDTree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)

    `rxDTree` サポート、`maxDepth`パラメーターで、デシジョン ツリーの深さを制御します。 として`maxDepth`は大きくしても、パフォーマンスが低下、ため、パフォーマンスの低下と深さを増やすことのメリットを分析することが重要です。

    などのパラメーターを調整することで時間の複雑さと予測の精度のバランスを制御することもできます。 `maxNumBins`、 `maxDepth`、 `maxComplete`、および`maxSurrogate`します。 深さを 10 または 15 を超えた値に増やすと、計算が非常に不経済になる可能性があります。

+ [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)

    使用してください、`cube`引数が数式の最初の従属変数が因子変数である場合。
    
    ときに`cube`に設定されている`TRUE`、高速である可能性があり、標準の回帰計算よりもメモリを使用するパーティションの逆関数を使用して、回帰を実行します。 数式に大量の変数がある場合は、パフォーマンスが大幅に向上する可能性があります。

+ [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)

    使用して、`cube`引数の最初の従属変数が因子変数である場合。
    
    ときに`cube`に設定されている`TRUE`アルゴリズムは、高速である可能性がありより少ないメモリを使用するパーティションの逆関数を使用します。 数式に大量の変数がある場合は、パフォーマンスが大幅に向上する可能性があります。

RevoScaleR の最適化については、次の記事を参照してください。

+ サポートの記事:[パフォーマンス チューニング rxDForest と rxDTree のオプション](https://support.microsoft.com/kb/3104235)

+ ブースト ツリー モデルでモデルを制御する方法に合わせて:[の推定モデルを使用して確率的勾配ブースティング](https://docs.microsoft.com/r-server/r/how-to-revoscaler-boosting)

+ RevoScaleR の移動し、データ処理の概要: [ScaleR でカスタムのチャンク アルゴリズムを記述します。](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ RevoScaleR のプログラミング モデル: [RevoScaleR でスレッドを管理します。](https://docs.microsoft.com/r-server/r/how-to-developer-manage-threads)

+ 関数リファレンス[rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

+ 関数リファレンス[rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)

### <a name="use-microsoftml"></a>MicrosoftML を使用します。

また、新しいを調査することをお勧め**MicrosoftML**パッケージで、計算コンテキストと RevoScaleR で提供される変換に使用できるスケーラブルな機械学習アルゴリズムを提供します。

+ [MicrosoftML を概要します。](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)

+ [MicrosoftML アルゴリズムを選択する方法](https://docs.microsoft.com/r-server/r/how-to-choose-microsoftml-algorithms-cheatsheet)

### <a name="operationalize-a-solution-using-microsoft-r-server"></a>Microsoft R Server を使用してソリューションを運用化します。

場合は、シナリオでは、格納されたモデルを使用して予測を高速をアプリケーションに machine learning の統合、使用することもできます、 [operationalization](https://docs.microsoft.com/r-server/what-is-operationalization) (旧称 DeployR)、Microsoft R Server で機能します。

+ として、**データ サイエンティスト**を使用して、 [mrsdeploy パッケージ](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package)、他のコンピューターと R コードを共有し、web、デスクトップ、モバイル、およびダッシュ ボード アプリケーション内での R 分析を統合する:[を発行する方法R Server で R の web サービスおよび管理](https://docs.microsoft.com/r-server/operationalize/how-to-deploy-web-service-publish-manage-in-r)

+ として、**管理者**、パッケージの管理、web のノードを監視する方法について説明しますとコンピューティング ノード、および R ジョブでのセキュリティを制御:[と対話し、R での web サービスを使用する方法](https://docs.microsoft.com/r-server/operationalize/how-to-consume-web-service-interact-in-r)

## <a name="articles-in-this-series"></a>このシリーズの記事

[パフォーマンス チューニング-R の概要](sql-server-r-services-performance-tuning.md)

[R で SQL Server の構成のパフォーマンス チューニング](sql-server-configuration-r-services.md)

[R の R のパフォーマンス チューニング コードとデータの最適化](r-and-data-optimization-r-services.md)

[パフォーマンス チューニング - 結果のケース スタディ](performance-case-study-r-services.md)
