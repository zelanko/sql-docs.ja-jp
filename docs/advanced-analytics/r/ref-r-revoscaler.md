---
title: RevoScaleR の R 関数のライブラリの SQL Server Machine Learning サービス
description: SQL Server 2016 R Services で R と SQL Server 2017 Machine Learning Services RevoScaleR 関数ライブラリの概要
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 3745c6cd8c340ce4ad89cac84c5b6286126e3f89
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641932"
---
# <a name="revoscaler-r-library-in-sql-server"></a>RevoScaleR (SQL Server での R ライブラリ)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**RevoScaleR**は Microsoft から高パフォーマンスのデータ サイエンスの職務のライブラリです。 関数は、データのインポート、データ変換、集約、視覚化、および分析をサポートします。

基本の R 関数とは異なり、並列および分散ファイル システムで、非常に大きいデータセットに対して RevoScaleR 操作を実行できます。 関数に収まり切らないメモリ チャンクを使用してとを組み合わせる際の結果によって操作が完了するときにデータセットを操作できます。

RevoScaleR 関数が付いた、 **rx**または**Rx**プレフィックスを簡単に特定できるようにします。

RevoScaleR は、分散したデータ サイエンス用のプラットフォームとして機能します。 最新のアルゴリズムでな RevoScaleR コンピューティング コンテキストと変換を使用するなど、 [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package)します。 使用することも[rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec)基本の R 関数を並列で実行します。

## <a name="full-reference-documentation"></a>完全なリファレンス ドキュメント

**RevoScaleR**ライブラリは、複数のマイクロソフト製品で配布されますが、使用量は同じライブラリは、SQL Server または別の製品を取得するかどうか。 関数では同じですが、ため[個々 の RevoScaleR 関数に関するドキュメントの](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)が下の 1 つの場所に発行される、 [R 参照](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference)の Microsoft Machine Learning Server。 製品固有の動作の存在、相違点は、関数のヘルプ ページに記録されます。

## <a name="versions-and-platforms"></a>バージョンとプラットフォーム

**RevoScaleR**ライブラリは、R から 3.4.3 に基づいており、使用可能な次の Microsoft 製品やダウンロードのいずれかをインストールする場合にのみ。

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [SQL Server 2017 の Machine Learning サービス](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 またはそれ以降](https://docs.microsoft.com/machine-learning-server/)
+ [Microsoft R client](set-up-a-data-science-client.md)

> [!NOTE]
> 完全な製品リリース バージョンは、Windows 専用にする、SQL Server 2017 以降します。 Linux サポート**RevoScaleR**新[SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md)。

## <a name="functions-by-category"></a>カテゴリ別の関数

このセクションでは、それぞれの使用方法の概要を把握するためのカテゴリ別の関数を示します。 使用することも、[目次](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference)関数をアルファベット順に検索します。

## <a name="1-data-source-and-compute"></a>1-データ ソースとコンピューティング

**RevoScaleR**データ ソースの作成および、場所を設定するための関数が含まれますか*コンピューティング コンテキスト*の計算が実行されます。 データ ソース オブジェクトは、接続文字列と一緒に必要な一連のデータを指定するコンテナーです。テーブル、ビュー、またはクエリとして定義されます。 ストアド プロシージャの呼び出しはサポートされていません。 SQL Server のシナリオに関連する関数は、次の表に一覧表示されます。

SQL Server と R は、場合によっては異なるデータ型を使用します。 SQL と R のデータ型の間のマッピングの一覧は、次を参照してください。 [R-SQL データ型](r-libraries-and-data-types.md)します。

| 関数| 説明|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinsqlserver) |  リモート インスタンスに計算をプッシュには、SQL Server 計算コンテキスト オブジェクトを作成します。 いくつか**RevoScaleR**関数が引数としてコンピューティング コンテキストを受け取ります。 |
|[rxGetComputeContext / rxSetComputeContext](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsetcomputecontext) | 取得またはアクティブなコンピューティング コンテキストを設定します。 |
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata) | SQL Server のクエリまたはテーブルに基づくデータ オブジェクトを作成します。 |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxodbcdata) | ODBC 接続に基づいてデータ ソースを作成します。 |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxxdfdata) | ローカル XDF ファイルに基づくデータ ソースを作成します。 XDF ファイルはディスクにデータをメモリ内の負荷を軽減するよく使用されます。 1 つのバッチ内のデータベースから転送できる以上のデータまたはメモリ内に収まるよりも多くのデータを扱うとき、XDF ファイルは役に立ちます。 たとえば、ローカル ワークステーションに、データベースから定期的に大量のデータを移動する場合クエリではなく R 操作ごとに繰り返しデータベースするとして使用できます XDF ファイルある種のキャッシュをローカル データを保存し、R ワークスペースで作業し。|

