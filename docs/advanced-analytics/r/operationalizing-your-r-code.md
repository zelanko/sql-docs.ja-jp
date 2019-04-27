---
title: ストアド プロシージャ - SQL Server Machine Learning Services を使用して R コードを運用化します。
description: SQL Server データベースへのアクセス権を持つ任意のクライアント アプリケーションで使用できるようにする SQL Server ストアド プロシージャで R 言語のコードを埋め込みます。
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/15/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 2d00e96162b492d28f0c0ec107612023c8e15e48
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642030"
---
# <a name="operationalize-r-code-using-stored-procedures-in-sql-server-machine-learning-services"></a>SQL Server Machine Learning Services でのストアド プロシージャを使用して R コードを運用化します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server Machine Learning Services での R と Python の機能を使用する場合、ソリューションを運用環境に移動するための最も一般的なアプローチは、ストアド プロシージャにコードを埋め込むことです。 この記事では、SQL Server を使用して R コードの運用時に考慮する SQL 開発者向けの重要な点をまとめます。

## <a name="deploy-production-ready-script-using-t-sql-and-stored-procedures"></a>T-SQL やストアド プロシージャを使用して実稼働可能なスクリプトをデプロイします。

これまでは、パフォーマンスとの統合をサポートするために広範な再コーディングのデータ サイエンス ソリューションの統合を意味します。 SQL Server Machine Learning Services では、R と Python のコードは、SQL Server で実行できるため、このタスクを簡略化し、ストアド プロシージャを使用して呼び出されます。 ストアド プロシージャにコードを埋め込むのしくみの詳細についてを参照してください。

+ [クイック スタート:SQL Server で R スクリプトの"hello world"](../../advanced-analytics/tutorials//quickstart-r-run-using-tsql.md)
+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

ストアド プロシージャを使用して R コードを運用環境にデプロイのより包括的な例をご覧[チュートリアル。SQL 開発者向けの R データの分析](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

## <a name="guidelines-for-optimizing-r-code-for-sql"></a>SQl の R コードを最適化するためのガイドライン

SQL で R コードの変換がいくつかの最適化は、R または Python のコードで事前に行われる場合に簡単です。 問題が発生するデータ型を回避する、不要なデータの変換を回避して簡単にパラメーター化できる 1 つの関数呼び出しとして R コードの書き直しが含まれます。 詳細については、以下をご覧ください。

+ [R ライブラリとデータ型](r-libraries-and-data-types.md)
+ [R Services で使用するための R コードの変換](converting-r-code-for-use-in-sql-server.md)
+ [Sqlrutils ヘルパー関数を使用します。](ref-r-sqlrutils.md)

## <a name="integrate-r-and-python-with-applications"></a>R および Python アプリケーションを統合します。

ストアド プロシージャから R または Python を実行できますが、ため、T-SQL ステートメントを送信し、結果を処理する任意のアプリケーションからスクリプトを実行することができます。 たとえば、スケジュールに従ってモデルを再トレーニングを使用して可能性があります、 [T-SQL 実行タスク](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task)Integration Services、またはストアド プロシージャを実行できる他のジョブ スケジューラを使用しています。

スコア付けは、自動、または外部アプリケーションから開始できるは簡単に重要なタスクです。 モデルをトレーニングする事前に、R、Python、またはストアド プロシージャを使用して、[バイナリ形式でモデルを保存](../tutorials/walkthrough-build-and-save-the-model.md)テーブルにします。 次に、これらのオプションのいずれかを T-SQL からスコア付けを使用して、ストアド プロシージャの呼び出しの一部として変数に、モデルを読み込むことができます。

+ [リアルタイム](../real-time-scoring.md)小さなバッチ用に最適化されたスコア付け、
+ 単一行のスコア付け、アプリケーションからの呼び出し
+ [ネイティブ スコアリング](../sql-native-scoring.md)を呼び出さずに R から SQL Server の高速のバッチ予測

このチュートリアルでは、バッチおよび単一行モードの両方のストアド プロシージャを使用してスコア付けの例を示します。

+ [エンド ツー エンドの SQL Server で R のデータ サイエンスのチュートリアル](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

アプリケーションでのスコア付けを統合する方法の例についてはこれらのソリューション テンプレートを参照してください。

+ [小売りの予測](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [不正行為の検出](https://github.com/Microsoft/r-server-fraud-detection)
+ [顧客のクラスタ リング](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

## <a name="boost-performance-and-scale"></a>パフォーマンスの向上とスケール

オープン ソース R 言語がわかっていますが、大きなデータ セットに関して制限事項、 [RevoScaleR パッケージ Api](ref-r-revoscaler.md)に含まれている SQL Server Machine Learning サービスは大規模なデータセットを処理でき、マルチ スレッドのメリット、マルチコア、マルチ プロセスのデータベースで計算します。

R ソリューションでは、複雑な集計を使用または大規模なデータセットでは、SQL Server の非常に効率的なインメモリ集計と列ストア インデックスを活用し、R コード、統計の計算結果を処理し、スコア付けします。

SQL Server Machine Learning でのパフォーマンスを向上させる方法の詳細についてを参照してください。

+ [SQL Server R Services のパフォーマンス チューニング](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [パフォーマンスの最適化に関するヒントとテクニック](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>他のプラットフォーム用の R コードを改変または計算コンテキスト

に対して実行した同じ R コード[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データは、使用する場合、HDFS 上の Spark などの他のデータ ソースに対して使用できます、[スタンドアロン サーバー オプション](../install/sql-machine-learning-standalone-windows-install.md)で SQL Server のセットアップまたは非 SQL ブランド付きの製品をインストールするときにMicrosoft Machine Learning Server (旧称**Microsoft R Server**)。

+ [Machine Learning Server ドキュメント](https://docs.microsoft.com/r-server/)

+ [RevoScaleR に R を調べる](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

+ [チャンク アルゴリズムを記述します。](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [R でのビッグ データ コンピューティング](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [独自の並列アルゴリズムを開発します。](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

