---
title: SQL Server Machine Learning と R Services (In-database) |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 05a2a17988912d7066b0d9f6bf398b889a3cd882
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174779"
---
# <a name="sql-server-machine-learning-and-r-services-in-database"></a>SQL Server Machine Learning と R Services (In-database)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Machine learning のデータベースのインストールは、常駐のデータ、SQL Server インスタンスでの R と Python の外部スクリプトのサポートを提供する、SQL Server データベース エンジン インスタンスのコンテキスト内で動作します。 Machine learning を統合するため[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データの近くで分析を保持し、コストとデータの移動に関連付けられているセキュリティ上のリスクを排除できます。

データベース エンジンは、マルチ インスタンスであるために、1 つ以上のインスタンスのデータベース内分析、または古いも、新しいバージョンのサイド バイをインストールできます。 どちらかの選択肢が含まれます[SQL Server 2017 の Machine Learning Services (In-database)](../install/sql-machine-learning-standalone-windows-install.md)で R、Python、または[SQL Server 2016 R Services (In-database)](../install/sql-r-standalone-windows-install.md)で R だけです 

インスタンスに依存しないとして machine learning コンポーネントをインストールすることも[スタンドアロン サーバー](r-server-standalone.md)します。 一般に、お勧めします (スタンドアロン) を処理している (データベース内) のインストールと相互に十分なリソースがある場合は、リソースの競合を回避するために排他がない禁止メッセージに対して、同じ物理コンピューターに両方をインストールします。

## <a name="choosing-between-in-database-and-standalone-analytics"></a>スタンドアロン データベースでの分析の使い分け

開発要件の理解に役立ちます (スタンドアロン) に近づくし、(データベース) を選択します。 スタンドアロン サーバーは、簡単に構成および管理する場合はその使用方法、最大限の柔軟性、またはもさまざまな SQL Server の外部データ ソースに接続する場合。 

SQL Server 内のデータとの統合には、データベース内分析が設計されています。 R または Python 関数を呼び出すし、SQL Server Management Studio または任意のツールまたは外部または埋め込まれた T-SQL に使用されるアプリで、スクリプトを実行する T-SQL クエリを記述することができます。 R または Python コードを実行する必要がある場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ストアド プロシージャを使用して、または SQL Server を使用してインスタンスとして、[コンピューティング コンテキスト](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context)データベース内分析機能をインストールする必要があります。 このオプションは、最大のデータのセキュリティと SQL Server のツールとの統合を提供します。

両方のデータベース内とスタンドアロン サーバーは、オープン ソース R と Python のメモリと処理の制約を軽減できます。 両方のオプションには、読み込む、複数コアで大量のデータを処理し、単一の統合の出力に結果を集計することができます、同じパッケージとツールが含まれます。 関数とアルゴリズムがスケールとユーティリティの両方に設計されていますエンジニア リングとでサポートされている予測分析、統計モデリング、データの視覚化、および最先端の機械学習、商用のサーバー製品でアルゴリズムを提供する。Microsoft。 

## <a name="components-of-an-in-database-installation"></a>データベースのインストールのコンポーネント

SQL Server 2016 には R のみです。 SQL Server 2017 では、R と Python がサポートされています。 次の表では、各バージョンの機能について説明します。 このテーブルは、SQL Server スタート パッド サービスを除くで提供されるものと同じでは、[スタンドアロン server の記事](r-server-standalone.md)します。

| コンポーネント | 説明 |
|-----------|-------------|
| SQL Server スタート パッド サービス | 外部の R と Python のランタイム間の通信を管理するサービスと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。 |
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

+ [SQL Server 2017 Machine Learning サービス (データベース)](../install/sql-machine-learning-services-windows-install.md)

+ [SQL Server 2016 R を Services (In-database) - R のみ](../install/sql-r-services-windows-install.md)
 
### <a name="step-2-configure-a-development-tool"></a>手順 2: 開発ツールを構成します。

Machine Learning Server バイナリを使用する開発ツールを構成します。 Python の詳細については、次を参照してください。[リンク Python バイナリ](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools)します。 R Studio に接続する方法については、次を参照してください。 [R の別のバージョンのを使用して](https://support.rstudio.com/hc/en-us/articles/200486138-Using-Different-Versions-of-R)C:\Program files \microsoft SQL Server\140\R_SERVER\bin\x64 にツールをポイントします。 試しても[R Tools for Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation)します。 

データ サイエンティスト通常 R または Python を使用、独自のラップトップ コンピューターや開発ワークステーションにデータを探索し、ビルド、適切な予測モデルを実現するまでは、予測モデルを調整します。 

SQL server の in-database analytics では、このプロセスを変更する必要はありません。 R または Python コードを実行するにはインストールが完了したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ローカルまたはリモートで。

![rsql_keyscenario2](media/rsql-keyscenario2.png) 

+ **必要に応じて IDE を使用して**します。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] クライアント コンポーネントは、データ サイエンティストに実験や開発に必要なすべてのツールを提供します。 これらのツールには、R ランタイム、標準的な R 演算のパフォーマンスを向上させる Intel Math Kernel Library、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]での R コードの実行をサポートする一連の拡張 R パッケージが含まれます。  

