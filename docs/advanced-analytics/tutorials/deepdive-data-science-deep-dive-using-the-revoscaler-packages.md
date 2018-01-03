---
title: "データ サイエンス deep dive: SQL Server で、RevoScaleR パッケージを使用して |Microsoft ドキュメント"
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: c2efb3f2-cad5-4188-b889-15d68b742ef5
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 62bcad211bac049151d5feba79004ba72883196b
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="data-science-deep-dive-using-the-revoscaler-packages-with-sql-server"></a>データ サイエンス deep dive: SQL Server で、RevoScaleR パッケージを使用

このチュートリアルで提供される強化された R パッケージを使用する方法を示します[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]SQL Server のデータを操作および高パフォーマンスのビッグ データ分析のコンピューティング コンテキストとしてサーバーを使用して、スケーラブルな R ソリューションを作成します。

ローカルおよびリモート計算コンテキスト間でデータを移動するリモート計算コンテキストを作成する方法について説明し、リモートの SQL Server で R コードを実行します。 分析し、ローカルとリモート サーバーの両方にデータをプロットする方法と作成し、モデルを配置する方法についても説明します。

> [!NOTE]
> 
> このチュートリアルでは、Windows では、SQL Server のデータで具体的には機能し、データベース内の計算コンテキストを使用します。 Teradata、Linux、Hadoop など、他のコンテキストで R を使用する場合は、これらの Microsoft R Server チュートリアルを参照してください。 
> + [R サーバー sparklyr を使用します](https://docs.microsoft.com/machine-learning-server/r/tutorial-sparklyr-revoscaler)
> + [25 の関数で R と ScaleR を探索する](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler)
> + [Hadoop MapReduce ScaleR を概要します。](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-hadoop)

## <a name="overview"></a>概要

このチュートリアルでは、RevoScaleR パッケージの柔軟性と処理能力が発生するには、データとスワップ計算コンテキスト頻繁に移動します。 説明するため、ここではいくつかのタスクのこのチュートリアルでは。

+ 最初に、CSV ファイルまたは XDF ファイルからデータを取得します。 データをインポートする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]RevoScaleR パッケージで、関数を使用します。
+ モデルのトレーニングおよびスコア付けを使用して実行、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンテキストを計算します。 
+ RevoScaleR 関数を使用して、[新規作成] を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スコアリング結果を保存するテーブル。
+ サーバーで両方のプロットを作成し、ローカルの計算コンテキスト。
+ 内のデータに対してモデルのトレーニング[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]R を実行しているデータベース、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。
+ データのサブセットを抽出し、ローカル ワークステーションの分析で再利用 XDF ファイルとして保存します。
+ ODBC 接続を開くことによって、スコアリングのための新しいデータの取得、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。 スコアリングは、ローカル ワークステーションで行われます。
+ カスタムの R 関数を作成し、コンピューティング コンテキストをシミュレーションを実行するサーバーで実行します。

### <a name="article-list-and-time-required"></a>記事の一覧と必要な時間

このチュートリアルでは約 75 分を完了すると、セットアップは含まれません。

1. [R を使用する SQL Server データを操作します。](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)
2. [RxSqlServerData を使用して SQL Server のデータ オブジェクトを作成する](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
3. [SQL Server データに対するクエリおよび変更](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)
4. [計算コンテキストの定義と使用](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)
5. [作成し、R スクリプトを実行します。](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
6. [R を使用する SQL Server データを視覚化します。](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)
7. [R モデルを作成します。](../../advanced-analytics/tutorials/deepdive-create-models.md)
8. [新しいデータのスコア](../../advanced-analytics/tutorials/deepdive-score-new-data.md)
9. [R を使用したデータの変換](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)
10. [RxImport を使用しているメモリにデータを読み込む](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)
11. [RxDataStep を使用して新しい SQL Server テーブルを作成します。](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
12. [rxDataStep を使用したチャンク分析の実行](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
13. [ローカル計算コンテキストでデータを分析する](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)
14. [XDF ファイルを使用して SQL Server からデータを移動します。](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
15. [簡単なシミュレーションを作成する](../../advanced-analytics/tutorials/deepdive-create-a-simple-simulation.md)

### <a name="target-audience"></a>対象読者

このチュートリアルは、データ サイエンティスト向けまたはおよびデータ サイエンス タスクの概要とモデルの作成など、R とある程度理解しているユーザーのものです。  ただし、すべてのコードが提供される、R に慣れていない場合でもは、コードを実行し、たら、必要なサーバーとクライアントの環境があると仮定するとします。

慣れておく必要があります[!INCLUDE[tsql](../../includes/tsql-md.md)]構文にアクセスする方法を知っていると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]これらなどのツールを使用してデータベースします。

+ [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 
+ Visual Studio でのデータベース ツール 
+ 無料[Visual Studio Code の mssql 拡張子](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode)です。
  
> [!TIP]
> 中断した箇所からを容易に再開できるように、レッスンの合間に R ワークスペースを保存してください。

### <a name="prerequisites"></a>Prerequisites

- **SQL Server の R のサポート**
  
    SQL Server 2016 をインストールし、R Services (In-database) を有効にします。 SQL Server 2017 をインストールし、Machine Learning のサービスを有効にし、R 言語を選択します。
  
-  **データベース権限**
  
    モデルのトレーニングで使用するクエリを実行するには、データが格納されているデータベースに対して **db_datareader** 権限が必要です。 R を実行するには、EXECUTE ANY EXTERNAL SCRIPT、アクセス許可が、ユーザーに必要です。

-   **データ サイエンス開発用コンピューター**
  
    R 開発環境として使用するコンピューターに、RevoScaleR パッケージと関連するプロバイダーをインストールする必要があります。 Microsoft R クライアントをインストールする最も簡単な方法は、Microsoft R Server (スタンドアロン) または Machine Learning Server (スタンドアロン)。 
      
    > [!NOTE] 
    > 他のバージョンの Revolution R Enterprise または Revolution R Open はサポートされていません。
    > 
    > R のオープン ソース ディストリビューションは、RevoScaleR 関数のみがリモート計算コンテキストを使用できるため、このチュートリアルでは使用できません。
  
-   **追加の R パッケージ**
  
    このチュートリアルでは、次のパッケージをインストールする: **dplyr**、 **ggplot2**、 **ggthemes**、 **reshape2**、および**e1071**. 手順は、チュートリアルの中で説明します。
  
    2 つの場所のすべてのパッケージをインストールする必要があります: R ソリューションの開発では、使用するコンピューターと、SQL Server コンピューターに R スクリプトを実行します。 サーバー コンピューターにパッケージをインストールするアクセス許可があるない場合、管理者に問い合わせてください。 
    
    **ユーザー ライブラリにはパッケージをインストールしないでください。** パッケージは、SQL Server のインスタンスによって使用される R パッケージ ライブラリでインストールする必要があります。

詳細については、次を参照してください。[データ サイエンスのチュートリアルの前提条件](../../advanced-analytics/tutorials/walkthrough-prerequisites-for-data-science-walkthroughs.md)です。

## <a name="next-step"></a>次の手順

[R を使用する SQL Server データを操作します。](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)

