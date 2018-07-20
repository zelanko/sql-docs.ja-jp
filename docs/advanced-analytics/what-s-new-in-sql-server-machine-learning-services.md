---
title: どのような&#39;s の SQL Server Machine Learning Services の新機能 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bf56d52823727609d713639d534e277be57caaef
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174809"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>SQL Server Machine Learning Services の新機能新機能 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

機械学習機能は、展開、拡張、およびデータ プラットフォームとデータ サイエンス、分析、統合を深めるに伴いに SQL Server に各リリースで追加され、教師あり学習のデータを実装します。 

## <a name="new-in-sql-server-2017"></a>SQL Server 2017 の新機能

このリリースでは、Python のサポートと業界最先端の機械学習アルゴリズムを追加します。 新しいスコープを反映するように名前変更、SQL Server 2017 のマークの導入に伴い**SQL Server Machine Learning サービス (In-database)** Python と R. の両方の言語サポート 

また、このリリース**SQL Server Machine Learning Server (スタンドアロン)** R と Python のワークロード専用のシステム上で実行する SQL Server の完全に独立しました。 スタンドアロン サーバーで、配布でき、SQL Server を使用せず、R または Python のソリューションをスケールできます。

| リリース | 機能更新プログラム |
|---------|----------------|
| CU 6 | バグの修正とパッケージのリフレッシュは新機能のお知らせの。 修正は、事前トレーニング済みモデルが不足している場合に DateTime データ型のサポートを SPEES クエリに、Python と microsoftml の強化されたエラー メッセージを含めます。 |
| CU 5 | バグの修正とパッケージのリフレッシュは新機能のお知らせの。 修正プログラムには、RxExec rx_exec 関数、および改訂版の警告メッセージをループバック接続を修正 rxInstallPackages で時間の長いパスに関連するエラーを修正 revoscalepy の関数と変数を変換する機能強化が含まれます。 |
| CU 4 | バグの修正とパッケージのリフレッシュは新機能のお知らせの。 |
| CU 3 | Python モデルの revoscalepy でのシリアル化を使用して、 [rx_serialize_model 関数](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model)します。<br/><br/>[ネイティブ スコアリング](sql-native-scoring.md)の機能強化と[リアルタイム スコアリング](real-time-scoring.md)します。 スループットはあたり 100万行をデータベースでのスコアリング、2 つ目の R モデルを使用します。 この更新により、リアルタイム スコアリングおよびネイティブ スコアリングは、単一行、バッチ スコアリングでパフォーマンスの向上を提供します。 ネイティブ スコアリングは高速なスコアリングのための T-SQL 関数は Linux 上であっても、SQL Server の任意のエディションで実行できます。 関数には、R または追加の構成のインストールは不要です。 つまり、他の場所でモデルをトレーニング、SQL Server に保存およびこれまで R. を呼び出さずにスコア付けを実行し、方法論をスコア付けの詳細については、次を参照してください。[リアルタイムのスコア付けまたはネイティブ スコアリングを実行する方法について](r/how-to-do-realtime-scoring.md)します。 |
| CU 2 | バグの修正とパッケージのリフレッシュは新機能のお知らせの。 |
| CU 1 | Revoscalepy での SQL Server データ、ように、ソースからスキーマ情報を返す rx_create_col_info を追加します[rxCreateColInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcreatecolinfo) r 向け。 <br/><br/>機能強化[rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec)を使用して並列のシナリオをサポートするために、`RxLocalParallel`コンピューティング コンテキスト。|
| 最初のリリース |[**データベース内分析用の Python 統合**](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/) <br/><br/>[Revoscalepy](python/what-is-revoscalepy.md)パッケージは、Python と同等の RevoScaleR します。 線形およびロジスティック回帰、デシジョン ツリー、ブースト ツリー、およびランダム フォレスト、並列処理がすべて、およびリモート計算コンテキストで実行中の対応の Python のモデルを作成することができます。 このパッケージは、複数のデータ ソースとリモート コンピューティング コンテキストの使用をサポートします。 データ サイエンティストまたは開発者は、データの探索や、データを移動せずにモデルを構築する、リモートの SQL Server での Python コードを実行できます。 <br/><br/>[Microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)パッケージは、Python と同等の MicrosoftML の R パッケージ。<br/><br/>T-SQL と Python の統合を通じて[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)します。 このストアド プロシージャを使用してすべての Python コードを呼び出すことができます。 このセキュリティで保護されたインフラストラクチャには、Python のモデルと単純なストアド プロシージャを使用して、アプリケーションから呼び出すことができるスクリプトのエンタープライズ レベルの展開ができます。 SQL から Python プロセスと MPI リングの並列処理にデータをストリーミングでは、追加のパフォーマンスの向上を達成します。 <br/><br/>T-SQL を使用することができます[PREDICT](../t-sql/queries/predict-transact-sql.md)関数を実行する[ネイティブ スコアリング](sql-native-scoring.md)以前指定したバイナリ形式で保存されている事前トレーニング済みモデルにします。|
| 最初のリリース | [**MicrosoftML (R)** ](using-the-microsoftml-package.md)スケールまたは実行でのリモート計算コンテキストは、アルゴリズムとデータの変換の学習最新の状態にはが含まれています。 カスタマイズ可能なディープ ニューラル ネットワーク、高速なデシジョン ツリーとデシジョン フォレスト、線形回帰、およびロジスティック回帰アルゴリズムが含まれます。 |
| 最初のリリース | [**事前トレーニング済みモデル**](install/sql-pretrained-models-install.md)画像認識と正、負のセンチメント分析のためです。 これらのモデルを使用すると、独自のデータで予測を生成します。 |
| 最初のリリース | [**R パッケージ管理**](r/install-additional-r-packages-on-sql-server.md)、次のハイライトを含む: データベースのパッケージの管理し、パッケージをインストールするアクセス許可を割り当てる DBA のためのロールを[CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)する t-sql ステートメントヘルプ Dba は、R を知らなくてもパッケージを管理し、豊富な一連の R 関数の[RevoScaleR](r/use-revoscaler-to-manage-r-packages.md)ユーザーによって所有されているため、インストール、削除、またはパッケージをリストします。 |
| 最初のリリース | [**Mrsdeploy 経由で運用化**](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)を展開すると、web サービスとしての R スクリプトをホストします。 R スクリプトのみ (Python 同等はありません) に適用されます。 他の SQL Server 操作とリソースの競合を回避するために、(スタンドアロン) のサーバー オプションの対象としています。 |


