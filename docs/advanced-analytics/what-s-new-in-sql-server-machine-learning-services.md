---
title: SQL Server Machine Learning Services の新機能 - |Microsoft Docs
description: 新しい機能のお知らせの各リリースの SQL Server 2016 R Services、R Server、SQL Server 2017 Machine Learning サービス。
ms.date: 02/28/2019
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 64e98073dabd490965fb5d582102a6eb962c5a13
ms.sourcegitcommit: 11ab8a241a6d884b113b3cf475b2b9ed61ff00e3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/18/2019
ms.locfileid: "58161830"
---
# <a name="whats-new-in-sql-server-machine-learning-services"></a>SQL Server Machine Learning Services の新機能新機能

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

機械学習機能は、展開、拡張、およびデータ プラットフォーム、高度な分析は、データ サイエンスとの統合を深めるに伴い、各リリースの SQL Server に追加されます。 

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2019-preview"></a>SQL Server 2019 プレビューの新機能

このリリースでは、SQL Server で R と Python の machine learning 操作の要求の多い機能を追加します。 このリリースの機能のすべての詳細については、次を参照してください。[で SQL Server 2019 新](../sql-server/what-s-new-in-sql-server-ver15.md)と[Release Notes for SQL Server 2019](../sql-server/sql-server-ver15-release-notes.md)します。

| リリース | 機能更新プログラム |
|---------|----------------|
| CTP 2.3 | サポートする新しい[Java データ型](java/java-sql-datatypes.md)します。 |
| | Windows の場合のみ、上の Java コードを外部ライブラリを使用して、アクセスできる、[外部ライブラリの作成 (TRANSACT-SQL)](../t-sql/statements/create-external-library-transact-sql.md)ステートメント。 同等の機能は今後の CTP での Linux で利用可能になります。 詳細情報:[SQL Server から Java を呼び出す方法](java/howto-call-java-from-sql.md)します。 |
| | Windows の場合のみでの Python コードを外部ライブラリを使用して、アクセスできる、[外部ライブラリの作成 (TRANSACT-SQL)](../t-sql/statements/create-external-library-transact-sql.md)ステートメント。 同等の機能は今後の CTP での Linux で利用可能になります。 |
| CTP 2.2 | 変更はありません。 |
| CTP 2.1 | 変更はありません。 |
| CTP 2.0 | R と Python の機械学習用の Linux プラットフォームのサポート。 概要[インストール SQL Server Machine Learning Services on Linux](../linux/sql-server-linux-setup-machine-learning.md)します。 |
|   | [Java 言語の拡張機能](java/extension-java.md)Windows と Linux の両方では、SQL Server 2019 プレビューの新機能です。 できるコードのコンパイル済みの Java 利用できるようにする SQL Server アクセス許可の割り当てをパスを設定します。 SQL Server のアクセス権を持つクライアント アプリはデータを使用でき、コードを呼び出すことによって実行[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)、SQL Server で R と Python の統合に使用する同じ手順です。 | 
|  | [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)簡単にパーティション分割されたデータから複数のモデルを生成するための 2 つの新しいパラメーターが導入されています。 このチュートリアルで詳しく[を R でのパーティションに基づくモデルを作成する](tutorials/r-tutorial-create-models-per-partition.md)します。 |
|   | Windows と Linux、SQL Server スタート パッド サービスがすべてのノードで開始と仮定した場合に、フェールオーバー クラスターのサポートはサポートされています。 詳細については、次を参照してください。 [SQL Server フェールオーバー クラスター インストール](../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)します。 |

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="new-in-sql-server-2017"></a>SQL Server 2017 の新機能

このリリースで追加[Python のサポートと業界最先端の機械学習アルゴリズム](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)します。 新しいスコープを反映するように名前変更、SQL Server 2017 のマークの導入に伴い[SQL Server Machine Learning サービス (In-database)](what-is-sql-server-machine-learning.md)Python と R. の両方の言語サポート 

機能のお知らせすべて時に、次を参照してください。 [SQL Server 2017 の新](../sql-server/what-s-new-in-sql-server-2017.md)します。

### <a name="r-enhancements"></a>R の機能強化

SQL Server 2017 Machine Learning Services の R コンポーネントには、基本の R、RevoScaler、およびその他のパッケージの更新バージョンでの SQL Server 2016 R Services では、次世代です。

R 用の新しい機能が含まれます[**パッケージ管理**](r/install-additional-r-packages-on-sql-server.md)、次の点で。 

