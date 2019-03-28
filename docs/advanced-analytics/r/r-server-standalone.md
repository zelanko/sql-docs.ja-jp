---
title: スタンドアロン R Server または Machine Learning Server インストールの SQL Server Machine Learning サービス
description: スタンドアロン R Server の概要概要と SQL Server セットアップでの Machine Learning Server
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: overview
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 47edd434445d57c5ca25373b5dc15fa328f94019
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513239"
---
# <a name="r-server-standalone-and-machine-learning-server-standalone-in-sql-server"></a>R Server (スタンドアロン) と SQL Server での Machine Learning Server (スタンドアロン)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server では、スタンドアロン R Server または SQL Server とは無関係に実行する Machine Learning Server インストールのサポートを提供します。 SQL Server のバージョンによっては、スタンドアロン サーバーはあり、その基盤のオープン ソース R と Python、大規模統計および予測分析を追加する、Microsoft からの高パフォーマンス ライブラリ オーバーレイの可能性があります。 ライブラリには、R または Python でスクリプト化された機械学習タスクも有効にします。 

SQL Server 2016 では、この機能は呼**R Server (スタンドアロン)** であり、R 専用です。 SQL Server 2017 で呼び出されます**Machine Learning Server (スタンドアロン)** R と Python の両方が含まれています。  

> [!Note]
> スタンドアロン サーバーは、機能的には、SQL のブランド化されていないバージョンの SQL Server セットアップによってインストールされている、 [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)、リモートの実行など、ユーザー シナリオをサポートしています。サービスの運用化と web サービス、および R と Python ライブラリの完全なコレクション。

## <a name="components"></a>コンポーネント

SQL Server 2016 には R のみです。 SQL Server 2017 では、R と Python がサポートされています。 次の表では、各バージョンの機能について説明します。

