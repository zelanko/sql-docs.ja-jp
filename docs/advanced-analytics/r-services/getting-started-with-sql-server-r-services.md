---
title: "SQL Server R Services の概要 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "12/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: 5b28a663-effe-41f6-9bda-eda95f0c6943
caps.latest.revision: 34
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 32
---
# SQL Server R Services の概要
 高度な分析ソリューションを構築する一般的なワークフローは、データ探索と予測モデリングから始まりますが、データ サイエンティストは、すぐにタスクに役立つ R スクリプトとモデルを開発しています。 スクリプトとモデルが準備できたら、運用環境に展開し、既存または新規のアプリケーションと統合できます。   
  
SQL Server R Services は、このようなデータ サイエンス タスクの完了に役立つように設計されています。 お気に入りの R または SQL ツールを引き続き使用することもできますが、SQL Server R サービスは、追加のハードウェアなしで何十億件ものレコードまで分析可能で、パフォーマンスを向上し、不要なデータ移動を回避できます。 別の言語で書き換えることなく、R コードを運用環境に配置できるようになりました。 また、SQL では実装が困難な統計計算にも R を使いやすくなりました。 同時に、インメモリ データベース エンジン、列ストア インデックスなどの SQL Server の機能を活用して最大のパフォーマンスを達成できます。  
  
以下のセクションでは、一般的な分析ワークフローの概要と、SQL Server R Services で分析ワークフローを有効にする方法について説明します。  

> [!TIP] 迅速に導入するには、このチュートリアルを参照してください。 このチュートリアルでは、スキー レンタル業で、機械学習を使用して今後のレンタル状況を予測し、需要に合わせてスタッフのスケジュールを作成する方法を学びます。
> 
> [SQL Server と R を使用してインテリジェンス アプリを構築する](https://www.microsoft.com/sql-server/developer-get-started/r)


  
-   **開発**  
  
     通常、データ サイエンティストは R を使用してデータを探索し、任意の R IDE を使用してそのワークステーションから予測モデルを構築します。 データ サイエンティストは、適切な予測モデルが構築されるまで、テストとチューニングを繰り返します。 
     
     [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] クライアント コンポーネントは、データ サイエンティストに実験や開発に必要なすべてのツールを提供します。 これらのツールには、R ランタイム、標準的な R 演算のパフォーマンスを向上させる Intel Math Kernel Library、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] での R コードの実行をサポートする一連の拡張 R パッケージが含まれます。  
  
     データ サイエンティストは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、通常どおり、ローカル分析のためにクライアントにデータを移動できます。 ただし、より優れたソリューションは、 **ScaleR** API を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに計算をプッシュすることです。これにより、コストのかかる安全でないデータ移動を回避できます。  
  
     R ソリューションを開発するために、データ サイエンティストは R をサポートする任意の Windows ベースの IDE を使用できます。これには、[R Tools for Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx) や RStudio が含まれます。  
 
    ![rsql_keyscenario2](../../advanced-analytics/r-services/media/rsql-keyscenario2.PNG) 
 
     詳細については、「 [Data Exploration and Predictive Modeling with R](../../advanced-analytics/r-services/data-exploration-and-predictive-modeling-with-r.md)」を参照してください。  

  
-   **最適化**  
  
     R での大規模なデータセットを分析する際に、多くの場合、データ サイエンティストはパフォーマンスやスケールの問題に直面します。これは、共通ランタイムの実装がシングル スレッドであり、ローカル コンピューター上の使用可能なメモリに収まるデータ セットしか格納できないためです。 パフォーマンスを向上させ、より多くのデータを処理するために、データ サイエンティストは、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の一部として提供される **ScaleR** API を使用できます。 **RevoScaleR** パッケージには、並列処理とスケール機能を提供するために再設計された、最も一般的ないくつかの R 関数の実装が含まれます。 パッケージには、通常ははるかに大きなメモリと計算能力がある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに計算をプッシュして、パフォーマンスとスケールをさらに向上させる機能も含まれます。  
  
     詳細については、「 [Data Exploration and Predictive Modeling with R](../../advanced-analytics/r-services/data-exploration-and-predictive-modeling-with-r.md)」を参照してください。  
  
