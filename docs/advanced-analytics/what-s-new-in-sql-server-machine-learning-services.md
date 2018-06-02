---
title: どのような&#39;s SQL Server の Machine Learning のサービスの新機能 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 092216f7bc1142125156b3658f035154d809c2e9
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34586074"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>SQL Server の Machine Learning のサービスの新機能 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

マシン学習機能は、展開、拡張、およびデータ プラットフォームおよびデータ サイエンス、分析、間の統合を深めるに伴いに SQL Server を各リリースで追加され、教師あり学習データを実装する場合です。 

## <a name="new-in-sql-server-2017"></a>SQL Server 2017 年 1 の新機能

このリリースには、Python をサポートおよび業界をリードする機械学習アルゴリズムが追加されました。 新しいスコープを反映するように名前の変更、SQL Server 2017 マークの導入**SQL Server マシン ラーニング Services (In-database)** Python と R. の両方の言語サポート 

また、このリリース**SQL Server マシン ラーニング サーバー (スタンドアロン)**、完全に独立した、SQL Server の専用のシステム上で実行する R および Python のワークロードのためです。 スタンドアロン サーバーでは、配布し、SQL Server を使用せずに R または Python のソリューションをスケールします。

| リリース | フィーチャーの更新 |
|---------|----------------|
| CU 6 | バグの修正とパッケージの更新がないお知らせを新機能です。 修正プログラムは、事前トレーニング済みモデルが存在しない場合 DateTime データ型のサポートを SPEES クエリに、Python と microsoftml で改善されたエラー メッセージの含めます。 |
| CU 5 | バグの修正とパッケージの更新がないお知らせを新機能です。 修正プログラムには、revoscalepy、RxExec と rx_exec 関数、および警告メッセージにリビジョンをループバックに接続を修正して rxInstallPackages の長いパスに関連するエラーを修正の関数と変数を変換するの機能強化が含まれます。 |
| CU 4 | バグの修正とパッケージの更新がないお知らせを新機能です。 |
| CU 3 | Python revoscalepy でのシリアル化のモデルを使用して、 [rx_serialize_model 関数](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model)です。<br/><br/>[ネイティブ スコアリング](sql-native-scoring.md)の強化に加えて[リアルタイム スコアリング](real-time-scoring.md)です。 データベース内のスコアリング、スループットは 100万行あたり 2 番目の R モデルを使用します。 この更新により、リアルタイムのスコアリングとネイティブ スコアリングは、単一行およびバッチ スコアリングでパフォーマンスの向上を提供します。 使用してスコア付けネイティブ高速スコアリングのための T-SQL 関数は Linux 上であっても、SQL Server の任意のエディションで実行できます。 関数には、R または追加の構成のインストールは不要です。 つまり、他の場所で、モデルのトレーニング、SQL Server に保存および R. を呼び出さないでスコアリングを実行し、スコアリング方法の詳細については、次を参照してください。[リアルタイム スコアリングまたはネイティブ スコアリングを実行する方法](r/how-to-do-realtime-scoring.md)です。 |
| CU 2 | バグの修正とパッケージの更新がないお知らせを新機能です。 |
| CU 1 | Revoscalepy で追加、SQL Server、ようにデータ ソースからスキーマ情報を返す rx_create_col_info [rxCreateColInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcreatecolinfo)対象です。 <br/><br/>機能強化[rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec)を使用した並列のシナリオをサポートするために、`RxLocalParallel`コンテキストを計算します。|
| 最初のリリース |[**データベース内の分析の Python の統合**](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/) <br/><br/>[Revoscalepy](python/what-is-revoscalepy.md)パッケージは、RevoScaleR の Python と同等です。 線形とロジスティック回帰、デシジョン ツリー、ブースト ツリー、およびランダム フォレスト、すべて並列処理、およびリモート計算コンテキストで実行中の対応の Python モデルを作成することができます。 このパッケージには、複数のデータ ソースとリモート計算コンテキストの使用がサポートしています。 データ科学者や開発者は、データを参照するか、データを移動せずにモデルを構築する、リモートの SQL Server での Python コードを実行できます。 <br/><br/>[Microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)パッケージが MicrosoftML R パッケージの Python と同等です。<br/><br/>T-SQL と Python の統合を通じて[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)です。 このストアド プロシージャを使用してすべての Python コードを呼び出すことができます。 このセキュリティで保護されたインフラストラクチャでは、Python モデルと単純なストアド プロシージャを使用して、アプリケーションから呼び出すことができるスクリプトのエンタープライズ レベルの展開できるようにします。 追加のパフォーマンスが向上によって SQL から Python プロセスと MPI リングの並列化にデータをストリーミングします。 <br/><br/>T-SQL ステートメントを使用することができます[PREDICT](../t-sql/queries/predict-transact-sql.md)を実行する関数[ネイティブ スコアリング](sql-native-scoring.md)以前指定したバイナリ形式で保存されている事前トレーニング済みモデルにします。|
| 最初のリリース | [**MicrosoftML (R)** ](using-the-microsoftml-package.md)は最新の機械学習のスケールまたは実行のリモート計算コンテキストは、アルゴリズムとデータの変換が含まれています。 深層ニューラル ネットワークのカスタマイズ可能な高速なデシジョン ツリーとデシジョン フォレスト、線形回帰、およびロジスティック回帰アルゴリズムが含まれます。 |
| 最初のリリース | [**事前トレーニング済みモデル**](r/install-pretrained-models-sql-server.md)画像認識と正、負のセンチメント分析のためです。 これらのモデルを使用すると、独自のデータでの予測を生成できます。 |
| 最初のリリース | [**R パッケージの管理**](r/install-additional-r-packages-on-sql-server.md)、次の点を含む: データベースの DBA は、パッケージの管理し、パッケージをインストールするアクセス許可を割り当てるためのロールを[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)する t-sql ステートメントヘルプの Dba は、R を知らなくてもパッケージを管理および R の豊富な一連の関数で[RevoScaleR](r/use-revoscaler-to-manage-r-packages.md)のため、インストール、削除、またはパッケージ一覧は、ユーザーが所有します。 |
| 最初のリリース | [**Mrsdeploy を操作運用**](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)展開および web サービスとしての R スクリプトをホストしているのためです。 R スクリプトのみ (Python 該当するショートカットはありません) に適用されます。 他の SQL Server 操作とリソースの競合を回避する (スタンドアロン) のサーバー オプションの目的としています。 |


