---
title: "SQL Server のインスタンスの自動開始の回避 (SQL Server 構成マネージャー) | Microsoft Docs"
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
  - "SQL Server を停止します。"
  - "SQL Server, 自動開始"
  - "自動開始のキャンセル"
  - "停止、SQL Server"
  - "自動開始の回避 [SQL Server]"
ms.assetid: 782663cf-f3d7-4cc6-b621-21e4550f0322
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# SQL Server のインスタンスの自動開始の回避 (SQL Server 構成マネージャー)
  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で SQL Server 構成マネージャーを使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインスタンスが自動的に開始されないようにする方法について説明します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は通常、自動的に開始するように構成されます。 インスタンスの開始モードを手動に設定することによって、その構成を変更できます。  
  
##  <a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### SQL Server のインスタンスの自動開始を回避するには  
  
1.  **[スタート]** メニューで、 **[すべてのプログラム]**、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]**の順にポイントして、 **[SQL Server 構成マネージャー]**をクリックします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソール プログラムのスナップインであり、スタンドアロン プログラムではないため、新しいバージョンの Windows では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーはアプリケーションとして表示されません。  
    >   
    >  -   **Windows 10**:  
    >          [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを開くには、**スタート画面**で、「SQLServerManager13.msc」([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] の場合) と入力します。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の場合は、13 をより小さい数値に置き換えます。 SQLServerManager13.msc をクリックすると、構成マネージャーが開きます。 スタート画面やタスク バーに構成マネージャーをピン留めするには、SQLServerManager13.msc を右クリックして、**[ファイルの場所を開く]** をクリックします。 エクスプローラーでは、SQLServerManager13.msc を右クリックし、**[スタート画面にピン留め]** または **[タスクバーにピン留め]** をクリックします。  
    > -   **Windows 8**:  
    >          [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを開くには、**検索**チャームの **[アプリ]** で、「**SQLServerManager\<version>.msc**」(「**SQLServerManager13.msc**」など) と入力し、**Enter** キーを押します。  
  
2.  [SQL Server 構成マネージャー] で **[サービス]** を展開し、**[SQL Server]** をクリックします。  
  
3.  詳細ペインで、**[MSSQLServer]** を右クリックし、**[プロパティ]** をクリックします。  
  
4.  **[SQL Server \<***instancename***> のプロパティ]** ダイアログ ボックスの **[プロパティ]** ボックスで、**[開始モード]** の値を **[手動]** に設定します。  
  
5.  **[OK]** をクリックして **[SQL Server \<***instancename***> のプロパティ]** ダイアログ ボックスを閉じ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを閉じます。  
  
## 参照  
 [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](../../database-engine/configure-windows/start, stop, pause, resume, restart sql server services.md)  
  
  