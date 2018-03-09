---
title: "レポート デザインとレポートの展開の計画 |Reporting Services | Microsoft Docs"
ms.custom: 
ms.date: 09/12/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 1c1e265e-52a2-4de3-96fd-ca4abae01c02
caps.latest.revision: "19"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 4d4a2081da55117fa6fa6b6ad84ac4ec21b84ee6
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="plan-for-report-design-and-report-deployment--reporting-services"></a>レポート デザインとレポート配置の計画 | Reporting Services
[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] には、ページ分割されたレポートの作成と配置に関していくつかのアプローチが用意されています。 レポートの作成とレポート サーバーを併用する環境を計画する方法について説明します。

このトピックでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のコンポーネントでサポートされているレポート定義の概要を示します。 レポート定義は、レポート定義言語 (RDL : Report Definition Language) またはクライアント向けレポート定義言語 (RDLC : Report Definition Language for Clients) で記述された XML ファイルです。 どちらのレポート定義も、そのファイルの冒頭に指定された特定のスキーマ バージョンに準拠しています。  
  
 RDL ファイルは [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] のレポート デザイナー、またはレポート ビルダーで作成します。 RDLC ファイルは、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]に搭載されている ReportViewer コントロールを使用して作成します。
  
##  <a name="bkmk_rdl_schema_versions"></a> RDL スキーマのバージョン  
 次の表は、利用できるスキーマ バージョンとその省略形の対応表です。このトピックの説明には、以降、これらの省略形を使用します。  
  
|省略形|スキーマ バージョン|  
|------------------|--------------------|  
|2016 RDL|`http://schemas.microsoft.com/sqlserver/reporting/2016/01/reportdefinition`|
|2010 RDL|`http://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition`|  
|2008 RDL|`http://schemas.microsoft.com/sqlserver/reporting/2008/01/reportdefinition`|  
|2005 RDL<br /><br /> 2005 RDLC|`http://schemas.microsoft.com/sqlserver/reporting/2005/01/reportdefinition`|  
|2000 RDL|`http://schemas.microsoft.com/sqlserver/reporting/2003/10/reportdefinition`|  
  
 RDL と RDL スキーマの詳細については、次のトピックを参照してください。  
  
-   [Microsoft SQL Server XML スキーマ](http://go.microsoft.com/fwlink/?LinkId=31850)  
  
-   [レポート定義言語の仕様](http://go.microsoft.com/fwlink/?linkid=116865)  
  
-   [レポート定義言語 (SSRS)](../reporting-services/reports/report-definition-language-ssrs.md)  
  
 ReportViewer コントロールの詳細については、「[ReportViewer コントロール (Visual Studio)](http://msdn.microsoft.com/library/ms251671.aspx)」を参照してください。  
  
##  <a name="bkmk_report_server_rdl_schema_support"></a> レポート サーバーと RDL スキーマのサポート  
 レポート定義ファイルは、次の方法で [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] レポート サーバーに配置できます。  
  
-   **レポート デザイナー:** [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)]のレポート デザイナーからレポートを配置する。  
  
-   **レポート ビルダー:** レポート ビルダーからレポート サーバーにレポートを保存する。  
  
-   **Web ポータル:** [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]からネイティブ モード レポート サーバーにレポートをアップロードします。  
  
-   **SharePoint:** SharePoint モード レポート サーバーで構成された SharePoint サイトにレポートをアップロードする。  
  
-   **プログラムから:** プログラムから SOAP API インターフェイスを使用してレポート サーバーにレポートをパブリッシュする。 詳しくは、「 [Report Server Web Service](../reporting-services/report-server-web-service/report-server-web-service.md)」をご覧ください。  
  
 次の表は、サポートされる RDL スキーマのバージョンをレポート サーバーのバージョン別に示したものです。  
  
|レポート サーバーのバージョン|RDL スキーマのバージョン|  
|---------------------------|------------------------|  
|SQL Server 2016|2016 RDL<br /><br />2010 RDL<br /><br /> 2008 RDL<br /><br /> 2005 RDL<br /><br /> 2000 RDL
|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<br /><br /> スイッチまたは<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]<br /><br /> スイッチまたは<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|2010 RDL<br /><br /> 2008 RDL<br /><br /> 2005 RDL<br /><br /> 2000 RDL|  
|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]|2008 RDL<br /><br /> 2005 RDL<br /><br /> 2000 RDL|  
  
 レポート定義をレポート サーバーにアップロードするか、既存のレポートが保存されたレポート サーバーをアップグレードすると、レポート定義は元の形式のまま維持されます。 レポート サーバー データベース内のレポートは、**初回使用時に**レポート サーバーによってバイナリ形式へとアップグレードされて初めて、閲覧が可能となります。 レポート定義 (.rdl) そのものはアップグレードされません。  
  
 レポート サーバーからレポート定義ファイル (.rdl) の読み取り専用コピーを抽出できます。 ネイティブ モード レポート サーバーで、 [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]を参照し、 **[ダウンロード]**をクリックします。 SharePoint モードの配置で、ドキュメント ライブラリを参照し、レポートを選択して、 **[コピーのダウンロード]**をクリックします。  
  
 レポート定義をアップグレードするには、アップグレードするレポートをレポート作成環境 (SQL Server Data Tools、レポート ビルダーなど) で開いて保存する必要があります。  
  
 レポートのアップグレードと、サポートされているスキーマ バージョンの詳細については、「 [レポートのアップグレード](../reporting-services/install-windows/upgrade-reports.md)」を参照してください。  
  
