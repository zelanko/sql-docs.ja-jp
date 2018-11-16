---
title: SQL Server Machine Learning で revoscalepy Python パッケージの概要 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8b2e217f599112019e96f3e20b727456b9da607f
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51697570"
---
# <a name="introducing-revoscalepy-in-sql-server-machine-learning"></a>SQL Server Machine Learning で revoscalepy の概要
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**revoscalepy**はマイクロソフト分散コンピューティングをサポートするために、リモート計算コンテキスト、および高性能アルゴリズム Python 開発者向けの新しい Python ライブラリです。

基にして、 **RevoScaleR** Microsoft R Server と SQL Server R Services では、同じ機能を提供する目的で提供されていた R 用のパッケージ。

+ 複数の計算コンテキスト、ローカルとリモートの両方をサポートしています
+ データ変換と視覚エフェクトの revoscaler ものと同等の機能を提供します。
+ 分散または並列処理の RevoScaleR 機械学習アルゴリズムの Python のバージョンを提供します。
+ パフォーマンスを向上させる、Intel 数値演算ライブラリの使用を含む

MicrosoftML パッケージは、R と Python の両方のも提供されます。 詳細については、次を参照してください[MicrosoftML SQL Server の使用。](../using-the-microsoftml-package.md)

## <a name="versions-and-supported-platforms"></a>バージョンとサポートされているプラットフォーム

**Revoscalepy**モジュールが使用可能なのみインストールすると、次の Microsoft 製品のいずれか。

+ Machine Learning サービス、SQL server 2017
+ Microsoft Machine Learning Server 9.2.0 またはそれ以降

Revoscalepy の最新バージョンを入手するには、SQL Server 2017 Cumulative Update 1 をインストールします。 など、Python では、多くの機能強化が含まれます。

+ 新しい Python 関数`rx_create_col_info`のように、SQL Server データ ソースからスキーマ情報を取得する[rxCreateColInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcreatecolinfo)の 
+ 機能強化[rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec)を使用して並列のシナリオをサポートするために、`RxLocalParallel`コンピューティング コンテキスト。 

## <a name="supported-functions-and-data-types"></a>サポートされている関数とデータ型

このセクションでは、Python のデータ型とでサポートされる新しい Python 関数の概要を示します、 **revoscalepy** SQL Server 2017 CTP 2.0 リリース以降では、モジュール。 

最新の日付にリリースされた Python ライブラリの関数の一覧は次のリンク先を参照してください。

+ [Python 用 revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)

+ [Python 用の microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)

### <a name="data-types-data-sources-and-compute-contexts"></a>データ型、データ ソース、および計算コンテキスト

SQL Server と Python は、場合によっては異なるデータ型を使用します。 SQL と Python のデータ型の間のマッピングの一覧は、次を参照してください。 [Python 拡張機能](../concepts/extension-python.md)します。

SQL Server での Python の machine learning のサポートされるデータ ソースには、ODBC データ ソース、SQL Server データベース、および XDF ファイルを含むローカル ファイルが含まれています。

