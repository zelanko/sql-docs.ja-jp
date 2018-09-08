---
title: 予測および SQL Server で機械学習モデルを使用して予測を生成する方法 |Microsoft Docs
description: ネイティブの予測のスコア付けと R および SQL Server Machine Learning で Pythin で予測のため、リアルタイムのスコア付けまたは予測の T-SQL rxPredict、または sp_rxPredict を使用します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/30/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 09b94de43aaba54dced6d300587c0492b00c8f3d
ms.sourcegitcommit: 2a47e66cd6a05789827266f1efa5fea7ab2a84e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2018
ms.locfileid: "43348213"
---
# <a name="how-to-generate-forecasts-and-predictions-using-machine-learning-models-in-sql-server"></a>予測および SQL Server で機械学習モデルを使用して予測を生成する方法
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

既存のモデルを使用して、予測または新しいデータ入力の結果を予測するは、machine learning でのコア タスクです。 この記事では、SQL Server での予測を生成するためのアプローチを列挙します。 アプローチの間では速度がの増分の削減をに基づいて、高速の予測の内部処理の方法論を実行時の依存関係。 依存関係は、高速の予測を意味します。

内部処理インフラストラクチャを使用して (リアルタイムまたはネイティブのスコアリング) に必要なライブラリが付属します。 Microsoft ライブラリから関数があります。 CLR または C++ の拡張機能では、R または Python のコードがオープン ソースまたはサードパーティ製の関数の呼び出しがサポートされていません。

次の表では、予測および予測のスコア付けのフレームワークをまとめたものです。 

| 手法           | インターフェイス         | ライブラリの要件 | 処理速度 |
|-----------------------|-------------------|----------------------|----------------------|
| 機能拡張フレームワーク | R: [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) <br/>Python: [rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) | [なし] : モデルは、任意の R または Python 関数に基づくことができます。 | 数百ミリ秒かかります。 <br/>ランタイム環境の読み込みとが固定コストは、新しいデータをスコア付けする前に 3 つを 600 ミリ秒単位の平均を計算します。 |
| リアルタイム スコアリングの CLR の拡張機能 | [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql)でシリアル化されたモデル | R: RevoScaleR、MicrosoftML <br/>Python: revoscalepy、microsoftml | 数十ミリ秒単位の平均です。 |
| ネイティブの C++ 拡張機能をスコア付け| [T-SQL の予測関数](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)でシリアル化されたモデル | R: RevoScaleR <br/>Python: revoscalepy | 平均の数は 20 ミリ秒です。 | 

処理の速度と出力のない物質は、差別化機能です。 同じ機能および入力と仮定すると、スコア付けされた出力が変わることはありませんを使用するアプローチを。

モデルは、サポートされている関数を使用して作成し、ディスクに保存またはデータベースにバイナリ形式で格納されている生のバイト ストリームにシリアル化する必要があります。 ストアド プロシージャまたは T-SQL を使用してロードし、新しい入力の予測スコアを生成するときに完了するまで時間が短くなり R または Python の言語の実行時間のオーバーヘッドなしのバイナリ モデルを使用できます。

CLR と C++ の拡張機能の重要性は、データベース エンジン自体に近いです。 データベース エンジンのネイティブ言語は、C++ で、拡張機能の依存関係を含むを実行する C++ で記述されたことを意味します。 これに対し、CLR の拡張機能は、.NET Core に依存します。 

ご想像のとおり、これらの実行時環境でにプラットフォームのサポートに影響します。 ネイティブ データベース エンジンの拡張機能は、リレーショナル データベースがサポートされている任意の場所を実行します。 Windows、Linux で Azure。 .NET Core の要件と CLR の拡張機能は現在 Windows のみです。

## <a name="scoring-overview"></a>スコア付けの概要

