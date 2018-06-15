---
title: SQL Server マシン ラーニング Server (スタンドアロン) と R Server (スタンドアロン) |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 2c416049692f8860e4ba608e58f401ce527b135c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203044"
---
# <a name="sql-server-machine-learning-server-standalone-and-r-server-standalone"></a>SQL Server マシン ラーニング Server (スタンドアロン) と R Server (スタンドアロン)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

スタンドアロン サーバーは、SQL Server データベース エンジンのインスタンスとは無関係に実行される R、Python の特徴として表記、マシン学習コンポーネントのインストールです。 自体は、スタンドアロン サーバーをインストールするには SQL Server の依存関係のないとします。 スタンドアロン サーバーが SQL Server、構成および管理タスクから独立しており、ツールでについてを参照して、マシン学習サーバーの SQL 以外のバージョンと非常に似ているため[この資料](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)です。

スタンドアロンの machine learning サーバーの目的は、小規模の大きいデータ セットを独自のパッケージおよび計算エンジンを使用して経由での R、Python のワークロードの分散および並列処理で、高機能な開発環境を提供するにはサーバーと共にインストールされます。 スタンドアロン サーバー上の R および Python パッケージは、コードの移植性のため、SQL Server (In-database) のインストールで提供されているものと同じと[コンピューティング コンテキストの切り替え](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context)です。

主な理由は、開発者にとどまらず、オープン ソース R、Python のメモリと処理の制約は、スタンドアロンの machine learning サーバーを選択します。 スタンドアロン サーバーできますと複数のコアで大量のデータを処理を読み込んで 1 つの統合された出力に結果を集計します。 関数とアルゴリズムがスケールとユーティリティの両方のエンジニア リング: エンジニア リングおよびでサポートされている予測分析、統計的なモデリング、データの視覚化、および最先端の機械学習商用のサーバー製品でアルゴリズムを提供します。Microsoft です。

一般に、ことをお勧め (スタンドアロン) を処理している (In-database) のインストールに相互排他を十分なリソースがある場合は、リソースの競合を回避するのにはありません禁止これらの両方を同じ物理コンピューターにインストールする対象です。

コンピューターの 1 つのスタンドアロン サーバーしか持てない: か[SQL Server 2017 Machine Learning サーバー (スタンドアロン)](../install/sql-machine-learning-standalone-windows-install.md)または[SQL Server 2016 R Server (スタンドアロン)](../install/sql-r-standalone-windows-install.md)です。 別のバージョンをインストールする前に、1 つのバージョンを手動でアンインストールする必要があります。

## <a name="components-of-a-standalone-server"></a>スタンドアロン サーバーのコンポーネント

SQL Server 2016 では、R がだけです。 SQL Server 2017 では、R と Python がサポートされています。 次の表では、各バージョンの機能について説明します。

