---
title: "SQL Server のインスタンスが自動的に開始されるようにする設定 (SQL Server 構成マネージャー) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server の自動開始"
  - "SQL Server, 自動開始"
  - "SQL Server の起動, 自動"
ms.assetid: aa2b6bde-e76d-4fea-a560-54a63745d9b1
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# SQL Server のインスタンスが自動的に開始されるようにする設定 (SQL Server 構成マネージャー)
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で SQL Server 構成マネージャーを使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインスタンスを自動的に開始するように設定する方法について説明します。 セットアップのとき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は通常、自動的に開始するように構成されます。 手動で開始するように構成した場合、この設定をいつでも変更できます。  
  
##  <a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### SQL Server のインスタンスを自動的に起動するように設定するには  
  
1.  **[スタート]** メニューで、 **[すべてのプログラム]**、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]**の順にポイントして、 **[SQL Server 構成マネージャー]**をクリックします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソール プログラムのスナップインであり、スタンドアロン プログラムではないため、新しいバージョンの Windows では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーはアプリケーションとして表示されません。  
    >   
    >  -   **Windows 10**:  
    >          [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを開くには、**スタート画面**で、「SQLServerManager13.msc」([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] の場合) と入力します。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の場合は、13 をより小さい数値に置き換えます。 SQLServerManager13.msc をクリックすると、構成マネージャーが開きます。 スタート画面やタスク バーに構成マネージャーをピン留めするには、SQLServerManager13.msc を右クリックして、**[ファイルの場所を開く]** をクリックします。 エクスプローラーで SQLServerManager13.msc を右クリックし、**[スタート画面にピン留め]** または **[タスク バーにピン留め]** をクリックします。  
    > -   **Windows 8**:  
    >          [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを開くには、**検索**チャームの **[アプリ]** で、「**SQLServerManager\<バージョン>.msc**」(「**SQLServerManager13.msc**」など) と入力し、**Enter** キーを押します。  
  
2.  **[SQL Server 構成マネージャー]**で **[サービス]**を展開し、 **[SQL Server]**をクリックします。  
  
3.  詳細ペインで、自動的に開始するインスタンスの名前を右クリックし、**[プロパティ]** をクリックします。  
  
4.  **[SQL Server \<***インスタンス名***> のプロパティ]** ダイアログ ボックスで、**[開始モード]** を **[自動]** に設定します。  
  
5.  **[OK]**をクリックして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを閉じます。  
  
## 参照  
 [SQL Server のインスタンスの自動開始の回避 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/scm services - prevent automatic startup of an instance.md)   
 [別のコンピューターへの接続 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/connect-to-another-computer-sql-server-configuration-manager.md)   
 [SQL Server ツールでサーバーの状態を表示できるようにする WMI の構成](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  