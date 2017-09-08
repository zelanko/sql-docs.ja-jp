---
title: "Power BI 統合 (web ポータル) の設定 |Microsoft ドキュメント"
ms.date: 08/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- pbi
- power bi
- power bi integration
ms.assetid: 85c2fac7-80bf-45b7-8654-764b5f5231f5
caps.latest.revision: 15
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 7d5bc198ae3082c1b79a3a64637662968b0748b2
ms.openlocfilehash: 8e627f20918a4d6ee5f882677ccc7b2c26616e2f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/17/2017

---

# <a name="my-settings-for-power-bi-integration-web-portal"></a>Power BI 統合の個人用設定 (Web ポータル)

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] の **[個人用設定]** ページは、ユーザーが [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] へのサインインを管理するために使用します。 レポート アイテムをピン留めするための手順を実行すると、自動的にサインインするよう求められます。  ただし、手動でサインインする必要がある場合やサインアウトする必要がある場合は、 **[個人用設定]** ページを使用できます。  **[My Settings]** (個人用設定) メニュー オプションが表示されていない場合は、レポート サーバーが  [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]と統合されていません。  詳細については、「 [Power BI レポート サーバーの統合 &#40;構成マネージャー&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)へのサインインを管理するために使用します。  
  
![ssRS_WebPortal_MySettings](../reporting-services/media/ssrs-webportal-mysettings.png)  
  
## <a name="why-sign-in"></a>サインインする理由

 サインインすると、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ユーザー アカウントと [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] アカウントとの間に関係が確立されます。  サインインすることにより、90 日間有効のセキュリティ トークンが作成されます。 トークンの有効期限が切れ、Power BI に固定されたアイテムがある場合は、通知が表示されます。  
   
 ![ssRS_WebPortal_PowerBI_Notification](../reporting-services/media/ssrs-webportal-powerbi-notification.png)    
   
[!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] のダッシュボード内のタイルは、 **[個人用設定]**を通じて再度サインインするまで更新されません。  
  
![ssRS_WebPortal_PowerBI_SignIn_Again](../reporting-services/media/ssrs-webportal-powerbi-signin-again.png)  
  
一度サインインすると、新しいセキュリティ トークンが作成されます。  ダッシュボードのタイルは以前に構成したスケジュールに基づいて更新されます。  

## <a name="next-steps"></a>次の手順

[Power BI のレポート サーバーの統合](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)   
[Power BI ダッシュボードへの Reporting Services のアイテムのピン留め](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md)   
[Power BI のダッシュボード](https://powerbi.microsoft.com/documentation/powerbi-service-dashboards/)  
[Web ポータル](../reporting-services/web-portal-ssrs-native-mode.md)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
