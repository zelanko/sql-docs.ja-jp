---
title: SharePoint 製品用 Reporting Services アドインの検索場所 | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- rsSharePoint
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 11/16/2015
ms.openlocfilehash: 8f5b935636c4d00f39324e4a343419e3da68284b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66108576"
---
# <a name="where-to-find-the-reporting-services-add-in-for-sharepoint-products"></a>SharePoint 製品用 Reporting Services アドインの検索場所

SharePoint 製品およびテクノロジ (rsSharePoint.msi) 用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (SSRS) アドインは Web からダウンロードでき、SharePoint で構築した配置にレポート サーバーを統合する機能を提供します。  
  
> [!IMPORTANT]  
>  サポートされる組み合わせの一覧については、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]アドイン、レポート サーバー、および SharePoint の詳細についてを参照してくださいを参照してください[SharePoint の組み合わせをサポートし、Reporting Services サーバーとアドイン&#40;SQL Server 2014&#41; 。](supported-combinations-of-sharepoint-and-reporting-services-server.md).  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SharePoint 製品用 Reporting Services アドイン  
 アドインをダウンロードしてインストールするには、以下の [!INCLUDE[msCoName](../../includes/msconame-md.md)] ダウンロード センターを参照してください。  
  
-   [Microsoft SharePoint 用 Microsoft® SQL Server® 2014 Reporting Services アドイン](https://go.microsoft.com/fwlink/?LinkID=324852)  
  
 このアドインの [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] バージョンは、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] インストール ウィザードでも提供されます。  
  
-   セットアップ ウィザードの **[機能の選択]** ページで、 **[SharePoint 製品用 Reporting Services アドイン]** を選択します。  
  
-   コマンド プロンプトでのインストールから、 **RS_SHPWFE** オプションを使用してアドインをインストールします。 詳細については[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]コマンド プロンプト インストールを参照してください[コマンド プロンプト インストールの Reporting Services SharePoint モードとネイティブ モード](install-reporting-services-at-the-command-prompt.md)します。  
  
##  <a name="bkmk_sql11sp1"></a> [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] SharePoint 製品用 Reporting Services アドイン  
 アドインとレポート サーバーの [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] バージョンには、SharePoint Server 2013 のサポートが追加されます。  
  
 アドインをダウンロードしてインストールするには、以下の [!INCLUDE[msCoName](../../includes/msconame-md.md)] ダウンロード センターを参照してください。  
  
-   **SP1 アドイン:** [Microsoft® SQL Server® 2012 SP1 Reporting Services アドインの Microsoft® SharePoint® 用](https://www.microsoft.com/download/details.aspx?id=35583)(https://www.microsoft.com/download/details.aspx?id=35583) します。  
  
-   **SP 1:** [Microsoft® SQL Server® 2012 Service Pack 1 (SP1)](https://go.microsoft.com/fwlink/p/?LinkID=255906) (https://go.microsoft.com/fwlink/p/?LinkID=255906) します。  
  
##  <a name="bkmk_sql11"></a> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SharePoint 2010 製品用 Reporting Services アドイン  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] リリースから、アドインは [機能の選択] ページで SQL Server インストール ウィザードの一部としてインストールできるようになりました。 アドインを別途ダウンロードしてインストールする場合、このファイルの最新バージョンは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ダウンロード センターの「 [Microsoft® SharePoint® テクノロジ 2010 用 Microsoft® SQL Server® 2012 Reporting Services アドイン](https://go.microsoft.com/fwlink/?LinkID=207242) 」ページからオンラインで入手できます。  
  
##  <a name="bkmk_sql2008r2"></a> SQL Server 2008 R2 Reporting Services アドインを SharePoint 2010 製品用  
 Microsoft SharePoint 2010 製品用 Microsoft SQL Server 2008 R2 Reporting Services アドインは、SharePoint 2010 製品準備ツール (**PreRequisiteInstaller.exe**) によってインストールされます。 アドインを別途ダウンロードしてインストールする場合、このファイルの最新バージョンは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ダウンロード センターの「 [Microsoft SharePoint テクノロジ 2010 用 SQL Server 2008 R2 Reporting Services アドイン](https://go.microsoft.com/fwlink/?LinkID=164654)」ページからオンラインで入手できます。  
  
> [!TIP]  
>  これを、Cumulative Update #8 以降を含む SQL Server 2008 Service Pack 1 (SP1) と使用する場合は、「 [SQL Server 2008 SP2 Report Servers と SharePoint 2010 の統合](https://technet.microsoft.com/library/ff946055%28SQL.100%29.aspx)」の「SharePoint 2010 統合での既知の問題」を確認してください。  
  
##  <a name="bkmk_sql2008sp2"></a> SQL Server 2008 SP2 Reporting Services アドインを SharePoint 2007 製品およびテクノロジ  
 Microsoft SQL Server 2008 SP2 Reporting Services アドインは、SharePoint 2007 製品と 2008 R2 レポート サーバーの統合のサポートを追加する 2008 アドインの更新バージョンです。  
  
 このファイルの最新バージョンは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ダウンロード センターの「 [Microsoft SharePoint テクノロジ用 Microsoft SQL Server 2008 SP2 Reporting Services アドイン](https://go.microsoft.com/fwlink/?LinkID=204594)」ページからオンラインで入手できます。  
  
##  <a name="bkmk_sql2008"></a> SQL Server 2008 Reporting Services アドインを SharePoint 2007 製品およびテクノロジ  
 Microsoft SharePoint テクノロジ用 Microsoft SQL Server 2008 Reporting Services アドインは、Windows SharePoint Services 3.0 または Microsoft Office SharePoint Server 2007 で構築した配置内でレポート サーバーを実行するための機能を提供します。  
  
 このファイルの最新バージョンは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ダウンロード センターの「 [Microsoft SharePoint テクノロジ用 Microsoft SQL Server 2008 Reporting Services アドイン](https://www.microsoft.com/download/details.aspx?id=622)」ページからオンラインで入手できます。  
  
## <a name="see-also"></a>参照  
 [インストールまたはアンインストール、Reporting Services アドイン、SharePoint の&#40;SharePoint 2010 および SharePoint 2013&#41;](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [レポート サーバー コンテンツ タイプをライブラリに追加&#40;Reporting Services の SharePoint 統合モード&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md)   
 [Reporting Services アドインをアンインストールした後は、既定以外のゾーンで SharePoint ページを参照することはできません。](https://support.microsoft.com/kb/2009212)  
  
  
