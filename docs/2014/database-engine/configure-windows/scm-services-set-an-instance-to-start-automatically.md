---
title: SQL Server のインスタンスを自動的に開始するように設定する (SQL Server 構成マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, automatic startup
- starting SQL Server, automatically
ms.assetid: aa2b6bde-e76d-4fea-a560-54a63745d9b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5c5bb930015d3b566e68a2815aea5074819803bf
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935023"
---
# <a name="set-an-instance-of-sql-server-to-start-automatically-sql-server-configuration-manager"></a>SQL Server のインスタンスが自動的に開始されるようにする設定 (SQL Server 構成マネージャー)
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で SQL Server 構成マネージャーを使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインスタンスを自動的に開始するように設定する方法について説明します。 セットアップのとき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は通常、自動的に開始するように構成されます。 手動で開始するように構成した場合、この設定をいつでも変更できます。  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### <a name="to-set-an-instance-of-sql-server-to-start-automatically"></a>SQL Server のインスタンスを自動的に起動するように設定するには  
  
1.  **[スタート]** メニューで、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソール プログラムのスナップインであり、スタンドアロン プログラムではないため、新しいバージョンの Windows では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーはアプリケーションとして表示されません。  
    >   
    >  -   **Windows 10**:  
    >          Configuration Manager を開くには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **スタートページ**で「「sqlservermanager12.msc」 (の場合)」と入力 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] します。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の場合は、12 をより小さい数値に置き換えます。 SQLServerManager12.msc をクリックすると、構成マネージャーが開きます。 Configuration Manager をスタートページまたはタスクバーにピン留めするには、「Sqlservermanager12.msc」を右クリックし、[**ファイルの場所を開く**] をクリックします。 Windows エクスプローラーで「Sqlservermanager12.msc」を右クリックし、[**スタート画面にピン留めする**] または [**タスクバーにピン留め**する] をクリックします。  
    > -   **Windows 8**:  
    >          Configuration Manager を開くには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、**検索**チャームで、[**アプリ**] の下に「 **SQLServerManager \<version> ** 」と入力し、 `SQLServerManager12.msc` **enter**キーを押します。  
  
2.  **[SQL Server 構成マネージャー]** で **[サービス]** を展開し、 **[SQL Server]** をクリックします。  
  
3.  詳細ペインで、自動的に開始するインスタンスの名前を右クリックし、 **[プロパティ]** をクリックします。  
  
4.  [ **SQL Server の \<***instancename***> プロパティ**] ダイアログボックスで、[**開始モード**] を [**自動**] に設定します。  
  
5.  **[OK]** をクリックして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを閉じます。  
  
## <a name="see-also"></a>参照  
 [SQL Server のインスタンスの自動開始の回避 &#40;SQL Server 構成マネージャー&#41;](scm-services-prevent-automatic-startup-of-an-instance.md)   
 [別のコンピューターへの接続 &#40;SQL Server 構成マネージャー&#41;](scm-services-connect-to-another-computer.md)   
 [SQL Server ツールでサーバーの状態を表示できるようにする WMI の構成](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
