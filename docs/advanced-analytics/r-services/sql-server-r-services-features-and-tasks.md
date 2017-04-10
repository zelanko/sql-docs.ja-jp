---
title: "SQL Server R Services の機能とタスク | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52ad3f10-6d24-477a-aeb6-110456b2ed1c
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 13
---
# SQL Server R Services の機能とタスク
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] データ ストレージと管理、ワークフローの開発、およびレポートの視覚エフェクト用のエンタープライズ レベルのツールを使用して、機能とオープン ソース R 言語の柔軟性を結合します。 次の 4 つの異なるデータのプロフェッショナル向けやシナリオのニーズをサポートします。  
  
## データ サイエンティスト: R と SQL Server を使用した分析、モデル、および評価  
 データ サイエンティストは、使い慣れた Excel やオープン ソース プラットフォームから深い技術的知識を必要とする高価な統計スイートに至るまで、データ分析と機械学習のための多様なツールにアクセスできます。 特に、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] は、計算をデータベースにプッシュすることで、データの移動を回避し、企業のセキュリティ ポリシーに準拠できるため、独自のメリットを提供します。 さらに、データ サイエンティストによって作成された R コードを簡単に運用環境に展開し、使い慣れたエンタープライズ ツールとソリューション ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに基づくアプリケーション、BI レポート ツール、およびダッシュ ボード) によって呼び出すことができます。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]を使用することで、データ サイエンティストは、セキュリティ、展開の容易さ、管理と監視、アクセス監査などのエンタープライズ データ管理の標準要件を満たしながら、分析ソリューションを展開し、更新できます。  
  
-   **使い慣れたユーザー インターフェイス。**  選択した R 開発環境を使用して、ソリューションを開発し、テストします。  
  
-   **データベース内処理。**  R コードを実行し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスをホストするコンピューターで計算を実行させます。 このため、データを移動する必要がありません。  
  
-   **パフォーマンスとスケール。**  スケーラブルな R パッケージや Api では、不要になったは r です。 シングル スレッド、メモリにバインドされたアーキテクチャによって制限されているため大規模なデータセットとマルチ スレッド、マルチコア、マルチ プロセスの計算に使用できます。  
    
-   **コードの移植性。**  に対して実行する同じ R コード [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データは、Hadoop などのデータ ソースに対して簡単に再利用できます。  
  
 関連する手順と概念の詳細については、次を参照してください。 [データの探索と R で予測モデリング](../../advanced-analytics/r-services/data-exploration-and-predictive-modeling-with-r.md)します。  
  
## アプリケーションおよびデータベース開発者: R ソリューションの展開  
 データベース開発者は、企業全体で共有できるように、多数のテクノロジを統合し、結果をまとめる任務を負っています。 データベース開発者は、アプリケーション開発者、SQL 開発者、およびデータ サイエンティストと協力して、ソリューションを設計し、データの管理方法を推奨して、ソリューションを構築して展開します。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] はデータ サイエンティストと協力する開発者に多くのメリットを提供します。  
  
