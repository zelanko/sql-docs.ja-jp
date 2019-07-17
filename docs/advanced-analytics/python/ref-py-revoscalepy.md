---
title: revoscalepy Python パッケージ - SQL Server Machine Learning サービス
description: Python を使用した SQL Server 2017 Machine Learning Services で revoscalepy モジュールを紹介します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/12/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 3482a15392fa04f7f10d2acbb0843d124e27dc21
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962744"
---
# <a name="revoscalepy-python-module-in-sql-server"></a>revoscalepy (SQL Server での Python モジュール)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**revoscalepy**はマイクロソフト分散コンピューティングをサポートする、リモート計算コンテキスト、および高パフォーマンスのデータ サイエンスのアルゴリズムから Python35 と互換性のあるモジュールです。 基にして、 **RevoScaleR** R 用 (Microsoft R Server と SQL Server R Services と共に配布)、同様の機能を提供するパッケージ。

+ ローカルとリモート コンピューティング コンテキストの同じバージョンのシステムで**revoscalepy**
+ データ変換および視覚化関数
+ データ サイエンスの職務、拡張性の高い分散または並列処理
+ パフォーマンスを向上させる、Intel 数値演算ライブラリの使用を含む

データ ソースと計算コンテキストで作成した**revoscalepy**機械学習アルゴリズムでも使用できます。 これらのアルゴリズムの概要については、次を参照してください。 [microsoftml Python モジュールは SQL Server で](ref-py-microsoftml.md)します。

## <a name="full-reference-documentation"></a>完全なリファレンス ドキュメント

**Revoscalepy**ライブラリは、複数のマイクロソフト製品で配布されますが、使用量は同じライブラリは、SQL Server または別の製品を取得するかどうか。 関数では同じですが、ため[revoscalepy を個々 の関数のドキュメントを](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)が下の 1 つの場所に発行される、 [Python リファレンス](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)の Microsoft Machine Learning Server。 製品固有の動作の存在、相違点は、関数のヘルプ ページに記録されます。

## <a name="versions-and-platforms"></a>バージョンとプラットフォーム

**Revoscalepy**モジュールは、Python 3.5 に基づいており、使用可能な次の Microsoft 製品やダウンロードのいずれかをインストールする場合にのみ。

