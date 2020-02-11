---
title: SharePoint と Reporting Services Server およびアドインのサポートされている組み合わせ (SQL Server 2014) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SharePoint mode
- add-in for sharepoint
ms.assetid: dc6a3372-db26-43f0-b7aa-f725acc635c2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05f0997cb73a156e54b22ad280fa5d6eb0ec7d73
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108651"
---
# <a name="supported-combinations-of-sharepoint-and-reporting-services-server-and-add-in-sql-server-2014"></a>SharePoint、Reporting Services サーバー、Reporting Services アドインのサポートされる組み合わせ (SQL Server 2014)
  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーは SharePoint モードでインストールし、SharePoint 配置と統合できます。 レポート サーバー、SharePoint 用 Reporting Services アドイン、および SharePoint 製品のすべての組み合わせで、すべての機能がサポートされているわけではありません。 このトピックでは、サポートされる組み合わせの概要を説明します。 で[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]は、次の組み合わせによって統合が行われます。  
  
-   
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーのバージョンが SharePoint モード用に構成されていること。  
  
-   SharePoint 製品。  
  
-   SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインを SharePoint サーバーにインストールします。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** Sharepoint 2013 &#124; sharepoint 2010 &#124; sharepoint 2007|  
  
## <a name="supported-combinations-of-sharepoint-and-reporting-services-components"></a>SharePoint および Reporting Services コンポーネントのサポートされる組み合わせ  
 次の表には、レポート サーバー、SharePoint 製品用 Reporting Services アドイン、および SharePoint 製品のサポートされる組み合わせの概要が示されています。 次の表に記載されていない組み合わせはサポートされません。  
  
### <a name="supported-combinations"></a>サポートされる組み合わせ  
  
||レポート サーバー|アドイン|SharePoint バージョン|サポートされています|  
|-|-------------------|-------------|------------------------|---------------|  
|1 で保護されたプロセスとして起動されました|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2013|はい|  
|2|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|はい|  
|3|[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]そして[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2013|はい|  
|4|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]そして[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|はい<br /><br /> 例外: Power View の統合はサポートされていません。|  
|5|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|SharePoint 2010|はい|  
|6|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|はい|  
|7|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]そして[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2010|はい|  
|8|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|SharePoint 2010|はい|  
|9|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|SharePoint 2007|はい|  
|10|
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]もたらし|SharePoint 2010|はい|  
|11|
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] および [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|SharePoint 2007|はい|  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]機能とレポートサーバーのモードの詳細については、「[レポートサーバーの Reporting Services](../reporting-services-report-server.md)」を参照してください。  
  
 **その他の注意事項:**  
  
-   Power View の統合など、SharePoint 2013 のサポートには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーと SQL Server 2012 SP1 以降のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインが必要です。  
  
-   Power View は [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]で導入されました。 したがって、SharePoint 2010 と Power View の統合には、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降のアドインが必要です。  
  
-   SQL Server 2008 R2 アドインは、SQL Server 2012 (以降) のレポート サーバーではサポートされていません。 SharePoint 2010 の必須コンポーネントのインストーラーによって、SQL Server 2008 R2 アドインが自動的にインストールされます。 新しいバージョンのアドインをインストールする前に、SQL Server 2008 R2 アドインをアンインストールする必要があります。 アドインのインプレース アップグレードはサポートされていません。  
  
-   **アップグレード:**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]アドインがインストールされている sharepoint 2010 は、sharepoint 2013 にインプレースアップグレードすることはできません。 SharePoint 2013 には、 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 以降の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインとレポート サーバーが必要です。 アップグレードの詳細については、「 [Reporting Services のアップグレードと移行](upgrade-and-migrate-reporting-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SharePoint 製品用の Reporting Services アドインの検索場所](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Upgrade and Migrate Reporting Services](upgrade-and-migrate-reporting-services.md)  
  
  
