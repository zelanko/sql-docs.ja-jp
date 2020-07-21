---
title: SQL Server Data Tools を使用した多次元モデルの作成 (SSDT) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SSAS, environments
- Analysis Services, development
- SQL Server Analysis Services, environments
- projects [Analysis Services]
- solutions [Analysis Services]
ms.assetid: 132ed779-3ec8-4734-9698-802116d1b017
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2773b7a65749057e1ed19d2863bcf3b14c715ec0
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547254"
---
# <a name="creating-multidimensional-models-using-sql-server-data-tools-ssdt"></a>SQL Server データ ツール (SSDT) を使用した多次元モデルの作成
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]には、ソリューションの構築、配置、および管理を行うための2つの異なる環境 (および) が用意されて [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] います。 この 2 つの環境には、プロジェクト システムが実装されています。 Visual Studio プロジェクトの詳細については、MSDN ライブラリの「 [コンテナーとしてのプロジェクト](https://go.microsoft.com/fwlink/?LinkId=63960) 」を参照してください。  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 2010 をベースにした開発環境であり、ビジネス インテリジェンス ソリューションを作成および変更する場合に使用します。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクト (キューブやディメンションなど) の定義が含まれる [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを作成し、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) の要素が含まれる XML ファイルに保存します。 これらのプロジェクトは、やなど、他のコンポーネントのプロジェクトも含むことができるソリューションに含まれてい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ます。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]では、特定の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに依存しないソリューションの一部として [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを開発できます。 開発時にテストするためにテスト サーバー上のインスタンスにオブジェクトを配置し、同じ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを使用して 1 つ以上のステージング サーバーまたは実稼働サーバー上のインスタンスにそのオブジェクトを配置できます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を含むソリューション内のプロジェクトとアイテムは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe などのソース コード コントロールと統合できます。 を使用したでのプロジェクトの作成の詳細について [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、「 [Create a Analysis Services project &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md)」を参照してください。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用して既存の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに直接接続し、プロジェクトの操作や XML ファイルへのオブジェクト定義の保存を行わずに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトを作成したり変更したりすることもできます。 詳細については、「 [多次元モデル データベース (SSAS)](multidimensional-model-databases-ssas.md)、および [Analysis Services データベースへのオンライン モードでの接続](connect-in-online-mode-to-an-analysis-services-database.md)という 2 つの環境が提供されています。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は管理環境であり、主に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のインスタンスを管理するために使用します。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトを管理 (バックアップや処理などを実行) でき、XMLA スクリプトを使用することにより、既存の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス上で新しいオブジェクトを直接作成することもできます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、多次元式 (MDX)、データ マイニング拡張機能 (DMX)、および XML for Analysis (XMLA) で記述されたスクリプトを開発して保存できる Analysis Services スクリプト プロジェクトが提供されています。 通常、Analysis Services スクリプト プロジェクトは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスで管理タスクを実行したり、データベースやキューブなどのオブジェクトを再作成したりするために使用します。 そのようなプロジェクトをソリューションの一部として保存し、ソース コード コントロールと統合できます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で Analysis Server スクリプト プロジェクトを作成する方法については、「 [SQL Server Management Studio での Analysis Services スクリプト プロジェクト](../instances/analysis-services-scripts-project-in-sql-server-management-studio.md)」を参照してください。  
  
## <a name="introducing-solutions-projects-and-items"></a>ソリューション、プロジェクト、およびアイテムの説明  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] と [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、ソリューションに構成されるプロジェクトが提供されます。 ソリューションには複数のプロジェクトを含めることができます。通常、プロジェクトには複数のアイテムが含まれています。 プロジェクトを作成すると、新しいソリューションが自動的に生成されます。必要に応じて、既存のソリューションにプロジェクトを追加できます。 プロジェクトに含まれているオブジェクトは、プロジェクトの種類によって異なります。 各プロジェクト コンテナー内のアイテムは、ファイル システムのプロジェクト フォルダーにファイルとして保存されます。  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] には、ビジネス インテリジェンス プロジェクトというプロジェクトの種類の下に次のプロジェクトが含まれています。  
  
|Project|説明|  
|-------------|-----------------|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト|1 つの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースのオブジェクト定義が含まれています。 プロジェクトを作成する方法の詳細については [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、「 [create a Analysis Services PROJECT &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md)」を参照してください。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 2008 データベースのインポート|既存の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースからオブジェクト定義をインポートして、新しい [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを作成するためのウィザードを提供します。|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクト|一連の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのオブジェクト定義が含まれています。 詳細については、「 [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)」を参照してください。|  
|レポート プロジェクト ウィザード (Report Project Wizard)|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を使用したレポート プロジェクトの作成を支援するウィザードを提供します。 詳細については、「[Reporting Services (SSRS)](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。|  
|レポート モデル プロジェクト|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート モデルのオブジェクト定義が含まれています。 詳細については、「[Reporting Services (SSRS)](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。|  
|レポート サーバー プロジェクト|1 つ以上の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートのオブジェクト定義が含まれています。 詳細については、「[Reporting Services (SSRS)](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。|  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] には、次の表に示すように、さまざまなクエリやスクリプトに的を絞ったプロジェクトの種類もいくつか含まれています。  
  
|Project|説明|  
|-------------|-----------------|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] スクリプト|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の DMX スクリプト、MDX スクリプト、XMLA スクリプトと、これらのスクリプトを実行できる [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスへの接続が含まれています。 詳細については、「 [SQL Server Management Studio での Analysis Services スクリプト プロジェクトの設定](../instances/analysis-services-scripts-project-in-sql-server-management-studio.md)」を参照してください。|  
|SQL Server Compact スクリプト|SQL Server Compact 用の SQL スクリプトと、これらのスクリプトを実行できる SQL Server Compact インスタンスへの接続が含まれています。|  
|SQL Server スクリプト|[!INCLUDE[tsql](../../includes/tsql-md.md)] インスタンスの [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] スクリプトおよび XQuery スクリプトと、これらのスクリプトを実行できる [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] インスタンスへの接続が含まれています。 詳細については、「 [SQL Server データベース エンジン](../../database-engine/sql-server-database-engine-overview.md)」を参照してください。|  
  
 ソリューションとプロジェクトの詳細について [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] は、.net のドキュメントまたは MSDN ライブラリの「ソリューション、プロジェクト、およびファイルの管理」を参照してください。  
  
## <a name="choosing-between-sql-server-management-studio-and-sql-server-data-tools"></a>SQL Server Management Studio と SQL Server データ ツールの使い分け  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]で既存のオブジェクトの管理および構成を行うために設計されています。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の機能を含むビジネス インテリジェンス ソリューションを開発するために設計されています。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] と [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]には、以下のような相違点があります。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスに接続して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンス内のオブジェクトを構成、管理するための統合環境です。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ではスクリプトを使用することによって、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクト自体の作成や変更も行えます。ただし、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] には、オブジェクトの設計および定義を行うためのグラフィカル インターフェイスは用意されていません。  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は、ビジネス インテリジェンス ソリューションの統合開発環境です。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] はプロジェクト モードで使用できます。このモードでは、プロジェクトおよびソリューションに含まれている [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] オブジェクトの XML ベースの定義が使用されます。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] をプロジェクト モードで使用すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] オブジェクトに変更を加える際に、これらの XML ベースのオブジェクト定義が変更されます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス上のオブジェクトに対する直接的な変更は、ソリューションが配置されて初めて反映されます。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] をオンライン モードで使用することもできます。この場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに直接接続して、既存のデータベース内のオブジェクトを操作することになります。  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスへのアクティブな接続がなくても、ソース管理されたマルチユーザー環境で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを操作できるため、ビジネス インテリジェンス アプリケーションの開発が強化されます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、クエリとテストのために既存のオブジェクトに直接アクセスでき、以前にスクリプトが作成された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースをより短時間で実装できます。 ただし、いったん実稼働環境にプロジェクトを配置したら、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースとそのオブジェクトを [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] および [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で操作する際には慎重に行う必要があります。 既存のデータベース内のオブジェクトへの変更が上書きされたり、配置されたソリューションを当初生成した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトへの変更が上書きされないように注意してください。 詳細については、「 [開発段階における Analysis Services プロジェクトおよびデータベースの操作](work-with-analysis-services-projects-and-databases-in-development.md)」および「 [実稼働環境における Analysis Services プロジェクトおよびデータベースの操作](work-with-analysis-services-projects-and-databases-in-production.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [Analysis Services プロジェクトの作成 (SSDT)](create-an-analysis-services-project-ssdt.md)  
  
-   [Analysis Services プロジェクトのプロパティの構成 (SSDT)](configure-analysis-services-project-properties-ssdt.md)  
  
-   [Analysis Services プロジェクトのビルド &#40;SSDT&#41;](build-analysis-services-projects-ssdt.md)  
  
-   [Analysis Services プロジェクトの配置 &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md)  
  
-   [開発段階における Analysis Services プロジェクトおよびデータベースの操作](work-with-analysis-services-projects-and-databases-in-development.md)  
  
-   [実稼働環境における Analysis Services プロジェクトおよびデータベースの操作](work-with-analysis-services-projects-and-databases-in-production.md)  
  
## <a name="see-also"></a>参照  
 [SSDT&#41;&#40;Analysis Services プロジェクトを作成する](create-an-analysis-services-project-ssdt.md)   
 [SQL Server Management Studio 内の Analysis Services Scripts プロジェクト](../instances/analysis-services-scripts-project-in-sql-server-management-studio.md)   
 [多次元モデル データベース &#40;SSAS&#41;](multidimensional-model-databases-ssas.md)  
  
  
