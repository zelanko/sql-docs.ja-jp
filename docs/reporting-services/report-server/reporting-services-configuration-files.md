---
title: Reporting Services 構成ファイル | Microsoft Docs
ms.date: 05/30/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], configuration files
- configuration options [Reporting Services]
- modifying configuration files
- configuration files [Reporting Services]
ms.assetid: 21e5c32f-ad67-4917-b55a-8e21bd64f5a6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 25b695456bbac34e2c6ce8bf8c312c4108dd852e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66506653"
---
# <a name="reporting-services-configuration-files"></a>Reporting Services 構成ファイル
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レジストリと構成ファイルにコンポーネント情報が格納されます。この構成ファイルは、セットアップ時にファイル システムへコピーされます。 構成ファイルには、内部専用値とユーザー定義値を組み合わせたものが含まれています。 ユーザー定義値は、セットアップ、構成ツール、コマンド ライン ユーティリティを通じて指定するか、構成ファイルを手動で編集して指定します。  
  
 構成ファイルの変更が必要になるのは、詳細設定を追加したり構成したりする場合だけです。 構成設定は、XML 要素または XML 属性のいずれかとして指定されます。 XML ファイルおよび構成ファイルを理解している場合は、テキスト エディターまたはコード エディターを使用して、ユーザーが定義可能な設定を変更できます。 構成ファイルをどのように変更するか、または、レポート サーバーが最新の構成設定をどのように読み取るかの詳細については、「[Reporting Services の構成ファイル (rsreportserver.config) の変更](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)」を参照してください。  
  
> [!NOTE]  
> 以前のリリースでは、RSWebApplication.config という名前の独自の構成ファイルが使用されていました。今後、このファイルは使用されません。 以前の環境からアップグレードした場合、このファイルは削除されませんが、レポート サーバーは、このファイルから一切設定を読み取りません。 このファイルがコンピューターに存在する場合は、削除してください。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、レポート マネージャーと Web ポータルの構成設定はすべて RSReportServer.config ファイルに格納され、このファイルから読み取られます。 設定が削除または移動された一覧を確認する方法については、「 [SQL Server 2016 における SQL Server Reporting Services の重大な変更](../../reporting-services/breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)」を参照してください。  
  
 この記事の内容は次のとおりです。  
  