> [!TIP]
> を初めて使用するデータ ソースの概念または計算コンテキストを始めることがお勧め[分散コンピューティング](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing)Microsoft Machine Learning Server ドキュメント。

### <a name="perform-ddl-statements"></a>DDL ステートメントを実行します。

インスタンスとデータベースで必要なアクセス許可がある場合は、R から DDL ステートメントを実行できます。 次の関数では、ODBC 呼び出しを使用して、DDL ステートメントの実行や、データベース スキーマを取得します。

| 関数| 説明|
| ------- | ---------- |
| [rxSqlServerTableExists と rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) | 削除、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]テーブル、またはデータベース テーブルまたはオブジェクトの存在を確認します。 |
| [rxExecuteSQLDDL](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexecutesqlddl) | 定義またはデータベース オブジェクトを操作するデータ定義言語 (DDL) コマンドを実行します。 この関数は、データを返すことはできませんし、取得または変更、オブジェクトのスキーマやメタデータにのみ使用されます。|

## <a name="2-data-manipulation-etl"></a>2-データの操作 (ETL)

データ ソース オブジェクトを作成した後は、そこにデータを読み込み、データを変換または指定したコピー先に新しいデータを書き込むにはオブジェクトを使用できます。 ソースのデータのサイズによりますが、データ ソースの一部としてバッチ サイズを定義し、データをチャンク単位で動かすことができます。

| 関数 | 説明 |
|----------|-------------|
| [rxOpen メソッド](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxopen-methods) | データ ソースが使用できる、開かれているかどうかを確認または データ ソースを閉じますソースからデータを読み取るし、ターゲットにデータを書き込むデータ ソースを閉じます。|
| [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) | File storage に、またはデータ フレームには、データ ソースからデータを移動します。|
| [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) | データ ソース間の移動中にデータを変換します。|

<a name="graphing-functions"></a>

## <a name="3-graphing-functions"></a>関数の 3-グラフの作成

