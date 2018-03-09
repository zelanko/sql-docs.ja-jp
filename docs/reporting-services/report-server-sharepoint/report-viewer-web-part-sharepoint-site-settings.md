---
title: "レポート ビューアー Web パーツに関する SharePoint サイト設定 - SSRS | Microsoft Docs"
ms.custom: 
ms.date: 10/31/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-server-sharepoint
ms.reviewer: 
ms.suite: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jt000
ms.author: jasontre
ms.workload: Inactive
ms.openlocfilehash: c5fa90156519843a81538dd4f867939910fc25d1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="sharepoint-site-settings-for-the-report-viewer-web-part---reporting-services"></a>レポート ビューアー Web パーツに関する SharePoint サイト設定

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

レポート ビューアー Web パーツには、構成できる設定がいくつかあります。 これらの設定は、サイト管理者が SharePoint サイトの設定ページで有効または無効にすることができます。 各サイトには独自の設定があることに注意してください。 さらに、これらの設定はレポート ビューアー Web パーツを再インストール後で、リセットされません。

## <a name="accessing-the-site-settings-page"></a>サイトの設定ページへのアクセス

サイトの設定には、次の方法でアクセスできます。

1. SharePoint サイトで、左上にある**歯車**アイコンを選び、**[サイトの設定]** を選びます。

    ![歯車アイコンを使用したサイトの設定。](media/sharepoint-site-settings.png)

2. **Reporting Services** のサイトの設定グループで、**[レポート ビューアー Web パーツの設定]** をクリックします。

    > [!NOTE]
    > `<site>/_layouts/15/ReportViewerWebPart/ReportViewerWebPartSettings.aspx` に直接移動して、サイトの設定にアクセスすることもできます。

## <a name="report-viewer-web-part-settings"></a>レポート ビューアー Web パーツの設定

|設定|コメント|  
|-------------|--------------|  
|使用状況データの収集|エラーおよび使用状況の情報を Microsoft に送信して製品の品質向上に協力します。 Microsoft のエラー報告データ収集のポリシーについては、「[Microsoft SQL Server のプライバシーに関する声明](https://go.microsoft.com/fwlink/?linkid=860782&clcid=0x409)」を参照してください。|  
|レポートのアクセシビリティ メタデータを有効にする|表示レポート用の [ `AccessibleTablix`デバイス情報](../html-device-information-settings.md)を設定します。| 
