---
title: "機械学習のライフ サイクル、および、チーム プロセス |Microsoft ドキュメント"
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ad3f10-6d24-477a-aeb6-110456b2ed1c
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 22cd61895126a1d6daa1d69991ec0075d1cd684d
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="machine-learning-lifecycle-and-personas"></a>Machine learning のライフ サイクルとペルソナ

Machine learning プロジェクト スキルとプロフェッショナル向けのさまざまな一連の共同作業に必要なため、複雑なことはできます。 この記事では、マシン学習のライフ サイクルであり、機械学習、および SQL Server がニーズをサポートする方法を行っているデータ担当者の種類の主なタスクについて説明します。

> [!TIP]
> 
> ツールとによって提供されるベスト プラクティスを確認することをお勧め、機械学習のプロジェクトで開始する前に、 [Microsoft チーム データ サイエンス プロセス](https://blogs.technet.microsoft.com/machinelearning/2017/10/09/the-microsoft-team-data-science-process-tdsp-recent-updates/)、または TDSP です。 このプロセスは、機械学習の計画と機械学習のプロジェクトの反復処理のベスト プラクティスを統合する Microsoft コンサルタントによって作成されました。 TDSP にそのルートに CRISP-DM などの業界標準が DevOps と視覚エフェクトなどの最新のプラクティスが組み込まれています。

## <a name="machine-learning-life-cycle"></a>Machine learning のライフ サイクル

機械学習は、企業内のデータのすべての側面がある複雑なプロセスと多くの machine learning プロジェクト最終的に長い時間かかっていて、予想よりも複雑です。 次に、企業内のデータ プロフェッショナルのサポートが必要である機械学習の方法のいくつかを示します。

+ 機械学習では、目標とビジネス ルールの id で始まります。
+ Machine learning のプロフェッショナルを格納する、抽出、およびデータの監査のポリシーの対応にする必要があります。
+ 該当する可能性のあるデータのコレクションは、[次へ] です。  データ ソースを識別する必要があります、され、センサー、ビジネス アプリケーションから、適切なデータが抽出されます。 
+ Machine learning の作業の品質は、使用可能なデータが抽出、処理、およびデータの格納に使用される非常に処理の種類だけでなくに大きく依存します。 
+ Machine learning プロジェクトすることが完成報告し分析、および可能性のある顧客の契約とフィードバックの戦略がなければです。

SQL Server では、多くの企業のデータ プロフェッショナルと machine learning エキスパートの間のギャップを埋めるのに役立ちます。

+ 社内に保存できるデータはクラウド内、または
+ エンタープライズ データ処理、レポートなど、ETL の各段階で SQL Server を統合します。
+ SQL Server には、データのセキュリティ、データの冗長性、および監査がサポートしています
+ リソース管理を提供します。

## <a name="data-scientists"></a>データ サイエンティスト

データ サイエンティストは、データ分析と機械学習、Excel または無料のオープン ソース プラットフォームから深い技術的知識を必要とする高価な統計スイートまでのさまざまなツールを使用します。 ただし、SQL Server で R または Python を使用すると、これらの従来のツールと比較するといくつか一意の利点があります。

+ 開発して、任意の開発環境を使用して、ソリューションをテストし、T-SQL コードの一部として R または Python コードをデプロイすることができます。
+ データ サイエンティストのラップトップ コンピューター オフと企業のセキュリティ ポリシーに準拠するデータの移動を回避する、サーバー上に複雑な計算を移動します。
+ 特殊な R パッケージと Api を介して、パフォーマンスと拡張性が向上します。 不要になった、R のシングル スレッド、メモリ バインド アーキテクチャによって制限されているし、大規模なデータセットとマルチ スレッド、マルチコア、マルチ プロセス計算を処理できます。
+ コードの移植性: ソリューションは、SQL Server、Hadoop または Linux を実行できますを使用して[Machine Learning サーバー](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)です。 1 回コードは、任意の場所を展開します。

## <a name="application-and-database-developers"></a>アプリケーションとデータベース開発者

データベース開発者は、企業全体で共有できるように、多数のテクノロジを統合し、結果をまとめる任務を負っています。 データベース開発者は、ソリューションを設計、データの管理方法を推奨し、設計またはソリューションの配置するには、アプリケーション開発者、SQL 開発者、およびデータ サイエンティストで動作します。

SQL Server との統合では、データの開発者に多くの利点があります。

+ データ サイエンティストは、データの開発者は、SQL Server Management Studio を使用して、ソリューションを配置中に、RStudio で作業できます。 これ以上の R または Python のソリューションの再コーディングします。
+ T-SQL、R、Python の最高レベルを使用して、ソリューションを最適化します。 はるかに効率的に R. 活用して、データベース担当者の情報でよりも SQL Server を使用して、メモリ内列ストア インデックスを使用して、マシン学習ソリューションのパフォーマンスを向上させるために大規模なデータセットに対して複雑な操作を実行することができ、SQL セットベースの操作を使用して集計します。 
+ 簡単に実稼働データの予測スコアを生成するなど、データの大量に繰り返し実行する必要がありますタスクを自動化します。 
+ パラメーター化を使用するアプリケーションから R または Python スクリプトのアクセス[!INCLUDE[tsql](../../includes/tsql-md.md)]です。 モデルのトレーニング、プロットを生成または予測を出力するストアド プロシージャを呼び出すだけです。
+ Api では、大規模なデータセットをストリーム配信でき、マルチ スレッド、マルチコア、マルチ プロセスのデータベース内計算メリットを享受することができます。

関連タスクについてを参照してください。
+ [R コードの運用](../../advanced-analytics/r/operationalizing-your-r-code.md)

### <a name="database-administrators"></a>データベース管理者

データベース管理者は競合するプロジェクトと優先順位を 1 箇所の連絡先 (データベース サーバー) に統合する必要があります。 データベース管理者は、運用とレポート用のデータ ストアの正常性を維持しながら、データ サイエンティストに対してだけでなく、さまざまなレポート開発者、ビジネス アナリスト、およびビジネス データのユーザーにデータのアクセス権を与える必要があります。 企業において、DBAは、データ サイエンス用の効率的なインフラストラクチャのビルドと展開のきわめて重要な部分です。 

SQL Server では、データ サイエンスの役割をサポートする必要があります、データベース管理者のための独自の機能を提供します。

+ SQL Server でのセキュリティ: のアーキテクチャ[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]データベースをセキュリティで保護された状態をデータベース インスタンスの操作からのセッションを外部スクリプトの実行を分離します。 Machine learning のスクリプトを実行し、データベース ロールを使用してパッケージを管理するアクセス許可を持っているユーザーを指定することができます。

+ R、Python のセッションは、サーバーが引き続き、外部スクリプトに問題が発生した場合でも、通常どおり実行できるように別のプロセスで実行されます。

+ SQL Server を使用してリソース管理を使用して、メモリとサーバーの全体的なパフォーマンスが損なわれない大規模な計算を防ぐために、外部のランタイムに割り当てられているプロセスを制御できます。

関連タスクについてを参照してください。
+ [Machine Learning ソリューションの管理と監視](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)

## <a name="architects-and-data-engineers"></a>設計者およびデータ エンジニア

アーキテクトは、machine learning のライフ サイクルのすべての側面にまたがる統合ワークフローを設計します。 データ エンジニアは、設計、ETL ソリューションを構築およびと機械学習機能エンジニア リング タスクを最適化する方法を決定します。 全体的なデータ プラットフォームは、競合するビジネス ニーズのバランスを設計する必要があります。

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] は、ビジネス インテリジェンスおよびデータ ウェアハウス スタック、エンタープライズ クラウドおよびモビリティ ツール、Hadoop などの他の Microsoft ツールと緊密に統合し、高度な分析を推進する必要があるデータ エンジニアやシステム アーキテクトに多大なメリットをもたらします。

+ データセットを作成、グラフィックスを生成または予測を取得のシステム ストアド プロシージャを使用して、Python または R スクリプトを呼び出します。 ない以上設計並列のワークフロー データ サイエンスおよび ETL ツールです。 Azure Data Factory および Azure SQL Database のサポートでは、機械学習のワークフローでのクラウド データ ソースを使用してやすくなります。

+ スケジュールを設定して、機械学習タスクの管理、SQL Server Integration Services、SQL エージェント、または Azure Data Factory に基づくで標準の自動化のワークフローを使用します。 または、使用して、[操作運用機能](https://docs.microsoft.com/machine-learning-server/operationalize/how-to-deploy-web-service-publish-manage-in-r)Machine Learning のサーバーにします。

関連タスクについてを参照してください。

+ [SQL Server で machine learning ワークフローの作成](../../advanced-analytics/r/creating-workflows-that-use-r-in-sql-server.md)