+ データベース ロールは、パッケージの管理、およびパッケージのインストールのアクセス許可を割り当て、Dba を支援します。
+ [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)により Dba は、使い慣れた T-SQL 言語でパッケージを管理します。
+ [RevoScaleR](r/use-revoscaler-to-manage-r-packages.md)関数は、インストール、削除、またはパッケージの一覧は、ユーザーが所有するを支援します。 詳細については、次を参照してください。 [RevoScaleR 関数を使用して、見つからないか、R をインストールする方法は、SQL Server にパッケージ](r/use-revoscaler-to-manage-r-packages.md)します。

### <a name="r-libraries"></a>R ライブラリ

| [パッケージ] | 説明 |
|---------|-------------|
| [**MicrosoftML**](r/ref-r-microsoftml.md) | このリリースで MicrosoftML 前の SQL Server 2016 R Services で必要なアップグレード手順を排除することに既定の R インストールで含まれます。 MicrosoftML は、最新の状態の機械学習アルゴリズムとスケールまたはリモート計算コンテキストで実行できるデータの変換を提供します。 カスタマイズ可能なディープ ニューラル ネットワーク、高速なデシジョン ツリーとデシジョン フォレスト、線形回帰、およびロジスティック回帰アルゴリズムが含まれます。  |

### <a name="python-integration-for-in-database-analytics"></a>データベース内分析用の Python 統合

Python は優れた柔軟性と、さまざまな機械学習タスクのための電力を提供する言語です。 Python 用のオープン ソース ライブラリには、カスタマイズ可能なニューラル ネットワークでは、いくつかのプラットフォームと自然言語処理の人気のあるライブラリが含まれます。 ここで、この広く使用されている言語は、SQL Server 2017 の Machine Learning でサポートされます。

Python は、データベース エンジンと統合されているので、データの近くで分析し、コストとデータの移動に関連付けられているセキュリティ上のリスクを排除できます。 Visual Studio などのツールを使用して Python に基づく機械学習ソリューションを展開することができます。 運用アプリケーションが、モデルの予測を取得または SQL Server のデータを使用して、Python 3.5 ランタイムからビジュアル メソッドにアクセスします。

T-SQL と Python の統合はによってサポート、 [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)システム ストアド プロシージャ。 このストアド プロシージャを使用してすべての Python コードを呼び出すことができます。 Python のモデルとスクリプトでは、単純なストアド プロシージャを使用してアプリケーションから呼び出すことのエンタープライズ レベルの展開を可能にするセキュリティで保護された、デュアル アーキテクチャでコードが実行されます。 SQL から Python プロセスと MPI リングの並列処理にデータをストリーミングでは、追加のパフォーマンスの向上を達成します。

T-SQL を使用することができます[PREDICT](../t-sql/queries/predict-transact-sql.md)関数を実行する[ネイティブ スコアリング](sql-native-scoring.md)以前指定したバイナリ形式で保存されている事前トレーニング済みモデルにします。

### <a name="python-libraries"></a>Python ライブラリ

| [パッケージ] | 説明 |
|---------|-------------|
|[**revoscalepy**](python/ref-py-revoscalepy.md)| Python と同等の RevoScaleR します。 線形およびロジスティック回帰、デシジョン ツリー、ブースト ツリー、およびランダム フォレスト、並列処理がすべて、およびリモート計算コンテキストで実行中の対応の Python のモデルを作成することができます。 このパッケージは、複数のデータ ソースとリモート コンピューティング コンテキストの使用をサポートします。 データ サイエンティストまたは開発者は、データの探索や、データを移動せずにモデルを構築する、リモートの SQL Server での Python コードを実行できます。 |
|[**microsoftml**](python/ref-py-microsoftml.md) |MicrosoftML の R パッケージの Python と等価です。 |

### <a name="pre-trained-models"></a>トレーニング済みモデル

[**事前トレーニング済みモデル**](install/sql-pretrained-models-install.md) Python と R. は、画像認識と正、負のセンチメント分析、これらのモデルを使用して、独自のデータで予測を生成するを利用します。 

### <a name="standalone-server-as-a-shared-feature-in-sql-server-setup"></a>SQL Server セットアップで、共有機能として、スタンドアロン サーバー

このリリースでも追加[SQL Server Machine Learning Server (スタンドアロン)](r/r-server-standalone.md)R と Python の統計および予測分析をサポートしている、完全に独立したデータ サイエンス サーバー。 R のサービスと同様、このサーバーは、SQL Server 2016 R Server (スタンドアロン) の次のバージョン。 スタンドアロン サーバーで、配布でき、SQL Server の依存関係のない R または Python のソリューションをスケールできます。
::: moniker-end

