---
title: "データ サイエンスのエンド ツー エンド チュートリアル | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: edd76ae9-4125-45a8-bf42-47a85b9d9a32
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# データ サイエンスのエンド ツー エンド チュートリアル
このチュートリアルでは、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]を使用して予測モデリングのエンド ツー エンド ソリューションを開発します。  
  
このチュートリアルは、よく知られている公開データ セット、ニューヨーク市タクシー データセットに基づいています。 R コード、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ、カスタム SQL 関数の組み合わせを使用して、ドライバーが特定のタクシー乗車でチップを受け取ることができる確率を示す分類モデルを構築します。 また、R モデルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に配置し、サーバーのデータを使用してモデルに基づくスコアを生成します。  
  
この例は、販売キャンペーンに対する顧客の反応の予測や、イベントの訪問者による支出の予測など、あらゆる種類の実際の問題に合わせて簡単に拡張できるためです。 このモデルはストアド プロシージャから呼び出すことができるため、アプリケーションにも簡単に埋め込むことができます。  
  
**対象読者**  
  
このチュートリアルは、R の開発者向けです。 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用したデータベースの作成、テーブルの作成、テーブルへのデータのインポート、テーブルの照会などの基本的なデータベース操作についての知識も必要です。  実行する SQL および R のスクリプトは提供されます。  
  
初めて R を使用する場合でも、データベースについての知識があれば、このチュートリアルによって、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]を使用して R を企業のワークフローに統合する方法の概要を把握することができます。 R のコーディングは必要ありません。すべてのスクリプトが用意されています。 コマンドを実行するには、特定の種類の R IDE がインストールされている必要があります。  
  
**前提条件**  
  
このチュートリアルを実行するには、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] がインストールされている [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] のインスタンスにアクセスできる必要があります。 ローカルの環境として、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続できるデータ サイエンス ワークステーションを準備し、必要な R ライブラリをインストールします。  
  
詳細については、[「データ サイエンスのチュートリアルの前提条件 (SQL Server R Services)」](../../advanced-analytics/r-services/prerequisites-for-data-science-walkthroughs-sql-server-r-services.md)を参照してください。  
  
## <a name="overview"></a>概要  
このチュートリアルでは、高度な分析の一般的なエンド ツー エンド ソリューションについて説明します。 次の順序でレッスンを完了する必要があります。  
  
||推定所要時間|  
|-|------------------------------|  
|[レッスン 1: データを準備する (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)<br /><br />分析プロセスは、モデルを構築するために使用されるデータを取得することから始まります。 公開されているデータセットをダウンロードして、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに保存します。|30 分|  
|[レッスン 2: データの表示と調査 (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-2-view-and-explore-the-data-data-science-end-to-end-walkthrough.md)<br /><br />データ サイエンティストは、多くの場合、データの調査とモデリングのための準備、新機能の作成、必要に応じたデータの変換に、かなりの時間を費やしています。  SQL と R の両方を使用して、データを調査し、サマリーを生成します。|20 分|  
|[レッスン 3: データ機能の作成 (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-3-create-data-features-data-science-end-to-end-walkthrough.md)<br /><br />R および [!INCLUDE[tsql](../../includes/tsql-md.md)]のカスタム関数を使用して新しいデータ機能を作成します。|10 分|  
|[レッスン 4: モデルの構築と保存 (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-4-build-and-save-the-model-data-science-end-to-end-walkthrough.md)<br /><br />データの準備ができたら、データ サイエンティストはモデルのパフォーマンスを評価し、さまざまなパラメーターを試しながら、モデルのトレーニングと調整を行います。 このチュートリアルでは、分類モデルを作成し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でデータを使用して予測を生成します。 また、R を使用してモデルの精度のプロットも作成します。|15 分|  
|[レッスン 5: モデルの配置と使用 (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-5-deploy-and-use-the-model-data-science-end-to-end-walkthrough.md)<br /><br />最後に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースにモデルを保存することによって実稼働環境にモデルを配置し、ストアド プロシージャからモデルを呼び出して予測を生成します。|10 分|  
  
## <a name="notes"></a>注  
このチュートリアルは、R 開発者に [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]を紹介することを目的として設計されているため、R を使用してできるだけ多くの操作を実行しています。これは、必ずしも R が各タスクに最適なツールであるという意味ではありません。 多くの場合、特にデータ集計と機能エンジニアリングについては、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の方が優れたパフォーマンスを示す可能性があります。 このようなタスクでは、特に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の新機能 (メモリ最適化列ストア インデックスなど) のメリットが得られます。  
  
## <a name="next-step"></a>次の手順  
[レッスン 1: データを準備する (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
