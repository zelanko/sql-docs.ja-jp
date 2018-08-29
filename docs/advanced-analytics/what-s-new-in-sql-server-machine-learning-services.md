---
title: どのような&#39;s の SQL Server Machine Learning Services の新機能 |Microsoft Docs
description: 新しい機能のお知らせの各リリースの SQL Server 2016 R Services、R Server、SQL Server 2017 Machine Learning サービス。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/28/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8d3dc4c730ea9c7c9ba0126a50ed4bb8129efc9c
ms.sourcegitcommit: fb269accc3786715c78f8b6e2ec38783a6eb63e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2018
ms.locfileid: "43152582"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>SQL Server Machine Learning Services の新機能新機能 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

機械学習機能は、展開、拡張、およびデータ プラットフォームとデータ サイエンス、分析、統合を深めるに伴いに SQL Server に各リリースで追加され、教師あり学習のデータを実装します。 

## <a name="new-in-sql-server-2017"></a>SQL Server 2017 の新機能

このリリースで追加[Python のサポートと業界最先端の機械学習アルゴリズム](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)します。 新しいスコープを反映するように名前変更、SQL Server 2017 のマークの導入に伴い[SQL Server Machine Learning サービス (In-database)](what-is-sql-server-machine-learning.md)Python と R. の両方の言語サポート 

また、このリリース[SQL Server Machine Learning Server (スタンドアロン)](r/r-server-standalone.md)R と Python のワークロード専用のシステム上で実行する SQL Server の完全に独立しました。 スタンドアロン サーバーで、配布でき、SQL Server を使用せず、R または Python のソリューションをスケールできます。

### <a name="python-integration-for-in-database-analytics"></a>データベース内分析用の Python 統合

T-SQL と Python の統合はサポートされています、 [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)システム ストアド プロシージャ。 このストアド プロシージャを使用してすべての Python コードを呼び出すことができます。 Python のモデルとスクリプトでは、単純なストアド プロシージャを使用してアプリケーションから呼び出すことのエンタープライズ レベルの展開を可能にするセキュリティで保護された、デュアル アーキテクチャでコードが実行されます。 SQL から Python プロセスと MPI リングの並列処理にデータをストリーミングでは、追加のパフォーマンスの向上を達成します。

T-SQL を使用することができます[PREDICT](../t-sql/queries/predict-transact-sql.md)関数を実行する[ネイティブ スコアリング](sql-native-scoring.md)以前指定したバイナリ形式で保存されている事前トレーニング済みモデルにします。

### <a name="python-libraries"></a>Python ライブラリ

| [パッケージ] | 説明 |
|---------|-------------|
[**revoscalepy**](python/what-is-revoscalepy.md)| Python と同等の RevoScaleR します。 線形およびロジスティック回帰、デシジョン ツリー、ブースト ツリー、およびランダム フォレスト、並列処理がすべて、およびリモート計算コンテキストで実行中の対応の Python のモデルを作成することができます。 このパッケージは、複数のデータ ソースとリモート コンピューティング コンテキストの使用をサポートします。 データ サイエンティストまたは開発者は、データの探索や、データを移動せずにモデルを構築する、リモートの SQL Server での Python コードを実行できます。 |
|[**microsoftml**](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) |MicrosoftML の R パッケージの Python と等価です。 |

### <a name="r-libraries"></a>R ライブラリ

| [パッケージ] | 説明 |
|---------|-------------|
| [**MicrosoftML (R)**](using-the-microsoftml-package.md) | 最新の機械学習アルゴリズムとデータ変換の実行のサイズまたはリモートにできるコンテキストを計算します。 カスタマイズ可能なディープ ニューラル ネットワーク、高速なデシジョン ツリーとデシジョン フォレスト、線形回帰、およびロジスティック回帰アルゴリズムが含まれます。  |
| [**R パッケージの管理**](r/install-additional-r-packages-on-sql-server.md) | このリリースでは、次の点で強化されていますデータベースのパッケージの管理と、パッケージをインストールするアクセス許可を割り当てる DBA のためのロールを[CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) dba がないパッケージの管理には、t-sql ステートメント。R、および豊富な一連の R 関数を知らなくても[RevoScaleR](r/use-revoscaler-to-manage-r-packages.md)ユーザーによって所有されているため、インストール、削除、またはパッケージをリストします。 |

### <a name="pre-trained-models"></a>トレーニング済みモデル