_スコア付け_は 2 段階のプロセスです。 最初に、テーブルからの読み込みに既にトレーニング済みのモデルを指定します。 次に、新しいパスの入力データを予測値を生成する関数に (または_スコア_)。 入力は、表形式または 1 つのいずれかの行を返す、T-SQL クエリでは多くの場合です。 確率を表す 1 つの列の値を出力するか信頼区間、エラー、またはその他の便利なを補完する、予測サービスなど、いくつかの値を出力する可能性があります。

一歩モデルを準備するプロセス全体のバックアップし、スコアを生成し、要約できるこのように。

1. サポートされているアルゴリズムを使用してモデルを作成します。
2. 特別なバイナリ形式を使用して、モデルをシリアル化します。
3. モデルを SQL Server が使用できるようにします。 つまり、通常、シリアル化されたモデルを SQL Server テーブルに格納します。
4. 関数またはパラメーターとして、モデルと入力データの指定のストアド プロシージャを呼び出します。

入力には、多くのデータ行が含まれているときにこれは通常高速化、スコア付けプロセスの一環として、テーブルに、予測値を挿入します。  1 つのスコアを生成するはするフォームまたはユーザーの要求からの入力値を取得し、クライアント アプリケーションにスコアを返すシナリオではより一般的です。 パフォーマンスを向上させるには、連続するスコアを生成するときにメモリに再読み込みできるように、SQL Server は、モデルをキャッシュする可能性があります。

## <a name="compare-methods"></a>メソッドを比較します。

コア データベース エンジン プロセスの整合性を保持するためには、R と Python のサポートは、RDBMS 処理から言語の処理を分離するデュアル アーキテクチャで有効です。 SQL Server 2016 以降、Microsoft は、T-SQL から実行する R スクリプトを可能にする機能拡張フレームワークを追加します。 SQL Server 2017 では、Python の統合が追加されました。 

機能拡張フレームワークには、R または Python では、複雑な機械学習モデルをトレーニングする単純な関数の範囲で任意の操作がサポートしています。 ただし、デュアル プロセス アーキテクチャでは、操作の複雑さに関係なく、すべての呼び出しの外部 R または Python プロセスを呼び出す必要があります。 ワークロードには、テーブルからの事前トレーニング済みモデルの読み込みや、SQL Server の既存のデータにスコアを付けることが必要、外部プロセスの呼び出しのオーバーヘッドは、特定の状況で許容できる待機時間を追加します。 たとえば、不正行為の検出では、高速のスコア付けが関係する必要があります。

不正行為の検出などのシナリオでのスコア付けの速度を向上させるのには、SQL Server は、R と Python のスタートアップ プロセスのオーバーヘッドが生じないように C++ と CLR の拡張機能として、スコアリングの組み込みのライブラリを追加します。

[**リアルタイム スコアリング**](../real-time-scoring.md)が高パフォーマンスをスコア付けの最初のソリューションです。 R と Python の RevoScaleR、MicrosoftML (R)、revoscalepy、Microsoft が管理機能を介して処理される代わりに CLR ライブラリに依存する SQL Server 2016 以前のバージョンの SQL Server 2017 およびそれ以降の更新で導入された、リアルタイム スコアリングし、microsoftml (Python)。 使用して CLR ライブラリが呼び出される、 **sp_rxPredict**ストアド プロシージャを R または Python のランタイムを呼び出さずに、任意のサポートされているモデル型からスコアを生成します。

[**ネイティブ スコアリング**](../sql-native-scoring.md)は RevoScaleR と revoscalepy モデルに対してのみが、ネイティブの C++ ライブラリとして実装されている、SQL Server 2017 の機能です。 最も迅速かつより安全なアプローチですが、他の方法論の基準とした関数の小さなセットをサポートしています。

## <a name="choose-a-scoring-method"></a>スコアリング方法を選択します。

プラットフォームの要件には、どのスコア付けの方法論を使用する多くの場合、によって決まります。

