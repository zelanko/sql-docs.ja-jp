---
title: "Disable or Pause Report and サブスクリプションの処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/29/2015
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pausing schedules
- subscriptions [Reporting Services], pausing
- report processing [Reporting Services], pausing
- shared data sources [Reporting Services]
- pausing subscription processing
- pausing report processing
- temporarily stopping report processing
- disabling shared data sources
- roles [Reporting Services], modifying
- shared schedules [Reporting Services], pausing
ms.assetid: 3cf9a240-24cc-46d4-bec6-976f82d8f830
caps.latest.revision: 47
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9fa43a5766fc82bfb716f275600b50eaab6c1ed0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="disable-or-pause-report-and-subscription-processing"></a>レポートとサブスクリプションの処理を無効化または一時停止する
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のレポートやサブスクリプションの処理を無効化または一時停止するには、複数の方法があります。 このトピックで説明する範囲は、サブスクリプションの無効化から、データ ソース接続の中断までです。 両方の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サーバー モードですべての方法を使用することはできません。次の表は、方法とサポートされる [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サーバー モードをまとめたものです。  
  
##  <a name="bkmk_top"></a> このトピックの内容  
  
||サポートされるサーバー モード|  
|-|---------------------------|  
|[サブスクリプションを有効または無効にする](#bkmk_disable_subscription)|ネイティブ モード|  
|[共有スケジュールを一時停止する](#bkmk_pause_schedule)|ネイティブ モードと SharePoint モード|  
|[共有データ ソースを無効にする](#bkmk_disable_shared_datasource)|ネイティブ モードと SharePoint モード|  
|[レポートへのアクセスを禁止するためのロールの割り当てを変更する (ネイティブ モード)](#bkmk_modify_role_assignment)|ネイティブ モード|  
|[ロールからサブスクリプション管理アクセス許可を削除する (ネイティブ モード)](#bkmk_remove_manage_subscriptions_permission)|ネイティブ モード|  
|[配信拡張機能を無効にする](#bkmk_disable_extensions)|ネイティブ モードと SharePoint モード|  
  
##  <a name="bkmk_disable_subscription"></a> サブスクリプションを有効または無効にする  
  
> [!TIP]  
>  [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]での新機能です。 **サブスクリプションを有効または無効にすることができます**。 新しいユーザー インターフェイス オプションを使用して、サブスクリプションを簡単に無効または有効にできます。 サブスクリプションを無効にしても、スケジュールなどの他の構成プロパティは維持され、簡単に有効にすることができます。 また、プログラムを使用してサブスクリプションを有効または無効にしたり、無効にされたサブスクリプションを監査したりすることもできます。  
  
 ![reporting services のサブスクリプションのリボン](../../reporting-services/subscriptions/media/ssrs-subscription-ribbon.png "reporting services のサブスクリプションのリボン")  
  
 ネイティブ モードのレポート マネージャーで、 **[個人用サブスクリプション]** ページまたは個別のサブスクリプションの **[管理]** ページからサブスクリプションに移動します。 1 つまたは複数のサブスクリプションを選択し、無効にするかをクリックして![reporting services のサブスクリプションを無効にする](../../reporting-services/subscriptions/media/ssrs-disable-subscription.png "reporting services のサブスクリプションを無効にする")ボタンまたはボタンを有効にする![reporting services のサブスクリプションを有効にする](../../reporting-services/subscriptions/media/ssrs-enable-subscription.png "reporting services のサブスクリプションを有効にする")リボン上。 警告アイコンが無効なサブスクリプションのフラグが立てられて![services subscriptio のレポート処理のステータスの警告](../../reporting-services/subscriptions/media/ssrs-subscription-warning.png "subscriptio services のレポート処理のステータスの警告")として状態が表示されて**無効になっている**です。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ログに 1 行書き込み、サブスクリプションが有効になると別のエントリを書き込みます。 次はレポート サーバーのログ ファイルの例です。  
  
 `C:\Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\LogFiles\ReportServerService__10_16_2014_00_02_18.log`  
  
 このファイルに次のような行が書き込まれます。  
  
 `library!ReportServer_0-1!b08!10/16/2014-16:21:14:: i INFO: Call to DisableSubscriptionAction(SubscriptionID=e843bc2b-023e-45a3-ba23-22f9dc9a0934)`  
  
 `library!ReportServer_0-1!2eec!10/16/2014-16:44:18:: i INFO: Call to EnableSubscriptionAction(SubscriptionID=e843bc2b-023e-45a3-ba23-22f9dc9a0934).`  
  
 ![PowerShell 関連コンテンツ](../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")**を 1 つのサブスクリプションを無効にする Windows PowerShell を使用して:**を特定のサブスクリプションを無効にする、次の PowerShell スクリプトを使用します。 サーバー名とサブスクリプション ID を更新します。  
  
```  
#disable specific subscription  
$rs2010 = New-WebServiceProxy -Uri "http://SERVERNAME/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptionID = "subscription guid”;  
$rs2010.DisableSubscription($subscriptionID);  
  
```  
  
 次のスクリプトを使用すると、すべてのサブスクリプションとその ID を一覧表示できます。 サーバー名を更新します。  
  
```  
#list all subscriptions  
$rs2010 = New-WebServiceProxy -Uri "http://SERVERNAME /ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/");  
$subscriptions | select subscriptionid, report, status, path  
  
```  
  
 ![PowerShell 関連コンテンツ](../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")**をすべて無効になったサブスクリプションを一覧表示する Windows PowerShell を使用して:**次の PowerShell スクリプトを使用して、現在のネイティブ モード レポート サーバーで無効なサブスクリプションのすべてを一覧表示します。 サーバー名を更新します。  
  
```  
#list all disabled subscriptions  
$rs2010 = New-WebServiceProxy -Uri "http://uetestb03/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/");  
Write-Host "--- Disabled Subscriptions ---";  
Write-Host "----------------------------------- ";  
$subscriptions | Where-Object {$_.Active.DisabledByUserSpecified -and $_.Active.DisabledByUser } | select subscriptionid, report, status, lastexecuted,path | format-table -auto  
```  
  
 ![PowerShell 関連コンテンツ](../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")**をすべて無効になったサブスクリプションを有効にする Windows PowerShell を使用して:**現在無効になっているすべてのサブスクリプションを有効にする、次の PowerShell スクリプトを使用します。 サーバー名を更新します。  
  
```  
#enable all subscriptions  
$rs2010 = New-WebServiceProxy -Uri "http://SERVERNAME/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/") | Where-Object {$_.status -eq "disabled" } ;  
ForEach ($subscription in $subscriptions)  
{  
    $rs2010.EnableSubscription($subscription.SubscriptionID);  
    $subscription | select subscriptionid, report, path  
}  
  
```  
  
 ![PowerShell 関連コンテンツ](../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")**すべてのサブスクリプションを無効にする Windows PowerShell を使用して:**リストを無効にするには、次の PowerShell スクリプトを使用して**すべて**サブスクリプション。  
  
```  
#DISABLE all subscriptions  
$rs2010 = New-WebServiceProxy -Uri "http://SERVERNAME/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/") ;  
ForEach ($subscription in $subscriptions)  
{  
    $rs2010.DisableSubscription($subscription.SubscriptionID);  
    $subscription | select subscriptionid, report, path  
}  
```  
  
##  <a name="bkmk_pause_schedule"></a> 共有スケジュールを一時停止する  
 レポートまたはサブスクリプションが共有スケジュールから実行される場合、スケジュールを一時停止して処理を中止できます。 一時停止したスケジュールで実行されるすべてのレポートおよびサブスクリプションの処理は、スケジュールが再開されるまで延期されます。  
  
-   **SharePoint モード:** ![SharePoint 設定](../../analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 設定")で**サイトの設定****共有スケジュールの管理**です。 スケジュールを選択し、 **[選択したスケジュールの一時停止]**をクリックします。  
  
-   **ネイティブ モード:** レポート マネージャーで、 **[サイトの設定]**をクリックします。 スケジュールを選択し、 **[一時停止]**をクリックします。  
  
##  <a name="bkmk_disable_shared_datasource"></a> 共有データ ソースを無効にする  
 共有データ ソースを使用する利点の 1 つは、共有データ ソースを無効にして、レポートまたはデータ ドリブン サブスクリプションの実行を中止できることです。 共有データ ソースを無効にすると、レポートは外部ソースから切断されます。 共有データ ソースが無効な間は、すべてのレポートと共有データ ソースを使用するサブスクリプションで共有データ ソースを使用できません。  
  
 データ ソースが使用できない場合でも、レポートは読み込まれることに注意してください。 レポートにはデータは含まれていませんが、適切な権限を持ったユーザーは、レポートに関連付けられたプロパティ ページ、セキュリティ設定、レポート履歴、およびサブスクリプション情報にアクセスできます。  
  
-   **SharePoint モード:** SharePoint モードのレポート サーバーで共有データ ソースを無効にするには、データ ソースを含むドキュメント ライブラリに移動します。 ![共有データ ソース アイコン](../../reporting-services/report-data/media/hlp-16datasource.png "共有データ ソース アイコン")データ ソースをクリックし、オフ、**このデータ ソースを有効にする**チェック ボックスをオンします。  
  
-   **ネイティブ モード:** ネイティブ モードのレポート サーバーで共有データ ソースを無効にするには、レポート マネージャーでデータ ソースを開き、 **[このデータ ソースを有効にする]** チェック ボックスをオフにします。  
  
##  <a name="bkmk_modify_role_assignment"></a> レポートへのアクセスを禁止するためのロールの割り当てを変更する (ネイティブ モード)  
 レポートを使用できないようにする方法の 1 つは、レポートにアクセスするためのロールの割り当てを一時的に削除することです。 この方法は、データ ソースへの接続方法に関係なくすべてのレポートに使用できます。 この方法は、ロールの割り当てを一時的に削除したレポートのみに有効で、他のレポートやアイテムの操作には影響しません。  
  
 ロールの割り当てを削除するには、レポート マネージャーでレポートの [セキュリティ] プロパティ ページを開きます。 そのレポートが親レポートからセキュリティを継承している場合は、 **[アイテムのセキュリティを編集]** をクリックして、広範囲なアクセスを提供するロールの割り当てを削除する、制限付きのセキュリティ ポリシーを作成できます。たとえば、Everyone にアクセスを提供するロールの割り当てを削除し、Administrators など小さなユーザー グループにアクセスを提供するロールの割り当てを保持できます。  
  
##  <a name="bkmk_remove_manage_subscriptions_permission"></a> ロールからサブスクリプション管理アクセス許可を削除する (ネイティブ モード)  
 ユーザーがサブスクリプションを作成できないようにするには、ロールから **[個別のサブスクリプションを管理]** タスクをオフにします。 このタスクを削除すると、[サブスクリプション] ページは使用できなくなります。 レポート マネージャーでは、[個人用サブスクリプション] ページには、既にサブスクリプションが含まれていても、何も表示されません (このページは削除できません)。 サブスクリプション関連タスクを削除すると、ユーザーはサブスクリプションを作成および変更できなくなりますが、既存のサブスクリプションは削除されません。 既存のサブスクリプションは、削除されない限り、引き続き実行されます。 アクセス許可を削除するには:  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開きます。  
  
2.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーに接続します。  
  
3.  **[セキュリティ]** ノードを展開します。  
  
4.  ロールを選択し、 **[個別のサブスクリプションを管理]** タスクをオフにします。  
  
##  <a name="bkmk_disable_extensions"></a> 配信拡張機能を無効にする  
 レポート サーバーにインストールされたすべての配信拡張機能は、特定のレポートのサブスクリプションを作成する権限を持つユーザーが使用できます。 使用できる配信拡張機能は次のとおりです。自動的に構成されます。  
  
-   Windows ファイル共有  
  
-   SharePoint ライブラリ (SharePoint 統合モードのレポート サーバーと統合された SharePoint サイトからのみ利用可能)  
  
 電子メール配信は使用前に構成する必要があります。 構成が済んでいない場合、使用できません。 詳細については、「 [電子メール配信用にレポート サーバーを構成する (SSRS 構成マネージャー)](http://msdn.microsoft.com/en-us/b838f970-d11a-4239-b164-8d11f4581d83)」を参照してください。  
  
 特定の拡張機能を無効にするには、 **RSReportServer.config** ファイルから拡張機能のエントリを削除します。 詳細については、 [「Reporting Services 構成ファイル」](../../reporting-services/report-server/reporting-services-configuration-files.md) および [「電子メール配信用にレポート サーバーを構成する (SSRS 構成マネージャー)」](http://msdn.microsoft.com/en-us/b838f970-d11a-4239-b164-8d11f4581d83)を参照してください。  
  
 配信拡張機能の削除後は、この機能はレポート マネージャーまたは SharePoint サイトで使用できなくなります。 配信拡張機能を削除すると、サブスクリプションが無効になることがあります。 配信拡張機能を削除する前に、このようなサブスクリプションを削除するか、または別の配信拡張機能を使用するように構成する必要があります。  
  
## <a name="see-also"></a>参照  
 [サブスクリプションと配信 (Reporting Services)](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Reporting Services 構成ファイル](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [レポート マネージャー &#40; を構成します。ネイティブ モード &#41;](../../reporting-services/report-server/configure-report-manager-native-mode.md)   
 [Reporting Services レポート サーバー & #40 です。ネイティブ モード &#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [レポート マネージャーと &#40; です。SSRS ネイティブ モードと &#41; です。](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [セキュリティのプロパティ ページ、項目 & #40 です。レポート マネージャー &#41;](http://msdn.microsoft.com/library/351b8503-354f-4b1b-a7ac-f1245d978da0)  
  
  

