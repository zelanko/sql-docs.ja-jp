---
title: "SQL Server 2016 技術ドキュメント | Microsoft Docs"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.portal.f1"
helpviewer_keywords: 
  - "ドキュメント [SQL Server]、ホーム ページ"
  - "ヘルプ [SQL Server]"
  - "SQL Server、ドキュメント"
  - "ホーム ページ [SQL Server]"
  - "ヘルプ [SQL Server]、ドキュメント ホーム ページ"
  - "オンライン ブック [SQL Server]、ホーム ページ"
  - "ポータル ページ [SQL Server]"
ms.assetid: 674933a8-e423-4d44-a39b-2a997e2c2333
caps.latest.revision: 106
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# SQL Server 技術ドキュメント
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

 SQL Server のインストール、構成、および使用の際に役立つドキュメントです。 コンテンツには、エンド ツー エンドの例、コード サンプル、およびビデオが含まれています。 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 言語のトピックについては、「[言語リファレンス](../t-sql/language-reference.md)」を参照してください。

**SQL Server vNext**

最新のリリース ノートについては、「[SQL Server vNext リリース ノート](../sql-server/sql-server-vnext-release-notes.md)」を参照してください。

新機能に関する最新情報については、「[SQL Server vNext の新機能](../sql-server/what-s-new-in-sql-server-vnext.md)」を参照してください。
 
**SQL Server 2016:**
 
 [SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md)

[SQL Server 2016 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)
    
 **SQL Server をお試しください。**    
    
 - [**Evaluation Center から SQL Server 2016 をダウンロードする**](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)    
    
- **[SQL Server 2016 がインストール済みの Virtual Machine をすぐにご利用いただけます](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)**    
    