次の表に示す関数を使用して、データ ソース オブジェクトを作成します。 データ ソースを定義するには、後にロードまたは適切なを使用してデータを変換[ETL 関数](#bkmk_etl)します。

> [!IMPORTANT]
> 多くの関数名は、CTP 2.0 での Python の初期リリース以降に変更されました。

**SQL Server のデータ**

+ 使用[RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata)クエリまたはテーブルからデータ ソースを定義するには
+ 使用[RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserver) SQL Server のコンピューティング コンテキストを作成するには
+ 使用[RxOdbcData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxodbcdata) ODBC 接続からデータ ソースを作成するには

**revoscalepy**もサポートしています、 [XDF データ ソースの](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxxdfdata)メモリと他のデータ ソース間でデータを移動するために使用します。

> [!TIP]
> Machine learning での分散コンピューティングの仕組みに関する情報を読み取ったで開始することをお勧めは新しいデータ ソースの概念を計算コンテキストまたは[RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-introduction)します。


### <a name="bkmk_algorithms"></a>Machine learning と集計関数

SQL Server 2017 CTP 2.0 以降では、次の機械学習アルゴリズムと RevoScaleR から集計関数が含まれます。

| 機能| 説明|注|
| ------ | ------ |------ |
|`rx_btrees` | 確率的勾配増幅デシジョン ツリーを合わせる|`rx_btrees_ex` CTP 2.0 で|
|`rx_dforest` | 分類と回帰のデシジョン フォレストを合わせる|`rx_dforest_ex` CTP 2.0 で|
|`rx_dtree` | 分類と回帰ツリーの適合 |`rx_dtree_ex` CTP 2.0 で|
|`rx_lin_mod` | 線形モデルを作成します。|`rx_lin_mod_ex` CTP 2.0 で|
|`rx_logit` | ロジスティック回帰モデルを作成する|`rx_logit_ex` CTP 2.0 で|
|`rx_predict` | トレーニング済みモデルから予測を生成します。|`rx_predict_ex` CTP 2.0 で|
|`rx_summary` | モデルの概要を生成します。||

新しい機械学習アルゴリズムは、Python のバージョンのでも用意されています[MicrosoftML](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package):

| 機能| 説明|
| ------ | ------ |
|`rx_fast_forest` |デシジョン フォレスト モデルを作成します。|
|`rx_fast_linear` | 確率的双対座標を使用した線形回帰|
|`rx_fast_trees` | ブースト ツリー モデルを作成します。 |
|`rx_logistic_regression` | ロジスティック回帰モデルを作成する|
|`rx_neural_network` | カスタマイズ可能なニューラル ネットワーク モデルを作成します。 |
|`rx_oneclass_svm` | 異常検出で使用するため、不均衡なデータセットに SVM モデルを作成します。|

> [!TIP]
> これらのアルゴリズムの多くは、Azure Machine Learning でモジュールとして既に提供します。

Python 用の MicrosoftML も含まれています、さまざまな変換およびヘルパー関数など。

+ `rx_predict` トレーニング済みのモデルから予測を生成し、リアルタイム スコアリングのために使用できます
+ イメージの特徴の生成関数
+ テキストの処理とセンチメントの抽出関数

詳細については、次を参照してください[MicrosoftML の概要。](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)


> [!NOTE]
> Python コミュニティでは、何をご利用いただけます、すべて小文字の英字とアンダー スコアではなくパラメーター名にキャメル ケースを含むよりも異なる可能性があるコーディング規則を使用します。 また、おそらく気付きを**revoscalepy**ライブラリは、常に小文字です。 その通りです！ Python の別の規則。
> 
> Microsoft r: [Python 関数のヘルプ] の Python のリファレンス ドキュメントのヒントをチェック_アウト[Python 関数のヘルプ](https://docs.microsoft.com/r-server/python-reference/introducing-python-package-reference)

## <a name="examples"></a>使用例

含んだコードを実行する**revoscalepy**ローカルまたはリモート コンピューティング コンテキストで機能します。 ストアド プロシージャで Python コードを埋め込むことによって、SQL Server 内部での Python を実行することもできます。

ローカルで実行時に通常の Python スクリプト、コマンドラインから、または Python の開発環境から指定して実行するのいずれかを使用して SQL Server 計算コンテキスト、 **revoscalepy**関数。 全体のコードでは、または個々 の関数は、リモート コンピューティング コンテキストを使用できます。 たとえば、最新のデータを使用し、データの移動を回避するサーバーにモデルのトレーニングをオフロードする可能性があります。

場合は、ストアド プロシージャ内部で完全な Python スクリプトを配置する[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)入力と出力を明確に定義する 1 つの関数としてコードを書き換えることをお勧めします。 入力と出力である必要があります**pandas**データ フレーム。 これが完了したら、T-SQL をサポートする任意のクライアントから、ストアド プロシージャを呼び出す、簡単に、入力として SQL クエリを渡すして SQL テーブルに結果を保存します。 例については、次を参照してください。 [SQL 開発者向けの In-database Python Analytics](../tutorials/sqldev-in-database-python-for-sql-developers.md)します。

### <a name="using-remote-compute-contexts"></a>リモート計算コンテキストを使用します。

+ [Revoscalepy を使用して、モデルを作成します。](../tutorials/use-python-revoscalepy-to-create-model.md)

  この例では、計算コンテキストとして SQL Server のインスタンスを使用して Python を実行する方法を示します。

### <a name="using-a-stored-procedure"></a>ストアド プロシージャの使用

+ [T-SQL を使用した Python の実行](../tutorials/run-python-using-t-sql.md)

  この例では、ストアド プロシージャに埋め込まれた Python スクリプトを呼び出すことの基本的なメカニズムを示します。

### <a name="using-revoscalepy-with-microsoftml"></a>MicrosoftML で revoscalepy を使用します。

MicrosoftML の Python 関数は、計算コンテキストと revoscalepy に用意されているデータ ソースと統合されます。 そのため、MicrosoftML アルゴリズムを使用して定義し、Python でモデルをトレーニングして、ローカル、または SQl Server のコンピューティング コンテキストでの Python コードを実行する revoscalepy 関数を使用する可能性があります。

Python コード内のモジュールをインポートし、必要がある個々 の関数を参照します。

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

### <a name="requirements"></a>要件

SQL Server での Python コードを実行する必要がありますがインストールした SQL Server 2017 機能と共に**Machine Learning サービス**、Python 言語を有効にします。 SQL Server の以前のバージョンは、Python の統合をサポートしていません。

> [!NOTE]
> Python のオープン ソース ディストリビューションは、SQL Server 計算コンテキストをサポートしていません。 ただし、発行および Windows からの Python アプリケーションを利用する必要がある場合は、SQL Server をインストールしなくても、Microsoft Machine Learning Server をインストールできます。 詳細については、次を参照してください。[インストール SQL Server 2017 Machine Learning Server (スタンドアロン)](../install/sql-machine-learning-standalone-windows-install.md)します。

## <a name="get-more-help"></a>詳細情報します。

製品がリリースされたときに、これらの Api に関する完全なドキュメントは使用可能になります。 それまでは、RevoScaleR または MicrosoftML ライブラリ内の対応する関数を参照することをお勧めします。

+ [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler)します。
+ [MicrosoftML](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml)

モジュールをインポートし、呼び出すことによって、任意の Python 関数に関するヘルプを表示できます`help()`します。 たとえば、実行している`help(revoscalepy)`Python IDE からそのシグネチャを持つ、revoscalepy モジュール内のすべての関数の一覧を返します。

Python Tools for Visual Studio を使用する場合は、構文と引数のヘルプを表示する IntelliSense を使用できます。 詳細については、次を参照してください。 [Visual Studio での Python サポート](https://docs.microsoft.com/visualstudio/python/installation)、および Visual Studio のバージョンに一致する拡張機能をダウンロードします。 Python と Visual Studio 2015 および 2017、または以前のバージョンを使用することができます。

## <a name="see-also"></a>参照

[Python のチュートリアル](../tutorials/sql-server-python-tutorials.md)
