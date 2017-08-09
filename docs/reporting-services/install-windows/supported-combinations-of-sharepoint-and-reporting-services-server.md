---
title: "SharePoint と Reporting Services サーバーのサポートされる組み合わせ |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/01/2017
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
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 507c09d09f22f8326898b557997bc109785f30c0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---

# <a name="supported-combinations-of-sharepoint-and-reporting-services-server"></a>SharePoint と Reporting Services サーバーのサポートされる組み合わせ

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

SharePoint モードでインストールされた SQL Server Reporting Services レポート サーバーには、SharePoint サーバーにインストールする SharePoint 製品用の SharePoint と SQL Server Reporting Services アドイン (rsSharePoint.msi) のバージョンが必要です。 このトピックでは、サポートされる組み合わせの概要を説明します。

> [!NOTE]
> SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。

## <a name="supported-combinations-of-sharepoint-and-reporting-services-components"></a>SharePoint および Reporting Services コンポーネントのサポートされる組み合わせ

 次の表には、レポート サーバー、SharePoint 製品用 Reporting Services アドイン、および SharePoint 製品のサポートされる組み合わせの概要が示されています。 次の表に記載されていない組み合わせはサポートされません。

### <a name="supported-combinations"></a>サポートされる組み合わせ

||レポート サーバー|アドイン|SharePoint バージョン|
|-|-------------------|-------------|------------------------|
|1|SQL Server 2016|SQL Server 2016|SharePoint 2016|
|2|SQL Server 2016|SQL Server 2016|SharePoint 2013|
|3|SQL Server 2014|SQL Server 2014|SharePoint 2013|
|4|SQL Server 2014|SQL Server 2014|SharePoint 2010|
|5|SQL Server 2012 SP3|SQL Server 2014 および SQL Server 2012 SP3|SharePoint 2013|
|6|SQL Server 2012 SP2|SQL Server 2014 および SQL Server 2012 SP2|SharePoint 2013|
|7|SQL Server 2012 SP1|SQL Server 2014 および SQL Server 2012 SP1|SharePoint 2013|
|8|SQL Server 2012 および SQL Server 2012 SP1 *|SQL Server 2014|SharePoint 2010|
|9|SQL Server 2012|SQL Server 2012|SharePoint 2010|
|10|SQL Server 2008 R2|SQL Server 2014|SharePoint 2010|
|11|SQL Server 2008 R2|SQL Server 2012 および SQL Server 2012 SP1 以降|SharePoint 2010|
|12|SQL Server 2008 R2|SQL Server 2008 R2|SharePoint 2010|
|13|SQL Server 2008 R2|SQL Server 2008 SP2|SharePoint 2007|
|14|SQL Server 2008 SP2|SQL Server 2008 R2|SharePoint 2010|
|15|SQL Server 2008 SP2|SQL Server 2008 および SQL Server 2008 SP2|SharePoint 2007|

 * 例外: Power View の統合はサポートされていません。

 アドインのダウンロード ページへのリンクについては、「 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)」を参照してください。  

 **追加情報:**

- 必ず、ファーム内のすべての SharePoint サーバーをアップグレードしてください。 これには、アプリと Web フロントエンド サーバーが含まれます。

- Power View の統合など、SharePoint 2016 のサポートには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーと SQL Server 2016 以降のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインが必要です。

- Power View の統合など、SharePoint 2013 のサポートには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーと SQL Server 2012 SP1 以降のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインが必要です。

- Power View は、SQL Server 2012 で導入されました。 そのため、SharePoint 2010 と Power View の統合には、SQL Server 2012 以降のアドインが必要です。

- SQL Server 2008 R2 アドインは、SQL Server 2012 (以降) のレポート サーバーではサポートされていません。 SharePoint 2010 の必須コンポーネントのインストーラーによって、SQL Server 2008 R2 アドインが自動的にインストールされます。 新しいバージョンのアドインをインストールする前に、SQL Server 2008 R2 アドインをアンインストールする必要があります。 アドインのインプレース アップグレードはサポートされていません。

- **アップグレード:** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインと共にインストールされた SharePoint 2010 を SharePoint 2013 にインプレース アップグレードすることはできません。 SharePoint 2013 には、SQL Server 2012 SP1 が必要がありますまたはそれ以降の[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]アドインとレポート サーバー。 アップグレードの詳細については、「 [Reporting Services のアップグレードと移行](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)」を参照してください。

## <a name="next-steps"></a>次の手順

 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [SQL Server 2016 の各エディションでサポートされる機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)   
 [SQL Server 2016 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