## <a name="new-in-sql-server-2016"></a>SQL Server 2016 の新機能

このリリースが導入された機械を介して SQL Server に機能を学習**SQL Server 2016 の R Services**、データベース エンジンのインスタンス内の常駐のデータの処理 R スクリプトのデータベース内分析エンジンです。

さらに、 **SQL Server 2016 R Server (スタンドアロン)** R Server、Windows server をインストールする方法としてリリースされました。 最初に、SQL Server セットアップでは、R Server for Windows をインストールする唯一の方法が用意されています。 今後のリリースで開発者や R Server on Windows を抑えようとしたデータ サイエンティストは、同じ目標を実現するために別のスタンドアロン インストーラーを使用できます。 SQL Server のスタンドアロン サーバーは機能的には、スタンドアロンのサーバー製品[Microsoft R Server の for Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)です。

| リリース |フィーチャーの更新 |
|---------|----------------|
| CU の追加 | [**リアルタイムのスコアリング**](real-time-scoring.md)最適化されたバイナリ形式で格納されているモデルを読み込むし、R ランタイムを呼び出さずに予測を生成するネイティブの C++ ライブラリに依存しています。 これにより、スコア付けの操作をはるかに高速です。 リアルタイムのスコアリングでストアド プロシージャを実行したり、リアルタイムの R コードのスコア付けを実行できます。 インスタンスが、最新のリリースにアップグレードした場合は SQL Server 2016 用に使用可能なリアルタイム スコアリングも[!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]します。 |
| 最初のリリース | [**データベース内の分析のための R 統合**](r/sql-server-r-services.md)です。 <br/><br/> 呼び出し元の R の R パッケージは、T-SQL では、その逆に機能します。 RevoScaleR 関数は、調整、コンポーネント部分にデータをチャンクでスケールで R 分析を提供し、処理、および結果を集計する分散を管理します。 SQL Server 2016 R Services (In-database)、RevoScaleR エンジンは、データと同じ処理コンテキストでまとめて分析がかかったり、データベース エンジン インスタンスと統合されています。 <br/><br/>経由の T-SQL と R 統合[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)です。 このストアド プロシージャを使用して任意の R コードを呼び出すことができます。 このセキュリティで保護されたインフラストラクチャ Rn モデルと単純なストアド プロシージャを使用して、アプリケーションから呼び出すことができるスクリプトのエンタープライズ レベルの展開を有効にします。 その他のパフォーマンスが向上 SQL からのストリーミングのデータを R のプロセスと MPI リングの並列化します。 <br/><br/>T-SQL ステートメントを使用することができます[PREDICT](../t-sql/queries/predict-transact-sql.md)を実行する関数[ネイティブ スコアリング](sql-native-scoring.md)以前指定したバイナリ形式で保存されている事前トレーニング済みモデルにします。|

## <a name="linux-support-roadmap"></a>Linux サポートのロードマップ

データベースを使用して R または Python での機械学習は SQL Server on Linux で現在サポートされていません。 以降のリリースのお知らせを参照してください。

ただし、Linux で行うことができます[ネイティブ スコアリング](sql-native-scoring.md)T-SQL で予測関数を使用します。 ネイティブのスコア付けするには、設定しなくても呼び出すことも、R ランタイム、非常に高速で、事前トレーニング済みモデルからスコア付けすることができます。 これは、Linux に SQL Server を使用するには非常に高速で、クライアント アプリケーションを提供する予測を生成することを意味します。

<a name="azure-sql-database-roadmap"></a>

## <a name="azure-sql-database-roadmap"></a>Azure SQL データベースのロードマップ

Azure SQL データベースでの R のサポートが制限されて: Premium 層で作成されたサービスで、西中央アメリカでのみ使用できます。 Python のサポートなど、展開されたカバレッジは、将来のリリースで従う可能性があります。 ただしは射影されたリリース日この時点で、  

## <a name="next-steps"></a>次のステップ

+ [SQL Server 2017 Machine Learning Services (In-database) のインストールします。](install/sql-machine-learning-services-windows-install.md)
+ [Machine learning のチュートリアルおよびサンプル](tutorials/machine-learning-services-tutorials.md)
