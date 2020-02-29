---
title: Reporting Services を使ったスクリプトの作成と PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c5198b614047d36c53cf41a1d82a44f612c62be6
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177106"
---
# <a name="scripting-and-powershell-with-reporting-services"></a>Reporting Services を使ったスクリプトの作成と PowerShell
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] は、スクリプトによる開発および管理のさまざまなシナリオをサポートしています。スクリプトには、rs.exe コマンド ライン ユーティリティや SharePoint モードのレポート サーバー用の PowerShell コマンドレットを含むもの、またネイティブ モードと SharePoint モードの両方の PowerShell からの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] オブジェクト モデルを利用するものがあります。

-   管理者は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] でスクリプトを作成して、レポート サーバーのインストールを配置および管理する方法を自動化できます。 また、レポート サーバー データベースを作成、構成、および更新する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを生成し、実行することもできます。 さらに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] でスクリプトの記録機能と再生機能を使用して、定期的なメンテナンス タスクを自動化することもできます。

-   開発者は、スクリプトを含むカスタム アプリケーションを作成して、 レポート サーバー Web サービスを呼び出すスクリプトを実行できます。 マネージド コードで記述できるほとんどすべての操作は、スクリプトで記述することもできます。

-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET スクリプトを、RS.exe ユーティリティ (レポート サーバーで実行されるスクリプト ホスト) によって処理されるスクリプト言語としてサポートしています。

## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a>Reporting Services SharePoint モードの PowerShell コマンドレットとサンプル
 ![PowerShell 関連コンテンツ](../media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint モードには、レポート サーバー管理用の [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] コマンドレットが含まれています。

-   [PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) には、以下の例が含まれています。

    -   サービス アプリケーションとプロキシの作成

    -   配信拡張機能の確認と更新

    -   Reporting Services アプリケーション データベースのプロパティの取得と設定 (たとえば、データベースのタイムアウト)

    -   データ拡張機能の一覧

## <a name="reporting-services-object-model-and-powershell-samples"></a>Reporting Services のオブジェクト モデルと Powershell サンプル
 ![PowerShell 関連コンテンツ](../media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")

 コア オブジェクト モデルを呼び出す PowerShell。ほとんどの場合、SharePoint モードとネイティブ モードにも有効です。たとえば、移行作業、サブスクリプション作業、SQL15 でのサブスクリプション作業の関連するサンプルなどです。

-   [PowerShell を使用した Reporting Services サブスクリプション所有者の変更および一覧表示とサブスクリプションの実行](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)。

-   [PowerShell を使用したネイティブ モードのレポート サーバーを含む Azure VM の作成](https://msdn.microsoft.com/library/azure/dn449661.aspx)。

-   「[Reporting Services WMI プロバイダーへのアクセス](access-the-reporting-services-wmi-provider.md)」の「PowerShell を使用した WMI クラスへのアクセス」セクションを参照してください。

-   [PowerShell を使用して SSRS を管理する方法](https://www.sqlshack.com/how-to-administer-sql-server-reporting-services-ssrs-subscriptions-using-powershell/)scriptin

## <a name="rsexe-scripting-samples"></a>RS.exe スクリプトのサンプル

-   [サンプル Reporting Services、レポートサーバー間でコンテンツを移行するための rs .Exe スクリプト](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)です。

-   その他のスクリプト、アプリケーション、および拡張機能の例については、「 [SQL Server Reporting Services の製品例](https://go.microsoft.com/fwlink/?LinkId=177889)」を参照してください。

## <a name="see-also"></a>参照
 Rs[ユーティリティ &#40;&#41;SSRS](rs-exe-utility-ssrs.md)ユーティリティ[と Web サービスを使用して](script-with-the-rs-exe-utility-and-the-web-service.md)[スクリプトの展開および管理タスク](script-deployment-and-administrative-tasks.md)スクリプトを実行する


