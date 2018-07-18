---
title: SQL Server Machine Learning Services での R コードを運用化 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 41da5cfe2e545bdcbc59f8d557afc599177c9d5e
ms.sourcegitcommit: f083867f97bb740caa211ca37cb046641172b8c0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38952465"
---
# <a name="operationalize-r-code-machine-learning-services"></a>R コード (Machine Learning サービス) を操作します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

データベース開発者は、企業全体で共有できるように、多数のテクノロジを統合し、結果をまとめる任務を負っています。 データベース開発者は、ソリューションを設計およびデプロイには、アプリケーション開発者は、SQL 開発者、およびデータ サイエンティストで動作します。

この記事では、SQL Server を使用して R コードの運用時に考慮する、データベース開発者の重要な点をまとめます。

## <a name="get-started-with-r-code-in-sql-server"></a>SQL Server での R コードを概要します。

これまでは、パフォーマンスとの統合をサポートするために広範な再コーディングの機械学習ソリューションの統合を意味します。 ただし、R と Python のコードを運用環境には、コードは、SQL Server で実行できるため、SQL Server Machine Learning のサービスではるかに簡単に移動を使用して呼び出すストアド プロシージャ。 引き続きの使い慣れたツールを使用することができ、R 開発環境をインストールする必要はありません。 

基本的な構文の詳細についてを参照してください。

+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)
+ [SQL での R コードを使用して](../../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)します。

ストアド プロシージャを使用して、運用環境に R コードをデプロイする方法の例を参照してください。

+ [データベース内分析 SQL 開発者向けの](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)します。

## <a name="optimize-your-r-code"></a>R コードを最適化します。

もちろん、SQL で R コードを変換することがいくつかの最適化は、R または Python のコードで事前に行われる場合に簡単です。 問題が発生するデータ型を回避する、不要なデータの変換を回避して簡単にパラメーター化できる 1 つの関数呼び出しとして R コードの書き直しが含まれます。 詳細については、以下をご覧ください。

+ [R ライブラリとデータ型](r-libraries-and-data-types.md)

+ [R Services で使用するための R コードの変換](converting-r-code-for-use-in-sql-server.md)

+ [Sqlrutils を使用してストアド プロシージャを R を生成します。](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)

## <a name="integrate-r-and-python-with-applications"></a>R および Python アプリケーションを統合します。

Machine Learning サービスを開始するには、ストアド プロシージャから、ためには、T-SQL ステートメントを送信し、結果を処理する任意のアプリケーションから R または Python スクリプトを実行できます。

たとえば、Integration Services で T-SQL 実行タスクを使用して、またはストアド プロシージャを実行できる他のジョブ スケジューラを使用して、スケジュールに従ってモデルを再トレーニング可能性があります。

スコア付けは、自動、または外部アプリケーションから開始できるは簡単に重要なタスクです。 モデルの事前トレーニング R、Python またはストアド プロシージャを使用し、テーブルにバイナリ形式でモデルを保存します。 次に、これらのオプションのいずれかを T-SQL からスコア付けを使用して、ストアド プロシージャの呼び出しの一部として変数に、モデルを読み込むことができます。

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

オープン ソース R 言語は制限があることをわかっていますが、RevoScaleR パッケージ Api 処理大規模なデータセットに対してでき、マルチ スレッド、マルチコア、マルチ プロセスのデータベース内計算のメリットです。

R ソリューションでは、複雑な集計を使用または大規模なデータセットでは、SQL Server の非常に効率的なインメモリ集計と列ストア インデックスを活用し、R コード、統計の計算結果を処理し、スコア付けします。

SQL Server Machine Learning でのパフォーマンスを向上させる方法の詳細についてを参照してください。

+ [SQL Server R Services のパフォーマンス チューニング](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [パフォーマンスの最適化に関するヒントとテクニック](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>他のプラットフォーム用の R コードを改変または計算コンテキスト

に対して実行した同じ R コード[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データは、Hadoop などの他のデータ ソースに対して使用できるし、他の計算コンテキスト。

Microsoft R によってサポートされるプラットフォームの詳細についてを参照してください。

+ [Microsoft R の概要](https://docs.microsoft.com/r-server/)

+ [RevoScaleR を調査します。](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

大規模なデータまたは複数のプラットフォームで実行する、Microsoft R ソリューションを最適化する方法の詳細についてを参照してください。

+ [チャンク アルゴリズムを記述します。](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [R でのビッグ データ コンピューティング](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [独自の並列アルゴリズムを開発します。](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

