---
title: "データ サイエンスの詳細: RevoScaleR パッケージの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
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
ms.assetid: c2efb3f2-cad5-4188-b889-15d68b742ef5
caps.latest.revision: 18
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 17
---
# データ サイエンスの詳細: RevoScaleR パッケージの使用
このチュートリアルは、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] で提供されている拡張 R パッケージを紹介することを目的とします。 スケーラブルなエンタープライズ フレームワークを使用して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の R パッケージを実行する方法について説明します。   これらのスケーラブルな R 関数を使用することで、データ サイエンティストは、ローカル コンテキストまたはサーバー コンテキストで実行されるカスタム R ソリューションを構築し、高パフォーマンスのビッグ データ分析をサポートできます。  
  
このチュートリアルでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と R ワークステーションの間でデータを移動する方法、データを分析してプロットする方法、モデルを作成して配置する方法について説明します。  
    
## 概要 
 
ScaleR パッケージの柔軟性と処理能力を示すため、このチュートリアルでは、データの移動と計算コンテキストの切り替えを頻繁に行います。

+ 最初に、CSV ファイルまたは XDF ファイルからデータを取得します。 RevoScaleR パッケージの関数を使用して、データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にインポートします。    
+ モデルのトレーニングとスコア付けは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の計算コンテキストで実行されます。 
    スコア付けの結果を保存するために、**rx** 関数を使用して新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルを作成します。    
+ サーバーとローカル両方の計算コンテキストで、プロットを作成します。  
+ モデルのトレーニングでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに既に格納されているデータを使用します。 計算はすべて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで実行されます。    
+ データのサブセットを抽出し、それを分析時に再利用できるように XDF ファイルとしてローカル ワークステーション上に保存します。    
+ スコア付けのプロセス中に使用する新しいデータは、ODBC 接続を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースから抽出されます。 すべての計算がローカル ワークステーションで実行されます。 
+ 最後に、サーバーの計算コンテキストを使用して、カスタム R 関数に基づくシミュレーションを実行します。

### 作業開始  

このチュートリアルの所要時間は約 1 時間です。これに、セットアップの時間は含まれていません。  

-   [レッスン 1: R を使用して SQL Server のデータを操作する](../../advanced-analytics/r-services/lesson-1-work-with-sql-server-data-using-r-data-science-deep-dive.md)  
  
-   [レッスン 2: R スクリプトの作成と実行](../../advanced-analytics/r-services/lesson-2-create-and-run-r-scripts-data-science-deep-dive.md)  
  
-   [レッスン 3: R を使用したデータの変換](../../advanced-analytics/r-services/lesson-3-transform-data-using-r-data-science-deep-dive.md)  
  
-   [レッスン 4: ローカル計算コンテキストでデータを分析する](../../advanced-analytics/r-services/lesson-4-analyze-data-in-local-compute-context-data-science-deep-dive.md)  
  
-   [レッスン 5: 簡単なシミュレーションを作成する](../../advanced-analytics/r-services/lesson-5-create-a-simple-simulation-data-science-deep-dive.md)  

      
### 対象読者  
  
このチュートリアルの対象読者は、データ サイエンティスト、または R、および調査、統計分析、モデル調整などのデータ サイエンス タスクについて既にある程度理解している方です。  ただし、すべてのコードが提供されているので、必要なサーバーとクライアントの環境があれば、コードを簡単に実行して調べることができます。  
  
読者はまた、[!INCLUDE[tsql](../../includes/tsql-md.md)] 構文に精通していて、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] またはその他のデータベース ツール (Visual Studio など) を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースにアクセスする方法を理解している必要があります。  
  
> [!TIP]  
> 中断した箇所からを容易に再開できるように、レッスンの合間に R ワークスペースを保存してください。  
  
### 前提条件  
  
