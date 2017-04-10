---
title: "SQL Server で R を使用するワークフローの作成 | Microsoft Docs"
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
ms.assetid: 34c3b1c2-97db-4cea-b287-c7f4fe4ecc1b
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# SQL Server で R を使用するワークフローの作成
  リレーショナル データベースは、トランザクション処理、ストレージ、およびデータのクエリを実行するスケーラブルなソリューションを提供するための高度に最適化されたテクノロジです。 ただし、従来 R ソリューションが通常のいましたをさらにデータの探索とモデリングを実行する、CSV 形式で多くの場合、さまざまなソースからデータをインポートする方法。 これは非効率であるだけでなく、危険な方法です。  
  
 使用して [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 複数の利点を提供します。  
  
-   データのセキュリティです。 R の電源が、データベースに読み込まれるデータのソースに近い場所にします。 無駄であり、またはセキュリティ保護されていないデータの移動を回避できます。  
  
-   速度です。 データベースは、セット ベースの操作に適しています。 さらに、データベースの最新の革新的技術など、メモリ内のテーブルおよび列指向データ ストレージをさらにデータ サイエンスので向上集計の高速化します。  
  
-   統合。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] その他の多くのデータ管理タスクと enterprise を使用するアプリケーションの操作のサーバーの全体のポイントです。 既にデータベースにデータを使用しているにより、データが一貫して最新の状態であります。 R のデータを処理ではなくなど、エンタープライズ データ パイプラインに依存することができます [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Azure Data Factory とします。 結果の分析レポートは、Power BI を使用して簡単または [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]です。  
  
 さまざまなデータ処理や分析タスクで SQL と R を正しく組み合わて使用することで、データ サイエンティストと開発者の両方の生産性がさらに向上します。 このセクションでは、R と、データの転送、分析、レポートのための他のエンタープライズ ソリューションの統合方法について説明します。  
  
##  <a name="bkmk_ssis"></a> R とデータベースにまたがる効率的なワークフローの作成  
 データ サイエンス ワークフローは何度も繰り返され、スケーリング、集計、確率計算、および属性の名前変更とマージなど、多くのデータ変換を含みます。 データの科学者は R、Python、または別の言語でこれらのタスクの多くの作業に慣れています。ただし、企業データにこのようなワークフローを実行するには、ETL ツールやプロセスとシームレスに統合する必要があります。  
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] TRANSACT-SQL およびストアド プロシージャを使用して、R の複雑な操作を実行することができます再最小限の開発作業を行わず、既存の ETL プロセスと R に固有のタスクを統合することができます。 はなくメモリ ntensive タスクのチェーンを実行すると、R よりもデータの準備を最適化できますなど、最も効率的なツールを使用して [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] と [!INCLUDE[tsql](../../includes/tsql-md.md)]です。  
  
 たとえば、"R"を組み合わせることができます [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ようなシナリオで。  
  
-   使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] SQL データベースに必要なオブジェクトを作成するタスク  
  
-   条件分岐を使用して、R ジョブの計算コンテキストを切り替える。  
  
-   独自のデータを生成する R ジョブを実行する。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、テキスト変数で保存されている R スクリプトを呼び出す。  
  
### サンプルおよびリソース  
 [SQL Server 2016 の SSIS と R のサービスを使用して、machine learning プロジェクトは運用に対応します。](https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/)  
  
 このブログの投稿で学習する方法。  
  
-   SQL 実行タスクで R を使用してデータを生成しの保存 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   ストアド プロシージャを使用して R モデルのトレーニングをデータベースに格納  
  
-   スクリプト タスクおよび SQL 実行タスクを使用して、モデルのスコア付けを実行します。  
  
##  <a name="bkmk_ssrs"></a> R とエンタープライズ レポート ツールにまたがる視覚エフェクトの作成  
 R ではチャートや注意を引く視覚エフェクトを作成できますが、外部データ ソースに十分に統合されません。つまり、各チャートまたはグラフを個別に生成する必要があります。 共有も困難になります。  
  
 使用して [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], 、経由での R の複雑な操作を実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャで、さまざまなエンタープライズ レポートなどのツールで簡単に利用する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と Power BI します。  
  
-   R スクリプトから返されたグラフィック オブジェクトを視覚化します。   
    使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   Power BI でのテーブルの使用  
  
## サンプルおよびリソース  
 [Microsoft Reporting Services (SSRS) 用の R グラフィックス デバイス](https://rgraphicsdevice.codeplex.com/)  
  
 この CodePlex プロジェクトは、カスタム レポート アイテムを作成するためにコードでは、R のグラフィックス出力をレンダリングで使用できるイメージとして [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートします。  カスタム レポート アイテムを使用すると、次の操作を実行できます。  
  
-   グラフと R グラフィックス デバイスを使用して作成されたプロット発行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ダッシュ ボード  
  
-   渡す [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] R プロットするパラメーター  
  
> [!NOTE]  
>  Visual Studio でだけでなく、Reporting Services サーバーで Reporting Services の R グラフィックス デバイスをサポートするコードをインストールする必要に注意してください。 手動によるコンパイルと構成も必要です。  
  
  