| 製品のバージョンとプラットフォーム | 手法 |
|------------------------------|-------------|
| Windows、SQL Server 2017 Linux、および Azure SQL Database 上の SQL Server 2017 | **ネイティブ スコアリング**T-SQL での予測と |
| SQL Server 2017 (Windows のみ)、SQL Server 2016 R Services SP1 以上 | **リアルタイム スコアリング**sp\_rxPredict ストアド プロシージャ |

PREDICT 関数を使用したネイティブ スコアリングをお勧めします。 Sp を使用して\_rxPredict では、SQLCLR の統合を有効にすることが必要です。 このオプションを有効にする前に、セキュリティへの影響を検討してください。

## <a name="serialization-and-storage"></a>シリアル化および保存

で高速のスコア付けのオプションのいずれかを、モデルを使用するには、特別なシリアル化された形式でサイズに対して最適化されているし、効率性をスコア付けのモデルを保存します。

+ 呼び出す[rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel)にサポートされているモデルを記述する、**生**形式。
+ 呼び出す[rxUnserializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel)' その他の R コードで使用するモデルを再構築するため、またはモデルを表示します。

**SQL を使用します。**

SQL コードを使用して、モデルをトレーニングできます[sp_execute_external_script](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)、型の列では、テーブルに、トレーニング済みモデルを直接挿入**varbinary (max)** します。 簡単な例では、次を参照してください[を R で preditive モデルを作成する。](../tutorials/rtsql-create-a-predictive-model-r.md)

**R を使用します。**

R コードから呼び出して、 [rxWriteObject](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxwriteobject)モデルをデータベースに直接書き込む RevoScaleR パッケージから関数。 **RxWriteObject()** 関数が SQL Server などの ODBC データ ソースから R オブジェクトを取得またはオブジェクトを SQL Server に書き込むことができます。 API は、単純なキー値ストアの後にモデル化されます。
  
この関数を使用する場合は、モデルを使用して、シリアル化することを確認する[rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel)最初。 次に、設定、*シリアル化*で引数**rxWriteObject**をシリアル化の手順を回避するために、FALSE にします。

バイナリ形式へのモデルをシリアル化するには、便利ですが、R を使用して予測をスコア付けは、その拡張性フレームワークでの Python ランタイム環境は必要ありません。 ファイルの生のバイト形式で、モデルを保存し、その SQL Server に、ファイルから読み取ることがことができます。 このオプションは、環境間でのモデルのコピーまたは移動する場合に便利です。

## <a name="scoring-in-related-products"></a>関連する製品でのスコア付け

使用する場合、[スタンドアロン サーバー](r-server-standalone.md)または[Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)、ストアド プロシージャと予測をすばやく生成するための T-SQL 関数だけでなく、その他のオプションがあります。 スタンドアロン サーバーと Machine Learning Server の両方の概念をサポートする、 *web サービス*コードのデプロイ。 R をバンドルするまたは実行時に新しいデータ入力の評価と呼ばれる、web サービスとして事前トレーニング済みモデル Python。 詳細については、次の記事を参照してください。

+ [Machine Learning Server での web サービスとは](https://docs.microsoft.com/machine-learning-server/operationalize/concept-what-are-web-services)
+ [運用化とは何ですか。](https://docs.microsoft.com/machine-learning-server/operationalize/concept-operationalize-deploy-consume)
+ [Python のモデルを azureml モデル管理 sdk を使用した web サービスとしてデプロイします。](https://docs.microsoft.com/machine-learning-server/operationalize/python/quickstart-deploy-python-web-service)
+ [新しい web サービスとして、R コードのブロックまたはリアルタイムのモデルを発行します。](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)
+ [R の mrsdeploy パッケージ](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)


## <a name="see-also"></a>関連項目

+ [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)  
+ [rxRealTimeScoring](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxrealtimescoring)
+ [sp rxPredict](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql)
+ [T-SQL を予測します。](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)