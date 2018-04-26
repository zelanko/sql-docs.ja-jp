---
title: SQL Server のドキュメント | Microsoft Docs
ms.date: 02/28/2018
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
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
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Active
monikerRange: '>= sql-server-2014 || = sqlallproducts-allversions'
ms.openlocfilehash: 06ccc15f14599c1d9861af90d6a56d65b71e3e0e
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="sql-server-documentation"></a>SQL Server のドキュメント
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server は Microsoft データ プラットフォームの中心部です。 SQL Server は、オペレーション データベース管理システム (ODBMS) 業界のリーダーといえる製品です。 このドキュメントは、SQL Server のインストール、構成、使用の際に役立ちます。 コンテンツには、エンド ツー エンドの例、コード サンプル、およびビデオが含まれています。 SQL Server 言語のトピックについては、「[言語リファレンス](../t-sql/language-reference.md)」を参照してください。

::: moniker range="=sql-server-2017"
|新機能  | リリース ノート  |
|---------|---------|
|[SQL Server 2017 の新機能](../sql-server/what-s-new-in-sql-server-2017.md)     | [SQL Server 2017 リリース ノート](../sql-server/sql-server-2017-release-notes.md)        |
::: moniker-end
::: moniker range="=sql-server-2016"
|新機能  | リリース ノート  |
|---------|---------|
|[SQL Server 2016 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)     | [SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md)        |
::: moniker-end

