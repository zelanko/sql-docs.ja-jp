---
title: "個人用サブスクリプション (ネイティブ モード レポート サーバー) を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subscriptions [Reporting Services], My Subscriptions page
- My Subscriptions page [Reporting Services]
ms.assetid: e96623ba-677e-4748-8787-f32bed3b5c12
caps.latest.revision: 40
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: bc870d25cc341f84909e595cde4a411fecbf6603
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="use-my-subscriptions-native-mode-report-server"></a>個人用サブスクリプションを使用する (ネイティブ モードのレポート サーバー)
[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web ポータルには、すべてのサブスクリプションを 1 か所で構成する **[個人用サブスクリプション]** ページが含まれています。 *[個人用サブスクリプション]* を使用して、既存のサブスクリプションを表示、変更、有効化、無効化、および削除できます。 ただし、このページは、サブスクリプションの作成には使用できません。  [個人用サブスクリプション] では、自分で作成したサブスクリプションだけが表示されます。 他のユーザーが所有しているサブスクリプションにサブスクライバーとして自分が追加されていても、そのサブスクリプションは一覧表示されません。データ ドリブン サブスクリプションも表示されません。
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード|  
  
検索フィールドに条件を入力すると、サブスクリプションの一覧が動的にフィルター処理されます。サブスクリプションを名前で検索することはできません。また、トリガー情報、状態情報などを基にサブスクリプションを検索することもできません。 詳細については、「 [ネイティブ モード レポート サーバーのサブスクリプションの作成と管理](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md)」を参照してください。
  
## <a name="to-open-the-my-subscriptions-page"></a>[個人用サブスクリプション] ページを開くには  
1. [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] Web ポータルを開きます。
2. ツールバーで設定 ![ssrs_portal_settings_gear](../../reporting-services/subscriptions/media/ssrs-portal-settings-gear.png) をクリックします。
3. **[個人用サブスクリプション]**をクリックします。

詳細については、「 [Web portal (SSRS Native Mode)](../../reporting-services/web-portal-ssrs-native-mode.md)」を参照してください。

## <a name="use-windows-powershell-to-list-mysubscriptions"></a>Windows PowerShell を使用した個人用サブスクリプションの一覧表示  
 ![PowerShell 関連コンテンツ](../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")  
  
 次の PowerShell スクリプトは、現在のユーザーのサブスクリプションとサブスクリプションのプロパティの一覧を返します。 詳細については、「 [ReportingService2010.ListMySubscriptions メソッド](http://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx)」を参照してください。  
  
```  
#server -  all subscriptions of the current user at the given server or site  
$server="[server name]/reportserver"  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
  
$subscriptions=ListMySubscriptions(ItemPathOrSiteURL)  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status  
#uncomment the following to list all the subscription properties  
#$subscriptions

```  
  
## <a name="see-also"></a>参照  
 [データ ドリブン サブスクリプション](../../reporting-services/subscriptions/data-driven-subscriptions.md)   
 [サブスクリプションと配信 & #40 です。Reporting Services &#41;](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [作成とネイティブ モード レポート サーバーの サブスクリプションの管理](http://msdn.microsoft.com/en-us/7f46cbdb-5102-4941-bca2-5e0ff9012c6b)  
  
  

