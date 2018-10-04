---
title: SharePoint ファーム (アップグレード アドバイザー) に必要なドメイン アカウント |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 90cd6d3e-a271-4cb8-81f2-fc555b2d3cab
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 983e01046fd90fbaf8d9ff680492f1b385435f61
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222272"
---
# <a name="domain-accounts-required-for-sharepoint-farm-upgrade-advisor"></a>SharePoint ファームに必要なドメイン アカウント (アップグレード アドバイザー)
  ファーム環境向けに構成されている SharePoint 製品では、ドメイン アカウントを使用する必要があります。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRS](../../includes/ssrs.md)]  
  
### <a name="description"></a>説明  
 ファーム環境向けに構成されている SharePoint 製品では、サービスとデータベース接続にドメイン アカウントを使用する必要があります。 これには、Reporting Services サービス アカウントに指定したアカウントも含まれます。  
  
 SharePoint 2010 のサーバーの全体管理ページを使用すると、1 か所で、Reporting Services にドメイン ユーザー アカウントを使用していない場合の問題を確認できます。 Reporting Services 統合の構成を試みると、次のようなエラー メッセージが表示されます。  
  
 "レポート サーバーの実行に使用されているビルトイン NT AUTHORITY\NETWORK SERVICE アカウントは、SharePoint ファームのインストールでサポートされていません。 再構成してください、レポート サーバーをドメイン アカウントで実行します。"  
  
## <a name="corrective-action"></a>修正措置  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]以前のバージョンでは、Reporting Services 構成マネージャーを使用して、レポート サーバー サービス アカウントとして割り当てられているアカウントを変更するとします。  
  
#### <a name="to-change-the-service-account-from-configuration-manager"></a>構成マネージャーでサービス アカウントを変更するには  
  
1.  **開始**メニューの [**すべてのプログラム**、] をクリックし、 **Microsoft SQL Server 2008 R2**します。  
  
2.  選択**構成ツール**、 をクリックし、 **Reporting Services 構成マネージャー**します。  
  
3.  Configuration Manager での選択、**サービス アカウント**タブ。  
  
4.  選択**別のアカウントを使用して、** ドメイン アカウントの資格情報を入力します。  
  
5.  **[適用]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [レポート サーバー サービス アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
  
  
