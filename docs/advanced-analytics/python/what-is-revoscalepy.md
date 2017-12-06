---
title: "Introducing revoscalepy |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: ad525f173ad6082f587324b41af768816077e371
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="introducing-revoscalepy"></a>Revoscalepy の概要

**revoscalepy**新しいライブラリが分散コンピューティングをサポートするために Microsoft によってリモート計算コンテキスト、および高パフォーマンス アルゴリズム Python の用意されています。

基にして、 **RevoScaleR** Microsoft R Server と SQL Server R Services と同じ機能を提供する目的で提供された r パッケージ。

+ 複数のコンピューティング コンテキストをリモートおよびローカルの両方をサポートしています
+ データ変換と視覚エフェクトの RevoScaleR のものと同等の機能を提供します。
+ 分散または並列処理の RevoScaleR 機械学習アルゴリズムの Python バージョンを提供します。
+ パフォーマンスの向上、Intel 数値演算ライブラリの使用を含む

MicrosoftML パッケージは、R、Python の両方も提供されます。 詳細については、次を参照してください[SQL server を使用して MicrosoftML。](../using-the-microsoftml-package.md)

## <a name="versions-and-supported-platforms"></a>バージョンとサポートされるプラットフォーム

**Revoscalepy**のみインストールするときに、次の Microsoft 製品のいずれかのモジュールが利用。

+ 機械学習の SQL Server 2017 では、サービス
+ Microsoft Machine Learning Server 9.2.0 以降

Revoscalepy の最新バージョンを入手するには、SQL Server 2017 の Cumulative Update 1 をインストールします。 含む、Python で多くの機能強化が含まれています。

+ 新しい Python 関数の場合、`rx_create_col_info`と同様に、SQL Server データ ソースからスキーマ情報を取得する[rxCreateColInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcreatecolinfo)の 
+ 機能強化[rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec)を使用した並列のシナリオをサポートするために、`RxLocalParallel`コンテキストを計算します。 

## <a name="supported-functions-and-data-types"></a>サポートされている関数とデータ型

このセクションでは、Python のデータ型およびでサポートされる新しい Python 関数の概要を示します、 **revoscalepy**モジュール、SQL Server 2017 CTP 2.0 のリリースを開始します。 

最新の日付にリリースされた Python ライブラリ内の関数の一覧では、これらのリンクを参照してください。

+ [Python の revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)

+ [Python の microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)

### <a name="data-types-data-sources-and-compute-contexts"></a>データ型、データ ソース、および計算コンテキスト

SQL Server および Python は、場合によっては異なるデータ型を使用します。 SQL と Python のデータ型間のマッピングの一覧は、次を参照してください。 [Python ライブラリとデータ型](python-libraries-and-data-types.md)です。

SQL Server での Python の機械学習のサポートされるデータ ソースには、ODBC データ ソース、SQL Server データベース、および XDF ファイルなど、ローカル ファイルが含まれています。

