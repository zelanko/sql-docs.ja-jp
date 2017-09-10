---
title: "R コード (Machine Learning サービス) を使用できるように |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f15696b1-2479-4e5f-ac5e-4beaf958a043
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d858352ed7dc519dfde9f625ea24cea6a538be5b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="operationalize-r-code-machine-learning-services"></a>R コード (Machine Learning サービス) を使用できるように

データベース開発者は、企業全体で共有できるように、多数のテクノロジを統合し、結果をまとめる任務を負っています。 データベース開発者は、設計およびソリューションを展開するには、アプリケーション開発者、SQL 開発者、およびデータ サイエンティストで動作します。

この記事は、SQL Server を使用して R コードの運用時に考慮する、データベース開発者の重要な点をまとめたものです。

## <a name="get-started-with-r-code-in-sql-server"></a>SQL Server での R コードを概要します。

従来、マシン学習ソリューションの統合が意図したものでパフォーマンスとの統合をサポートするために広範な再コーディングします。 ただし、実稼働環境への R、Python コードが、SQL Server でコードを実行できるため、Microsoft Machine Learning サービスにはるかに簡単に移動を使用して呼び出すストアド プロシージャです。 使い慣れたツールを使用して続行でき、R 開発環境をインストールする必要はありません。 

基本的な構文の詳細についてを参照してください。

+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)
+ [SQL での R コードを使用して](../../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)です。

ストアド プロシージャを使用して、実稼働環境に R コードを配置する方法の例を参照してください。

+ [データベース内分析 SQL 開発者のため](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)です。

## <a name="optimize-your-r-code"></a>R コードを最適化します。

もちろん、SQL で R コードの変換は、最適化によっては、R、または Python コードで事前行われる場合は簡単です。 これらには、問題が発生するデータ型を回避し、不要なデータ変換を回避して、簡単にパラメーター化できる 1 つの関数の呼び出しと、R コードの書き直しが含まれます。 詳細については、以下をご覧ください。

+ [R ライブラリとデータ型](r-libraries-and-data-types.md)

+ [R Services で使用するための R コードの変換](converting-r-code-for-use-in-sql-server.md)

+ [Sqlrutils を使用してストアド プロシージャを生成する R](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)

## <a name="integrate-r-and-python-with-applications"></a>R と Python アプリケーションと統合します。

Machine Learning のサービスを開始するには、ストアド プロシージャから、ために、T-SQL ステートメントを送信し、結果を処理できるすべてのアプリケーションから R または Python スクリプトを実行できます。

など、Integration Services では、T-SQL 実行タスクを使用して、またはストアド プロシージャを実行できる別のジョブのスケジューラを使用して、スケジュールに基づいてモデルを再トレーニング可能性があります。

スコアリングは、簡単に自動化すると、または外部アプリケーションから起動できる重要なタスクです。 モデルのトレーニングをあらかじめ、R、Python またはストアド プロシージャを使用してテーブルにバイナリ形式でモデルを保存します。 次に、これらのオプションのいずれかの T-SQL をスコア付けを使用して、ストアド プロシージャの呼び出しの一部として変数に、モデルを読み込むことができます。

+ [リアルタイム](../real-time-scoring.md)小さなバッチ用に最適化された、スコア付け
+ 単一の行をアプリケーションから呼び出すことのスコア付け
+ [ネイティブ スコアリング](../sql-native-scoring.md)R を呼び出さずに SQL Server の高速バッチ予測

このチュートリアルでは、バッチおよび単一行モードの両方でストアド プロシージャを使用してスコア付けの例を示します。

+ [エンド ツー エンドの SQL Server で R のデータ サイエンスのチュートリアル](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

これらのソリューション テンプレートをアプリケーションでスコアリングを統合する方法の例についてを参照してください。

+ [小売予測](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [不正行為の検出](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/FraudDetection/Introduction.md)
+ [顧客のクラスタ リング](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

## <a name="boost-performance-and-scale"></a>パフォーマンスの向上と小数点以下桁数

オープン ソース R 言語は限界があることがわかって、RevoScaleR パッケージ Api 大規模なデータセットを処理でき恩恵をマルチ スレッド、マルチコア、マルチ プロセスのデータベース内計算できます。

場合、R ソリューションでは、複雑な集計を使用してまたは大規模なデータセットでは、SQL Server の効率的なインメモリ集計と列ストア インデックスを利用して R コードを使用できます統計の計算結果を処理し、スコア付けします。

SQL Server の Machine Learning でのパフォーマンスを向上させる方法の詳細についてを参照してください。

+ [SQL Server R Services のパフォーマンスの調整](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [パフォーマンスの最適化ヒントとテクニック](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>他のプラットフォーム用の R コードを改変または計算コンテキスト

に対して実行される同じ R コード[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データは、Hadoop などのデータ ソースに対して使用できるし、他の計算コンテキスト。

Microsoft R でサポートされているプラットフォームの詳細についてを参照してください。

+ [Microsoft R の概要](https://docs.microsoft.com/r-server/)

+ [RevoScaleR を調べる](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

大規模なデータまたは複数のプラットフォームで実行する、Microsoft R ソリューションを最適化する方法の詳細についてを参照してください。

+ [チャンク アルゴリズムを書き込む](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [R での big data コンピューティング](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [独自の並列アルゴリズムを開発します。](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)


