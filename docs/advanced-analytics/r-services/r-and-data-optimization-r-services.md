---
title: "R とデータの最適化 (R Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6104878-ed19-47a7-ac37-21e4d6e2a1af
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# R とデータの最適化 (R Services)
このトピックでは、パフォーマンスを向上させる、または既知の問題を回避するには、R コードを更新するための方法を説明します。

## コンテキストを計算します。

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] いずれかの方法、 __ローカル__ または __SQL__ 分析を実行するときにコンテキストを計算します。 使用する場合、 __ローカル__ 分析、コンピューティングのコンテキストは、クライアント コンピューターに対して実行されからデータをフェッチする必要があります [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ネットワーク経由でします。 このネットワークの転送は、転送データがネットワークの速度のサイズによって異なりますし、同時に発生しているその他のネットワーク転送、パフォーマンスの低下が発生します。

計算コンテキストは場合 __SQL Server__, 、分析関数内で実行されますし、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。 ネットワークのオーバーヘッドが追加されていないために、データは分析タスクでは、ローカルです。 

大きなデータ セットを使用する場合は、SQL 計算コンテキストを常に使用する必要があります。

## 要素

R 言語は、要素に、テーブルから文字列を変換します。 多くのデータ ソース オブジェクトを `colInfo` 列の処理方法を制御するパラメーターとして。 たとえば、 `c(“fruit” = c(type = “factor”, levels=as.character(c(1:3)), newLevels=c(“apple”, “orange”, “banana”)))` は 1、2、およびテーブルから 3 の整数を使用し、レベルの要因として扱われるように `apple`, 、`orange`, 、および `banana`です。 

データの科学者は、数式で係数変数を使用する多くの場合、ただし、ソース データが整数であるときに、要素を使用するいると、パフォーマンスが低下整数は、実行時に文字列に変換が発生します。 ただし、列に文字列が含まれている場合は、時間を使用して前のレベルを指定できます `colInfo`します。 この場合は、同等のステートメントがなります  `c(“fruit” = c(type = “factor”, levels= c(“apple”, “orange”, “banana”)))`, を読み取るときに、要素として文字列を処理します。 

実行時の変換を避けるためには、テーブル内の整数としてのレベルを保存して、最初の式の例に示すように、メッセージを処理を検討してください。 モデルの生成でセマンティックな相違点がない場合は、このアプローチは、パフォーマンスの向上をもたらすことができます。

## [データの変換]

データの科学者は、多くの場合、分析の一部として R で記述された変換関数を使用します。 変換関数は、テーブルから取得したそれぞれの行に適用する必要があります。  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], 、この変換は、バッチ モードで動作し、R インタープリターは、分析エンジンとの間の通信を伴います。 変換を実行するのには、分析エンジンと R インタープリター プロセスと背面にも、データは SQL から移動します。 ため、変換が可能悪影響を及ぼすことに大きな影響、アルゴリズムのパフォーマンスを使用して、データの量によって発生します。

テーブルまたはビューの分析を実行する前にすべての必要な列があるように、計算の際の変換の回避をより効率的です。 既存のテーブルに列を追加しない場合は、変換後の列を含む別のテーブルまたはビューの作成を検討し、適切なクエリを使用してデータを取得します。

## [バッチ処理]

SQL データ ソース (`RxSqlServerData`) パラメーターを使用してバッチ サイズを指定するオプションが追加されて `rowsPerRead`します。 このパラメーターは、同時に処理する行の数を指定します。 実行時にアルゴリズムが指定した各バッチ内の行の番号は読み取ります。 既定では、このパラメーターの値はメモリが不足してマシン上でもアルゴリズムを実行できることを確認する 50,000 を設定します。 コンピューターに十分なメモリがある場合は、500,000 個以上も膨大な数には、この値を増やすと、特に、大きなテーブルの場合、パフォーマンスを向上できます。 