データ ソース オブジェクトを作成するには、次の表に示す関数を使用します。 データ ソースを定義した後で読み込みまたは適切なを使用してデータを変換[ETL 関数](#bkmk_etl)です。

> [!IMPORTANT]
> 多くの関数名は、CTP 2.0 での Python の初期リリース以降に変更されました。

**SQL Server データ**

+ 使用して[RxSqlServerData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxsqlserverdata)クエリまたはテーブルからデータ ソースを定義するには
+ 使用して[RxInSqlServer](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxinsqlserver)を SQL Server のコンピューティング コンテキストを作成するには
+ 使用して[RxOdbcData](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxodbcdata) ODBC 接続からデータ ソースを作成するには

**revoscalepy**もサポートしています、 [XDF データ ソース](https://docs.microsoft.com/r-server/python-reference/revoscalepy/rxxdfdata)メモリと他のデータ ソース間でデータを移動するために使用します。

> [!TIP]
> 機械学習での分散コンピューティング機能の説明を読むで開始することをお勧めデータ ソースの概念に追加された新しいコンテキストを計算するか、 [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-introduction)です。


### <a name="bkmk_algorithms"></a>機械学習と集計関数

CTP 2.0 以降で、SQL Server 2017 には、次の機械学習アルゴリズムと RevoScaleR から集計関数が含まれます。

| 関数| Description|注|
| ------ | ------ |------ |
|`rx_btrees` | 確率的勾配ブースト デシジョン ツリーに合わせて|`rx_btrees_ex`CTP 2.0 で|
|`rx_dforest` | 適合するように分類と回帰のデシジョン フォレスト|`rx_dforest_ex`CTP 2.0 で|
|`rx_dtree` | 適合するように分類と回帰ツリー |`rx_dtree_ex`CTP 2.0 で|
|`rx_lin_mod` | 線形モデルを作成します。|`rx_lin_mod_ex`CTP 2.0 で|
|`rx_logit` | ロジスティック回帰モデルを作成する|`rx_logit_ex`CTP 2.0 で|
|`rx_predict` | トレーニング済みモデルから予測を生成します。|`rx_predict_ex`CTP 2.0 で|
|`rx_summary` | モデルの概要を生成します。||

Python のバージョンので新しい機械学習アルゴリズムが指定されても[MicrosoftML](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package):

| 関数| Description|
| ------ | ------ |
|`rx_fast_forest` |デシジョン フォレスト モデルを作成します。|
|`rx_fast_linear` | 確率的デュアル座標アセントを使用した線形回帰|
|`rx_fast_trees` | ブースト ツリー モデルを作成します。 |
|`rx_logistic_regression` | ロジスティック回帰モデルを作成する|
|`rx_neural_network` | カスタマイズ可能なニューラル ネットワーク モデルを作成します。 |
|`rx_oneclass_svm` | 異常検出で使用するための不均衡がデータセットに SVM モデルを作成します。|

> [!TIP]
> これらのアルゴリズムの多くは、Azure Machine Learning でモジュールとして既に提供します。

Python の MicrosoftML もなどが含まれるさまざまな変換およびヘルパー関数。

+ `rx_predict`トレーニング済みのモデルから予測を生成し、リアルタイムのスコアリングのために使用できます
+ イメージの特性付け関数
+ テキスト処理とセンチメント抽出関数

詳細については、「 [MicrosoftML の概要](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)


> [!NOTE]
> Python コミュニティは、何に使用される、すべて小文字のアルファベット、アンダー スコアではなくパラメーター名の camel 形式の組み合わせを含むよりも異なる可能性がありますコーディング規則を使用します。 また、状況によって異なる気付きかもを**revoscalepy**ライブラリは、常に小文字です。 その通りです！ Python の別の規則。
> 
> Microsoft r: [Python 関数ヘルプ] の Python のリファレンス ドキュメントに関するヒントをチェック_アウト[Python 関数のヘルプ](https://docs.microsoft.com/r-server/python-reference/introducing-python-package-reference)

## <a name="examples"></a>使用例

含んだコードを実行する**revoscalepy**ローカルまたはリモート計算コンテキストで機能します。 ストアド プロシージャでの Python コードを埋め込むことによって SQL Server の内部 Python を実行することもできます。

ローカルでの実行中、通常、コマンドラインまたは Python の開発環境から Python スクリプトを実行してのいずれかを使用して SQL Server のコンピューティング コンテキストを指定、 **revoscalepy**関数。 全体のコードでは、または個々 の関数のリモート計算コンテキストを使用することができます。 たとえば、モデルのトレーニングを最新のデータを使用し、データ移動を回避するためにサーバーの負荷を軽減することができます。

ストアド プロシージャ内の完全な Python スクリプトを配置する場合[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)入力と出力を明確に定義される 1 つの関数として、コードを書き換えることをお勧めします。 入力と出力がある必要があります**パンダ**データ フレーム。 これを実行すると、T-SQL をサポートする任意のクライアントからストアド プロシージャを呼び出して、簡単に SQL クエリを入力として渡すでき SQL テーブルに結果を保存できます。 例については、次を参照してください。 [SQL 開発者のため、データベース内の Python Analytics](../tutorials/sqldev-in-database-python-for-sql-developers.md)です。

### <a name="using-remote-compute-contexts"></a>リモート計算コンテキストを使用します。

+ [Revoscalepy を使用して、モデルを作成します。](../tutorials/use-python-revoscalepy-to-create-model.md)

  この例では、SQL Server のインスタンスを使用して、計算コンテキストとして Python を実行する方法を示します。

### <a name="using-a-stored-procedure"></a>ストアド プロシージャの使用

+ [T-SQL を使用して実行の Python](../tutorials/run-python-using-t-sql.md)

  この例では、ストアド プロシージャに埋め込まれている Python スクリプトの呼び出しの基本的なメカニズムを示します。

### <a name="using-revoscalepy-with-microsoftml"></a>MicrosoftML で revoscalepy の使用

MicrosoftML の Python 関数は、計算コンテキストと revoscalepy に用意されているデータ ソースと統合されます。 したがって、MicrosoftML アルゴリズムを使用して定義し、Python でモデルをトレーニングして revoscalepy 関数を使用して、ローカルまたは SQl Server のコンピューティング コンテキストに Python コードを実行します。

だけ、Python コード内のモジュールをインポートし、必要がある個々 の関数を参照します。

```Python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

### <a name="requirements"></a>必要条件

SQL Server での Python コードを実行する必要がありますがインストールした SQL Server 2017 機能と共に**Machine Learning サービス**、Python 言語を有効にします。 SQL Server の以前のバージョンは、Python の統合をサポートしていません。

> [!NOTE]
> Python のオープン ソース ディストリビューションは、SQL Server のコンピューティング コンテキストをサポートしていません。 ただし、発行および Windows から Python アプリケーションを使用する必要がある場合は、SQL Server をインストールしなくても、Microsoft Machine Learning のサーバーをインストールできます。 詳細については、次を参照してください[スタンドアロン R Server の作成。](../r/create-a-standalone-r-server.md)

## <a name="get-more-help"></a>詳細なヘルプを取得します。

製品がリリースされたときに、これらの Api に関する完全なドキュメントは使用可能になります。 その間は、RevoScaleR または MicrosoftML ライブラリ内の対応する関数を参照していることをお勧めします。

+ [RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler)です。
+ [MicrosoftML](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml)

インポートして、モジュールを呼び出すことで、任意の Python 関数に関するヘルプを表示できる`help()`です。 たとえば、実行している`help(revoscalepy)`Python IDE から revoscalepy モジュールでの署名付きで、すべての関数の一覧を返します。

Python Tools for Visual Studio を使用する場合は、構文および引数のヘルプを表示する IntelliSense を使用することができます。 詳細については、次を参照してください。 [Visual Studio での Python サポート](http://docs.microsoft.com/visualstudio/python/installation)、および Visual Studio のバージョンに一致する拡張機能をダウンロードします。 Visual Studio 2015 と 2017、Python または以前のバージョンを使用することができます。

## <a name="see-also"></a>参照

[Python のチュートリアル](../tutorials/sql-server-python-tutorials.md)