| 関数名 | 説明 |
|---------------|-------------|
|[rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram)  |データからヒストグラムを作成します。 | 
|[rxLinePlot](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlineplot) |データから線形プロットを作成します。 | 
|[rxLorenz](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlorenz)  |プロットできるローレンツ曲線を計算します。 | 
|[rxRocCurve](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |計算し、実際と予測データから ROC 曲線をプロットします。 | 

<a name="statistics-functions"></a>

## <a name="4-descriptive-statistics"></a>4 記述統計量

| 関数名 | 説明 |
|---------------|-------------|
|[rxQuantile](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxquantile) <sup>*</sup> |計算では、並べ替えなし .xdf ファイルとデータ フレームの分位を概算します。 | 
|[rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary) <sup>*</sup> |グループごとの計算を含む、データの基本的な概要統計情報。 サポートされていない .xdf ファイルにグループの計算を記述します。 | 
|[rxCrossTabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) <sup>*</sup> |式ベースのクロス集計データです。 | 
|[rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) <sup>*</sup> |代替の数式に基づくクロス集計のキューブの結果を返す効率のよい表記に設計されています。 出力は、サポートされていない .xdf ファイルを書き込みます。 | 
|[rxMarginals](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxmarginals)  |クロス集計のマージナル概要。 | 
|[as.xtabs](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/as.xtabs)  |Xtabs オブジェクトにクロス集計結果を変換します。 | 
|[rxChiSquaredTest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Xtabs オブジェクトに対しては、カイ 2 乗検定を実行します。 小さなデータ セットで使用され、データはチャンクに分割されません。 | 
|[rxFisherTest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |Xtabs オブジェクトに対してフィッシャーの正確確率検定を実行します。 小さなデータ セットで使用され、データはチャンクに分割されません。 | 
|[rxKendallCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxchisquaredtest)  |ケンドールの順位相関係数 xtabs オブジェクトを使用して計算します。 | 
|[rxPairwiseCrossTab](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpairwisecrosstab)  |Xtabs オブジェクトの列と行の一対の組み合わせに関数を適用します。 | 
|[rxRiskRatio](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |2 xtabs オブジェクトに対する相対的リスクを計算します。 | 
|[rxOddsRatio](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxriskratio)  |2 xtabs オブジェクトに対するオッズ比を計算します。 | 

<sup>*</sup> このカテゴリで最も人気のある関数を示します。

<a name="prediction-functions"></a>

## <a name="5-prediction-functions"></a>5 予測関数

| 関数名 | 説明 |
|---------------|-------------|
|[rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) <sup>*</sup> |データに線形モデルを適合させます。 | 
|[rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) <sup>*</sup> |データをロジスティック回帰モデルを適合させます。 | 
|[rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm) <sup>*</sup> |データに一般化線形モデルを適合させます。 | 
|[rxCovCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) <sup>*</sup> |共変性、相関関係、または合計の平方和/クロス積を計算する一連の変数の行列。 | 
|[rxDTree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) <sup>*</sup> |データの分類または回帰ツリーに適合させます。 | 
|[rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees) <sup>*</sup> |確率的勾配ブースティング アルゴリズムを使用してデータを分類または回帰のデシジョン フォレストを収めます。 | 
|[rxDForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) <sup>*</sup> |データを分類または回帰のデシジョン フォレストを収めます。 | 
|[rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxPredict) <sup>*</sup> |適合モデルの予測を計算します。 出力は、XDF のデータ ソースである必要があります。 | 
|[rxKmeans](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxkmeans) <sup>*</sup> |K-means クラスタ リングを実行します。 | 
|[rxNaiveBayes](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxnaivebayes) <sup>*</sup> |Naive Bayes 分類を実行します。 | 
|[rxCov](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor) |一連の変数の共分散マトリックスを計算します。 | 
|[rxCor](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |一連の変数の相関マトリックスを計算します。 | 
|[rxSSCP](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcovcor)  |合計の平方和/クロス積を計算する一連の変数の行列。 | 
|[rxRoc](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxroc)  |二項分類器のシステムから、実際の予測値を使用して受信者操作特性 (ROC) の計算。 | 

<sup>*</sup> このカテゴリで最も人気のある関数を示します。


## <a name="how-to-work-with-revoscaler"></a>RevoScaleR を操作する方法

関数の**RevoScaleR**ストアド プロシージャにカプセル化された R コードで呼び出すことができます。 ほとんどの開発者がビルド**RevoScaleR**ソリューションをローカルにし、完成した R コードをデプロイの手順としてストアド プロシージャに移行します。

ローカルで実行中、通常 R スクリプトをコマンドラインから、または、R 開発環境から指定して実行するのいずれかを使用して SQL Server 計算コンテキスト、 **RevoScaleR**関数。 全体のコードでは、または個々 の関数は、リモート コンピューティング コンテキストを使用できます。 たとえば、最新のデータを使用し、データの移動を回避するサーバーにモデルのトレーニングをオフロードする可能性があります。

R スクリプト、ストアド プロシージャ内部でカプセル化する準備ができたら[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)入力と出力を明確に定義する 1 つの関数として、コードの書き直しをお勧めします。 

## <a name="see-also"></a>関連項目

+ [R のチュートリアル](../tutorials/sql-server-r-tutorials.md)
+ [計算コンテキストを使用する方法を学習します。](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [SQL 開発者向けの R:トレーニングし、モデルの運用化](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [GitHub の Microsoft の製品サンプル](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [R の参照 (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 
