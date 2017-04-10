---
title: "R でのデータ探索および予測モデリング | Microsoft Docs"
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
ms.assetid: bf6de7e2-f394-4b8a-a4b7-0b8dadf25426
caps.latest.revision: 20
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 19
---
# R でのデータ探索および予測モデリング
  多くの場合、データ サイエンティストは R を使用してデータを探索し、予測モデルを構築します。 通常、適切な予測モデルが構築されるまで、試行錯誤が繰り返されます。 経験豊富なデータ サイエンティストであれば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続し、RODBC パッケージを使用してローカル ワークステーションにデータをフェッチし、データを探索して標準的な R パッケージを使用して予測モデルを構築する場合があります。  
  
 ただし、この方法には欠点があります。 データの移動が遅い、非効率である、あるいは安全でない場合があり、R 自体のパフォーマンスとスケールに制限があります。 これらの欠点は、大量のデータを移動して分析する必要がある場合、またはコンピューターで使用可能なメモリに収まらないデータ セットを使用する場合に、より明白になります。  
  
 R 関数を含む、新しい拡張可能なパッケージを使用してこれらの課題を克服できます [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]します。 **RevoScaleR** パッケージには、並列処理とスケール機能を提供するために再設計された、最も一般的ないくつかの R 関数の実装が含まれます。 また、RevoScaleR パッケージでは *実行コンテキスト*の変更もサポートされます。 つまり、ソリューション全体または 1 つの関数のみの場合、ローカル ワークステーションではなく、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスをホストするコンピューターのリソースを使用して計算を行う必要があることを示すことができます。 これを行う利点は複数あります。不要なデータ移動を回避し、サーバー コンピューター上のより多くの計算リソースを活用することができます。  
  
 このセクションでは、データ サイエンティスト向けの [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の使用方法および R ソリューションの開発とテストに関するタスクの実行方法について説明します。  
  
##  <a name="bkmk_RDevTools"></a> R 開発ツール  
 Microsoft R クライアントでは、データ科学者に、開発し、予測モデルのテストの完全な環境が与えられます。 R のクライアントは次のとおりです。  
  
-  **[!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)]:** R ランタイムおよび一連の標準的な R 操作のパフォーマンスを向上 Intel math カーネル ライブラリなどのパッケージの配布。  
  
-   **RevoScaleR:** を使用すると、R パッケージのインスタンスへの計算のプッシュ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 [!INCLUDE[rsql_rre-noversion](../../includes/rsql-rre-noversion-md.md)]」を参照してください。 一般的な R 関数は高いパフォーマンスと拡張性を提供する設計が変更されましたのセットも含まれています。 これらの強化された関数は、 **rx** プレフィックスで識別できます。 さまざまなソースの強化されたデータ プロバイダーも含まれています。これらの関数が付いている **Rx**します。  
  
-   **可能な開発ツールを無料:** など、R をサポートする任意の Windows ベースのコード エディターを使用する [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] または RStudio です。 ダウンロード [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)] R RGui.exe などの一般的なコマンド ライン ツールも含まれます。  
  
##  <a name="bkmk_packages"></a> R の環境とパッケージ  
 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] でサポートされている R 環境は、ランタイム、オープン ソース言語、複数のパッケージでサポートされ拡張されたグラフィック エンジンで構成されます。 この言語では、パッケージを使用して実装されるさまざまな拡張機能を使用できます。  
  
 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] で使用できる追加の R パッケージのソースをいくつか以下に示します。  
  
  
-   パブリック リポジトリから汎用 R パッケージです。 データ サイエンティストが使用できる 6,000 個を超えるパッケージをホストする、CRAN などのパブリック リポジトリから最も一般的なオープン ソース R パッケージを取得することができます。  
  
     追加のパッケージは、財務やゲノムなど、特殊なドメインで予測分析をサポートするために使用できます。  
  
     Windows プラットフォーム向け R パッケージ zip ファイルとして提供されるとできますダウンロードしてインストール GPL ライセンスに基づいてします。  
  
     使用するためのサード パーティ製のパッケージをインストールする方法については [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], を参照してください [SQL Server の他の R パッケージのインストール](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)  
  