この値を大きくより良い結果を常になります可能性があります、最適な値を確認するには、いくつか実験が必要な場合があります。 この利点は複数のプロセスで大量のデータ セットでより明らかになります (`numTasks` より大きい値に設定 `1`)。

## 並列処理

Rx 内で分析関数を実行中のパフォーマンスを向上させる [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], 、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] で使用できるコアを使用して並列処理に依存しています、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] マシンです。 2 つの方法による並列処理を実現するために [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]:

* 使用する場合、 `sp_execute_external_script` R スクリプトを実行するストアド プロシージャの設定、 `@parallel` パラメーターを `1`します。 これは、R スクリプトの「受信」が付いている通常 RevoScaleR 機能を使用しないに便利です。 スクリプトが RevoScaleR 関数を使用して、並列処理が自動的に処理および設定しないでください場合 `@parallel` に `1`します。

    R スクリプトを並列化できる場合、 [!INCLUDE[tsql_md](../../includes/tsql-md.md)] クエリを並列化できる、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 並列の複数のプロセスが作成されます (最大、 __MAXDOP を並列処理の次数を最大__ の設定 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)],、) し、すべてのプロセス間で同じスクリプトを実行します。 各プロセスのみが受信した、データの一部など、すべてのデータを表示する必要がありますスクリプトではありませんので、モデルのトレーニング時にします。 ただし、便利な場合はバッチ予測などのタスクを並列で実行します。 並列化を使用する方法について [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), を参照してください、 __ヒントの詳細: 並列処理__ の [TRANSACT-SQL での R コードの使用](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md)します。

* Rx 関数を使用して、SQL Server の計算コンテキストで、設定 `numTasks` を作成するプロセスの数にします。 によって作成されたプロセスの実際の数を決定 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], 、および要求するよりも少ない可能性があります。 作成されたプロセスの数にはなりません以上 __MAXDOP__します。

    R スクリプトを並列化できる場合、 [!INCLUDE[tsql_md](../../includes/tsql-md.md)] クエリを並列化できる、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] rx 関数を実行するときに複数の並列処理を作成します。

作成されるプロセスの数は、さまざまなリソースのガバナンスなどの要因、リソース、その他のセッション、および R スクリプトを使用するクエリにクエリ実行プランの現在の使用量によって異なります。 

### クエリの並列処理

確実にデータを並列で分析できます、データを取得するためのクエリはことにレンダリングできる並列実行用のような方法で囲む必要があります。 

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 使用して SQL データ ソースの操作をサポートしている `RxSqlServerData` ソースを指定します。 ソースには、テーブルまたはクエリのいずれかを指定できます。 たとえば、次のコード サンプル両方は、SQL クエリに基づく R データ ソース オブジェクトを定義します。
~~~~
RxSqlServerData(table=”airline”, connectionString = sqlConnString)
~~~~

~~~~
RxSqlServerData(sqlquery=”select [ArrDelay],[CRSDepTime],[DayOfWeek] from airlineWithIndex where rowNum <= 100000”, connectionString = sqlConnString)
~~~~ 

分析アルゴリズムが大量のテーブルからデータをプルすることが重要いることを確認する指定されたクエリ `RxSqlServerData` 並列実行用に最適化されています。 並列実行プランのクエリとすると、計算のための 1 つのプロセスになります。

[!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] 実行プランを分析し、クエリのパフォーマンスを向上させるために使用します。 たとえば、テーブルの欠落インデックスは、クエリの実行にかかる時間に反映できます。 参照してください [パフォーマンスの監視し、チューニング](../../relational-databases/performance/monitor-and-tune-for-performance.md) の詳細。

パフォーマンスに影響を与える他の監視は、クエリは、必要な数を超える列を取得する場合です。 たとえば、数式は 3 個の列に基づいており、テーブルに 30 個の列が場合、使わないクエリなど `select *` またはいずれかのために必要な数を超える列を選択します。