| コンポーネント | 説明 |
|-----------|-------------|
| R パッケージ | [**RevoScaleR** ](ref-r-revoscaler.md)スケーラブルな R データ操作、変換、視覚エフェクトと分析のための関数とは、プライマリ ライブラリ。  <br/>[**MicrosoftML** ](ref-r-microsoftml.md)テキスト分析、画像分析、およびセンチメント分析のカスタム モデルを作成する機械学習アルゴリズムを追加します。 <br/>[**sqlRUtils** ](ref-r-sqlrutils.md) T-SQL ストアド プロシージャに R スクリプトを配置すること、データベースでストアド プロシージャを登録すると、R 開発環境からストアド プロシージャを実行しているヘルパー関数を提供します。<br/>[**mrsdeploy** ](operationalization-with-mrsdeploy.md)プランの web サービス (SQL Server 2017 のみ) での展開。 <br/>[**olapR** ](ref-r-olapr.md)は R で MDX クエリを指定するため|
| Microsoft R Open (MRO) | [**MRO** ](https://mran.microsoft.com/open)は r です Microsoft のオープン ソース ディストリビューションには。パッケージおよびインタープリターが含まれます。 常にセットアップにまとめられた MRO のバージョンを使用します。 |
| R ツール | R コンソール ウィンドウとコマンド プロンプトは、R のディストリビューションで標準的なツールです。 \Program files\Microsoft SQL Server\140\R_SERVER\bin\x64 で見つけることです。 |
| R のサンプルとスクリプト |  オープン ソースの R と RevoScaleR パッケージには、作成して事前インストールされているデータを使用してスクリプトを実行できるように、組み込みのデータ セットが含まれます。 \Program files\Microsoft SQL Server\140\R_SERVER\library\datasets と \library\RevoScaleR でそれらを探します。 |
| Python パッケージ | [**revoscalepy** ](../python/ref-py-revoscalepy.md)データ操作、変換、視覚エフェクトと分析のための関数での Python のスケーラブルなは、プライマリ ライブラリ。 <br/>[**microsoftml** ](../python/ref-py-microsoftml.md)テキスト分析、画像分析、およびセンチメント分析のカスタム モデルを作成する機械学習アルゴリズムを追加します。  |
| Python ツール | 組み込みの Python のコマンド ライン ツールは、アドホック テストとタスクに適しています。 \Program files\Microsoft SQL Server\140\PYTHON_SERVER\python.exe でツールを検索します。 |
| Anaconda | Anaconda とは、Python と重要なパッケージのオープン ソース ディストリビューションです。 |
| Python のサンプルとスクリプト | R と Python には、組み込みのデータ セットとスクリプトが含まれています。 Revoscalepy データを掲載 \Program files\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-packages\revoscalepy\data\sample データ。 |
| R および Python で事前トレーニング済みモデル | 事前トレーニング済みモデルは特定のユース ケース用に作成し、microsoft データ サイエンスのエンジニア リング チームによって管理されます。 事前トレーニング済みモデルとして使用することができます-正、負のセンチメントをスコア付けで、テキストまたはイメージを提供する新しいデータの入力を使用して機能を検出します。 事前トレーニング済みモデルはサポートされていると、スタンドアロン サーバーで使用できますが、SQL Server セットアップでインストールすることはできません。 詳細については、次を参照してください。[インストールには、SQL Server で機械学習モデルが事前トレーニング済み](../install/sql-pretrained-models-install.md)します。 |

## <a name="using-a-standalone-server"></a>スタンドアロン サーバーを使用します。

R と Python の開発者は、通常、スタンドアロン サーバーにとどまらず、オープン ソース R と Python のメモリと処理の制約を選択します。 R と Python ライブラリがスタンドアロン サーバー上で実行は、ロードし複数コアで大量のデータを処理し、単一の統合の出力に結果を集計できます。 スケールとユーティリティの両方の高パフォーマンスな関数が設計されていますエンジニア リングとでサポートされている予測分析、統計モデリング、データの視覚化、および最先端の機械学習、商用のサーバー製品でアルゴリズムを提供する。Microsoft。

SQL Server から切り離されて独立したサーバーと、R と Python 環境が構成された、セキュリティ保護、および基になるオペレーティング システムと SQL サーバーではなく、スタンドアロン サーバーで提供される標準のツールを使用してアクセスします。 SQL Server のリレーショナル データの組み込みサポートはありません。 SQL Server のデータを使用する場合は、任意のクライアントの場合と、データ ソース オブジェクトとの接続を作成できます。

補完のため SQL Server、ローカルとリモートの両方を計算する必要がある場合、スタンドアロン サーバーは、強力な開発環境として役立ちますも。 スタンドアロン サーバー上の R と Python のパッケージは、コードの移植性のため、データベース エンジンのインストールで提供されるものと同じと[コンピューティング コンテキストの切り替え](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context)します。

## <a name="how-to-get-started"></a>開始する方法

セットアップを開始、バイナリを使い慣れた開発ツールにアタッチし、最初のスクリプトを記述します。

### <a name="step-1-install-the-software"></a>手順 1:ソフトウェアをインストールします。

これらのバージョンのいずれかをインストールします。

+ [SQL Server 2017 の Machine Learning Server (スタンドアロン)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Server (スタンドアロン) - R のみ](../install/sql-r-standalone-windows-install.md)

### <a name="step-2-configure-a-development-tool"></a>手順 2:開発ツールを構成します。

スタンドアロン サーバーでは、同じコンピューターにインストールされている開発を使用してローカルで動作する一般的です。

+ [R ツールの設定](set-up-a-data-science-client.md)
+ [Python ツールの設定](../python/setup-python-client-tools-sql.md)

### <a name="step-3-write-your-first-script"></a>手順 3:最初のスクリプトを作成します。

RevoScaleR、revoscalepy、および機械学習アルゴリズムから関数を使用して、R または Python のスクリプトを記述します。
  
  + [R と 25 の関数で RevoScaleR 探索](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler):基本的な R コマンドから開始して、高パフォーマンスとスケーリング R ソリューションを提供する RevoScaleR の再頒布可能分析関数にし、進行状況します。 最も一般的な R モデリング パッケージ (K-平均法クラスタリング、デシジョン ツリー、デシジョン フォレストなど) の並列化可能なバージョンの多くと、データ操作のツールを含みます。

  + [クイック スタート:Microsoftml の Python パッケージを二項分類の例](https://docs.microsoft.com/machine-learning-server/python/quickstart-binary-classification-with-microsoftml):Microsoftml とよく知られている乳がんがんのデータセットから関数を使用して二項分類モデルを作成します。

タスクの最適な言語を選択します。 R は、SQL を使用して実装するが困難な統計の計算に最適です。 データ セット ベース操作では、活用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]最大のパフォーマンスを実現するためにします。 列にわたって非常に高速計算、メモリ内データベース エンジンを使用します。

### <a name="step-4-operationalize-your-solution"></a>手順 4:ソリューションを運用化します。

スタンドアロン サーバーを使用できる、 [operationalization](https://docs.microsoft.com//machine-learning-server/what-is-operationalization)機能、SQL のノンブランドの[Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)します。 運用化は、これらのメリットを提供するスタンドアロン サーバーを構成することができます。 展開および web サービス、診断の実行、テストの web サービスの容量として、コードをホストします。

### <a name="step-5-maintain-your-server"></a>手順 5:サーバーを管理します。

SQL Server では、定期的に累積的更新プログラムを解放します。 累積的更新プログラムを適用するセキュリティと機能の拡張を既存のインストールに追加します。 

新規または変更された機能についての説明が記載されて、 [CAB のダウンロード](../install/sql-ml-cab-downloads.md)記事や、web ページの[SQL Server 2016 累積的更新プログラム](https://support.microsoft.com/help/3177312/sql-server-2016-build-versions)と[SQL Server 2017 の累積的更新プログラム](https://support.microsoft.com/help/4047329). 

既存のインスタンスに更新プログラムを適用する方法の詳細については、次を参照してください。[更新プログラムを適用](../install/sql-machine-learning-standalone-windows-install.md#apply-cu)のインストール手順。

## <a name="see-also"></a>関連項目

 [R Server (スタンドアロン) または Machine Learning Server (スタンドアロンを) インストールします。](../install/sql-machine-learning-standalone-windows-install.md)