-   その他のパッケージとで提供されるライブラリ [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]します。   
  
      **RevoScaleR** パッケージには、高パフォーマンスのビッグ データ分析、一般的なデータ サイエンス タスク、Naive Bayes、線形回帰、タイム シリーズ モデルとニューラル ネットワーク、および高度な数学ライブラリの最適な学習器をサポートする機能の強化されたバージョンが含まれています。  
  
     **RevoPemaR** パッケージでは、R で独自の並列外部メモリ アルゴリズムを開発できます。  
  
     これらのパッケージとその使用方法の詳細については、次を参照してください。 [データの探索と予測モデリングと #40 です。チュートリアル: SQL Server R サービスと #41;](../../advanced-analytics/r-services/sql-server-r-services.md)します。  
  
## データ ソースと計算コンテキストの使用  
 RevoScaleR パッケージを使用して接続するときに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 、R コードで使用するいくつか重要な新しい関数があります。  
  
-   [RxSqlServerData](RxSqlServerData.md) への接続を強化されたデータをサポートするために RevoScaleR パッケージで指定された関数は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
     R コードでこの関数を使用して、 *データ ソース*を定義します。 データ ソース オブジェクトではデータがあるテーブルとサーバーを指定し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に対するデータの読み取りおよび書き込みタスクを管理します。  
  
-    [RxInSqlServer](rxInSqlServer.md) 関数を使用して、指定、 *計算コンテキスト*します。  つまりを示す R コードを実行する必要があります。 ローカル ワークステーション、またはホストするコンピューターで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス。  
  
     計算コンテキストを設定すると、R の操作が RevoScaleR パッケージで提供され、関連する関数をリモートの実行コンテキストをサポートする唯一の計算が適用されます。 一般に、CRAN パッケージを標準に基づく R ソリューションでは実行できませんリモート コンピューティングのコンテキストで実行できる場合、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューターを T-SQL で開始された場合。 ただし、使用することができます、 `rxExec` R の個々 の関数を呼び出すし、それらをリモートで実行する関数 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]します。  
  
 作成し、データ ソースとの実行コンテキストを操作する方法の例については、チュートリアルを参照して開いた後。
 
 + [データ サイエンスの詳細情報](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
 +  [RevoScaleR SQL Server の概要](https://msdn.microsoft.com/microsoft-r/rserver/rserver-scaler-sql-server-getting-started)します。  
  
## 運用環境への R コードのデプロイ  
 データ サイエンスの重要な部分は、自分の分析を他のユーザーに提供したり、予測モデルを使用してビジネスの結果またはプロセスを改善することです。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]では、R スクリプトまたはモデルの準備ができている場合、運用環境に簡単に移行することができます。  
  
 実行するコードを移動する方法の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], を参照してください [R コードの任せています](../../advanced-analytics/r-services/operationalizing-your-r-code.md)します。  
  
 通常、デプロイ プロセスは、運用環境では不要なコードを削除するためのスクリプトのクリーンアップから始まります。 データに近いの計算を移動するより効率的に移動し、集計、または、R. 内のすべてを実行するよりデータを表示する方法を見つける可能性があります。  
  
 データ サイエンティストは、パフォーマンスを向上させる方法は、データベース開発者に問い合わせてくださいをソリューションの場合に特にデータ クレンジングと特徴エンジニア リングすることがありますでより効率的に SQL のことをお勧めします。 ビルドまたはモデルをスコア付けのワークフローが失敗しないする入力データが適切な形式で使用できることを確認に必要な ETL プロセスに変更します。  
  
##  <a name="bkmk_SQLInR"></a> このセクションの内容  

[スケーラ関数と CRAN R 関数の比較](Summary%20of%20rx%20Functions.md)

[SQL Server で操作するためのスケーラ関数](../../advanced-analytics/r-services/scaler-functions-for-working-with-sql-server-data.md)
   
## 参照  

 
 [SQL Server R Services の機能とタスク](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)   
 
 [R コードの運用](../../advanced-analytics/r-services/operationalizing-your-r-code.md)  
  
  