+ [SQL Server 2017 の Machine Learning サービス](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 またはそれ以降](https://docs.microsoft.com/machine-learning-server/)
+ [データ サイエンス クライアント用 Python クライアント ライブラリ](setup-python-client-tools-sql.md)

> [!NOTE]
> 完全な製品リリース バージョンは、Windows 専用にする、SQL Server 2017 以降します。 Linux サポート**revoscalepy**新[SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md)。

## <a name="functions-by-category"></a>カテゴリ別の関数

このセクションでは、それぞれの使用方法の概要を把握するためのカテゴリ別の関数を示します。 使用することも、[目次](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)関数をアルファベット順に検索します。

## <a name="1-data-source-and-compute"></a>1-データ ソースとコンピューティング

**revoscalepy**データ ソースの作成および、場所を設定するための関数が含まれますか*コンピューティング コンテキスト*の計算が実行されます。 SQL Server のシナリオに関連する関数は、次の表に一覧表示されます。

SQL Server と Python は、場合によっては異なるデータ型を使用します。 SQL と Python のデータ型の間のマッピングの一覧は、次を参照してください。 [Python、SQL データ型](python-libraries-and-data-types.md)します。

| 関数| 説明|
| ------- | ---------- |
| [RxInSqlServer](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxinsqlserver) |  リモート インスタンスに計算をプッシュには、SQL Server 計算コンテキスト オブジェクトを作成します。 いくつか**revoscalepy**関数が引数としてコンピューティング コンテキストを受け取ります。 コンテキストの切り替えの例では、次を参照してください。 [revoscalepy を使用してモデル作成](../tutorials/use-python-revoscalepy-to-create-model.md)です。|
| [RxSqlServerData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxsqlserverdata) | SQL Server のクエリまたはテーブルに基づくデータ オブジェクトを作成します。 |
| [RxOdbcData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxodbcdata)| ODBC 接続に基づいてデータ ソースを作成します。 |
| [RxXdfData](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rxxdfdata) | ローカル XDF ファイルに基づくデータ ソースを作成します。 XDF ファイルはディスクにデータをメモリ内の負荷を軽減するよく使用されます。 1 つのバッチ内のデータベースから転送できる以上のデータまたはメモリ内に収まるよりも多くのデータを扱うとき、XDF ファイルは役に立ちます。 たとえば、ローカル ワークステーションに、データベースから定期的に大量のデータを移動する場合クエリではなく R 操作ごとに繰り返しデータベースするとして使用できます XDF ファイルある種のキャッシュをローカル データを保存し、R ワークスペースで作業し。 |

> [!TIP]
> を初めて使用するデータ ソースの概念または計算コンテキストを始めることがお勧め[分散コンピューティング](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing)Microsoft Machine Learning Server ドキュメント。

## <a name="2-data-manipulation-etl"></a>2-データの操作 (ETL)

| 関数 | 説明 |
|----------|-------------|
|[rx_import](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-import) | .Xdf ファイルまたはデータ フレームにデータをインポートします。|
|[rx_data_step](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-data-step) | 出力データセットに、入力データ セットからデータを変換します。|

<a name="bkmk_algorithms"></a>

## <a name="3-training-and-summarization"></a>3-トレーニングと概要作成

| 関数| 説明|
| ------- | ---------- |
|[rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) | 確率的勾配増幅デシジョン ツリーを合わせる|
|[rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) | 分類と回帰のデシジョン フォレストを合わせる|
|[rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) | 分類と回帰ツリーの適合 |
|[rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) | 線形回帰モデルを作成する|
|[rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) | ロジスティック回帰モデルを作成する|
|[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) | Revoscalepy 内のオブジェクトの一変量の概要を生成します。|

内の関数を確認することも必要があります。 [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)ためのその他の手法です。

<a name="ml-scoring"></a>

## <a name="4-scoring-functions"></a>4-スコア付け関数

| 関数| 説明|
| ------- | ---------- |
| [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | トレーニング済みモデルから予測を生成します。|) | トレーニング済みのモデルから予測を生成し、リアルタイム スコアリングのために使用できます。 |
|[rx_predict_default](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-default) | 予測値と rx_lin_mod と rx_logit オブジェクトを使用して残差を計算します。 |
|[rx_predict_rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dforest) | Rx_dforest または rx_btrees オブジェクトからのデータ セットの予測または定数の値を計算します。 |
|[rx_predict_rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict-rx-dtree) | Rx_dtree オブジェクトからのデータ セットの予測または定数の値を計算します。 |

## <a name="how-to-work-with-revoscalepy"></a>Revoscalepy を使用する方法

関数の**revoscalepy**ストアド プロシージャにカプセル化された Python コードで呼び出すことができます。 ほとんどの開発者がビルド**revoscalepy**ソリューションをローカルにし、完成した Python コードをデプロイの手順としてストアド プロシージャに移行します。

ローカルで実行時に通常の Python スクリプト、コマンドラインから、または Python の開発環境から指定して実行するのいずれかを使用して SQL Server 計算コンテキスト、 **revoscalepy**関数。 全体のコードでは、または個々 の関数は、リモート コンピューティング コンテキストを使用できます。 たとえば、最新のデータを使用し、データの移動を回避するサーバーにモデルのトレーニングをオフロードする可能性があります。

Python スクリプト、ストアド プロシージャ内部でカプセル化する準備ができたら[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)入力と出力を明確に定義する 1 つの関数として、コードの書き直しをお勧めします。 

入力と出力である必要があります**pandas**データ フレーム。 これが完了したら、T-SQL をサポートする任意のクライアントから、ストアド プロシージャを呼び出す、簡単に、入力として SQL クエリを渡すして SQL テーブルに結果を保存します。 例については、次を参照してください。 [SQL 開発者向けの in-database Python 分析について説明します](../tutorials/sqldev-in-database-python-for-sql-developers.md)します。

### <a name="using-revoscalepy-with-microsoftml"></a>Microsoftml で revoscalepy を使用します。

Python 関数[microsoftml](ref-py-microsoftml.md) revoscalepy に用意されているコンピューティング コンテキストとデータ ソースと統合されます。 Microsoftml から関数を呼び出すときにたとえば場合の定義とモデルのトレーニング、または使用して revoscalepy 関数、Python を実行するローカル コード リモート SQl server 計算コンテキスト。

次の例では、Python コード内のモジュールをインポートするための構文を示します。 必要な個々 の関数を参照できます。

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>関連項目

+ [Python のチュートリアル](../tutorials/sql-server-python-tutorials.md)
+ [チュートリアル: T-SQL での Python コードを埋め込む](../tutorials/run-python-using-t-sql.md)
+ [Python リファレンス (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)
