---
title: SQL Server のサービス開始アカウントを変更する (SQL Server 構成マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server services, startup account changes
- startup accounts [SQL Server]
- changing startup accounts for services
ms.assetid: d721c796-0397-46a7-901b-1a9a3c3fb385
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 105592676413fb43c4cac5b572623096a517b147
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935107"
---
# <a name="change-the-service-startup-account-for-sql-server-sql-server-configuration-manager"></a>SQL Server のサービス開始アカウントの変更 (SQL Server 構成マネージャー)
  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスのスタートアップ オプションの変更や、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で使用されるサービス アカウントの変更を行う方法について説明します。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、または PowerShell を使用します。 適切なサービス アカウントの選択方法の詳細については、「 [Windows サービス アカウントと権限の構成](configure-windows-service-accounts-and-permissions.md)」を参照してください。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssDE](../../includes/ssde-md.md)] および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのサービス開始アカウントを変更する場合、変更を有効にするために [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス ( [!INCLUDE[ssDE](../../includes/ssde-md.md)]) を再起動する必要があります。 サービスを再起動すると、サービスが正常に再起動するまでは、その [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに関連付けられているすべてのデータベースが使用できなくなります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのサービス開始アカウントを変更する必要がある場合は、定期的なメンテナンスのときや、日常の運用を妨げることなくデータベースをオフラインにできるときに実行してください。  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
  
-   クラスター化されたサーバー  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで使用されているサービス アカウントを変更する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クラスターのアクティブなノードから実行する必要があります。  
  
     ドメイン グループを使用した既定以外の構成の Windows Server 2008 で実行している場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで使用されているサービス アカウントを変更する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、リソース グループをオフラインにして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を停止する必要があります。  
  
-   SKU アップグレード ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] から Express 以外の SKU へのアップグレード)  
  
     [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のインストール中に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスは、ネットワーク サービス アカウントを使用するように構成されますが、無効になっています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスに割り当てられたアカウントを変更できますが、このサービスを有効にしたり開始したりすることはできません。 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] から Express 以外に SKU をアップグレードした後、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが自動的に有効になることはありませんが、必要に応じて有効にすることができます。サービスを有効にするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、サービス開始モードを手動または自動に変更します。  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### <a name="to-change-the-sql-server-service-startup-account"></a>SQL Server のサービス開始アカウントを変更するには  
  
1.  **[スタート]** メニューで、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソール プログラムのスナップインであり、スタンドアロン プログラムではないため、新しいバージョンの Windows では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーはアプリケーションとして表示されません。  
    >   
    >  -   **Windows 10**:  
    >          Configuration Manager を開くには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **スタートページ**で「「sqlservermanager12.msc」 (の場合)」と入力 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] します。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の場合は、12 をより小さい数値に置き換えます。 SQLServerManager12.msc をクリックすると、構成マネージャーが開きます。 Configuration Manager をスタートページまたはタスクバーにピン留めするには、「Sqlservermanager12.msc」を右クリックし、[**ファイルの場所を開く**] をクリックします。 Windows エクスプローラーで「Sqlservermanager12.msc」を右クリックし、[**スタート画面にピン留めする**] または [**タスクバーにピン留め**する] をクリックします。  
    > -   **Windows 8**:  
    >          Configuration Manager を開くには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、**検索**チャームで、[**アプリ**] の下に「 **SQLServerManager \<version> ** 」と入力し、 `SQLServerManager12.msc` **enter**キーを押します。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、 **[SQL Server のサービス]** をクリックします。  
  
3.  詳細ペインで、サービス開始アカウントを変更する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス名を右クリックし、 **[プロパティ]** をクリックします。  
  
4.  [ **SQL Server の \<***instancename***> プロパティ**] ダイアログボックスで、[**ログオン**] タブをクリックし、[アカウントの種類] とし**て [ログオン**] を選択します。  
  
5.  新しいサービス開始アカウントを選択したら、 **[OK]** をクリックします。  
  
     メッセージ ボックスに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを再起動するかどうかを確認するメッセージが表示されます。  
  
6.  **[はい]** をクリックして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを閉じます。  
  
## <a name="see-also"></a>参照  
 [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](start-stop-pause-resume-restart-sql-server-services.md)   
 [SQL Server ツールでサーバーの状態を表示できるようにする WMI の構成](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