> [!NOTE]
> テーブルが、クエリではなく、データ ソースで指定されている場合 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 内部的に、テーブルから取得するために必要な列が決定されます。 ただし、この方法は恐れがある並列実行はできません。

## アルゴリズム パラメーター

Rx トレーニング アルゴリズムの多くは、トレーニング モデルを生成する方法を制御するパラメーターをサポートします。 精度とモデルの正確性は重要ですが、アルゴリズムのパフォーマンスが同様に重要な場合があります。 計算の速度を上げるためコマンドパッケージパラ モデルのトレーニングのパラメーターを変更でき、多くの場合、よう精度や正確性を損なうことがなくパフォーマンスを向上させることです。 

たとえば、 `rxDTree` をサポートしています、 `maxDepth` 最大ツリーの深さを制御するパラメーターです。 として `maxDepth` が増加すると、パフォーマンスが低下する可能性、パフォーマンスに与える影響と深さを増やすことの利点を分析することが重要であるためです。 

使用できるパラメーターの 1 つ `rxLinMod` と `rxLogit` は、 `cube` 引数。 この引数は、数式の最初の従属変数が因子変数であるときに使用できます。 場合 `cube` に設定されている `TRUE`, 、回帰直線の終了パーティションの逆関数を使用して、高速化して使用しようと標準の回帰の計算より少ないメモリです。 数式の変数の数が多い場合は、パフォーマンスの向上は重要なできます。

 [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler) ユーザー ガイドは、さまざまなアルゴリズムに合わせて、モデルを制御するために有用な情報を持ちます。 たとえば、 `rxDTree` などのパラメーターを調整することで時間の複雑さと予測の精度のバランスを制御できます `maxNumBins`, 、`maxDepth`, 、`maxComplete`, 、および `maxSurrogate`です。 10 や 15 を超えるに深さが増すと、計算が非常に不経済なことができます。

パフォーマンスのチューニングの詳細については `rxDForest` と `rxDTree`, を参照してください [パフォーマンス チューニング オプションの rxDForest/rxDTree](https://support.microsoft.com/kb/3104235)します。

## モデルと予測

トレーニングが完了し、最善のモデルを選択したことをお勧めの予測にすぐに使用できるように、モデルをデータベースに格納します。 予測を必要とするオンライン トランザクション処理、予測のデータベースから、事前計算済みのモデルの読み込みは、非常に効率的です。 サンプル スクリプトは、シリアル化し、モデルをデータベース テーブルに格納するこの方法を使用します。 予測モデルは、データベースからシリアル化解除されました。

特に大きなデータ セットで使用する場合、lm または glm などのアルゴリズムによって生成されたいくつかのモデルは非常に大きくできます。 格納できるデータ サイズの制限がある [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。 データベースに格納する前に、モデルをクリーンアップする必要があります。

> [!NOTE] 保存されたモデルを使用して、分析アプリケーションに統合する、高速な予測が重要なシナリオのかどうか、お勧め __DeployR__します。 Web、デスクトップ、モバイル、およびダッシュ ボード アプリケーション内で R の分析を簡単に統合するために使用します。 特に、モデルを格納して、保存されたモデルを使用して予測を 1 つの行を実行する場合に最適です。 詳細については、次を参照してください。 [に関する DeployR](https://msdn.microsoft.com/microsoft-r/rserver/deployr-about)します。

## 参照
[リソースのガバナンス](../../advanced-analytics/r-services/resource-governance-for-r-services.md)
[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)

[外部のリソース プールを作成します。](../../t-sql/statements/create-external-resource-pool-transact-sql.md)

 [SQL Server R サービス パフォーマンス チューニング ガイド](../../advanced-analytics/r-services/sql-server-r-services-performance-tuning.md)
 
 [R のサービスの SQL Server の構成](../../advanced-analytics/r-services/sql-server-configuration-r-services.md)
 
 [パフォーマンスのケース スタディ](../../advanced-analytics/r-services/performance-case-study-r-services.md)
 