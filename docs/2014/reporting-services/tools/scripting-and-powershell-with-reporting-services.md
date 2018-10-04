---
title: Reporting Services を使ったスクリプトの作成と PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 949ceb6b2aff0dd393cfa0c58e91355f20f4c741
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48166522"
---
# <a name="scripting-and-powershell-with-reporting-services"></a>Reporting Services を使ったスクリプトの作成と PowerShell
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] さまざまなスクリプトを rs.exe コマンド ライン ユーティリティ、SharePoint モードのレポート サーバーでは、PowerShell コマンドレットを活用することなどを開発および管理のシナリオをサポートしている、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]両方のネイティブの PowerShell からのオブジェクト モデルとSharePoint モード。  
  
-   管理者は、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] でスクリプトを作成して、レポート サーバーのインストールを配置および管理する方法を自動化できます。 また、レポート サーバー データベースを作成、構成、および更新する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを生成し、実行することもできます。 さらに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] でスクリプトの記録機能と再生機能を使用して、定期的なメンテナンス タスクを自動化することもできます。  
  
-   開発者は、スクリプトを含むカスタム アプリケーションを作成して、 レポート サーバー Web サービスを呼び出すスクリプトを実行できます。 マネージド コードで記述できるほとんどすべての操作は、スクリプトで記述することもできます。  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] サポート[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET スクリプトを RS.exe ユーティリティ、レポート サーバーで実行されるスクリプト ホストによって処理できるスクリプト言語として。  
  
## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a>Reporting Services SharePoint モードの PowerShell コマンドレットとサンプル  
 ![PowerShell 関連コンテンツ](../media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint モードを含む[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]レポート サーバー管理用コマンドレット。  
  
-   [PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) には、以下の例が含まれています。  
  
    -   サービス アプリケーションとプロキシの作成  
  
    -   配信拡張機能の確認と更新  
  
    -   Reporting Services アプリケーション データベースのプロパティの取得と設定 (たとえば、データベースのタイムアウト)  
  
    -   データ拡張機能の一覧  
  
## <a name="reporting-services-object-model-and-powershell-samples"></a>Reporting Services のオブジェクト モデルと Powershell サンプル  
 ![PowerShell 関連コンテンツ](../media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")  
  
 コア オブジェクト モデルを呼び出す PowerShell。ほとんどの場合、SharePoint モードとネイティブ モードにも有効です。たとえば、移行作業、サブスクリプション作業、SQL15 でのサブスクリプション作業の関連するサンプルなどです。  
  
-   [Use PowerShell to Change および Reporting Services サブスクリプション所有者を一覧表示し、サブスクリプションの実行](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)します。  
  
-   [PowerShell を使用したネイティブ モードのレポート サーバーを含む Azure VM の作成](http://msdn.microsoft.com/library/azure/dn449661.aspx)。  
  
-   「 [Access the Reporting Services WMI Provider](access-the-reporting-services-wmi-provider.md)」の「PowerShell を使用した WMI クラスへのアクセス」セクションを参照してください。  
  
-   [PowerShell.scriptin を使用して SSRS を管理する方法](http://curah.microsoft.com/13107/how-to-administer-ssrs-using-powershell)  
  
## <a name="rsexe-scripting-samples"></a>RS.exe スクリプトのサンプル  
  
-   [レポート サーバー間でコンテンツを移行するサンプル Reporting Services rs.exe スクリプト](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)  
  
-   その他のスクリプト、アプリケーション、および拡張機能の例については、「 [SQL Server Reporting Services の製品例](http://go.microsoft.com/fwlink/?LinkId=177889)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [RS.exe ユーティリティ&#40;SSRS&#41;](rs-exe-utility-ssrs.md)   
 [配置タスクおよび管理タスクのスクリプト作成](script-deployment-and-administrative-tasks.md)   
 [rs.exe ユーティリティと Web サービスを使用したスクリプト](script-with-the-rs-exe-utility-and-the-web-service.md)  
  
  
