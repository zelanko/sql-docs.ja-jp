---
title: レポートマネージャー URL (SSRS ネイティブモード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.reportmanagervirtualdirectory.f1
ms.assetid: 45768952-23a6-45a5-b541-e7bf192b4a78
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 53eaf828dd3fe6f5fa4056bda9dbc428dfa5d385
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054643"
---
# <a name="report-manager-url-ssrs-native-mode"></a>レポート マネージャー URL (SSRS ネイティブ モード)
  [レポート マネージャー URL] ページを使用すると、レポート マネージャーへのアクセスに使用する URL を構成または変更できます。 既定では、レポート マネージャーの URL は、レポート サーバー Web サービスの URL のプレフィックス、IP アドレス、およびポートを継承します。 これは、レポート マネージャーが同じレポート サーバー サービス内で実行される Web サービスへのフロントエンド アクセスを提供するためです。 サービス アプリケーションを分離し、レポート マネージャーを使用して別のコンピューター上のレポート サーバー Web サービスにアクセスする場合は、RSReportServer.config ファイルを編集して、レポート マネージャーが別のインスタンスを指すようにする必要があります。 リモートレポートサーバーへのレポートマネージャー接続の構成の詳細については、「 [Reporting Services Configuration Manager &#40;ネイティブモード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。  
  
 SharePoint 統合モードで動作するようにレポート サーバーを構成する場合は、レポート マネージャー URL を作成しないでください。 レポート マネージャーは、SharePoint 統合モードで動作するレポート サーバーではサポートされません。 レポート マネージャー用の URL が既に存在する場合は、SharePoint 統合モードで動作するようにレポート サーバーを構成すると、この URL が使用できなくなります。  
  
 このページを開くには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動して、ナビゲーション ウィンドウで **[レポート マネージャー URL]** をクリックします。 Configuration Manager を開始する方法の詳細については、「[ネイティブモード&#41;&#40;Reporting Services Configuration Manager ](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。  
  
> [!NOTE]  
>  レポート マネージャーが有効でない場合、このページのオプションは設定できません。 レポートマネージャーの有効化の詳細については、「[ネイティブモード&#41;&#40;Reporting Services Configuration Manager ](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **仮想ディレクトリ**  
 レポート マネージャーの仮想ディレクトリ名を指定します。 仮想ディレクトリ名は、同じコンピューター上のレポート マネージャー インスタンスごとに 1 つだけ指定できます。  
  
 **URL**  
 現在のレポート マネージャー インスタンスに対して定義されている URL が表示されます。  
  
 **詳細設定**  
 現在のレポート マネージャー インスタンスに対して URL を追加します。  
  
## <a name="see-also"></a>参照  
 [SSRS Configuration Manager の URL &#40;構成&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [構成ファイルの Url &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md)   
 [レポート サーバー URL の構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
