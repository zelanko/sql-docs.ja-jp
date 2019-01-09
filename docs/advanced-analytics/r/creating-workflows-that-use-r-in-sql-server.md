---
title: R で SQL Server Machine Learning Services を使用したビジネス インテリジェンス (BI) ワークフローを作成します。
description: Business intelligence (BI) と R 言語を組み合わせて統合シナリオでは、SQL Server と SQL Server Integration Services (SSIS) のサポートします。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 32dfb3317cb790c19289ab02362bf8ee765e5259
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432735"
---
# <a name="creating-bi-workflows-with-r"></a>R を使用した BI ワークフローの作成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

リレーショナル データベースは、データのトランザクション処理、ストレージ、クエリのためのスケーラブルなソリューションを提供するために確立され、大幅に最適化されたテクノロジです。

これに対し、従来 R ソリューション一般に依存してさらにデータを探索およびモデリングを実行する、CSV 形式で多くの場合、さまざまなソースからデータをインポートします。 これは非効率であるだけでなく、危険な方法です。

この記事では、よくある落とし穴と、データベース外部の機械学習ソリューションを開発する場合に発生する可能性があるセキュリティ リスクを回避する SQL Server で R の統合シナリオについて説明します。

Integration Services および Reporting Services では、特に、ビジネス インテリジェンス アプリケーションの R コードとの対話およびデータまたは R で生成されたグラフィックスを使用できる方法の例もについて説明します。

適用対象SQL Server 2016 R Services、SQL Server 2017 の Machine Learning サービス

## <a name="bring-compute-power-to-the-data"></a>データにコンピューティング能力をもたらす

SQL Server と machine learning の統合の主要な設計目標は、分析データの近くにするようにしています。 これは、複数の利点を提供します。

+ データのセキュリティ。 データのソースを R に近い場所を使えるように無駄や安全でないデータ移動を回避できます。

+ 速さ。 データベースは、セットベースの操作用に最適化されています。 インメモリ テーブルなどのデータベースの最新技術の概要と集計、処理が非常を行い、データ サイエンスを補完します。

+ 展開との統合が容易。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] その他の多くのデータ管理タスクやアプリケーションの操作のサーバーの全体のポイントです。 レポート ウェアハウスまたはデータベースに存在するデータを使用すると、機械学習ソリューションによって使用されるデータが一貫して最新の状態であることを確認します。 

+ クラウドとオンプレミス間の効率。 R でデータを処理する代わりに、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] や Azure Data Factory などのエンタープライズ データ パイプラインに依存できます。 Power BI や [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を使用して、結果や分析を簡単にレポートできます。

さまざまなデータ処理や分析タスクで SQL と R を正しく組み合わて使用することで、データ サイエンティストと開発者の両方の生産性がさらに向上します。

## <a name="use-integration-services-for-data-transformation-and-automation"></a>データの統合サービスを使用して変換と自動化

データ サイエンス ワークフローは何度も繰り返され、スケーリング、集計、確率計算、および属性の名前変更とマージなど、多くのデータ変換を含みます。 データ サイエンティストはこのようなタスクの多くを R、Python または他の言語で実行することに慣れていますが、これらのワークフローをエンタープライズ データで実行するには、ETL ツールとプロセスのシームレスな統合が必要になります。

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では Transact-SQL とストアド プロシージャを介して R で複雑な操作を実行できるため、再開発の最小限の作業も行わずに、既存の ETL プロセスに R 固有のタスクを統合できます。 はなく一連のメモリを消費するタスクを実行すると、R よりもデータの準備を最適化できますなど、最も効率的なツールを使用して[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]と[!INCLUDE[tsql](../../includes/tsql-md.md)]します。 

ここでは、データ処理を自動化する方法のいくつかのアイデアとモデリングのパイプラインを使用して[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ 使用[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]SQL データベースに必要なデータ特徴を作成するタスク
+ 条件分岐を使用して、R ジョブの計算コンテキストを切り替える。
+ データベースに独自のデータを生成する R ジョブを実行し、アプリケーションとそのデータを共有
+ 使用する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、R スクリプトのテキストの変数に保存されたを読み込むし、SQL Server で実行

### <a name="examples"></a>使用例

[Operationalize your machine learning project using SQL Server 2016 SSIS and R Services](https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/)(SQL Server 2016 SSIS と R Services を使用した機械学習を運用可能にする)  

このブログの投稿を使用して R コードを操作するための基本的な手法を示します[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]: 

+ データを生成し、それを保存する SQL 実行タスクを使用して R を呼び出す [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

+ ストアド プロシージャを使用し、R モデルをトレーニングしてデータベースに保存する

+ スクリプト タスクと SQL 実行タスクを使用して、モデルのスコアリングを実行する

##  <a name="bkmk_ssrs"></a> Reporting Services の視覚エフェクトを使用します。

R ではチャートや注意を引く視覚エフェクトを作成できますが、外部データ ソースに十分に統合されません。つまり、各チャートまたはグラフを個別に生成する必要があります。 共有も困難な可能性があります。

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] を使用すれば、[!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを介することで複雑な操作を R で実行できます。このストアド プロシージャは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] や Power BI などのさまざまなエンタープライズ レポート ツールで簡単に使用できます。

+  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]
+ Power BI でテーブルを使用する

### <a name="examples"></a>使用例

[R Graphics Device for Microsoft Reporting Services (SSRS)](https://rgraphicsdevice.codeplex.com/) (Microsoft Reporting Services (SSRS) 用の R グラフィックス デバイス)

この CodePlex プロジェクトが提供するコードを使用すると、R のグラフィックス出力を [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートで使用できるイメージとしてレンダリングする、カスタム レポート アイテムを作成できます。  カスタム レポート アイテムを使用すると、次の操作を実行できます。

+ R グラフィックス デバイスを使用して作成したグラフとプロットを [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ダッシュボードに公開する

+ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] パラメーターを R プロットに渡す

> [!NOTE]
> このサンプルでは、Reporting Services サーバー、および Visual Studio で、Reporting Services の R グラフィックス デバイスをサポートするコードをインストールする必要があります。 手動によるコンパイルと構成も必要です。
