---
title: SQL Server コンピューターの学習と R Services (In-database) |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 24ef28cd5bfb8e09e3f0ac7dbfe46b5838ce029c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sql-server-machine-learning-and-r-services-in-database"></a>SQL Server コンピューターの学習と R Services (In-database)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

機械学習のデータベースのインストールは、SQL Server インスタンスに常駐のデータを R、Python の外部スクリプトのサポートを提供する、SQL Server データベース エンジン インスタンスのコンテキスト内で動作します。 機械学習を統合しているため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データの近くで分析を行い、コストとデータの移動に関連付けられているセキュリティ上のリスクを削減できます。

データベース エンジンは、複数のインスタンスであるために、1 つ以上のインスタンス、データベース内の分析、または古いでもと新しいバージョン サイド バイ サイドをインストールできます。 いずれかの選択肢を含める[SQL Server 2017 Machine Learning Services (In-database)](../install/sql-machine-learning-standalone-windows-install.md) R と、Python または[SQL Server 2016 R Services (In-database)](../install/sql-r-standalone-windows-install.md) R だけと 

インスタンスにもとらわれないとして machine learning のコンポーネントをインストールすることも[スタンドアロン サーバー](r-server-standalone.md)です。 一般に、ことをお勧め (スタンドアロン) を処理している (In-database) のインストールと相互に、十分なリソースがある場合は、リソースの競合を避けるために限定されない禁止メッセージに対してこれらの両方を同じ物理コンピューターにインストールします。

## <a name="choosing-between-in-database-and-standalone-analytics"></a>データベース内とスタンドアロンの分析の使い分け

開発の要件の理解に役立ちます (In-database) の間を選択してください (スタンドアロン) アプローチです。 スタンドアロン サーバーが、構成および管理する場合はその使用方法、最大限の柔軟性、またはもさまざまな SQL Server の外部データ ソースに接続する場合に簡単です。 

データベース内の分析は、SQL Server 内のデータとの緊密な統合の設計されています。 R または Python 関数を呼び出すし、SQL Server Management Studio または任意のツールと外部または埋め込みの T-SQL を使用しているアプリで、スクリプトを実行する T-SQL クエリを記述することができます。 R、または Python コードを実行する必要がある場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ストアド プロシージャを使用して、または SQL Server を使用してインスタンスとして、[計算コンテキスト](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context)データベース内分析機能をインストールする必要があります。 このオプションは、最大のデータのセキュリティと SQL Server のツールとの統合を提供します。

両方のデータベース内とスタンドアロン サーバーは、オープン ソース R、Python のメモリと処理の制約を減らすことができます。 両方のオプションには、ロード複数のコアで大量のデータを処理し、単一の統合の出力に結果を集計する機能を同じパッケージとツールが含まれます。 関数とアルゴリズムがスケールとユーティリティの両方のエンジニア リング: エンジニア リングおよびでサポートされている予測分析、統計的なモデリング、データの視覚化、および最先端の機械学習商用のサーバー製品でアルゴリズムを提供します。Microsoft です。 

## <a name="components-of-an-in-database-installation"></a>データベースのインストールのコンポーネント

SQL Server 2016 では、R がだけです。 SQL Server 2017 では、R と Python がサポートされています。 次の表では、各バージョンの機能について説明します。 このテーブルで提供されるものと同じ SQL Server スタート パッド サービスを除き、[スタンドアロン server の記事「](r-server-standalone.md)です。

| コンポーネント | Description |
|-----------|-------------|
| SQL Server スタート パッド サービス | 外部の R、Python ランタイム間の通信を管理するサービス、および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。 |
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

+ [SQL Server 2017 Machine Learning Services (In-database)](../install/sql-machine-learning-services-windows-install.md)

+ [SQL Server 2016 の R を Services (In-database) - R のみ](../install/sql-r-services-windows-install.md)
 
### <a name="step-2-configure-a-development-tool"></a>手順 2: 開発ツールを構成します。

Machine Learning のサーバーのバイナリを使用する開発ツールを構成します。 Python の詳細については、次を参照してください。[リンク Python バイナリ](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools)です。 R Studio 内で接続する方法については、次を参照してください。 [R の別のバージョンを使用して](https://support.rstudio.com/hc/en-us/articles/200486138-Using-Different-Versions-of-R)ツールを C:\Program files \microsoft SQL Server\140\R_SERVER\bin\x64 をポイントします。 試しても[R Tools for Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation)です。 

データ サイエンティスト通常使用 R または Python が自分のラップトップ コンピューターや開発ワークステーションでデータを探索し、ビルド、および適切な予測モデルを実現するまでは、予測モデルを調整します。 

SQL Server のデータベース内の分析には、このプロセスを変更する必要はありません。 R または Python コードを実行するにはインストールが完了したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ローカルまたはリモートで。

![rsql_keyscenario2](media/rsql-keyscenario2.png) 

+ **必要に応じて、IDE を使用して**です。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] クライアント コンポーネントは、データ サイエンティストに実験や開発に必要なすべてのツールを提供します。 これらのツールには、R ランタイム、標準的な R 演算のパフォーマンスを向上させる Intel Math Kernel Library、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]での R コードの実行をサポートする一連の拡張 R パッケージが含まれます。  