[**事前トレーニング済みモデル**](install/sql-pretrained-models-install.md) Python と R. は、画像認識と正、負のセンチメント分析、これらのモデルを使用して、独自のデータで予測を生成するを利用します。 


## <a name="new-in-sql-server-2016"></a>SQL Server 2016 の新機能

学習の機能を使用して SQL Server にこのリリースに導入されたマシン**SQL Server 2016 R Services**、データベース エンジンのインスタンス内の常駐のデータの処理 R スクリプトのためのデータベース内分析エンジン。

さらに、 **SQL Server 2016 R Server (スタンドアロン)** Windows サーバー上の R Server をインストールする方法としてリリースされました。 最初に、SQL Server セットアップでは、R Server for Windows をインストールする唯一の方法が用意されています。 以降のリリースの Windows での R Server を望むデータ サイエンティストと開発者は同じ目標を達成するために別のスタンドアロン インストーラーを使用できます。 SQL Server のスタンドアロン サーバーは機能的には、スタンドアロンのサーバー製品[Microsoft R Server の用 Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)します。

| リリース |機能更新プログラム |
|---------|----------------|
| CU の追加 | [**リアルタイム スコアリング**](real-time-scoring.md) 、最適化されたバイナリ形式で格納されているモデルを読み取るし、R ランタイムを呼び出さずに予測を生成するネイティブの C++ ライブラリに依存しています。 これにより、スコア付けの操作をはるかに高速です。 リアルタイム スコアリングでは、ストアド プロシージャを実行または R コードからリアルタイムのスコアリングを実行できます。 リアルタイム スコアリングの最新リリースにアップグレードするインスタンスの場合は SQL Server 2016 の場合に使用可能なも[!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]します。 |
| 最初のリリース | [**データベース内分析用の R 統合**](r/sql-server-r-services.md)します。 <br/><br/> 呼び出し元の R 用の R パッケージは、T-SQL では、その逆に機能します。 RevoScaleR 関数は、調整のコンポーネント部分にデータをまとめることによって規模での R 分析を提供し、管理分散処理、結果を集計します。 SQL Server 2016 R Services (In-database)、RevoScaleR エンジンは、データと同じ処理コンテキストでまとめて分析がかかったり、データベース エンジン インスタンスと統合されます。 <br/><br/>T-SQL と R の統合を通じて[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)します。 このストアド プロシージャを使用して任意の R コードを呼び出すことができます。 このセキュリティで保護されたインフラストラクチャには、Rn モデルと単純なストアド プロシージャを使用して、アプリケーションから呼び出すことができるスクリプトのエンタープライズ レベルの展開ができます。 SQL から R プロセスと MPI リングの並列処理にデータをストリーミングでは、追加のパフォーマンスの向上を達成します。 <br/><br/>T-SQL を使用することができます[PREDICT](../t-sql/queries/predict-transact-sql.md)関数を実行する[ネイティブ スコアリング](sql-native-scoring.md)以前指定したバイナリ形式で保存されている事前トレーニング済みモデルにします。|

## <a name="linux-support-roadmap"></a>Linux サポートのロードマップ

データベースを使用して R または Python での machine learning が SQL Server on Linux で現在サポートされていません。 今後のリリースでアナウンスを探します。

ただし、Linux を実行できます[ネイティブ スコアリング](sql-native-scoring.md)T-SQL での予測関数を使用します。 ネイティブ スコアリングでは、呼び出しまたはも、R ランタイムを必要とすることがなく、非常に高速の事前トレーニング済みのモデルからスコア付けすることができます。 これは、Linux に SQL Server を使用するには、クライアント アプリケーション サービスを提供する非常に高速の予測を生成することを意味します。

<a name="azure-sql-database-roadmap"></a>

## <a name="azure-sql-database-roadmap"></a>Azure SQL Database のロードマップ

Azure SQL Database での R の制限付きサポートがある: 米国中西部、Premium レベルで作成されたサービス内でのみ使用できます。 展開されたカバレッジ、Python のサポートを含む将来のリリースで実行する可能性があります。 ただし、リリースされる予定日がこの時点でしません。  

## <a name="next-steps"></a>次の手順

+ [SQL Server 2017 Machine Learning Services (In-database) をインストールします。](install/sql-machine-learning-services-windows-install.md)
+ [Machine learning のチュートリアルとサンプル](tutorials/machine-learning-services-tutorials.md)
