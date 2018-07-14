---
title: 資格情報のウィザード (SSRS ネイティブ モード) の変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0163bff016043e31bf36a689220976b85e4ae097
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244298"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a>資格情報の変更ウィザード (SSRS ネイティブ モード)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャー ツールの資格情報の変更ウィザードを使用して、レポート サーバーがレポート サーバー データベースへの接続に使用するアカウントを再構成することができます。 資格情報を変更すると、構成マネージャーによって、レポート サーバーで使用中のレポート サーバー データベースのデータベース サーバー上のすべての権限とデータベース ログイン情報が更新されます。  
  
 ウィザードを開始するには、次のようにクリックします。**資格情報の変更**[データベース] ページで、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager。 開始する方法については、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager を参照してください[Reporting Services 構成マネージャー&#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)します。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード。  
  
## <a name="options"></a>および  
 **データベース サーバー**  
 名前を指定します、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスが、レポート サーバー データベースを実行します。  
  
 接続するため、[!INCLUDE[ssDE](../../includes/ssde-md.md)]インスタンス、データベース情報を更新したり、サーバーにログオンする権限を持つ資格情報を使用する必要があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager は、現在の Windows 資格情報を使用して、ログインまたはデータベースのアクセス許可がないを指定できますが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース ログインします。  
  
 別の Windows 資格情報を指定することはできません。 別の Windows ユーザー、そのユーザーとしてログインとして接続してから起動する場合、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager。  
  
 **資格情報**  
 レポート サーバーがレポート サーバー データベースへの接続に使用するアカウントを指定します。 有効な値は、レポート サーバー Web サービスのサービス アカウント、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で定義されているデータベース ログイン、[!INCLUDE[ssDE](../../includes/ssde-md.md)]レポート サーバー、または Windows アカウントをホストしているインスタンス。 Windows アカウントを使用している場合は、ローカル アカウントを指定できます (*\<computername >\\< ユーザー名\>*) 場合は、レポート サーバーとデータベースが同じコンピューターまたはドメイン ユーザーにはアカウント (*\<ドメイン >\\< ユーザー名\>*) 同じドメイン内の異なるコンピューター上にある場合。  
  
 レポート サーバーはデータベース ログインを作成し、指定したアカウントにデータベース権限を割り当てます。  
  
 レポート サーバーでは、アカウントの作成は行われません。 配置構成に対して有効な、既に存在するアカウントを指定する必要があります。 特に、データベースがリモート コンピューター上にある環境で、Windows アカウントを使用する場合は、そのコンピューターへのログオン権限のあるアカウントを指定する必要があります。  
  
 コンピューターが異なるか、または信頼されていないドメインにある場合は、使用を検討して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース ログインします。 アカウントの選択の詳細については、次を参照してください。[レポート サーバー データベース接続の構成&#40;SSRS 構成マネージャー&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)します。  
  
 **概要**  
 ウィザードを実行する前に、設定を確認します。  
  
 **進行状況と完了**  
 各タスクの進行状況を監視します。  
  
## <a name="see-also"></a>参照  
 [データベース&#40;SSRS ネイティブ モード&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [データベースの変更ウィザード&#40;SSRS ネイティブ モード&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md)   
 [ネイティブ モード レポート サーバー データベースの作成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services 構成マネージャーの F1 ヘルプ トピック&#40;SSRS ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [レポート サーバー データベース接続の構成&#40;SSRS 構成マネージャー&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