## <a name="new-in-sql-server-2016"></a>SQL Server 2016 の新機能

学習の機能を使用して SQL Server にこのリリースに導入されたマシン**SQL Server 2016 R Services**、データベース エンジンのインスタンス内の常駐のデータの処理 R スクリプトのためのデータベース内分析エンジン。

さらに、 **SQL Server 2016 R Server (スタンドアロン)** Windows サーバー上の R Server をインストールする方法としてリリースされました。 最初に、SQL Server セットアップでは、R Server for Windows をインストールする唯一の方法が用意されています。 以降のリリースの Windows での R Server を望むデータ サイエンティストと開発者は同じ目標を達成するために別のスタンドアロン インストーラーを使用できます。 SQL Server のスタンドアロン サーバーは機能的には、スタンドアロンのサーバー製品[Microsoft R Server の用 Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)します。

機能のお知らせすべて時に、次を参照してください。 [SQL Server 2016 の新](../sql-server/what-s-new-in-sql-server-2016.md)します。

| リリース |機能更新プログラム |
|---------|----------------|
| CU の追加 | [**リアルタイム スコアリング**](real-time-scoring.md) 、最適化されたバイナリ形式で格納されているモデルを読み取るし、R ランタイムを呼び出さずに予測を生成するネイティブの C++ ライブラリに依存しています。 これにより、スコア付けの操作をはるかに高速です。 リアルタイム スコアリングでは、ストアド プロシージャを実行または R コードからリアルタイムのスコアリングを実行できます。 リアルタイム スコアリングの最新リリースにアップグレードするインスタンスの場合は SQL Server 2016 の場合に使用可能なも[!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]します。 |
| 最初のリリース | [**データベース内分析用の R 統合**](r/sql-server-r-services.md)します。 <br/><br/> 呼び出し元の R 用の R パッケージは、T-SQL では、その逆に機能します。 RevoScaleR 関数は、調整のコンポーネント部分にデータをまとめることによって規模での R 分析を提供し、管理分散処理、結果を集計します。 SQL Server 2016 R Services (In-database)、RevoScaleR エンジンは、データと同じ処理コンテキストでまとめて分析がかかったり、データベース エンジン インスタンスと統合されます。 <br/><br/>T-SQL と R の統合を通じて[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)します。 このストアド プロシージャを使用して任意の R コードを呼び出すことができます。 このセキュリティで保護されたインフラストラクチャには、Rn モデルと単純なストアド プロシージャを使用して、アプリケーションから呼び出すことができるスクリプトのエンタープライズ レベルの展開ができます。 SQL から R プロセスと MPI リングの並列処理にデータをストリーミングでは、追加のパフォーマンスの向上を達成します。 <br/><br/>T-SQL を使用することができます[PREDICT](../t-sql/queries/predict-transact-sql.md)関数を実行する[ネイティブ スコアリング](sql-native-scoring.md)以前指定したバイナリ形式で保存されている事前トレーニング済みモデルにします。|

## <a name="linux-support-roadmap"></a>Linux サポートのロードマップ

SQL Server 2019 CTP 2.3 は、機械学習、データベース エンジンのインスタンスを使用してパッケージをインストールするときに、R、Python、および Java の Linux サポートを追加します。 詳細については、次を参照してください。[インストール SQL Server Machine Learning Services on Linux](../linux/sql-server-linux-setup-machine-learning.md)します。

Linux では、SQL Server 2017 が R または Python の統合が使用できます[ネイティブ スコアリング](sql-native-scoring.md)on Linux でその機能は、T-SQL で使用できるため、 [PREDICT](../t-sql/queries/predict-transact-sql.md)、on Linux を実行します。 ネイティブ スコアリングを使用しなくても呼び出すことも、R ランタイムから事前トレーニング済みモデルでは、高パフォーマンスのスコア付けできます。

<a name="azure-sql-database-roadmap"></a>

## <a name="machine-learning-services-in-azure-sql-database"></a>Machine Learning で Azure SQL Database サービス

(R) を使用した Azure SQL Database での machine Learning サービスはパブリック プレビュー段階です。 詳細については、次を参照してください。[クイック スタート。Azure SQL database (preview) (R) を使用した Machine Learning サービスを使用して](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-r)します。

## <a name="next-steps"></a>次のステップ

+ [SQL Server 2017 Machine Learning Services (In-database) をインストールします。](install/sql-machine-learning-services-windows-install.md)
+ [Machine learning のチュートリアルとサンプル](tutorials/machine-learning-services-tutorials.md)
