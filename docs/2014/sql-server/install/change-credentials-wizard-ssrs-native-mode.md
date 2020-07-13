---
title: 資格情報の変更ウィザード (SSRS ネイティブモード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 04d715bee7fdd8d61796040fa04b3fb68db1d15a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85045359"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a>資格情報の変更ウィザード (SSRS ネイティブ モード)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャー ツールの資格情報の変更ウィザードを使用して、レポート サーバーがレポート サーバー データベースへの接続に使用するアカウントを再構成することができます。 資格情報を変更すると、構成マネージャーによって、レポート サーバーで使用中のレポート サーバー データベースのデータベース サーバー上のすべての権限とデータベース ログイン情報が更新されます。  
  
 このウィザードを起動するには、 **構成マネージャーの [データベース] ページにある** [資格情報の変更] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をクリックします。 Configuration Manager を開始する方法については [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 、「 [Reporting Services Configuration Manager &#40;ネイティブモード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。  
  
## <a name="options"></a>オプション  
 **データベースサーバー**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] レポートサーバーデータベースを実行するインスタンスの名前を指定します。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスに接続するには、サーバーにログオンしてデータベース情報を更新するための権限がある資格情報を使用する必要があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーでは、現在の Windows 資格情報が使用されますが、ログイン権限またはデータベース権限がない場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ログインを指定できます。  
  
 別の Windows 資格情報を指定することはできません。 別の Windows ユーザーとして接続する場合は、ユーザーとしてログインし、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを起動します。  
  
 **資格情報**  
 レポート サーバーがレポート サーバー データベースへの接続に使用するアカウントを指定します。 指定できる値は、レポート サーバー Web サービスのサービス アカウント、レポート サーバーのホストに使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで定義されている [!INCLUDE[ssDE](../../includes/ssde-md.md)] データベース ログイン、または Windows アカウントです。 Windows アカウントを使用している場合は、レポートサーバーとデータベースが同じコンピューター上に存在する場合はローカルアカウント (* \<computername> \\<ユーザー名 \> *) を指定し、同じドメイン内の異なるコンピューターに存在する場合はドメインユーザーアカウント (* \<domain> \\<username \> *) を指定できます。  
  
 レポート サーバーはデータベース ログインを作成し、指定したアカウントにデータベース権限を割り当てます。  
  
 レポート サーバーでは、アカウントの作成は行われません。 配置構成に対して有効な、既に存在するアカウントを指定する必要があります。 特に、データベースがリモート コンピューター上にある環境で、Windows アカウントを使用する場合は、そのコンピューターへのログオン権限のあるアカウントを指定する必要があります。  
  
 コンピューターが別のドメインまたは信頼されていないドメイン内に存在する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ログインを使用することをお勧めします。 アカウントの選択の詳細については、「 [SSRS Configuration Manager&#41;&#40;レポートサーバーデータベース接続を構成](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)する」を参照してください。  
  
 **まとめ**  
 ウィザードを実行する前に、設定を確認します。  
  
 **[続行して完了する]**  
 各タスクの進行状況を監視します。  
  
## <a name="see-also"></a>参照  
 [データベース &#40;SSRS ネイティブモード&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [データベースの変更ウィザード &#40;SSRS ネイティブモード&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md)   
 [SSRS Configuration Manager &#40;ネイティブモードのレポートサーバーデータベースを作成&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services Configuration Manager F1 ヘルプトピック &#40;SSRS ネイティブモード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [レポート サーバー データベース接続の構成 &#40;SSRS構成マネージャー&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
