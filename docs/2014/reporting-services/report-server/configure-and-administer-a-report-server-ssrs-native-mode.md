---
title: レポート サーバーを構成および管理する (SSRS ネイティブ モード) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Reporting Services, components
- deploying [Reporting Services], component options
- report servers [Reporting Services], component options
- configuration options [Reporting Services]
- administering Reporting Services
- components [Reporting Services], configuring
- configuring servers [Reporting Services]
ms.assetid: cfec012b-56f1-4346-9814-247acf22351c
caps.latest.revision: 50
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: d5a004993ab886151ce9e3f5e3f7b2a2970f60d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077258"
---
# <a name="configure-and-administer-a-report-server-ssrs-native-mode"></a>レポート サーバーを構成および管理する (SSRS ネイティブ モード)
  このトピックでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を構成するための方法について説明します。 また、特定のコンポーネント、機能、サーバー機能の構成方法について説明しているトピックへのリストも記載されています。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]は次の方法で構成できます。  
  
-   Reporting Services 構成マネージャーを使用します。 このセクションの多くのトピックでは、このツールを使用して特定の機能を構成する方法について説明しています。  
  
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して、サーバーのプロパティのカスタマイズ、個人用レポートの有効化、トレース ログの有効化、および、サイト全体に対する既定値の設定を行います。 サイトの設定の詳細については、次を参照してください。 [Reporting Services レポート サーバー&#40;ネイティブ モード&#41;](reporting-services-report-server-native-mode.md) Management Studio のです。 サーバーのプロパティをプログラムから設定するスクリプトを作成して実行できます。 詳細については、次を参照してください。[スクリプトを展開および管理タスク](../tools/script-deployment-and-administrative-tasks.md)と[レポート サーバーのシステム プロパティ](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)です。  
  
-   レポート マネージャー使用して、レポート サーバーにアクセスするための権限を与えます。 権限は、各ユーザーまたはグループ アカウントに対して定義したロールの割り当てを通じて付与されます。 詳細については、「[ロールと権限 (Reporting Services)](../security/roles-and-permissions-reporting-services.md)」を参照してください。  
  
-   必要に応じて、構成ファイルを修正し、アプリケーションの設定を変更します。 各ファイルおよびそれらの変更に関するガイドラインの詳細については、次を参照してください。 [Reporting Services の構成ファイル](reporting-services-configuration-files.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [レポート サーバー URL の構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 レポート サーバーおよびレポート マネージャーへのアクセスに使用する URL の定義方法について説明します。  
  
 [レポート サーバー サービス アカウントを構成する&#40;SSRS 構成マネージャー&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 サービスのアカウントとパスワードを変更する方法の推奨事項と手順について説明します。  
  
 [レポート サーバー データベースの作成&#40;SSRS 構成マネージャー&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
 サーバーのメタデータやオブジェクトの格納に必要なレポート サーバー データベースを作成する方法について説明します。  
  
 [レポート サーバー データベース接続を構成する&#40;SSRS 構成マネージャー&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 レポート サーバーからレポート サーバー データベースへの接続に使用する接続文字列を変更する方法について説明します。  
  
 [レポート サーバー電子メール配信用に構成&#40;SSRS 構成マネージャー&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 電子メールによるレポートの配信をサポートするようにレポート サーバーを構成する方法について説明します。  
  
 [自動実行アカウントを構成する&#40;SSRS 構成マネージャー&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 自動実行モードでレポートを処理するようにユーザー アカウントを構成する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [レポート ビルダーへのアクセスを構成します。](configure-report-builder-access.md)   
 [Reporting Services 構成ファイル](reporting-services-configuration-files.md)   
 [Reporting Services 構成マネージャー&#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Reporting Services のセキュリティと保護](../security/reporting-services-security-and-protection.md)   
 [Reporting Services レポート サーバー &#40;ネイティブ モード&#41;](reporting-services-report-server-native-mode.md)  
  
  