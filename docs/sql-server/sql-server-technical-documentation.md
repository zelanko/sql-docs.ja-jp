---
title: "SQL Server 技術ドキュメント |Microsoft ドキュメント"
ms.date: 03/24/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.portal.f1
helpviewer_keywords:
- documentation [SQL Server], home page
- Help [SQL Server]
- SQL Server, documentation
- home page [SQL Server]
- Help [SQL Server], documentation home page
- Books Online [SQL Server], home page
- portal page [SQL Server]
ms.assetid: 674933a8-e423-4d44-a39b-2a997e2c2333
caps.latest.revision: 106
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 96f6a7eeb03fdc222d0e5b42bcfbf05c25d11db6
ms.openlocfilehash: 6ba40fbd036ee6476d7eb3439a5d9e816e79651d
ms.contentlocale: ja-jp
ms.lasthandoff: 05/25/2017

---
# <a name="sql-server-technical-documentation"></a>SQL Server 技術ドキュメント
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 > SQL Server の以前のバージョンに関連するコンテンツでは、次を参照してください。 [for SQL Server 2014 インストール](https://msdn.microsoft.com/en-US/library/bb500469(SQL.120).aspx)です。

 SQL Server のインストール、構成、および使用の際に役立つドキュメントです。 コンテンツには、エンド ツー エンドの例、コード サンプル、およびビデオが含まれています。 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 言語のトピックについては、「 [言語リファレンス](../t-sql/language-reference.md)」を参照してください。

**SQL Server 2017**

- [SQL Server 2017 年 1 リリース ノートします。](../sql-server/sql-server-2017-release-notes.md)
- [SQL Server 2017 年 1 の新機能](../sql-server/what-s-new-in-sql-server-2017.md)
 
**SQL Server 2016:**
 
- [SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md)
- [SQL Server 2016 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)
    
 **SQL Server をお試しください。**    
 - [**Evaluation Center から SQL Server 2016 をダウンロードする**](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) 
 - **[SQL Server 2016 がインストール済みの Virtual Machine をすぐにご利用いただけます](https://azure.microsoft.com/en-us/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)**    
 - **[最新バージョンの SQL Server Management Studio をダウンロードする](https://msdn.microsoft.com/library/mt238290.aspx)**   
      
## <a name="sql-server-technologies"></a>SQL Server のテクノロジ    
    
|||    
|-|-|    
|![SQL データベース エンジン](../sql-server/media/sql-database-engine.png "SQL データベース エンジン")|**[データベース エンジン](../database-engine/configure-windows/sql-server-database-engine.md)**<br /><br /> データベース エンジンは、データの格納、処理、およびセキュリティ保護を目的としたコア サービスです。 データベース エンジンでは、組織で利用しているアプリケーションのうち、データの使用頻度が最も高いアプリケーションの要件を満たすように、アクセスの制御や高速なトランザクション処理が行われます。 また、高可用性を実現するためのさまざまなサポートも提供されます。|    
|![R Server](../sql-server/media/r-server.png "R Server")|**[R Services](../advanced-analytics/r-services/r-services.md)**<br /><br /> Microsoft R Services を使用すると、さまざまな方法で R 言語をエンタープライズ ワークフローに組み込むことができます。<br /><br /> [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] が R 言語を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]と統合するので、 [!INCLUDE[tsql](../includes/tsql-md.md)] ストアド プロシージャを呼び出すことにより、簡単にモデルをビルド、再トレーニング、およびスコア付けすることができます。<br /><br /> Microsoft R Server は Hadoop や Teradata などのデータ ソースをサポートし、R を利用する企業にマルチプラット フォームのスケーラブルなサポートを提供します。|    
|![Data Quality Services](../sql-server/media/data-quality-services.png "Data Quality Services")|**[Data Quality Services](../data-quality-services/data-quality-services.md)**<br /><br /> SQL Server Data Quality Services (DQS) は、ナレッジ ドリブンのデータ クレンジング ソリューションを提供します。 DQS を使用すると、ナレッジ ベースを構築し、このナレッジ ベースを使用して、コンピューター支援型と対話形式の両方の方法で、データに対する修正および重複除去を行うことができます。 クラウドベースの Reference Data Services を使用すると、DQS を SQL Server Integration Services およびマスター データ サービスに統合するデータ管理ソリューションを構築できます。|    
|![Integration Services](../sql-server/media/integration-services.png "Integration Services")|**[Integration Services](../integration-services/sql-server-integration-services.md)**<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は、パフォーマンスの高いデータ統合ソリューションを構築するためのプラットフォームです。これには、データ ウェアハウジングに対して抽出、変換、および読み込み (ETL) の処理を提供するパッケージなどが含まれます。|    
|![マスター データ サービス](../sql-server/media/master-data-services.png)|**[マスター データ サービス](../master-data-services/master-data-services-installation-and-configuration.md)**<br /><br /> [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] は、マスター データ管理のための [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ソリューションです。 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で構築されたソリューションを使用すると、正しい情報に基づいたレポート作成と分析を行うことができます。 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]を使用すると、マスター データの中央リポジトリを作成できます。これにより、時間と共に変化するマスター データの記録を、監査およびセキュリティ保護が可能な形で管理できます。|    
|![Analysis Services](../sql-server/media/analysis-services.png "Analysis Services")|**[Analysis Services](../analysis-services/analysis-services.md)**<br /><br /> [!INCLUDE[ssASnoversion_md](../includes/ssasnoversion-md.md)] は、個人、チーム、および企業のビジネス インテリジェンスのための分析データ プラットフォームおよびツールセットです。 サーバーとクライアント デザイナーは、従来の OLAP ソリューションや新しいテーブル モデリング ソリューションに加えて、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]、Excel、および SharePoint Server 環境を使用するセルフサービス型の分析とコラボレーションをサポートしています。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] には、大量のデータ内部に隠されたパターンとリレーションシップを発見するためのデータ マイニング機能も含まれています。|    
|![レプリケーション サービス](../sql-server/media/replication-services.png "レプリケーション サービス")|**[レプリケーション](../relational-databases/replication/sql-server-replication.md)**<br /><br /> レプリケーションは、あるデータベースから別のデータベースへデータ オブジェクトやデータベース オブジェクトのコピーと配布を行い、一貫性を維持するためにデータベース間の同期を行うテクノロジ セットです。 レプリケーションでは、LAN や WAN、ダイヤル アップ接続、ワイヤレス接続、およびインターネットを使用して、異なる場所およびリモート ユーザーやモバイル ユーザーにデータを配布することができます。|    
|![Reporting Services](../sql-server/media/reporting-services.png "Reporting Services")|**[Reporting Services](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)**<br /><br /> Reporting Services は Web 対応のレポート機能を提供します。これによって組織では、さまざまなデータ ソースのコンテンツを表示するレポートの作成、さまざまな形式でのレポートのパブリッシュ、およびセキュリティやサブスクリプションの集中管理を行うことができます。|    

    
## <a name="earlier-sql-server-versions"></a>以前の SQL Server のバージョン
- [SQL Server 2014 オンライン ブックのオンライン ブック](https://msdn.microsoft.com/library/ms130214(v=sql.120).aspx)
- [SQL Server 2014 Express とその他の古いバージョンの SQL Server をインストールします](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx)。 (**インストーラー パッケージ リンクをすべて 1 か所に集めてくれた [Scott Hanselman](http://www.hanselman.com/) に感謝します**)  
- [SQL Server 2012 技術ドキュメント](https://technet.microsoft.com/library/bb418433(v=sql.10).aspx)  
- [SQL Server 2008 R2 製品ドキュメント](https://msdn.microsoft.com/library/hh278298(v=sql.10).aspx)  
- [SQL Server 2008 技術ドキュメント](https://msdn.microsoft.com/library/hh994727(v=sql.10).aspx) 
- [SQL Server 2005 アーカイブ ドキュメント](https://msdn.microsoft.com/library/hh278313(v=sql.10).aspx)    

**サンプル データベース**  
- [Wide World Importers のサンプル データベース](https://msdn.microsoft.com/library/mt734199(v=sql.1).aspx)  
- [SQL Server 2016 の AdventureWorks サンプル データベースとスクリプト](https://www.microsoft.com/en-us/download/details.aspx?id=49502) 
- [GitHub の SQL Server サンプル](https://github.com/Microsoft/sql-server-samples) 
   
 ## <a name="more-information"></a>詳細情報   
+ [SQL Server 構成マネージャー](../relational-databases/sql-server-configuration-manager.md)
+ サポート対象のすべてのバージョンのリンクと情報については、[SQL Server Update Center](https://msdn.microsoft.com/library/ff803383.aspx) を参照してください 
+ [SQL Server データベース エンジンのインストール](../database-engine/install-windows/install-sql-server-database-engine.md) 
+ [SSMS を使用した SQL Server 管理ツールのインストール](https://msdn.microsoft.com/library/bb500441.aspx) 
+ [Visual Studio 2015 の SQL Server Data Tools](https://msdn.microsoft.com/mt186501.aspx)
+ [ビデオ、サンプル、およびコミュニティ リソース](https://msdn.microsoft.com/library/dn237258.aspx)
  
[!INCLUDE[feedback_stackoverflow_msdn_connect-md](../includes/feedback-stackoverflow-msdn-connect-md.md)]