-  **[最新バージョンの SQL Server Management Studio をダウンロードする](https://msdn.microsoft.com/library/mt238290.aspx)**   
    
  
    
## <a name="sql-server-technologies"></a>SQL Server のテクノロジ    
    
|||    
|-|-|    
|![SQL database engine](../sql-server/media/sql-database-engine.png "SQL database engine")|**[データベース エンジン](../database-engine/configure-windows/sql-server-database-engine.md)**<br /><br /> データベース エンジンは、データの格納、処理、およびセキュリティ保護を目的としたコア サービスです。 データベース エンジンでは、組織で利用しているアプリケーションのうち、データの使用頻度が最も高いアプリケーションの要件を満たすように、アクセスの制御や高速なトランザクション処理が行われます。 また、高可用性を実現するためのさまざまなサポートも提供されます。|    
|![R Server](../sql-server/media/r-server.png "R Server")|**[R Services](../advanced-analytics/r-services/r-services.md)**<br /><br /> Microsoft R Services を使用すると、さまざまな方法で R 言語をエンタープライズ ワークフローに組み込むことができます。<br /><br /> [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] が R 言語を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] と統合するので、[!INCLUDE[tsql](../includes/tsql-md.md)] ストアド プロシージャを呼び出すことにより、簡単にモデルをビルド、再トレーニング、およびスコア付けすることができます。<br /><br /> Microsoft R Server は Hadoop や Teradata などのデータ ソースをサポートし、R を利用する企業にマルチプラット フォームのスケーラブルなサポートを提供します。|    
|![Data Quality Services](../sql-server/media/data-quality-services.png "Data Quality Services")|**[Data Quality Services](../data-quality-services/data-quality-services.md)**<br /><br /> SQL Server Data Quality Services (DQS) は、ナレッジ ドリブンのデータ クレンジング ソリューションを提供します。 DQS を使用すると、ナレッジ ベースを構築し、このナレッジ ベースを使用して、コンピューター支援型と対話形式の両方の方法で、データに対する修正および重複除去を行うことができます。 クラウドベースの Reference Data Services を使用すると、DQS を SQL Server Integration Services およびマスター データ サービスに統合するデータ管理ソリューションを構築できます。|    
|![Integration Services](../sql-server/media/integration-services.png "Integration Services")|**[Integration Services](../integration-services/sql-server-integration-services.md)**<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は、パフォーマンスの高いデータ統合ソリューションを構築するためのプラットフォームです。これには、データ ウェアハウジングに対して抽出、変換、および読み込み (ETL) の処理を提供するパッケージなどが含まれます。|    
|![マスター データ サービス](../sql-server/media/master-data-services.png)|**[マスター データ サービス](../master-data-services/master-data-services-installation-and-configuration.md)**<br /><br /> [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] は、マスター データ管理のための [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ソリューションです。 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で構築されたソリューションを使用すると、正しい情報に基づいたレポート作成と分析を行うことができます。 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]を使用すると、マスター データの中央リポジトリを作成できます。これにより、時間と共に変化するマスター データの記録を、監査およびセキュリティ保護が可能な形で管理できます。|    
|![Analysis Services](../sql-server/media/analysis-services.png "Analysis Services")|**[Analysis Services](../analysis-services/analysis-services.md)**<br /><br /> [!INCLUDE[ssASnoversion_md](../includes/ssasnoversion-md.md)] は、個人、チーム、および企業のビジネス インテリジェンスのための分析データ プラットフォームおよびツールセットです。 サーバーとクライアント デザイナーは、従来の OLAP ソリューションや新しいテーブル モデリング ソリューションに加えて、[!INCLUDE[ssGemini](../includes/ssgemini-md.md)]、Excel、および SharePoint Server 環境を使用するセルフサービス型の分析とコラボレーションをサポートしています。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] には、大量のデータ内部に隠されたパターンとリレーションシップを発見するためのデータ マイニング機能も含まれています。|    
|![Replication services](../sql-server/media/replication-services.png "Replication services")|**[レプリケーション](../relational-databases/replication/sql-server-replication.md)**<br /><br /> レプリケーションは、あるデータベースから別のデータベースへデータ オブジェクトやデータベース オブジェクトのコピーと配布を行い、一貫性を維持するためにデータベース間の同期を行うテクノロジ セットです。 レプリケーションでは、LAN や WAN、ダイヤル アップ接続、ワイヤレス接続、およびインターネットを使用して、異なる場所およびリモート ユーザーやモバイル ユーザーにデータを配布することができます。|    
|![Reporting Services](../sql-server/media/reporting-services.png "Reporting Services")|**[Reporting Services](../reporting-services/reporting-services-ssrs.md)**<br /><br /> Reporting Services は Web 対応のレポート機能を提供します。これによって組織では、さまざまなデータ ソースのコンテンツを表示するレポートの作成、さまざまな形式でのレポートのパブリッシュ、およびセキュリティやサブスクリプションの集中管理を行うことができます。|    
     
   
 ## <a name="more-information"></a>詳細情報   
+ [SQL Server 構成マネージャー](../relational-databases/sql-server-configuration-manager.md)
+ サポート対象のすべてのバージョンのリンクと情報については、[SQL Server Update Center](https://msdn.microsoft.com/library/ff803383.aspx) を参照してください 
+ [SQL Server データベース エンジンのインストール](../database-engine/install-windows/install-sql-server-database-engine.md) 
+ [SSMS を使用した SQL Server 管理ツールのインストール](https://msdn.microsoft.com/library/bb500441.aspx) 
+ [Visual Studio 2015 の SQL Server Data Tools](https://msdn.microsoft.com/mt186501.aspx)
+ [ビデオ、サンプル、およびコミュニティ リソース](https://msdn.microsoft.com/library/dn237258.aspx)
+ [SQL Server 2016 の概要](https://www.microsoft.com/en-us/server-cloud/products/sql-server/default.aspx?WT.srch=1&WT.mc_id=SEM_%5B_uniqid%5D&utm_source=Bing&utm_medium=CPC&utm_term=SQL%20Server%202016&utm_campaign=Data_Management)  
  
[!INCLUDE[feedback_stackoverflow_msdn_connect-md](../includes/feedback-stackoverflow-msdn-connect-md.md)]
