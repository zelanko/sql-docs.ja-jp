---
title: "Analysis Services | Microsoft Docs"
ms.date: "03/28/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "Analysis Services, Analysis Services の概要 - 多次元データ"
  - "SSAS"
  - "Analysis Services"
  - "SQL Server Analysis Services, Analysis Services の概要 - 多次元データ"
  - "SQL Server Analysis Services (SQL Server Analysis Services)"
  - "多次元データ [Analysis Services]"
  - "SSAS, Analysis Services の概要 - 多次元データ"
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
caps.latest.revision: 60
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 60
---
# Analysis Services
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は、意思決定支援とビジネス分析に使用されるオンライン分析データ エンジンであり、ビジネス レポートおよび、Power BI、Excel、Reporting Services レポート、他のデータ可視化ツールのようなクライアント アプリケーションによって使用される分析データを提供します。  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の一般的なワークフローには、多次元またはテーブルのデータ モデルを作成し、そのモデルをデータベースとして [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスに配置し、データまたはメタデータが読み込まれるようにデータベースを処理し、データ更新を設定し、エンドユーザーによるデータへのアクセスを許可する権限を割り当てることが含まれます。 準備が完了すると、複数の用途を持つこのセマンティック データ モデルに、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] をデータ ソースとしてサポートしている任意のクライアント アプリケーションがアクセスできるようになります。  
  
 モデルは、外部データ システムから取得したデータによって作成されます。通常は外部データ システムとして、SQL Server または Oracle リレーショナル データベース エンジンでホストされているデータ ウェアハウスを使用します (テーブル モデルでは、追加のデータ ソースの種類もサポートされています)。 モデルは、キューブなどのクエリ オブジェクトを指定しますが、複数のキューブ、計算、KPI (ビジネス ロジック、ナビゲーションやドリルスルー動作などの相互作用をカプセル化する) で使用できるディメンションも指定します。  
 
## <a name="analysis-services-on-premises-and-in-the-cloud"></a>オンプレミスとクラウドの Analysis Services
Analysis Services がクラウドで Azure のサービスとして使用できるようになりました。 現在、Azure Analysis Services のプレビュー版では互換性レベルが 1200 のテーブル モデルがサポートされています。 DirectQuery、パーティション、行レベルのセキュリティ、双方向のリレーションシップ、および翻訳がすべてサポートされます。 詳細を確認し、無料版をお試しになる場合は、「[Azure Analysis Services](https://azure.microsoft.com/en-us/services/analysis-services/)」を参照してください。 
  
## <a name="server-mode"></a>サーバー モード  
 構成中に [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] セットアップを利用し、Analysis Services をインストールするとき、そのインスタンスのサーバー モードを指定します。  各モードには、特定の Analysis Services ソリューションに特有の機能が含まれています。  
  
-   **多次元モードとデータ マイニング モード** - OLAP モデリング構造 (キューブ、ディメンション、メジャー) を実行します。  
  
-   **テーブルモード** - インメモリ リレーショナル データ モデリング構造 (モデル、表、列) を実行します。  
  
     テーブル モデルは、最新機能を使用し、既定の互換性レベル 1200 で作成することも、以前の 1103 互換性レベルで作成することもできます。 それぞれの互換性レベルには、大きな違いがあります。 レベルの違いについては、「[Analysis Services でのテーブル モデルの互換性レベル](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)」を参照してください。  
  
-   **Power Pivot Mode** - SharePoint 上で [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] と Excel データ モデルを実行します ([!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for SharePoint は中間層のデータ エンジンであり、SharePoint でホストされているデータ モデルの読み込み、クエリ、更新を実行します)。  
  
 1 つのインスタンスを構成するとき、利用できるモードは 1 つだけです。後で変更することはできません。  同じサーバーで複数のインスタンスを異なるモードでインストールできますが、セットアップを実行し、インスタンスごとに構成設定を指定する必要があります。  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の機能は、エディションによって異なります。 詳細については、「[SQL Server 2016 の各エディションでサポートされる機能](../sql-server/sql-server-2016-の各エディションとサポートされる機能.md)」を参照してください。 
  
## <a name="authoring-solutions"></a>ソリューションの作成  
 モデルを作成するには、SQL Server データ ツール (「 [Analysis Services で使用するツールとアプリケーション](../analysis-services/tools-and-applications-used-in-analysis-services.md)」を参照) を使用して、テーブルまたは多次元を選択し、データ マイニング プロジェクト テンプレートを選択します。 プロジェクト テンプレートには、モデルで必要とされるすべてのオブジェクトのフォルダーが含まれています。 ウィザードを使用して、データ ソース、データ ソース ビュー、ディメンション、キューブ、ロールなど、多くの基本的な要素を作成することができます。  
  
## <a name="documentation-by-area"></a>領域別のドキュメント  
Analysis Services に関するドキュメントは、作成するプロジェクトの種類に対応するセクション別に分類されます。 それぞれのモードまたは機能領域の詳細については、次のリンクから選択してください。  
   
 ![小さいファイル フォルダー アイコン](../analysis-services/media/filefolder-small.png "小さいファイル フォルダー アイコン") [新機能](../analysis-services/what-s-new-in-analysis-services.md)  
  
 ![小さいファイル フォルダー アイコン](../analysis-services/media/filefolder-small.png "小さいファイル フォルダー アイコン") [テーブル ソリューションと多次元ソリューションの比較](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)  
  
 ![小さいファイル フォルダー アイコン](../analysis-services/media/filefolder-small.png "小さいファイル フォルダー アイコン") [テーブル モデル](../analysis-services/tabular-models/tabular-models-ssas.md)  
  
 ![小さいファイル フォルダー アイコン](../analysis-services/media/filefolder-small.png "小さいファイル フォルダー アイコン") [多次元モデル](../analysis-services/multidimensional-models/multidimensional-models-ssas.md)  
  
 ![小さいファイル フォルダー アイコン](../analysis-services/media/filefolder-small.png "小さいファイル フォルダー アイコン") [データ マイニング](../analysis-services/data-mining/data-mining-ssas.md)  
  
 ![小さいファイル フォルダー アイコン](../analysis-services/media/filefolder-small.png "小さいファイル フォルダー アイコン") [ Power Pivot for SharePoint](../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
 ![小さいファイル フォルダー アイコン](../analysis-services/media/filefolder-small.png "小さいファイル フォルダー アイコン") [Analysis Services インスタンス管理](../analysis-services/instances/analysis-services-instance-management.md)  
   
 ![小さいファイル フォルダー アイコン](../analysis-services/media/filefolder-small.png "小さいファイル フォルダー アイコン") [Analysis Services チュートリアル](../analysis-services/analysis-services-tutorials-ssas.md)  
  
![小さいファイル フォルダー アイコン](../analysis-services/media/filefolder-small.png "小さいファイル フォルダー アイコン") [Analysis Services の開発者向けドキュメント](https://msdn.microsoft.com/library/bb500153(SQL.130).aspx)  
 
![小さいファイル フォルダー アイコン](../analysis-services/media/filefolder-small.png "小さいファイル フォルダー アイコン") [テクニカル リファレンス (SSAS)](../analysis-services/powershell/technical-reference-ssas.md)