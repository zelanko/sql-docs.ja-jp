---
title: 個人用サブスクリプションを使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- subscriptions [Reporting Services], My Subscriptions page
- My Subscriptions page [Reporting Services]
ms.assetid: e96623ba-677e-4748-8787-f32bed3b5c12
caps.latest.revision: 36
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: c1125792543e3a926ddb98e3d33e0f600328d232
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179237"
---
# <a name="use-my-subscriptions"></a>個人用サブスクリプションを使用する
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] レポート マネージャーが含まれています、**個人用サブスクリプション**すべてのサブスクリプションを 1 か所で構成するページ。 [個人用サブスクリプション] を使用して、既存のサブスクリプションを表示、変更、および削除できます。 ただし、このページは、サブスクリプションの作成には使用できません。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ネイティブ モード|  
  
 [個人用サブスクリプション] 内では、フォルダー、レポート、説明、トリガー、最後に実行された日時、状態によるサブスクリプションの並べ替えが可能です。 日時順に並べ替えられる [最終実行] を除いて、すべての値はアルファベット順に並べ替えられます。  
  
 [個人用サブスクリプション] では、自分で作成したサブスクリプションだけが表示されます。 他のユーザーが所有しているサブスクリプションにサブスクライバーとして自分が追加されていても、そのサブスクリプションは一覧表示されません。データ ドリブン サブスクリプションも表示されません。  
  
 サブスクリプションを名前で検索することはできません。また、トリガー情報、状態情報などを基にサブスクリプションを検索することもできません。 詳細については、次を参照してください。 [Create, Modify, and 標準のサブスクリプションを削除&#40;Reporting Services ネイティブ モードの&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md)です。  
  
## <a name="how-to-use-my-subscriptions"></a>個人用サブスクリプションを使用する方法  
 個人用サブスクリプションはレポート マネージャーから利用できます。 個人用サブスクリプションにアクセスするには、クリックして**個人用サブスクリプション**レポート マネージャーのグローバル ツールバー。  
  
## <a name="use-windows-powershell-to-list-mysubscriptions"></a>Windows PowerShell を使用した個人用サブスクリプションの一覧表示  
 ![PowerShell 関連コンテンツ](../media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")  
  
 次の PowerShell スクリプトは、現在のユーザーのサブスクリプションとサブスクリプションのプロパティの一覧を返します。 詳細については、「 [ReportingService2010.ListMySubscriptions メソッド](http://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx)」を参照してください。  
  
```  
#server -  all subscriptions of the current user at the given server or site  
$server="[server name]/reportserver"  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
  
$subscriptions=ListMySubscriptions(ItemPathOrSiteURL)  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status  
#uncomment the following to list all the subscription properties  
#$subscriptions  
  
```  
  
## <a name="see-also"></a>参照  
 [データ ドリブン サブスクリプション](data-driven-subscriptions.md)   
 [サブスクリプションと配信&#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [ネイティブ モード レポート サーバーのサブスクリプションの作成と管理](../create-manage-subscriptions-native-mode-report-servers.md)  
  
  