-   **配置**  
  
     R スクリプトまたはモデルを運用環境で使用する準備ができたら、データベース開発者はストアド プロシージャにコードまたはモデルを埋め込み、アプリケーションから保存したコードを呼び出すことができます。 R コードの格納と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からの実行には多くの利点があります。便利な [!INCLUDE[tsql](../../includes/tsql-md.md)] インターフェイスを使用でき、計算はすべてデータベースで行われるため、不要なデータ移動を回避できます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、運用環境で予測モデルからスコアを生成したり、R で生成されたプロットを返し、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]などのアプリケーションで表示したりできます。  
  
     システム ストアド プロシージャに埋め込まれた R コードをさらに最適化する場合は、より大規模なデータセットを操作可能な [ScaleR](https://msdn.microsoft.com/microsoft-r/rserver/rserver-scaler-getting-started) パッケージ API を使用することをお勧めします。 これらのパッケージでは、マルチスレッド、マルチコア、マルチプロセス計算でのデータベース内実行がサポートされます。  
  
     R コードを運用環境にデプロイする必要がある場合、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では R と SQL の両方の長所を活かすことができます。 SQL を使用して実装するのが困難な統計計算で R を使用できますが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能を利用し、メモリ内データベース エンジンや列ストア インデックスなどの機能を使用すれば、最高のパフォーマンスを実現できます。  
  
    ![rsql_keyscenario1](../../advanced-analytics/r-services/media/rsql-keyscenario1.PNG)  
  
     詳細については、「[R コードの運用](../../advanced-analytics/r-services/operationalizing-your-r-code.md)」を参照してください。  
 
 > [!TIP] SQL Server をデータ サイエンスと統合する方法については、Microsoft Virtual Academy から無料でダウンロードできるブック「[Data Science with Microsoft SQL Server 2016](https://mva.microsoft.com/ebooks/)」(データ サイエンスと Microsoft SQL Server 2016) を参照してください。

-   **管理および監視**  
  
     [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では、データベース エンジンをセキュリティで保護した状態で R セッションを分離する新しい拡張可能アーキテクチャを使用します。 また、R コードを実行できるユーザーを制御し、R コードでアクセス可能なデータベースを指定することもできます。 R ランタイムに割り当てられるリソースの量を制御し、大規模な計算によりサーバーの全体的なパフォーマンスが損なわれないようにすることができます。  
  
     R ジョブを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行すれば、アナリストが使用するデータを制御および監査したり、他のストアド プロシージャの場合と同じように、R スクリプトを含むジョブや作成者ワークフローをスケジュールしたりすることもできます。  
  
     詳細については、「 [Managing and Monitoring R Solutions](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)」をご覧ください。  
  
  
-   **統合**  
  
     エンタープライズ ツールを取得して一部の外部 R ランタイム環境で作業するために IT の予算を使う必要はなくなりました。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の使い慣れた環境で作業し、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] と [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を使用して、統合されたワークフローとレポート ソリューションを開発することができます。  
  
     詳細については、「[SQL Server で R を使用するワークフローの作成](../../advanced-analytics/r-services/creating-workflows-that-use-r-in-sql-server.md)」を参照してください。  
  
  
## <a name="how-do-i-get-it"></a>入手方法  
   
  
+   **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 以降をインストールし、R Services (In-Database) を有効にする**  
  
    [SQL Server R Services &#40;In-Database&#41; をセットアップする](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  
-   **クライアント ワークステーションをセットアップする**  
  
     [データ サイエンス クライアントをセットアップする](../../advanced-analytics/r-services/set-up-a-data-science-client.md)  
   
> [!TIP]   
>   
> R ジョブ用のサーバーを作成する必要があり、SQL Server は不要な場合は、 [Microsoft R Server](https://msdn.microsoft.com/library/mt674874.aspx)をお試しください。  
  
## <a name="how-to-run-r-code-using-sql-server-r-services"></a>SQL Server R Services を使用して R コードを実行する方法  
 インストールが完了したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャに R を埋め込むか、[!INCLUDE[tsql](../../includes/tsql-md.md)] データを操作するアドホック R スクリプトを記述して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で R コードを実行できます。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントから R を呼び出し、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で結果を返す方法  
  
     [Transact-SQL での R コードの使用](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md)  
  
-   SQL Server R Services を使用して高度な分析ソリューションを作成し、展開するまでの完全なフロー  
  
     [データ サイエンスのエンド ツー エンド チュートリアル](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md)  
  
-   スケーラブルで高パフォーマンスな分析のために RevoScaleR パッケージを使用する方法、および R 計算を SQL Server コンピューターにプッシュする方法  
  
     [データ サイエンスの詳細: RevoScaleR パッケージの使用](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
-   予測のためにモデルを呼び出したり、モデルを再トレーニングしたり、アプリケーションから予測を取得したりできるように、機能する R スクリプトを [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャに埋め込みます。  
  
     [SQL 開発者向けの高度な分析 (データベース内)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スタック内の関連ビジネス インテリジェンス ツールを使用して、機械学習プロセスを自動化します。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]を使用して、データ準備とレポート作成を自動化できます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] や Power View を使用したその他のレポートと共に、R プロットを表示できます。  
  
+ ソリューション テンプレートやサンプル R コードを含む追加のサンプル  
   [SQL Server R Services のチュートリアル](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server R サービス](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Microsoft R Server の概要 &#40;スタンドアロン&#41;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  