-   **使用して、R スクリプトの対話 [!INCLUDE[tsql](../../includes/tsql-md.md)]します。**  レポート開発者、アナリスト、およびデータベース開発者は、システム ストアド プロシージャを呼び出して、R スクリプトを呼び出すことができます。 計算でデータベースを実行または R の組み合わせを使用したソリューションは、複雑な集計が使用または大規模なデータセットと [!INCLUDE[tsql](../../includes/tsql-md.md)], に最適なパフォーマンスを提供する依存です。 [!INCLUDE[tsql](../../includes/tsql-md.md)] との簡単な統合は、実稼働データの予測スコアの生成など、大量のデータに対してタスクを繰り返し実行する必要がある場合に、特に役立ちます。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との統合は、 [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用する任意のアプリケーションから R スクリプトを実行できることも意味します。 ストアド プロシージャを簡単に呼び出すことなど、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートを R スクリプトを起動して、レポートに、予測とプロットを生成します。  
  
-   **パフォーマンスとスケール。**  によって RevoScaleR パッケージ Api が提供されるが、オープン ソース R 言語の制限がありますがわかっている [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 大規模なデータセットに対して機能し、マルチ スレッド、マルチコア、マルチ プロセスのデータベースで計算の恩恵をことができます。  
  
-   **標準の開発および管理ツール。**  管理や展開のための追加のツールが必要ありません。ストアド プロシージャを呼び出すことによって、すべての R ジョブを呼び出すことができます。 さらに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データに対して実行したものと同じ R コードを、Hadoop などの他のデータ ソースに対して利用できます。  
  
 関連する手順と概念の詳細については、次を参照してください。 [R コードの任せています](../../advanced-analytics/r-services/operationalizing-your-r-code.md)します。  
  
## データベース管理者: 高度な分析ソリューションの管理  
 データベース管理者は競合するプロジェクトと優先順位を 1 箇所の連絡先 (データベース サーバー) に統合する必要があります。 データベース管理者は、運用とレポート用のデータ ストアの正常性を維持しながら、データ サイエンティストに対してだけでなく、さまざまなレポート開発者、ビジネス アナリスト、およびビジネス データのユーザーにデータのアクセス権を与える必要があります。 企業において、DBAは、データ サイエンス用の効率的なインフラストラクチャのビルドと展開のきわめて重要な部分です。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] はデータ サイエンスの役割をサポートするデータベース管理者に多くの利点があります。  
  
-   **セキュリティ。**  アーキテクチャ [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] セキュリティで保護されたデータベースを保持およびデータベース インスタンスの操作から R セッションの実行を分離します。  
  
     R スクリプトを実行しで定義されている同じセキュリティ ロールを使用して、R のジョブで使用されるデータを管理することを確認する権限のあるユーザーを指定する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
-   **信頼性。**  R セッションで問題が発生した場合でも、サーバーが通常どおりに実行し続けるように、R セッションは個別のプロセスで実行されます。  
  
-   **リソース管理。**  R ランタイムに割り当てられるリソースの量を制御し、大規模な計算によりサーバーの全体的なパフォーマンスが損なわれないようにすることができます。  
  
 関連のタスクと概念の詳細については、「 [Managing and Monitoring R Solutions](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)」を参照してください。  
  
## アーキテクトや ETL 設計者: R と SQL Server にまたがる統合ワークフローの作成  
 データ エンジニアは、ETL ソリューションを設計し、ビルドします。 アーキテクトは、競合する補完的ビジネス ニーズに対応するデータ プラットフォームを設計します。  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の緊密な統合ビジネス インテリジェンスおよびデータ ウェアハウスのスタック、エンタープライズ クラウドおよびデータ移動のツールや Hadoop などの他の Microsoft ツールと高度な分析を昇格する必要のあるデータのエンジニアおよびシステムの設計者にメリットの配列を提供します。  
  
-   **幅広い一連の使い慣れた開発ツール。**  R ソリューションの開発時は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] およびシステム ストアド プロシージャを使用して、データセットを設定したり、R ジョブを実行したり、予測を取得したりします。 データ サイエンス ツールで追加の並列ワークフローを設計する必要はありません。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]の使い慣れた環境で、データ パイプラインをビルドします。  
  
     クラウド データを使用する必要がある場合、 Azure Data Factory および Azure SQL Database のサポートを簡単に変換し、データの管理、およびワークフローだけで使用するクラウドのデータ ソースなどの内部設置型の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ。  
  
-   **ワークフローの作成と管理。**  ジョブとシステム ストアド プロシージャを使用して、R スクリプトを含むワークフローを作成のスケジュールを設定します。  
  
 関連する手順と概念の詳細については、次を参照してください。 [作成ワークフロー SQL Server では、その使用 R](../../advanced-analytics/r-services/creating-workflows-that-use-r-in-sql-server.md)します。  
  
## 参照  
 [SQL Server R Services の概要](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
  
  