-   **R がサポートされているデータベース サーバー**  
  
    [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] をインストールして、SQL Server R Services (in-Database) を有効にします。 これについては、[SQL Server 2016 オンライン ブック](http://msdn.microsoft.com/library/mt696069(SQL.130).aspx)をご覧ください。  
  
-   **データベース権限**  
  
    モデルのトレーニングで使用するクエリを実行するには、データが格納されているデータベースに対して **db_datareader** 権限が必要です。  
  
  
-   **データ サイエンスのワークステーション**  
  
    RevoScaleR パッケージをインストールする必要があります。 このパッケージをインストールする最も簡単な方法は、Microsoft R Server (スタンドアロン) または Microsoft R Client をインストールすることです。 詳しくは、「[データ サイエンス クライアントのセットアップ](http://msdn.microsoft.co/library/mt696067(SQL.130).aspx)」をご覧ください。
      
    > [!NOTE] 
    > 他のバージョンの Revolution R Enterprise または Revolution R Open はサポートされていません。 
    > 
    > リモート計算コンテキストを使用できるのは ScaleR 関数だけなので、R のオープン ソース ディストリビューション (R 3.2.2 など) はこのチュートリアルでは動作しません。 
  
-   **追加の R パッケージ**  
  
    このチュートリアルでは、**dplyr**、**ggplot2**、**ggthemes**、**reshape2**、および **e1071** のパッケージをインストールする必要があります。 手順は、チュートリアルの中で説明します。  
  
    すべてのパッケージを、トレーニングが実行される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにもインストールする必要があります。 パッケージのインストール先を、SQL Server で使用される R パッケージ ライブラリとすることが重要です。 **ユーザー ライブラリにはパッケージをインストールしないでください。** このフォルダーにパッケージをインストールする権限がない場合は、データベース管理者に頼んでパッケージを追加してもらってください。   
  
詳細については、[「データ サイエンスのチュートリアルの前提条件 (SQL Server R Services)」](../../advanced-analytics/r-services/prerequisites-for-data-science-walkthroughs-sql-server-r-services.md)を参照してください。  
  
## 分散 R ソリューションのデータ戦略
    
一般に、ローカル開発環境で R スクリプトの記述および実行を開始する前に、必ず、少し時間をかけて、データの使用量を計画し、最適なパフォーマンスを引き出すためにソリューションの各部分を実行する場所を決定します。  

このチュートリアルでは、高パフォーマンスの関数を使用して、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] に含まれるデータの分析、モデルの構築、プロットの作成を行います。 他のオープン ソース R パッケージの派生関数と区別するため、これらの関数は一般に ScaleR または Microsoft R と呼ばれます。 Microsoft R とオープン ソース R の違いの詳細については、「[Microsoft R Getting Started Guide](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started#microsoft-r-products)」(Microsoft R 概要ガイド) をご覧ください。 

ScaleR 関数を使用する重要な利点は、ScaleR がローカルまたはサーバーの *"データ ソース"* の使用、およびローカルまたはリモートの *"計算コンテキスト"* の使用をサポートしていることです。  したがって、このチュートリアルを進めながら、実際のソリューションに採用する必要のあるデータ戦略について考えてください。
  
-   **どのような種類の分析を実行しますか? ** それは自分だけで使用するものですか、それともモデル、結果、グラフを他の人と共有しますか?
 
    このチュートリアルでは、開発環境とサーバーの間で結果を双方向に移動して共有と分析を容易にする方法を説明します。 
  
-   **R パッケージでリモート実行をサポートする必要がありますか?** [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] によって提供される ScaleR パッケージのすべての関数は、リモート計算コンテキストで実行でき、場合によっては並列実行を使用できます。 これに対し、サードパーティのパッケージの関数では、シングル スレッド実行のために追加リソースが必要な場合があります。 
    
    このチュートリアルでは、必要に応じてローカル計算コンテキストとリモート計算コンテキストを切り替えて、サーバーのリソースを利用する方法を説明します。 また、標準的な R 関数を *rxExec* にラップして任意の R 関数のリモート実行をサポートする方法も説明します。
    
  
-   **データはどこにありますか、データの特性はどのようなものですか? **  データがローカルに存在する場合は、すべての新しいデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアップロードするか、またはローカルでトレーニングしてモデルのみをデータベースに保存するかを、決定する必要があります。 ただし、実稼働環境に配置するときは、エンタープライズ データからトレーニングし、ETL プロセスを使用してデータをクリーンアップして読み込むことが必要な場合があります。  
  
-   スコア付けデータにも同様の質問が適用されます。 ワークステーションでデータをスコア付けするためにデータ パイプラインを作成しますか、あるいはエンタープライズ データ ソースを使用しますか?  ETL プロセスの一環としてデータのクレンジングおよび準備を実行する必要がありますか、または 1 回限りの実験を実行しますか?  

    このチュートリアルでは、ローカル R 環境と SQL Server の間で効率的かつ安全にデータを移動する方法を説明します。 
  
-   **どの計算コンテキストを使用する必要がありますか?** モデルのトレーニングはサンプリングされたデータでローカルに行い、テストと実稼働でサーバー データを使用するように切り替えることができます。

    このチュートリアルでは、R を使用して SQL Server と R の間でデータを移動する方法を説明します。また、XDF ファイルを使用してデータを操作する方法、および ScaleR 関数を使用してまとめてデータを処理する方法についても説明します。  
  
 
  
## 次の手順  
[レッスン 1: R を使用した SQL Server データの操作 (データ サイエンスの詳細)](../../advanced-analytics/r-services/lesson-1-work-with-sql-server-data-using-r-data-science-deep-dive.md)  
  
  
  
