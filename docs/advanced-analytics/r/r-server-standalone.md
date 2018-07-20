---
title: SQL Server Machine Learning Server (スタンドアロン) と R Server (スタンドアロン) |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a8cdceabc26c55b6eade57712fa610d3e84808f5
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174789"
---
# <a name="sql-server-machine-learning-server-standalone-and-r-server-standalone"></a>SQL Server Machine Learning Server (スタンドアロン) と R Server (スタンドアロン)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

スタンドアロン サーバーは、SQL Server データベース エンジンのインスタンスとは無関係に実行される R と Python の機能と示されます、machine learning コンポーネントのインストールです。 SQL Server の依存関係のない自体は、スタンドアロン サーバーをインストールできます。 スタンドアロン サーバーが SQL Server、構成および管理タスクに依存しないと、ツールは複数の Machine Learning Server についての非 SQL バージョンと似ていますので[今回](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)します。

スタンドアロンの machine learning server の目的は、独自のパッケージおよび計算エンジンを使用して、小規模から大規模のデータ セットを R と Python のワークロードの分散し並列処理の機能豊富な開発環境を提供するにはサーバーと共にインストールされます。 スタンドアロン サーバー上の R と Python のパッケージは、コードの移植性のため、SQL Server (In-database) のインストールで提供されているものと同じと[コンピューティング コンテキストの切り替え](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context)します。

主な理由は、開発者は、スタンドアロンの machine learning server はオープン ソース R と Python のメモリと処理の制約にとどまらないを選択します。 スタンドアロン サーバーは読み込みと複数コアで大量のデータを処理し、統合された 1 つの出力に結果を集計します。 関数とアルゴリズムがスケールとユーティリティの両方に設計されていますエンジニア リングとでサポートされている予測分析、統計モデリング、データの視覚化、および最先端の機械学習、商用のサーバー製品でアルゴリズムを提供する。Microsoft。

一般に、お勧めします (スタンドアロン) を処理している (データベース内) のインストールと相互に十分なリソースがある場合は、リソースの競合を回避するために排他がない禁止に対して同じ物理コンピューターに両方をインストールします。

1 つのスタンドアロン サーバーをコンピューターにしか: か[SQL Server 2017 の Machine Learning Server (スタンドアロン)](../install/sql-machine-learning-standalone-windows-install.md)または[SQL Server 2016 R Server (スタンドアロン)](../install/sql-r-standalone-windows-install.md)します。 別のバージョンをインストールする前に、1 つのバージョンを手動でアンインストールする必要があります。

## <a name="components-of-a-standalone-server"></a>スタンドアロン サーバーのコンポーネント

SQL Server 2016 には R のみです。 SQL Server 2017 では、R と Python がサポートされています。 次の表では、各バージョンの機能について説明します。