+ **リモートまたはローカルでの作業**です。 データ サイエンティストは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、通常どおり、ローカル分析のためにクライアントにデータを移動できます。 しかしより優れたソリューションは、使用する、 **RevoScaleR**または**revoscalepy**に計算をプッシュ Api、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター、コストのかかる安全でないデータ移動を回避します。

+ **R または Python スクリプトを埋め込む[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャ**です。 コードは完全に最適化された、ときに、不要なデータ移動を回避し、タスクのデータ処理を最適化するストアド プロシージャでラップします。

### <a name="step-3-write-your-first-script"></a>手順 3: 最初のスクリプトを記述します。

T-SQL スクリプト内から R または Python の関数を呼び出します。
  
  + [R: Transact-SQL での R コードの使用](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md) 
  + [R: SQL 開発者向けの高度な分析 (データベース内)](../tutorials/sqldev-in-database-r-for-sql-developers.md)
  + [Python: T-SQL を使用して Python を実行する](../tutorials/run-python-using-t-sql.md)
  + [Python: SQL 開発者向けの高度な分析 (データベース内)](../tutorials/sqldev-in-database-python-for-sql-developers.md)

タスクに最適な言語を選択します。 R は、SQL を使用して実装するが困難な統計の計算に最適です。 データに対するセットベースの操作での活用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]最大パフォーマンスを実現します。 列にわたって非常に高速計算用のメモリ内のデータベース エンジンを使用します。

### <a name="step-4-optimize-your-solution"></a>手順 4: ソリューションを最適化します。

モデルの企業データにスケール アウトする準備ができたらなどのプロセスを最適化するために、データベース管理者または SQL の開発者に多くの場合、データ サイエンティストは動作します。

+ 機能エンジニアリング
+ データの取り込みやデータの変換
+ ポイントの計算

従来 R を使用するデータ サイエンティストは、特に大規模なデータセットを使用する場合に、パフォーマンスとスケールの両方の問題を必要があります。 一般的なランタイムの実装はシングル スレッドし、ローカル コンピューターで使用可能なメモリに収まらないデータ セットのみに対応できるためです。 SQl Server マシン学習サービスとの統合より多くのデータのパフォーマンスを向上させるため、複数の機能を提供します。

+ **RevoScaleR**: この R パッケージには、最も一般的な R 関数、並列処理とスケールのために再設計のいくつかの実装が含まれています。 パッケージには、通常ははるかに大きなメモリと計算能力がある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに計算をプッシュして、パフォーマンスとスケールをさらに向上させる機能も含まれます。

+ **revoscalepy**です。 この Python ライブラリは、SQL Server 2017 で使用できるは、リモート計算コンテキストなど RevoScaleR で最も人気のある関数を実装しをサポートする多くのアルゴリズムが処理を分散します。

**リソース**

+ [パフォーマンスのケース スタディ](../../advanced-analytics/r/performance-case-study-r-services.md)
+ [R とデータの最適化](../../advanced-analytics/r/r-and-data-optimization-r-services.md)

### <a name="step-5-deploy-and-consume"></a>手順 5: 展開し、使用

スクリプトまたはモデルは、運用環境の使用可能な状態が、データベース開発者を埋め込むことがコードまたはモデル ストアド プロシージャで保存した R または Python コードをアプリケーションから呼び出すことができるようにします。 R コードの格納と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からの実行には多くの利点があります。便利な [!INCLUDE[tsql](../../includes/tsql-md.md)] インターフェイスを使用でき、計算はすべてデータベースで行われるため、不要なデータ移動を回避できます。

![rsql_keyscenario1](media/rsql-keyscenario1.png)

+ **安全で拡張性の高い**です。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] データベース エンジンをセキュリティで保護された状態 R、Python のセッションを分離する新しい拡張可能アーキテクチャを使用します。 スクリプトを実行できる、ユーザーを制御することはもとコードがアクセスできるデータベースを指定することができます。 サーバーの全体的なパフォーマンスが損なわれない大規模な計算を防ぐために、実行時に割り当てられたリソースの量を制御することができます。

+ **スケジュールおよび監査**です。 外部スクリプトのジョブの実行と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]制御することができます、および監査データは、データ サイエンティストが使用されます。 ジョブとその他の T-SQL ジョブまたはストアド プロシージャをスケジュールするのと同じように、外部の R または Python スクリプトを含むワークフローを作成をスケジュールすることもできます。

SQL Server で、リソースの管理およびセキュリ ティー機能の利点を使用するには、展開プロセスに、これらのタスクが含まれます。

+ ストアド プロシージャで最適に実行できる関数にコードを変換します。
+ セキュリティを設定して、特定のタスクで使用されるパッケージをロックダウン
+ リソース統制 (Enterprise edition が必要) を有効にします。

**リソース**

+ [R のリソース管理](resource-governance-for-r-services.md)
+ [SQL Server の R パッケージの管理](r-package-management-for-sql-server-r-services.md)

## <a name="see-also"></a>参照

 [SQL Server コンピューターの学習と R Server (スタンドアロン)](sql-server-r-services.md)