## <a name="new-in-sql-server-2016"></a>SQL Server 2016 の新機能

学習の機能を使用して SQL Server にこのリリースに導入されたマシン**SQL Server 2016 R Services**、データベース エンジンのインスタンス内の常駐のデータの処理 R スクリプトのためのデータベース内分析エンジン。

さらに、 **SQL Server 2016 R Server (スタンドアロン)** Windows サーバー上の R Server をインストールする方法としてリリースされました。 最初に、SQL Server セットアップでは、R Server for Windows をインストールする唯一の方法が用意されています。 以降のリリースの Windows での R Server を望むデータ サイエンティストと開発者は同じ目標を達成するために別のスタンドアロン インストーラーを使用できます。 SQL Server のスタンドアロン サーバーは機能的には、スタンドアロンのサーバー製品[Microsoft R Server の用 Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)します。

| リリース |機能更新プログラム |
|---------|----------------|
| CU の追加 | [**リアルタイム スコアリング**](real-time-scoring.md) 、最適化されたバイナリ形式で格納されているモデルを読み取るし、R ランタイムを呼び出さずに予測を生成するネイティブの C++ ライブラリに依存しています。 これにより、スコア付けの操作をはるかに高速です。 リアルタイムのスコアリング、ストアド プロシージャを実行またはリアルタイムの R コードからのスコア付けを実行できます。 リアルタイムのスコア付けが可能な SQL Server 2016 では、インスタンスの最新のリリースにアップグレードした場合は[!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]します。 |
| 最初のリリース | [**データベース内分析用の R 統合**](r/sql-server-r-services.md)します。 <br/><br/> 呼び出し元の R 用の R パッケージは、T-SQL では、その逆に機能します。 RevoScaleR 関数は、調整のコンポーネント部分にデータをまとめることによって規模での R 分析を提供し、管理分散処理、結果を集計します。 SQL Server 2016 R Services (In-database)、RevoScaleR エンジンは、データと同じ処理コンテキストでまとめて分析がかかったり、データベース エンジン インスタンスと統合されます。 <br/><br/>T-SQL と R の統合を通じて[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)します。 このストアド プロシージャを使用して任意の R コードを呼び出すことができます。 このセキュリティで保護されたインフラストラクチャには、Rn モデルと単純なストアド プロシージャを使用して、アプリケーションから呼び出すことができるスクリプトのエンタープライズ レベルの展開ができます。 SQL から R プロセスと MPI リングの並列処理にデータをストリーミングでは、追加のパフォーマンスの向上を達成します。 <br/><br/>T-SQL を使用することができます[PREDICT](../t-sql/queries/predict-transact-sql.md)関数を実行する[ネイティブ スコアリング](sql-native-scoring.md)以前指定したバイナリ形式で保存されている事前トレーニング済みモデルにします。|

## <a name="linux-support-roadmap"></a>Linux サポートのロードマップ

データベースを使用して R または Python での machine learning が SQL Server on Linux で現在サポートされていません。 今後のリリースでアナウンスを探します。

ただし、Linux を実行できます[ネイティブ スコアリング](sql-native-scoring.md)T-SQL での予測関数を使用します。 ネイティブ スコアリングでは、呼び出しまたはも、R ランタイムを必要とすることがなく、非常に高速の事前トレーニング済みのモデルからスコア付けすることができます。 これは、Linux に SQL Server を使用するには、クライアント アプリケーション サービスを提供する非常に高速の予測を生成することを意味します。

<a name="azure-sql-database-roadmap"></a>

## <a name="azure-sql-database-roadmap"></a>Azure SQL Database のロードマップ

Azure SQL Database での R の制限付きサポートがある: 米国中西部、Premium レベルで作成されたサービス内でのみ使用できます。 展開されたカバレッジ、Python のサポートを含む将来のリリースで実行する可能性があります。 ただし、リリースされる予定日がこの時点でしません。  

## <a name="next-steps"></a>次のステップ

+ [SQL Server 2017 Machine Learning Services (In-database) をインストールします。](install/sql-machine-learning-services-windows-install.md)
+ [Machine learning のチュートリアルとサンプル](tutorials/machine-learning-services-tutorials.md)
