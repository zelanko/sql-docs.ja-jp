---
title: レポート マネージャーの URL (SSRS ネイティブ モード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.reportmanagervirtualdirectory.f1
ms.assetid: 45768952-23a6-45a5-b541-e7bf192b4a78
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c2679abba1e452ec65b43ca16cc90fc7cb244436
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66092792"
---
# <a name="report-manager-url-ssrs-native-mode"></a>レポート マネージャー URL (SSRS ネイティブ モード)
  [レポート マネージャー URL] ページを使用すると、レポート マネージャーへのアクセスに使用する URL を構成または変更できます。 既定では、レポート マネージャーの URL は、レポート サーバー Web サービスの URL のプレフィックス、IP アドレス、およびポートを継承します。 これは、レポート マネージャーが同じレポート サーバー サービス内で実行される Web サービスへのフロントエンド アクセスを提供するためです。 サービス アプリケーションを分離し、レポート マネージャーを使用して別のコンピューター上のレポート サーバー Web サービスにアクセスする場合は、RSReportServer.config ファイルを編集して、レポート マネージャーが別のインスタンスを指すようにする必要があります。 リモートのレポート サーバーにレポート マネージャー接続を構成する方法の詳細については、次を参照してください。 [Reporting Services 構成マネージャー&#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)します。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード。  
  
 SharePoint 統合モードで動作するようにレポート サーバーを構成する場合は、レポート マネージャー URL を作成しないでください。 レポート マネージャーは、SharePoint 統合モードで動作するレポート サーバーではサポートされません。 レポート マネージャー用の URL が既に存在する場合は、SharePoint 統合モードで動作するようにレポート サーバーを構成すると、この URL が使用できなくなります。  
  
 このページを開くには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動して、ナビゲーション ウィンドウで **[レポート マネージャー URL]** をクリックします。 Configuration Manager を起動する方法の詳細については、次を参照してください。 [Reporting Services 構成マネージャー&#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)します。  
  
> [!NOTE]  
>  レポート マネージャーが有効でない場合、このページのオプションは設定できません。 レポート マネージャーを有効にする方法の詳細については、次を参照してください。 [Reporting Services 構成マネージャー&#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)します。  
  
## <a name="options"></a>および  
 **仮想ディレクトリ**  
 レポート マネージャーの仮想ディレクトリ名を指定します。 仮想ディレクトリ名は、同じコンピューター上のレポート マネージャー インスタンスごとに 1 つだけ指定できます。  
  
 **Url**  
 現在のレポート マネージャー インスタンスに対して定義されている URL が表示されます。  
  
 **詳細設定**  
 現在のレポート マネージャー インスタンスに対して URL を追加します。  
  
## <a name="see-also"></a>参照  
 [URL の構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [構成ファイル内の Url &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md)   
 [レポート サーバー URL の構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
