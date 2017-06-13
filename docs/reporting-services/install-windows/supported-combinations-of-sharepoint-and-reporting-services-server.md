---
title: "SharePoint と Reporting Services サーバーのサポートされる組み合わせ |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 10/07/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint mode
- add-in for sharepoint
- rsSharePoint
ms.assetid: dc6a3372-db26-43f0-b7aa-f725acc635c2
caps.latest.revision: 39
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2e66cac836de44e8d2a9f23d88a600daaa26c0d1
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="supported-combinations-of-sharepoint-and-reporting-services-server"></a>SharePoint と Reporting Services サーバーのサポートされる組み合わせ
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

  SharePoint モードでインストールされている [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーには、SharePoint のバージョン、および SharePoint サーバーにインストールする SharePoint 製品の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドイン (rsSharePoint.msi) が必要です。  このトピックでは、サポートされる組み合わせの概要を説明します。  
  
## <a name="supported-combinations-of-sharepoint-and-reporting-services-components"></a>SharePoint および Reporting Services コンポーネントのサポートされる組み合わせ  
 次の表には、レポート サーバー、SharePoint 製品用 Reporting Services アドイン、および SharePoint 製品のサポートされる組み合わせの概要が示されています。 次の表に記載されていない組み合わせはサポートされません。  
  
### <a name="supported-combinations"></a>サポートされる組み合わせ  
  
||レポート サーバー|アドイン|SharePoint バージョン|  
|-|-------------------|-------------|------------------------|  
|1|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|SharePoint 2016|  
|2|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|SharePoint 2013|  
|3|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2013|  
|4|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|  
|5|SQL Server 2012 SP3|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] および SQL Server 2012 SP3|SharePoint 2013|  
|6|SQL Server 2012 SP2|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] および SQL Server 2012 SP2|SharePoint 2013|  
|7|[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 」および「 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2013|  
|8|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 」および「 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]*|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|  
|9|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|SharePoint 2010|  
|10|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|  
|11|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 」および「 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2010|  
|12|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|SharePoint 2010|  
|13|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|SharePoint 2007|  
|14|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] R2|SharePoint 2010|  
|15|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] および [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|SharePoint 2007|  
  
 * 例外: Power View の統合はサポートされていません。  
  
 アドインのダウンロード ページへのリンクについては、「 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)」を参照してください。  
  
 **追加情報:**  

- 必ず、ファーム内のすべての SharePoint サーバーをアップグレードしてください。 これには、アプリと Web フロントエンド サーバーが含まれます。

-   Power View の統合など、SharePoint 2016 のサポートには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーと SQL Server 2016 以降のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインが必要です。  

-   Power View の統合など、SharePoint 2013 のサポートには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーと SQL Server 2012 SP1 以降のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインが必要です。  
  
-   Power View は [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]で導入されました。 したがって、SharePoint 2010 と Power View の統合には、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降のアドインが必要です。  
  
-   SQL Server 2008 R2 アドインは、SQL Server 2012 (以降) のレポート サーバーではサポートされていません。 SharePoint 2010 の必須コンポーネントのインストーラーによって、SQL Server 2008 R2 アドインが自動的にインストールされます。 新しいバージョンのアドインをインストールする前に、SQL Server 2008 R2 アドインをアンインストールする必要があります。 アドインのインプレース アップグレードはサポートされていません。  
  
-   **アップグレード:** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインと共にインストールされた SharePoint 2010 を SharePoint 2013 にインプレース アップグレードすることはできません。 SharePoint 2013 には、 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 以降の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインとレポート サーバーが必要です。 アップグレードの詳細については、「 [Reporting Services のアップグレードと移行](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [SQL Server 2016 の各エディションでサポートされる機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)   
 [SQL Server 2016 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
  