| コンポーネント | Description |
|-----------|-------------|
| R パッケージ | [RevoScaleR](revoscaler-overview.md)データ操作、変換、visualzation、および分析の機能と拡張性の高い R のプライマリ ライブラリは、します。  <br/>[MicrosoftML (R)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)テキスト分析、画像分析、およびセンチメント分析のカスタム モデルを作成する機械学習アルゴリズムを追加します。 <br/>[mrsdeploy](operationalization-with-mrsdeploy.md)オファー web サービスの展開で SQL Server 2017 のみ)。 <br/>[olapR](how-to-create-mdx-queries-using-olapr.md) R. の MDX クエリを指定するためには|
| Microsoft R Open (MRO) | [MRO](https://mran.microsoft.com/open)は r です Microsoft のオープン ソース ディストリビューションには。パッケージおよびインタープリターが含まれます。 常にセットアップにバンドル MRO のバージョンを使用します。 |
| R のツール | R コンソール ウィンドウとコマンド プロンプトは、R ディストリビューションで標準的なツールです。 \Program files\Microsoft SQL Server\140\R_SERVER\bin\x64 で見つけることです。 |
| R サンプルおよびスクリプト |  オープン ソース R と RevoScaleR パッケージには、作成したり、事前インストールされているデータを使用してスクリプトを実行できるように、組み込みのデータ セットが含まれます。 \Program files\Microsoft SQL Server\140\R_SERVER\library\datasets と \library\RevoScaleR でそれらを参照してください。 |
| Python パッケージ | [revoscalepy](../python/what-is-revoscalepy.md)データ操作、変換、visualzation、および分析のための関数での Python の拡張性の高いは、プライマリ ライブラリです。 <br/>[microsoftml (Python)](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)テキスト分析、画像分析、およびセンチメント分析のカスタム モデルを作成する機械学習アルゴリズムを追加します。  |
| Python tools | 組み込みの Python コマンド ライン ツールは、アドホック テストとタスクに役立ちます。 \Program files\Microsoft SQL Server\140\PYTHON_SERVER\python.exe でツールを検索します。 |
| Anaconda | Anaconda は、オープン ソースの Python と重要なパッケージです。 |
| Python のサンプルとスクリプト | 同様に R、Python には、組み込みのデータ セットやスクリプトが含まれています。 \Program files\Microsoft SQL で revoscalepy データを見つける Server\140\PYTHON_SERVER\lib\site packages\revoscalepy\data\sample データ。 |
| R、Python の事前トレーニング済みモデル | 事前トレーニング済みモデルはサポートされていると、スタンドアロン サーバーで使用できるが、SQL Server セットアップでインストールすることはできません。 Microsoft Machine Learning のサーバーのセットアップ プログラムをモデルでは、インストールすることができますを提供する無料です。 詳細については、次を参照してください。[インストールは、SQL Server 上の機械学習モデルを事前トレーニング済み](install-pretrained-models-sql-server.md)です。 |

## <a name="get-started-step-by-step"></a>詳細な手順を開始します。

セットアップを開始、バイナリを他の開発ツールにアタッチし、最初のスクリプトを記述します。

### <a name="step-1-install-the-software"></a>手順 1: ソフトウェアをインストールします。

これらのバージョンのいずれかをインストールします。

+ [SQL Server 2017 Machine Learning サーバー (スタンドアロン)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Server (スタンドアロン) - R のみ](../install/sql-r-standalone-windows-install.md)

### <a name="step-2-configure-a-development-tool"></a>手順 2: 開発ツールを構成します。

Machine Learning のサーバーのバイナリを使用する開発ツールを構成します。 Python の詳細については、次を参照してください。[リンク Python バイナリ](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools)です。 R Studio 内で接続する方法については、次を参照してください。 [R の別のバージョンを使用して](https://support.rstudio.com/hc/en-us/articles/200486138-Using-Different-Versions-of-R)ツールを C:\Program files \microsoft SQL Server\140\R_SERVER\bin\x64 をポイントします。 試しても[R Tools for Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation)です。 

### <a name="step-3-write-your-first-script"></a>手順 3: 最初のスクリプトを記述します。

RevoScaleR、revoscalepy、および、機械学習アルゴリズムから関数を使用して R または Python スクリプトを記述します。
  
  + [R と RevoScaleR 25 関数での探索](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): 基本的な R コマンドや、高いパフォーマンスを実現 RevoScaleR 配布可能な分析関数に進行状況をし、R ソリューションをスケーリングを開始します。 最も一般的な R モデリング パッケージ (K-平均法クラスタリング、デシジョン ツリー、デシジョン フォレストなど) の並列化可能なバージョンの多くと、データ操作のツールを含みます。

  + [クイック スタート: microsoftml Python パッケージに二項分類の例](https://docs.microsoft.com/machine-learning-server/python/quickstart-binary-classification-with-microsoftml): microsoftml とよく知られた乳がんのデータセットから関数を使用して二項分類モデルを作成します。

タスクに最適な言語を選択します。 R は、SQL を使用して実装するが困難な統計の計算に最適です。 データに対するセットベースの操作での活用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]最大パフォーマンスを実現します。 列にわたって非常に高速計算用のメモリ内のデータベース エンジンを使用します。

### <a name="step-4-operationalize-your-solution"></a>手順 4: ソリューションを運用します。

スタンドアロン サーバーを使用できます、[操作運用](https://docs.microsoft.com//machine-learning-server/what-is-operationalization)機能、SQL のノンブランドの[Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)です。 により、これらの利点と操作運用のスタンドアロン サーバーを構成することができます。 展開および web サービス、診断の実行、テストの web サービスの容量に、コードをホストします。

## <a name="see-also"></a>参照

 [SQL Server コンピューターのサービス (In-database) を学習](sql-server-r-services.md)