+ **リモートまたはローカルでの作業**します。 データ サイエンティストは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、通常どおり、ローカル分析のためにクライアントにデータを移動できます。 ただしより優れたソリューションは、使用する、 **RevoScaleR**または**revoscalepy**に計算をプッシュ Api、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター、コストのかかる安全でないデータ移動を回避します。

+ **R または Python スクリプトを埋め込む[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャ**します。 コードを完全に最適化するときは、不要なデータ移動を回避し、データ処理タスクを最適化するストアド プロシージャでラップします。

### <a name="step-3-write-your-first-script"></a>手順 3: 最初のスクリプトを記述します。

T-SQL スクリプト内で R または Python 関数を呼び出します。
  
  + [R: Transact-SQL での R コードの使用](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md) 
  + [R: SQL 開発者向けの高度な分析 (データベース内)](../tutorials/sqldev-in-database-r-for-sql-developers.md)
  + [Python: T-SQL を使用して Python を実行する](../tutorials/run-python-using-t-sql.md)
  + [Python: SQL 開発者向けの高度な分析 (データベース内)](../tutorials/sqldev-in-database-python-for-sql-developers.md)

タスクの最適な言語を選択します。 R は、SQL を使用して実装するが困難な統計の計算に最適です。 データ セット ベース操作では、活用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]最大のパフォーマンスを実現するためにします。 列にわたって非常に高速計算、メモリ内データベース エンジンを使用します。

### <a name="step-4-optimize-your-solution"></a>手順 4: ソリューションを最適化します。

モデルのエンタープライズ データを拡大縮小する準備ができたら、データ サイエンティストは多くの場合などのプロセスを最適化するために、データベース管理者または SQL の開発者で動作します。

+ 機能エンジニアリング
+ データの取り込みとデータ変換
+ ポイントの計算

従来からデータ サイエンティストが R を使用して問題がある両方のパフォーマンスとスケール、特に大規模なデータセットを使用する場合。 共通ランタイムの実装はシングル スレッドし、ローカル コンピューターの使用可能なメモリに収まるデータ セットのみに対応できるためです。 SQl Server Machine Learning Services との統合は、多くのデータをパフォーマンスの向上のための複数の機能を提供します。

+ **RevoScaleR**: この R パッケージには、並列処理とスケールを提供する再設計された、最も一般的な R 関数のいくつかの実装が含まれています。 パッケージには、通常ははるかに大きなメモリと計算能力がある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに計算をプッシュして、パフォーマンスとスケールをさらに向上させる機能も含まれます。

+ **revoscalepy**します。 この Python ライブラリは、SQL Server 2017 で利用可能な revoscaler のリモート計算コンテキストなど、最も人気のある関数を実装して、分散処理をサポートする多くのアルゴリズム。

**リソース**

+ [パフォーマンスのケース スタディ](../../advanced-analytics/r/performance-case-study-r-services.md)
+ [R とデータの最適化](../../advanced-analytics/r/r-and-data-optimization-r-services.md)

### <a name="step-5-deploy-and-consume"></a>手順 5: 展開し、使用

スクリプトまたはモデルが運用環境で使用できる状態と、データベース開発者を埋め込むことがコードまたはモデルでストアド プロシージャでは、アプリケーションから保存した R または Python コードを呼び出すことができるようにします。 R コードの格納と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からの実行には多くの利点があります。便利な [!INCLUDE[tsql](../../includes/tsql-md.md)] インターフェイスを使用でき、計算はすべてデータベースで行われるため、不要なデータ移動を回避できます。

![rsql_keyscenario1](media/rsql-keyscenario1.png)

+ **セキュリティで保護されたで拡張可能な**します。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 状態、データベース エンジンをセキュリティで保護された R と Python のセッションを分離する新しい拡張可能アーキテクチャを使用します。 コードでアクセスできるデータベースを指定することができますおよびスクリプトを実行できるユーザーを制御もあります。 サーバーの全体のパフォーマンスを損なうから大量の計算を防ぐために、実行時に割り当てられたリソースの量を制御できます。

+ **スケジュール設定と監査**します。 外部スクリプト ジョブの実行と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と監査データは、データ サイエンティストが使用を制御できます。 ジョブと他の T-SQL ジョブまたはストアド プロシージャをスケジュールするのと同じように、外部の R または Python スクリプトを含むワークフローを作成をスケジュールすることもできます。

SQL Server で、リソース管理とセキュリ ティーの機能の利点を実行するには、展開プロセスにこれらのタスクが含まれます。

+ コードをストアド プロシージャで最適に実行できる関数に変換します。
+ セキュリティを設定して、特定のタスクで使用されるパッケージのロックダウン
+ リソース ガバナンスが (Enterprise edition が必要) を有効にします。

**リソース**

+ [R 用のリソース ガバナンス](resource-governance-for-r-services.md)
+ [SQL Server の R パッケージ管理](install-additional-r-packages-on-sql-server.md)

## <a name="see-also"></a>参照

 [SQL Server Machine Learning と R Server (スタンドアロン)](sql-server-r-services.md)
