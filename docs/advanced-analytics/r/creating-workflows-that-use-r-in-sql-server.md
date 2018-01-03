---
title: "R での BI ワークフローの作成 |Microsoft ドキュメント"
ms.custom: SQL2016_New_Updated
ms.date: 04/18/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34c3b1c2-97db-4cea-b287-c7f4fe4ecc1b
caps.latest.revision: "11"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f9d289d2a5eaf2e04f771f0a51309e50d2821184
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="creating-bi-workflows-with-r"></a>R での BI ワークフローの作成

リレーショナル データベースは、データのトランザクション処理、ストレージ、クエリのためのスケーラブルなソリューションを提供するために確立され、大幅に最適化されたテクノロジです。

これに対し、従来 R ソリューションが一般に依存をこれ以上のデータ探索およびモデリングを実行する、CSV 形式で多くの場合、さまざまなソースからデータをインポートします。 これは非効率であるだけでなく、危険な方法です。

このトピックでは、一般的な落とし穴と machine learning のソリューションを開発して、データベース外部の場合に発生する可能性があるセキュリティ リスクを回避する SQL Server で R の統合シナリオを説明します。

Integration Services および Reportng Services、特に、ビジネス インテリジェンス アプリケーションの R コードとの対話およびデータまたは R. によって生成されたグラフィックスを処理できる方法の例についても説明します。

適用されます SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス。

## <a name="bring-compute-power-to-the-data"></a>データへのコンピューティング能力を取り込む

機械学習を SQL Server と統合することの重要な設計目標は、分析データの近くにされました。 これは、複数の利点を提供します。

+ データのセキュリティ。 データ ソースの R 近くすることには、無駄なまたは安全でないデータ移動が回避できます。

+ 速さ。 データベースは、セットベースの操作用に最適化されています。 インメモリ テーブルなどのデータベースの最新技術の概要と電光、集計を行いはデータ サイエンスを完全に補完します。

+ 展開との統合の容易さ。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]その他の多くのデータ管理タスクやアプリケーションに対する操作の中央ポイントです。 データベースまたはレポート ウェアハウス内に存在するデータを使用すると、機械学習ソリューションによって使用されるデータが一貫して最新の状態であることを確認します。 

+ クラウドとオンプレミス間の効率。 R でデータを処理する代わりに、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] や Azure Data Factory などのエンタープライズ データ パイプラインに依存できます。 Power BI や [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を使用して、結果や分析を簡単にレポートできます。

さまざまなデータ処理や分析タスクで SQL と R を正しく組み合わて使用することで、データ サイエンティストと開発者の両方の生産性がさらに向上します。

## <a name="use-integration-services-for-data-transformation-and-automation"></a>データの統合サービスを使用して変換し、オートメーション

データ サイエンス ワークフローは何度も繰り返され、スケーリング、集計、確率計算、および属性の名前変更とマージなど、多くのデータ変換を含みます。 データ サイエンティストはこのようなタスクの多くを R、Python または他の言語で実行することに慣れていますが、これらのワークフローをエンタープライズ データで実行するには、ETL ツールとプロセスのシームレスな統合が必要になります。

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では Transact-SQL とストアド プロシージャを介して R で複雑な操作を実行できるため、再開発の最小限の作業も行わずに、既存の ETL プロセスに R 固有のタスクを統合できます。 はなく R のメモリを消費するタスクのチェーンを実行するよりもデータの準備を最適化できますを含む、最も効率的なツールを使用して[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]と[!INCLUDE[tsql](../../includes/tsql-md.md)]です。 

ここでを使用してパイプラインをデータ、dmodeling の処理を自動化する方法のいくつか ideass [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ 使用して[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]SQL データベースに必要なデータの機能を作成するタスク
+ 条件分岐を使用して、R ジョブの計算コンテキストを切り替える。
+ データベースの独自のデータを生成する R ジョブを実行し、アプリケーションとそのデータを共有
+ 使用する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テキスト変数で保存されている R スクリプトを読み込んで、SQL Server の実行

### <a name="examples"></a>使用例

[Operationalize your machine learning project using SQL Server 2016 SSIS and R Services](https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/)(SQL Server 2016 SSIS と R Services を使用した機械学習を運用可能にする)  

このブログの投稿を使用して R コードを操作するための基本的な方法を示します[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]: 

+ データを生成しに保存する SQL 実行タスクを使用して R を呼び出す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

+ ストアド プロシージャを使用し、R モデルをトレーニングしてデータベースに保存する

+ スクリプト タスクと SQL 実行タスクを使用して、モデルのスコアリングを実行する

##  <a name="bkmk_ssrs"></a>Reporting Services の視覚エフェクトを使用します。

R ではチャートや注意を引く視覚エフェクトを作成できますが、外部データ ソースに十分に統合されません。つまり、各チャートまたはグラフを個別に生成する必要があります。 共有も困難な可能性があります。

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] を使用すれば、[!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを介することで複雑な操作を R で実行できます。このストアド プロシージャは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] や Power BI などのさまざまなエンタープライズ レポート ツールで簡単に使用できます。

+ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]
+ Power BI でテーブルを使用する

### <a name="examples"></a>使用例

[R Graphics Device for Microsoft Reporting Services (SSRS)](https://rgraphicsdevice.codeplex.com/) (Microsoft Reporting Services (SSRS) 用の R グラフィックス デバイス)

この CodePlex プロジェクトが提供するコードを使用すると、R のグラフィックス出力を [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートで使用できるイメージとしてレンダリングする、カスタム レポート アイテムを作成できます。  カスタム レポート アイテムを使用すると、次の操作を実行できます。

+ R グラフィックス デバイスを使用して作成したグラフとプロットを [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ダッシュボードに公開する

+ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] パラメーターを R プロットに渡す

> [!NOTE]
> このサンプルでは、Reporting Services サーバー上だけでなく Visual Studio で Reporting Services の R のグラフィックス デバイスをサポートするコードをインストールする必要があります。 手動によるコンパイルと構成も必要です。
