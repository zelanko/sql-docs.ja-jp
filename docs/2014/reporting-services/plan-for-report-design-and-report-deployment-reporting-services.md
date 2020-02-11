---
title: レポートのデザインとレポートの配置を計画する (Reporting Services 2014) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1c1e265e-52a2-4de3-96fd-ca4abae01c02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6104bfc97d2f66652ffa9b16e9ff0ae8f9b0550
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108047"
---
# <a name="plan-for-report-design-and-report-deployment-reporting-services-2014"></a>レポート デザインとレポート配置の計画 (Reporting Services 2014)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]には、レポートを作成および配置するためのいくつかの方法があります。 このトピックは、使用するレポート作成環境とレポート サーバーの組み合わせを計画するために役立ちます。 このトピックでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のコンポーネントでサポートされているレポート定義の概要を示します。 レポート定義は、レポート定義言語 (RDL : Report Definition Language) またはクライアント向けレポート定義言語 (RDLC : Report Definition Language for Clients) で記述された XML ファイルです。 どちらのレポート定義も、そのファイルの冒頭に指定された特定のスキーマ バージョンに準拠しています。  
  
 RDL ファイルは [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] のレポート デザイナー、またはレポート ビルダー 3.0 で作成します。 RDLC ファイルは、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]に搭載されている ReportViewer コントロールを使用して作成します。  
  
 このトピックの内容:  
  
