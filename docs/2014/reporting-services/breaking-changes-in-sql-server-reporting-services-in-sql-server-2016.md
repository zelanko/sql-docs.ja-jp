---
title: SQL Server 2014 における SQL Server Reporting Services における重大な変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Me.Value references
- Reporting Services, backward compatibility
- breaking changes [Reporting Services]
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
caps.latest.revision: 111
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2e13cebd7697f2ff497ad0f288333e517c9e575d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327622"
---
# <a name="breaking-changes-in-sql-server-reporting-services-in-sql-server-2014"></a>SQL Server 2014 における SQL Server Reporting Services の重大な変更
  このトピックでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]における重大な変更について説明します。 これらの変更によって、以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に基づくアプリケーション、スクリプト、または機能が使用できなくなる場合があります。 この問題は、アップグレードするとき、またはカスタムのスクリプトやレポートで発生することがあります。 詳細については、「 [Use Upgrade Advisor to Prepare for Upgrades](../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)」を参照してください。  
  
 **このトピックの内容:**  
  
-   [SQL Server 2014 Reporting Services の重大な変更](#bkmk_sql14)  
  
-   [SQL Server 2012 Reporting Services の重大な変更](#bkmk_rc0)  
  
-   [SQL Server 2008 R2 Reporting Services の重大な変更](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services の重大な変更  
 あるない[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]における重大な変更[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]します。  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services の重大な変更  
  
### <a name="sharepoint-mode-server-references-require-the-sharepoint-site"></a>SharePoint モードのサーバー参照では SharePoint サイトが必要  
 URL パスで仮想ディレクトリ名を使用して、レポート サーバーを直接参照することはできません。 以下に例を示します。  
  
 `http://<Server name>/ReportServer`  
  
 URL パスに SharePoint サイトを含める必要があります。 たとえば、サイト名が '`videos`' で、'`sites`' プレフィックスを使用している場合、URL は次のようになります。  
  
 `http://<Server Name>/sites/videos/_vti_bin/ReportServer`  
  
### <a name="changes-to-sharepoint-mode-command-line-installation"></a>SharePoint モードのコマンド ライン インストールでの変更  
 入力設定 **/RSINSTALLMODE** は、ネイティブ モード インストールでのみ機能し、SharePoint モード インストールでは機能しません。 たとえば、次はサポートされていませんで[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]: **/RSINSTALLMODE ="DefaultSharePointMode"** します。 この入力設定の代わりに、 **/RSSHPINSTALLMODE="DefaultSharePointMode"** を使用してください。  
  
 次のステートメントは、完全なインストール コマンドとパラメーター セットの例です: **setup /ACTION=install /FEATURES=SQL,RS /InstanceName=Denali_INST1 …. /RSSHPINSTALLMODE="DefaultSharePointMode"**  
  
 コマンド ライン インストールの詳細については、次を参照してください。[コマンド プロンプト インストールの Reporting Services SharePoint モードとネイティブ モード](install-windows/install-reporting-services-at-the-command-prompt.md)します。  
  
### <a name="the-reporting-services-wmi-provider-no-longer-supports-configuration-of-sharepoint-mode"></a>Reporting Services WMI プロバイダーでの SharePoint モードの構成操作の廃止  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint の構成は、PowerShell コマンドレットと SharePoint サーバーの全体管理を使用して行うようになりました。 新しい [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モード アーキテクチャでは、SharePoint サービス アーキテクチャが使用されます。 SharePoint では、WMI インターフェイスはサポートされません。  
  
 これらの変更によって影響を受けるコンポーネントとワークフローを次に示します。  
  
-   使用するカスタム アプリケーション、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]用 WMI プロバイダー [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モードでします。  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 構成マネージャー、rskeymgmt.exe、および rsconfig.exe。 これらのユーティリティを使用して、構成ではなく[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint モードでは、SharePoint サーバーの全体管理と PowerShell を使用します。  
  
-   SQL Server Management Studio: <machine_name>/<instance_name> のような構文でサーバーを参照することはできません。 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] リリース以降では、SharePoint サイト URL を使用する方法が推奨の方法となります。 たとえば、 **http://<sharepoint_server>/<sharePoint_site>** します。 以降で[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]、SharePoint サイトの URL は、唯一サポートされている構文。  
  
### <a name="report-model-designer-is-not-available-in-sql-server-data-tools"></a>レポート モデル デザイナーは SQL Server Data Tools では使用できません  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] レポート モデル プロジェクトをサポートしていません。 レポート モデル デザイナーは [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] では使用できません。 新しいレポート モデル プロジェクトを作成することはできませんか、既存のプロジェクトを開く[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]作成したり、レポート モデルを更新することはできません。 レポート モデルを更新するを使用することができます[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]以前のツール。 レポート モデルは、レポート ビルダーやレポート デザイナーなどの [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] ツールで作成されたレポートでデータ ソースとして使用し続けることができます。 使用できるレポート モデルからレポート データを抽出するクエリを作成するために使用するクエリ デザイナーが引き続き[!INCLUDE[ssSQL11](../includes/sssql11-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]します。  
  
##  <a name="bkmk_kj"></a> SQL Server 2008 R2 Reporting Services の重大な変更  
 このセクションで重大な変更を説明します[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]します。  
  
> [!NOTE]  
>  SQL Server 2008 R2 は SQL Server 2008 のマイナー バージョン アップグレードなので、SQL Server 2008 のセクションのコンテンツも確認することをお勧めします。  
  
### <a name="expanded-csv-data-renderer"></a>拡張された CSV データ レンダラー  
 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]、CSV ファイルには、グラフおよびゲージのデータが含まれています。 グラフとゲージの列が追加されたため、以前の CSV ファイル構造を使用するアプリケーションは動作しなくなる可能性があります。  
  
 詳細については、「[CSV ファイルへのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 における SQL Server Reporting Services の動作変更します。](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [新機能については&#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [SQL Server 2014 における SQL Server Reporting Services の非推奨の機能](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [SQL Server 2014 で廃止された SQL Server Reporting Services の機能](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
