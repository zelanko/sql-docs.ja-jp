---
title: レポート サーバー コンピューターの名前の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- renaming report servers
ms.assetid: 82fc4ba2-291a-4939-a025-271b8d687c54
caps.latest.revision: 45
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: be5f32d7859d21409930428711c247b208b97e23
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077041"
---
# <a name="rename-a-report-server-computer"></a>レポート サーバー コンピューターの名前の変更
  コンピューターの名前を変更すると、同じコンピューター上に存在する Web サーバーおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前が対応して変更されます。 場合によっては、コンピューター名を変更した後に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] にアクセスできなくなることがあります。 コンピューター名を変更した後にレポート サーバーを再構成するには、このトピックで説明する手順を使用します。  
  
## <a name="renaming-a-sql-server-database-engine"></a>SQL Server データベース エンジンの名前の変更  
 名前を変更する場合、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]レポート サーバー データベースで実行されるインスタンスは、次の操作します。  
  
1.  Reporting Services 構成ツールを起動し、名前が変更されたサーバー上のレポート サーバー データベースを使用するレポート サーバーに接続します。  
  
2.  [データベースのセットアップ] ページを開きます。  
  
3.  **[サーバー名]** で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前を入力または選択し、 **[接続]** をクリックします。  
  
4.  **[適用]** をクリックします。  
  
 レポート サーバーがローカルの [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスを使用している場合は、 *(local)* または *(local)\instancename* を使用して、サーバーを指定できます。 *(local)* を使用してサーバーを参照する場合は、サーバーの名前を変更しても、接続は引き続き機能します。 リモート サーバーを使用している場合や、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がサーバー名を使用して構成されている場合は、サーバー名を変更するたびに、データベース接続情報を更新する必要があります。  
  
## <a name="renaming-a-report-server-computer"></a>レポート サーバー コンピューターの名前の変更  
 レポート サーバーを実行するコンピューターの名前を変更する場合は、次の手順を実行します。  
  
1.  開いている**RSReportServer.config**をテキスト エディターで変更し、`UrlRoot`新しいサーバー名を反映するように設定します。 `UrlRoot` 設定は、レポート サーバーに格納されているアイテムへのアクセスに使用する URL を構成するために、配信拡張機能によって使用されます。 レポート サーバーの URL アドレスを変更するには、更新する必要があります、`UrlRoot`期待どおりにレポートを配信するサブスクリプションを続行するように設定します。  
  
2.  同じファイルで設定されている場合を変更、`ReportServerUrl`新しいサーバー名を反映するように設定します。 この設定はすべてのインストールで使用されているわけではありません。 この設定が空の場合は、何もしません。  
  
    > [!NOTE]  
    >  企業ネットワークで Windows インターネット ネーム サービス (WINS) を使用している場合は、レポート サーバーとレポート マネージャーを以前の名前でしばらく利用できることがあります。 WINS は、サービスを提供する各コンピューターに IP アドレスをマップします。 名前を変更したコンピューターの IP アドレスを WINS が更新した後は、古いコンピューター名を使用してレポート サーバーまたはレポート マネージャーにアクセスすることはできなくなります。  
  
## <a name="see-also"></a>参照  
 [RSReportServer 構成ファイル](rsreportserver-config-configuration-file.md)   
 [Reporting Services 構成マネージャー&#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Reporting Services レポート サーバー (ネイティブ モード)](reporting-services-report-server-native-mode.md)   
 [起動し、レポート サーバー サービスを停止します](start-and-stop-the-report-server-service.md)   
 [rsconfig ユーティリティ &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md)  
  
  