##  <a name="bkmk_report_authoring_and_deployment"></a> レポートの作成と配置のサポート  
 レポート作成環境は [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] のレポート デザイナー、またはレポート ビルダーです。 レポート作成環境には、レポートのアップグレード、レポート デザイン、ローカル モードでのレポート プレビュー、レポート サーバーでのレポート プレビュー、レポートの配置など、さまざまな機能がサポートされています。  
  
 次の表は、各種スキーマ バージョンのレポート定義の作成と配置に関するサポート状況をまとめたものです。  
  
|作成環境|作成される RDL バージョン|配置用の RDL バージョン|配置先レポート サーバーのバージョン|  
|---------------------------|--------------------------|------------------------|--------------------------------------|  
|SQL Server 2016 レポート ビルダー|Authors 2016 RDL<br /><br /> 旧バージョンの RDL を 2016 RDL にアップグレードします|2016 RDL|SQL Server 2016|
|SQL Server 2016 Data Tools のレポート デザイナー - Business Intelligence for Microsoft Visual Studio 2015|Authors 2016 RDL<br /><br /> 旧バージョンの RDL を 2016 RDL にアップグレードします|2016 RDL|SQL Server 2016|
|SQL Server 2014 Data Tools のレポート デザイナー - Business Intelligence for Microsoft Visual Studio 2012<br /><br /> スイッチまたは<br /><br /> SQL Server 2012 Data Tools のレポート デザイナー - Business Intelligence for Microsoft Visual Studio 2012<br /><br /> スイッチまたは<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Data Tools のレポート デザイナーは [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]に含まれています。|2010 RDL を作成<br /><br /> 旧バージョンの RDL を 2010 RDL にアップグレードします|2010 RDL|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|  
|[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Business Intelligence Development Studio のレポート デザイナー|2010 RDL を作成<br /><br /> 旧バージョンの RDL を 2010 RDL にアップグレードします|2010 RDL|[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|  
|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] Business Intelligence Development Studio のレポート デザイナー|2008 RDL を作成<br /><br /> 旧バージョンの RDL を 2008 RDL にアップグレードします|2008 RDL|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]|
  
 SQL Server Data Tools (SSDT) の詳細については、以下を参照してください。  
  
-   [SQL Server データ ツールの配置およびバージョン サポート (SSRS)](../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)  
  
-   [Visual Studio 2015 用 SQL Server Data Tools](../ssdt/download-sql-server-data-tools-ssdt.md)  
  
##  <a name="bkmk_reportviewer"></a> ReportViewer コントロール  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の ReportViewer コントロールは、ローカル プレビュー モードまたはリモート モードで .rdlc レポートを表示できるほか、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバーでホストされている .rdl ファイルを表示できます。 次の表は、ローカル処理 (.rdlc) 用の ReportViewer コントロールでサポートされている RDL バージョンの一覧です。 サーバー側の RDL のサポートについて、 [レポート サーバーと RDL スキーマのサポート](#bkmk_report_server_rdl_schema_support)にまとめられています。  
  
|製品の ReportViewer コントロール|ローカル プレビュー用の RDL のバージョン|  
|-------------------------------------|--------------------------------------|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 2015 <br/><br/>スイッチまたは<br/><br/>[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 2013<br /><br /> スイッチまたは<br /><br /> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 2012<br /><br /> スイッチまたは<br /><br /> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]|2008 RDL|  
|[!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]<br /><br /> スイッチまたは<br /><br /> [!INCLUDE[vsOrcas](../includes/vsorcas-md.md)]|2005 RDL|  
  
 詳細については、以下を参照してください。  
  
-   [RDLC ファイルから RDL ファイルへの変換](http://msdn.microsoft.com/library/ms252109.aspx)  
  
-   [ReportViewer コントロール (Visual Studio)](http://msdn.microsoft.com/library/ms251671.aspx)  
  
-   [ReportViewer コントロールの追加と構成](http://msdn.microsoft.com/library/ms252104.aspx)  
  
## <a name="see-also"></a>参照  
 [レポート、レポート パーツ、およびレポート定義 (レポート ビルダーおよび SSRS)](../reporting-services/report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md)   
 [Reporting Services ツール](../reporting-services/tools/reporting-services-tools.md)   
 [レポート定義言語 &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
