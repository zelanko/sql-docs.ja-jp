---
title: レポート サーバー コンピューターの名前の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- renaming report servers
ms.assetid: 82fc4ba2-291a-4939-a025-271b8d687c54
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23c96ae889017eab71378b91eeb1a9ea1881fb25
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66103498"
---
# <a name="rename-a-report-server-computer"></a>レポート サーバー コンピューターの名前の変更
  コンピューターの名前を変更すると、同じコンピューター上に存在する Web サーバーおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前が対応して変更されます。 場合によって[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]は、コンピューター名を変更した後に、にアクセスできなくなることがあります。 コンピューター名を変更した後にレポート サーバーを再構成するには、このトピックで説明する手順を使用します。  
  
## <a name="renaming-a-sql-server-database-engine"></a>SQL Server データベース エンジンの名前の変更  
 レポートサーバーデータベースを[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]実行するインスタンスの名前を変更する場合は、次の手順を実行します。  
  
1.  Reporting Services 構成ツールを起動し、名前が変更されたサーバー上のレポート サーバー データベースを使用するレポート サーバーに接続します。  
  
2.  [データベースのセットアップ] ページを開きます。  
  
3.  
  **[サーバー名]** で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前を入力または選択し、 **[接続]** をクリックします。  
  
4.  **[Apply]** をクリックします。  
  
 レポート サーバーがローカルの [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスを使用している場合は、 *(local)* または *(local)\instancename* を使用して、サーバーを指定できます。 
  *(local)* を使用してサーバーを参照する場合は、サーバーの名前を変更しても、接続は引き続き機能します。 リモート サーバーを使用している場合や、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がサーバー名を使用して構成されている場合は、サーバー名を変更するたびに、データベース接続情報を更新する必要があります。  
  
## <a name="renaming-a-report-server-computer"></a>レポート サーバー コンピューターの名前の変更  
 レポート サーバーを実行するコンピューターの名前を変更する場合は、次の手順を実行します。  
  
1.  テキストエディターで**Rsreportserver**を開き、新しいサーバー名を`UrlRoot`反映するように設定を変更します。 
  `UrlRoot` 設定は、レポート サーバーに格納されているアイテムへのアクセスに使用する URL を構成するために、配信拡張機能によって使用されます。 レポート サーバーの URL アドレスを変更するには、`UrlRoot` 設定を更新し、サブスクリプションによってレポートが引き続き適切に配信されるようにする必要があります。  
  
2.  同じファイルで、`ReportServerUrl` が設定されている場合は、新しいサーバー名を反映するようにこの設定を変更します。 この設定はすべてのインストールで使用されているわけではありません。 この設定が空の場合は、何もしません。  
  
    > [!NOTE]  
    >  企業ネットワークで Windows インターネット ネーム サービス (WINS) を使用している場合は、レポート サーバーとレポート マネージャーを以前の名前でしばらく利用できることがあります。 WINS は、サービスを提供する各コンピューターに IP アドレスをマップします。 名前を変更したコンピューターの IP アドレスを WINS が更新した後は、古いコンピューター名を使用してレポート サーバーまたはレポート マネージャーにアクセスすることはできなくなります。  
  
## <a name="see-also"></a>参照  
 [RSReportServer 構成ファイル](rsreportserver-config-configuration-file.md)   
 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Reporting Services レポートサーバー &#40;ネイティブモード&#41;](reporting-services-report-server-native-mode.md)   
 [Start and Stop the Report Server Service](start-and-stop-the-report-server-service.md)   
 [rsconfig ユーティリティ &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md)  
  
  
