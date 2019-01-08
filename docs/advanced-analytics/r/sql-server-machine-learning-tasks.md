---
title: 機械学習ライフ サイクルとチームのプロセス - SQL Server Machine Learning サービス
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 2218034dd6ac4cc3e7926b214c5c021815e57ed3
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432205"
---
# <a name="machine-learning-lifecycle-and-personas"></a>Machine learning のライフ サイクルとペルソナ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Machine learning プロジェクト スキルとプロフェッショナル向けのさまざまな一連の共同作業が必要なため、複雑なことはできます。 この記事では、machine learning のライフ サイクルであり、機械学習、および SQL Server がニーズをサポートする方法を行っているデータのプロフェッショナルの種類で、主なタスクについて説明します。

> [!TIP]
> 
> ツールとによって提供されるベスト プラクティスを確認することをお勧めの machine learning プロジェクトを開始する前に、 [Microsoft Team Data Science Process](https://blogs.technet.microsoft.com/machinelearning/2017/10/09/the-microsoft-team-data-science-process-tdsp-recent-updates/)、または TDSP します。 このプロセスは、machine learning の計画と機械学習のプロジェクトの反復処理に関するベスト プラクティスを統合するマイクロソフトのコンサルタントによって作成されました。 TDSP は CRISP-DM などの業界標準では、DevOps や視覚化などの最新のプラクティスが組み込まれています。

## <a name="machine-learning-life-cycle"></a>Machine learning のライフ サイクル

Machine learning は、企業内のデータのすべての側面がある複雑なプロセスと、時間がかかって、予想よりもさらに複雑な最終的に多くの machine learning プロジェクト。 Machine learning が、企業内のデータの専門家のサポートが必要である方法の一部を次に示します。

+ Machine learning は、目標とビジネス ルールの id で始まります。
+ Machine learning のプロフェッショナルは、ポリシーを格納する、抽出、および監査データを認識する必要があります。
+ 該当する可能性のあるデータのコレクションは、[次へ] です。  データ ソースを識別する必要があり、適切なデータがセンサーやビジネス アプリケーションから抽出します。 
+ Machine learning の取り組みの品質は、利用可能なデータが抽出、処理、およびデータの格納に使用される非常に処理の種類だけでなくに大きく依存します。 
+ Machine learning プロジェクトは完璧とは報告し分析、および可能性がある顧客エンゲージメントとフィードバックするための戦略なし。

SQL Server では、多くのエンタープライズ データ プロフェッショナルと機械学習専門家の間のギャップの橋渡しを支援します。

+ データはオンプレミスに保存できますまたは、クラウドで。
+ SQL Server はエンタープライズ データの処理、レポートなど、ETL の各段階で統合されています。
+ SQL Server データのセキュリティ、データの冗長性、および監査をサポートしています
+ リソース ガバナンスを提供します。

## <a name="data-scientists"></a>データ サイエンティスト

データ サイエンティストは、データ分析と機械学習、Excel または無料のオープン ソース プラットフォームから深い技術的知識を必要とする高価な統計スイートに至るまでのさまざまなツールを使用します。 ただし、SQL Server で R または Python を使用すると、これらの従来のツールと比べていくつか一意の利点があります。

+ 開発して、好みの開発環境を使用して、ソリューションをテストし、T-SQL コードの一部として、R または Python コードをデプロイすることができます。
+ データ科学者のラップトップ コンピューター オフと企業のセキュリティ ポリシーに準拠するデータの移動を回避、サーバー上に複雑な計算を移動します。
+ 特別な R パッケージと Api では、パフォーマンスとスケールが向上しました。 R のシングル スレッドのメモリ負荷の高いアーキテクチャに制限されなくと、大規模なデータセットとマルチ スレッド、マルチコア、マルチ プロセス計算を処理できます。
+ コードの移植性:ソリューションは、SQL Server、Hadoop または Linux を実行できますを使用して[Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)します。 コードの 1 回、場所にデプロイします。

## <a name="application-and-database-developers"></a>アプリケーションとデータベース開発者

データベース開発者は、企業全体で共有できるように、多数のテクノロジを統合し、結果をまとめる任務を負っています。 データベース開発者は、ソリューションを設計、データの管理方法をお勧めし、設計またはソリューションの配置には、アプリケーション開発者は、SQL 開発者、およびデータ サイエンティストで動作します。

SQL Server との統合には、データ開発者に多くの利点があります。

+ データ サイエンティストは、データ開発者は、SQL Server Management Studio を使用してソリューションをデプロイ中に、RStudio で作業できます。 これ以上の R または Python のソリューションの再コーディングします。
+ T-SQL、R、および Python の最適なを使用して、ソリューションを最適化します。 R. 活用して、データベース プロフェッショナルのサポート技術情報でよりも SQL Server を使用して、メモリ内列ストア インデックスを使用して machine learning のソリューションのパフォーマンスを向上させるよりはるかに効率的に大規模なデータセットに対して複雑な操作を実行することができ、SQL、セットベースの操作を使用して集計します。 
+ 実稼働データの予測スコアを生成するなどのデータを大量に繰り返し実行する必要がありますタスクを自動化できます。 
+ アクセスに使用する任意のアプリケーションからの R または Python スクリプトがパラメーター化された[!INCLUDE[tsql](../../includes/tsql-md.md)]します。 モデルをトレーニング、プロットを生成または予測を出力するストアド プロシージャを呼び出すだけです。
+ Api は、大規模なデータセットをストリーミングして、マルチ スレッド、マルチコア、マルチ プロセスのデータベース内計算のメリットします。

関連するタスクについてを参照してください。
+ [R コードの運用](../../advanced-analytics/r/operationalizing-your-r-code.md)

### <a name="database-administrators"></a>データベース管理者

データベース管理者は競合するプロジェクトと優先順位を 1 箇所の連絡先 (データベース サーバー) に統合する必要があります。 データベース管理者は、運用とレポート用のデータ ストアの正常性を維持しながら、データ サイエンティストに対してだけでなく、さまざまなレポート開発者、ビジネス アナリスト、およびビジネス データのユーザーにデータのアクセス権を与える必要があります。 企業において、DBAは、データ サイエンス用の効率的なインフラストラクチャのビルドと展開のきわめて重要な部分です。 

SQL サーバーでは、データ サイエンスの役割をサポートする必要があります、データベース管理者の独自の機能を提供します。

+ SQL Server でのセキュリティ:アーキテクチャ[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]データベースのセキュリティで保護し、データベース インスタンスの運用からセッションを外部スクリプトの実行を分離します。 Machine learning のスクリプトを実行し、データベース ロールを使用してパッケージを管理するためのアクセス許可を持っているユーザーを指定できます。

+ R と Python のセッションで、サーバーが外部スクリプトに問題が発生した場合でも、通常どおり実行を続けるようにする別のプロセスで実行されます。

+ SQL Server を使用してリソース管理では、メモリとサーバーの全体のパフォーマンスを損なうから大量の計算に外部のランタイムに割り当てられているプロセスを制御できます。

関連するタスクについてを参照してください。
+ [Machine Learning ソリューションの管理と監視](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)

## <a name="architects-and-data-engineers"></a>設計者およびデータ エンジニア

アーキテクトは、machine learning のライフ サイクルのすべての側面にまたがる統合ワークフローを設計します。 データ エンジニアは、設計し、ETL ソリューションを構築し、machine learning の機能エンジニア リング タスクを最適化する方法を決定します。 全体的なデータ プラットフォームを設計すると、競合するビジネス ニーズのバランスを取る必要があります。

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] は、ビジネス インテリジェンスおよびデータ ウェアハウス スタック、エンタープライズ クラウドおよびモビリティ ツール、Hadoop などの他の Microsoft ツールと緊密に統合し、高度な分析を推進する必要があるデータ エンジニアやシステム アーキテクトに多大なメリットをもたらします。

+ Python または R スクリプトを呼び出すには、システム ストアド プロシージャを使用してデータセットの設定、画像を生成または予測を取得します。 ない以上設計並列のワークフローのデータ サイエンスおよび ETL ツール。 Azure Data Factory と Azure SQL Database のサポートにより、簡単に機械学習のワークフローでのクラウド データ ソースを使用します。

+ スケジュール設定および機械学習タスクの管理のために、SQL Server Integration Services、SQL エージェント、または Azure Data Factory に基づくで標準的な自動化ワークフローを使用します。 または、使用して、[運用化機能](https://docs.microsoft.com/machine-learning-server/operationalize/how-to-deploy-web-service-publish-manage-in-r)Machine Learning Server にします。

関連するタスクについてを参照してください。

+ [SQL Server での機械学習のワークフローの作成](../../advanced-analytics/r/creating-workflows-that-use-r-in-sql-server.md)