-   [構成ファイルの概要 (ネイティブ モード)](#bkmk_config_file_Summary_native_mode)  
  
-   [構成ファイルの概要 (SharePoint モード)](#bkmk_config_file_Summary_sharepoint_mode)  
  
##  <a name="bkmk_config_file_Summary_native_mode"></a> 構成ファイルの概要 (ネイティブ モード)  
 次の表は、構成設定の格納先とその説明を一覧にしたものです。 ほとんどの構成設定は [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]に含まれている構成ファイルに格納されます。 既定では、インストール ディレクトリは次の場所にあります。  
  
'' のパスのインストール  
C:\Program files \microsoft の SQL Server\MSRSxx.MSSQLSERVER (xx は MS SQL のバージョン番号です) または  
C:\Program Files\Microsoft SQL Server Reporting Services\SSRS  
  SSRS のバージョンによって
```  
  
|Stored in:|Description|Location|  
|----------------|-----------------|--------------|  
|RSReportServer.config|Stores configuration settings for feature areas of the Report Server service: Report Manager or the web portal, the Report Server Web service, and background processing. For more information about each setting, see [RsReportServer.config Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).|\<Installation directory> \Reporting Services \ReportServer|  
|RSSrvPolicy.config|Stores the code access security policies for the server extensions. For more information about this file, see [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<Installation directory> \Reporting Services \ReportServer|  
|RSMgrPolicy.config|Stores the code access security policies for the web portal. For more information about this file, see [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|\<Installation directory> \Reporting Services \ReportManager|  
|Web.config for the Report Server Web service|Includes only those settings that are required for ASP.NET.|\<Installation directory> \Reporting Services \ReportServer|  
|Web.config for Report Manager|Includes only those settings that are required for ASP.NET if applicable for the SSRS version.|\<Installation directory> \Reporting Services \ReportManager|  
|ReportingServicesService.exe.config|Stores configuration settings that specify the trace levels and logging options for the Report Server service. For more information about the elements in this file, see [ReportingServicesService Configuration File](../../reporting-services/report-server/reportingservicesservice-configuration-file.md).|\<Installation directory> \Reporting Services \ReportServer \Bin|  
|Registry settings|Stores configuration state and other settings used to uninstall Reporting Services. If you are troubleshooting an installation or configuration problem, you can view these settings to get information about how the report server is configured.<br /><br /> Do not modify these settings directly as this can invalidate your installation.|HKEY_LOCAL_MACHINE \SOFTWARE \Microsoft \Microsoft SQL Server \\<InstanceID\> \Setup<br /><br /> **- And -**<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\Services\ReportServer|  
|RSReportDesigner.config|Stores configuration settings for Report Designer. For more information, see [RSReportDesigner Configuration File](../../reporting-services/report-server/rsreportdesigner-configuration-file.md).|\<drive>:\Program Files \Microsoft Visual Studio 10 \Common7 \IDE \PrivateAssemblies.|  
|RSPreviewPolicy.config|Stores the code access security policies for the server extensions used during report preview. For more information about this file, see [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).|C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssembliesr|  
  
##  <a name="bkmk_config_file_Summary_sharepoint_mode"></a> Summary of configuration Files (SharePoint mode)  
 The following table provides a description of configuration files used for a SharePoint mode report server. Most configuration settings are stored in SharePoint service application databases. For more information, see [Reporting Services SharePoint Service and Service Applications](../../reporting-services/report-server-sharepoint/reporting-services-sharepoint-service-and-service-applications.md).  
  
 By default, the installation directory for SharePoint mode is the following:  
  
```Install path
C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting  
```  
  
|格納先|[説明]|場所|  
|----------------|-----------------|--------------|  
|RSReportServer.config|レポート サーバー サービスの機能領域 (レポート マネージャーまたは Web ポータル、レポート サーバー Web サービス、バックグラウンド処理) の構成設定が格納されます。 各設定の詳細については、「 [RsReportServer.config 構成ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)」を参照してください。|\<インストール ディレクトリ> \Reporting Services \ReportServer|  
|RSSrvPolicy.config|サーバー拡張機能のコード アクセス セキュリティ ポリシーが格納されます。 このファイルの詳細については、「 [Using Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md)」を参照してください。|\<インストール ディレクトリ> \Reporting Services \ReportServer|  
|レポート サーバー Web サービスの Web.config|SSRS のバージョンについては該当する場合、ASP.NET の必要な設定のみが含まれています。|\<インストール ディレクトリ> \Reporting Services \ReportServer|  
|レジストリ設定|構成状態のほか、Reporting Services をアンインストールするための設定が格納されます。 各 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションに関する情報も格納されます。<br /><br /> これらの設定を直接変更することは避けてください。環境に不具合が生じる可能性があります。|HKEY_LOCAL_MACHINE \SOFTWARE \Microsoft \Microsoft SQL Server \\<InstanceID\> \Setup<br /><br /> インスタンス ID の例: MSSQL13.MSSQLSERVER<br /><br /> **- および -**<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\Reporting Services\Service Applications|  
|RSReportDesigner.config|レポート デザイナーの構成設定が格納されます。 詳細については、「 [RSReportDesigner Configuration File](../../reporting-services/report-server/rsreportdesigner-configuration-file.md)」をご覧ください。|\<ドライブ>:\Program Files \Microsoft Visual Studio 10 \Common7 \IDE \PrivateAssemblies|  
  
## <a name="see-also"></a>参照  
 [Reporting Services レポート サーバー (ネイティブ モード)](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Reporting Services の拡張機能](../../reporting-services/extensions/reporting-services-extensions.md)   
 [rsconfig ユーティリティ &#40;SSRS&#41;](../../reporting-services/tools/rsconfig-utility-ssrs.md)   
 [レポート サーバー サービスの開始と停止](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)  
  
  