-   [RDL スキーマのバージョン](#bkmk_rdl_schema_versions)  
  
-   [レポートサーバーと RDL スキーマのサポート](#bkmk_report_server_rdl_schema_support)  
  
-   [レポートの作成と配置のサポート](#bkmk_report_authoring_and_deployment)  
  
-   [ReportViewer コントロール](#bkmk_reportviewer)  
  
##  <a name="bkmk_rdl_schema_versions"></a>RDL スキーマのバージョン  
 次の表は、利用できるスキーマ バージョンとその省略形の対応表です。このトピックの説明には、以降、これらの省略形を使用します。  
  
|省略形|スキーマ バージョン|  
|------------------|--------------------|  
|2010 RDL|https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition|  
|2008 RDL|https://schemas.microsoft.com/sqlserver/reporting/2008/01/reportdefinition|  
|2005 RDL<br /><br /> 2005 RDLC|https://schemas.microsoft.com/sqlserver/reporting/2005/01/reportdefinition|  
|2000 RDL|https://schemas.microsoft.com/sqlserver/reporting/2003/10/reportdefinition|  
  
 RDL と RDL スキーマの詳細については、次のトピックを参照してください。  
  
-   [XML スキーマの Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=31850)  
  
-   [レポート定義言語の仕様](https://go.microsoft.com/fwlink/?linkid=116865)  
  
-   [レポート定義言語 &#40;SSRS&#41;](reports/report-definition-language-ssrs.md)  
  
 ReportViewer コントロールの詳細については、「[ReportViewer コントロール (Visual Studio)](https://msdn.microsoft.com/library/ms251671.aspx)」を参照してください。  
  
##  <a name="bkmk_report_server_rdl_schema_support"></a>レポートサーバーと RDL スキーマのサポート  
 レポート定義ファイルは、次の方法で [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] レポート サーバーに配置できます。  
  
-   **レポートデザイナー:** の[!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)]レポートデザイナーからレポートを配置します。  
  
-   **レポートビルダー:** レポートビルダーからレポートサーバーにレポートを保存します。  
  
-   **レポートマネージャー:** レポートマネージャーからネイティブモードのレポートサーバーにレポートをアップロードします。  
  
-   **SharePoint:** SharePoint モードのレポートサーバーで構成されている SharePoint サイトにレポートをアップロードします。  
  
-   **プログラムによる:** SOAP API インターフェイスを使用してレポートサーバーにレポートをプログラムでパブリッシュします。 詳細については、「 [Report Server Web Service](report-server-web-service/report-server-web-service.md)」を参照してください。  
  
 次の表は、サポートされる RDL スキーマのバージョンをレポート サーバーのバージョン別に示したものです。  
  
|レポート サーバーのバージョン|RDL スキーマのバージョン|  
|---------------------------|------------------------|  
|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<br /><br /> または<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]<br /><br /> または<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|2010 RDL<br /><br /> 2008 RDL<br /><br /> 2005 RDL<br /><br /> 2000 RDL|  
|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]|2008 RDL<br /><br /> 2005 RDL<br /><br /> 2000 RDL|  
|[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]|2005 RDL<br /><br /> 2000 RDL|  
  
 レポート定義をレポート サーバーにアップロードするか、既存のレポートが保存されたレポート サーバーをアップグレードすると、レポート定義は元の形式のまま維持されます。 レポートサーバーは、**初めて使用するときに**、レポートサーバーデータベースのレポートを、後続のビュー用に保持されているバイナリ形式にアップグレードします。 レポート定義 (.rdl) そのものはアップグレードされません。  
  
 レポート サーバーからレポート定義ファイル (.rdl) の読み取り専用コピーを抽出できます。 ネイティブ モード レポート サーバーで、レポート マネージャーを参照し、 **[ダウンロード]** をクリックします。 SharePoint モードの配置で、ドキュメント ライブラリを参照し、レポートを選択して、 **[コピーのダウンロード]** をクリックします。  
  
 レポート定義をアップグレードするには、アップグレードするレポートをレポート作成環境で開いて保存する必要があります。  
  
 レポートのアップグレードと、サポートされているスキーマ バージョンの詳細については、「 [レポートのアップグレード](install-windows/upgrade-reports.md)」を参照してください。  
  
##  <a name="bkmk_report_authoring_and_deployment"></a>レポートの作成と配置のサポート  
 レポート作成環境は [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] のレポート デザイナー、またはレポート ビルダーです。 レポート作成環境には、レポートのアップグレード、レポート デザイン、ローカル モードでのレポート プレビュー、レポート サーバーでのレポート プレビュー、レポートの配置など、さまざまな機能がサポートされています。  
  
 次の表は、各種スキーマ バージョンのレポート定義の作成と配置に関するサポート状況をまとめたものです。  
  
|作成環境|作成される RDL バージョン|配置用の RDL バージョン|配置先レポート サーバーのバージョン|  
|---------------------------|--------------------------|------------------------|--------------------------------------|  
|SQL Server 2014 Data Tools のレポート デザイナー - Business Intelligence for Microsoft Visual Studio 2012 (Microsoft ダウンロード センターから入手)<br /><br /> または<br /><br /> SQL Server 2012 Data Tools のレポート デザイナー - Business Intelligence for Microsoft Visual Studio 2012 (Microsoft ダウンロード センターから入手)<br /><br /> または<br /><br /> 
  [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Data Tools のレポート デザイナーは [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]に含まれています。|作成者 2010 RDL。 既存の RDL を開いたとき:<br /><br /> 2000 RDL、2010 RDL にアップグレード<br /><br /> 2005 RDL、2010 RDL にアップグレード<br /><br /> 2008 RDL、2010 RDL にアップグレード|2008 RDL<br /><br /> 2010 RDL|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|  
|
  [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Business Intelligence Development Studio のレポート デザイナー|作成者 2010 RDL。 既存の RDL を開いたとき:<br /><br /> 2000 RDL、2010 RDL にアップグレード<br /><br /> 2005 RDL、2010 RDL にアップグレード<br /><br /> 2008 RDL、2010 RDL にアップグレード|2008 RDL<br /><br /> 2010 RDL|[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|  
|
  [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] Business Intelligence Development Studio のレポート デザイナー|作成者 2008 RDL。 既存の RDL を開いたとき:<br /><br /> 2000 RDL、2008 RDL にアップグレード<br /><br /> 2005 RDL、2008 RDL にアップグレード|2008 RDL|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]|  
|[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]レポート ビルダー|作成者 2010 RDL。 既存の RDL を開いたとき:<br /><br /> 2000 RDL、2010 RDL にアップグレード<br /><br /> 2005 RDL、2010 RDL にアップグレード<br /><br /> 2008 RDL、2010 RDL にアップグレード|2010 RDL|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|  
|Visual Studio の RDLC レポート デザイナー|2005 RDLC|該当なし|該当なし|  
  
 
  [!INCLUDE[ss_dtbi_vs2013](../includes/ss-dtbi-vs2013-md.md)]の詳細については、次のトピックを参照してください。  
  
-   [SQL Server Data Tools &#40;SSRS&#41;での展開とバージョンのサポート](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)  
  
-   [Microsoft SQL Server Data Tools-Visual Studio 2012 用のビジネスインテリジェンス](https://www.microsoft.com/download/details.aspx?id=36843)。  
  
##  <a name="bkmk_reportviewer"></a>ReportViewer コントロール  
 
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の ReportViewer コントロールは、ローカル プレビュー モードまたはリモート モードで .rdlc レポートを表示できるほか、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバーでホストされている .rdl ファイルを表示できます。 次の表は、ローカル処理 (.rdlc) 用の ReportViewer コントロールでサポートされている RDL バージョンの一覧です。 サーバー側の RDL のサポートについて、 [レポート サーバーと RDL スキーマのサポート](#bkmk_report_server_rdl_schema_support)にまとめられています。  
  
|製品の ReportViewer コントロール|ローカル プレビュー用の RDL のバージョン|  
|-------------------------------------|--------------------------------------|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]2013<br /><br /> または<br /><br /> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]2012<br /><br /> または<br /><br /> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]|2008 RDL|  
|[!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]<br /><br /> または<br /><br /> [!INCLUDE[vsOrcas](../includes/vsorcas-md.md)]|2005 RDL|  
  
 詳細については、「  
  
-   [.RDLC ファイルから RDL ファイルへの変換](https://msdn.microsoft.com/library/ms252109.aspx)  
  
-   [ReportViewer コントロール (Visual Studio)](https://msdn.microsoft.com/library/ms251671.aspx)  
  
-   [ReportViewer コントロールの追加と構成](https://msdn.microsoft.com/library/ms252104.aspx)  
  
## <a name="see-also"></a>参照  
 [レポート、レポート パーツ、およびレポート定義 (レポート ビルダーおよび SSRS)](report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md)   
 [Reporting Services ツール](tools/reporting-services-tools.md)   
 [レポート定義言語 &#40;SSRS&#41;](reports/report-definition-language-ssrs.md)  
  
  