::: moniker range="=sql-server-2014"
![info_tip](../sql-server/media/info-tip.png) SQL Server 2014 のコンテンツは、.docs サイトに間もなく統合されます。  当面は、次を参照してください。
- [SQL Server 2014 オンライン ブック](https://msdn.microsoft.com/en-us/library/ms130214(v=sql.120).aspx)
- [SQL Server 2014 の新機能](https://msdn.microsoft.com/library/bb500435(v=sql.120).aspx)
- [SQL Server 2014 リリース ノート](../sql-server/sql-server-2014-release-notes.md)
- [以前のバージョン](https://docs.microsoft.com/en-us/previous-versions/sql/)
::: moniker-end

**SQL Server をお試しください。**
    + [![Evaluation Center からダウンロードする](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=829477) [SQL Server のダウンロード](http://go.microsoft.com/fwlink/?LinkID=829477)
    + [![Evaluation Center からダウンロードする](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) [SQL Server Management Studio (SSMS) のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)
    + [![Evaluation Center からダウンロードする](../includes/media/download2.png)](../ssdt/download-sql-server-data-tools-ssdt.md) [SQL Server Data Tools (SSDT) のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)
    + [![仮想マシンの作成](../includes/media/azure-vm.png)](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm) [SQL Server で仮想マシンをすぐにご利用いただけます](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)

::: moniker range=">=sql-server-2016 || = sqlallproducts-allversions"
## <a name="sql-server-technologies"></a>SQL Server のテクノロジ

|||
|-|-|
|![SQL データベース エンジン](../sql-server/media/sql-database-engine.png "SQL データベース エンジン")|**[データベース エンジン](../database-engine/sql-server-database-engine-overview.md)**<br /><br /> データベース エンジンは、データの格納、処理、およびセキュリティ保護を目的としたコア サービスです。 データベース エンジンでは、組織で利用しているアプリケーションのうち、データの使用頻度が最も高いアプリケーションの要件を満たすように、アクセスの制御や高速なトランザクション処理が行われます。 また、高可用性を実現するためのさまざまなサポートも提供されます。|
|![R Server](../sql-server/media/r-server.png "R Server")|**[Machine Learning サービス](../advanced-analytics/r-services/r-services.md)**<br /><br /> Microsoft Machine Learning サービスでは、一般的な R 言語や Python 言語を使用した、機械学習のエンタープライズ ワークフローへの統合がサポートされています。<br /><br /> Machine Learning サービス (データベース内) は、R および Python と SQL Server を統合し、ストアド プロシージャを呼び出すことで、モデルのビルド、リトレイン、評価を容易にします。  Microsoft Machine Learning Server では、SQL Server を必要としない、R および Python に対するエンタープライズ規模のサポートが提供されています。|
|![Integration Services](../sql-server/media/integration-services.png "Integration Services")|**[Integration Services](../integration-services/sql-server-integration-services.md)**<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は、パフォーマンスの高いデータ統合ソリューションを構築するためのプラットフォームです。これには、データ ウェアハウジングに対して抽出、変換、および読み込み (ETL) の処理を提供するパッケージなどが含まれます。|
|![Analysis Services](../sql-server/media/analysis-services.png "Analysis Services")|**[Analysis Services](../analysis-services/analysis-services.md)**<br /><br /> [!INCLUDE[ssASnoversion_md](../includes/ssasnoversion-md.md)] は、個人、チーム、および企業のビジネス インテリジェンスのための分析データ プラットフォームおよびツールセットです。 サーバーとクライアント デザイナーは、従来の OLAP ソリューションや新しいテーブル モデリング ソリューションに加えて、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]、Excel、および SharePoint Server 環境を使用するセルフサービス型の分析とコラボレーションをサポートしています。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] には、大量のデータ内部に隠されたパターンとリレーションシップを発見するためのデータ マイニング機能も含まれています。|    
|![Reporting Services](../sql-server/media/reporting-services.png "Reporting Services")|**[Reporting Services](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)**<br /><br /> Reporting Services は Web 対応のエンタープライズ レポート機能を提供します。  これによって組織では、さまざまなデータ ソースのコンテンツを表示するレポートの作成、さまざまな形式でのレポートのパブリッシュ、およびセキュリティやサブスクリプションの集中管理を行うことができます。|
|![レプリケーション サービス](../sql-server/media/replication-services.png "レプリケーション サービス")|**[レプリケーション](../relational-databases/replication/sql-server-replication.md)**<br /><br /> レプリケーションは、あるデータベースから別のデータベースへデータ オブジェクトやデータベース オブジェクトのコピーと配布を行い、一貫性を維持するためにデータベース間の同期を行うテクノロジ セットです。 レプリケーションでは、LAN や WAN、ダイヤル アップ接続、ワイヤレス接続、およびインターネットを使用して、異なる場所およびリモート ユーザーやモバイル ユーザーにデータを配布することができます。|
|![Data Quality Services](../sql-server/media/data-quality-services.png "Data Quality Services")|**[Data Quality Services](../data-quality-services/data-quality-services.md)**<br /><br /> SQL Server Data Quality Services (DQS) は、ナレッジ ドリブンのデータ クレンジング ソリューションを提供します。 DQS を使用すると、ナレッジ ベースを構築し、このナレッジ ベースを使用して、コンピューター支援型と対話形式の両方の方法で、データに対する修正および重複除去を行うことができます。 クラウドベースの Reference Data Services を使用すると、DQS を SQL Server Integration Services およびマスター データ サービスに統合するデータ管理ソリューションを構築できます。|
|![マスター データ サービス](../sql-server/media/master-data-services.png)|**[マスター データ サービス](../master-data-services/master-data-services-installation-and-configuration.md)**<br /><br /> [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] は、マスター データ管理のための [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ソリューションです。 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で構築されたソリューションを使用すると、正しい情報に基づいたレポート作成と分析を行うことができます。 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]を使用すると、マスター データの中央リポジトリを作成できます。これにより、時間と共に変化するマスター データの記録を、監査およびセキュリティ保護が可能な形で管理できます。|
::: moniker-end

## <a name="migrate-and-move-data"></a>データの移行と移動

- [SQL Server インポートおよびエクスポート ウィザードを使用してデータをインポートおよびエクスポートする](../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)
- [Microsoft Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595)
- [SQL Server データベースを Azure SQL Database に移行する](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

## <a name="update-your-version-of-sql-server"></a>SQL Server のバージョンの更新

- サポート対象のすべてのバージョンのリンクと情報については、[SQL Server Update Center](https://msdn.microsoft.com/library/ff803383.aspx) を参照してください

## <a name="samples"></a>サンプル

- [Wide World Importers のサンプル データベース](https://docs.microsoft.com/en-us/sql/samples/wide-world-importers-what-is)
- [SQL Server 2016 の AdventureWorks サンプル データベースとスクリプト](https://docs.microsoft.com/en-us/sql/samples/sql-samples-where-are) 
- [GitHub の SQL Server サンプル](https://github.com/Microsoft/sql-server-samples)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]