| コンポーネント | 説明 |
|-----------|-------------|
| R パッケージ | [RevoScaleR](revoscaler-overview.md)スケーラブルな R 関数のデータ操作、変換、visualzation、および分析とは、プライマリ ライブラリ。  <br/>[MicrosoftML (R)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)テキスト分析、画像分析、およびセンチメント分析のカスタム モデルを作成する機械学習アルゴリズムを追加します。 <br/>[mrsdeploy](operationalization-with-mrsdeploy.md)プランの web サービス (SQL Server 2017 のみ) での展開。 <br/>[olapR](how-to-create-mdx-queries-using-olapr.md)は R で MDX クエリを指定するため|
| Microsoft R Open (MRO) | [MRO](https://mran.microsoft.com/open)は r です Microsoft のオープン ソース ディストリビューションには。パッケージおよびインタープリターが含まれます。 常にセットアップにまとめられた MRO のバージョンを使用します。 |
| R ツール | R コンソール ウィンドウとコマンド プロンプトは、R のディストリビューションで標準的なツールです。 \Program files\Microsoft SQL Server\140\R_SERVER\bin\x64 で見つけることです。 |
| R のサンプルとスクリプト |  オープン ソースの R と RevoScaleR パッケージには、作成して事前インストールされているデータを使用してスクリプトを実行できるように、組み込みのデータ セットが含まれます。 \Program files\Microsoft SQL Server\140\R_SERVER\library\datasets と \library\RevoScaleR でそれらを探します。 |
| Python パッケージ | [revoscalepy](../python/what-is-revoscalepy.md)データ操作、変換、visualzation、および分析のための関数での Python のスケーラブルなは、プライマリ ライブラリ。 <br/>[microsoftml (Python)](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)テキスト分析、画像分析、およびセンチメント分析のカスタム モデルを作成する機械学習アルゴリズムを追加します。  |
| Python ツール | 組み込みの Python のコマンド ライン ツールは、アドホック テストとタスクに適しています。 \Program files\Microsoft SQL Server\140\PYTHON_SERVER\python.exe でツールを検索します。 |
| Anaconda | Anaconda とは、Python と重要なパッケージのオープン ソース ディストリビューションです。 |
| Python のサンプルとスクリプト | R と Python には、組み込みのデータ セットとスクリプトが含まれています。 Revoscalepy データを掲載 \Program files\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-packages\revoscalepy\data\sample データ。 |
| R および Python で事前トレーニング済みモデル | 事前トレーニング済みモデルはサポートされていると、スタンドアロン サーバーで使用できますが、SQL Server セットアップでインストールすることはできません。 Microsoft Machine Learning Server のセットアップ プログラムは、モデルでは、インストールすることができますを提供します。 無料です。 詳細については、次を参照してください。[インストールには、SQL Server で機械学習モデルが事前トレーニング済み](../install/sql-pretrained-models-install.md)します。 |

## <a name="get-started-step-by-step"></a>ステップ バイ ステップを開始します。

セットアップを開始、バイナリを使い慣れた開発ツールにアタッチし、最初のスクリプトを記述します。

### <a name="step-1-install-the-software"></a>手順 1: ソフトウェアをインストールします。

これらのバージョンのいずれかをインストールします。

+ [SQL Server 2017 の Machine Learning Server (スタンドアロン)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Server (スタンドアロン) - R のみ](../install/sql-r-standalone-windows-install.md)

### <a name="step-2-configure-a-development-tool"></a>手順 2: 開発ツールを構成します。

Machine Learning Server バイナリを使用する開発ツールを構成します。 Python の詳細については、次を参照してください。[リンク Python バイナリ](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools)します。 R Studio に接続する方法については、次を参照してください。 [R の別のバージョンのを使用して](https://support.rstudio.com/hc/en-us/articles/200486138-Using-Different-Versions-of-R)C:\Program files \microsoft SQL Server\140\R_SERVER\bin\x64 にツールをポイントします。 試しても[R Tools for Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation)します。 

### <a name="step-3-write-your-first-script"></a>手順 3: 最初のスクリプトを記述します。

RevoScaleR、revoscalepy、および機械学習アルゴリズムから関数を使用して、R または Python のスクリプトを記述します。
  
  + [R と 25 の関数で RevoScaleR 探索](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): 基本的な R コマンドと、高いパフォーマンスを実現する RevoScaleR の再頒布可能分析関数への進行状況と R ソリューションをスケーリングと開始します。 最も一般的な R モデリング パッケージ (K-平均法クラスタリング、デシジョン ツリー、デシジョン フォレストなど) の並列化可能なバージョンの多くと、データ操作のツールを含みます。

  + [クイック スタート: microsoftml の Python パッケージを二項分類の例](https://docs.microsoft.com/machine-learning-server/python/quickstart-binary-classification-with-microsoftml): microsoftml とよく知られている乳がんがんのデータセットから関数を使用して二項分類モデルを作成します。

タスクの最適な言語を選択します。 R は、SQL を使用して実装するが困難な統計の計算に最適です。 データ セット ベース操作では、活用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]最大のパフォーマンスを実現するためにします。 列にわたって非常に高速計算、メモリ内データベース エンジンを使用します。

### <a name="step-4-operationalize-your-solution"></a>手順 4: ソリューションを運用します。

スタンドアロン サーバーを使用できる、 [operationalization](https://docs.microsoft.com//machine-learning-server/what-is-operationalization)機能、SQL のノンブランドの[Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)します。 運用化は、これらのメリットを提供するスタンドアロン サーバーを構成することができます。 展開および web サービス、診断の実行、テストの web サービスの容量として、コードをホストします。

## <a name="see-also"></a>参照

 [SQL Server Machine Learning Services (In-database)](sql-server-r-services.md)

