---
title: "SQL Server エージェント サービスの開始、停止、または一時停止 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, starting
- SQL Server Agent, pausing
- SQL Server Agent, stopping
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: af137c019a7f96769b801d01f882e1d98b0da2ea
ms.contentlocale: ja-jp
ms.lasthandoff: 08/18/2017

---
# <a name="start-stop-or-pause-the-sql-server-agent-service"></a>SQL Server エージェント サービスの開始、停止、または一時停止
このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]の SQL Server エージェント サービスを開始、停止、または一時停止する方法について説明します。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスは、オペレーティング システムの起動時に自動的に開始するよう構成したり、ジョブの完了が必要なときに手動で開始できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスを停止または一時停止して、ジョブ、オペレーターへの通知、および警告を中断できます。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   [SQL Server Management Studio を使用して SQL Server エージェント サービスを開始、停止、または一時停止するには](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントがサービスとして実行されている必要があります。 詳細については、「 [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md)」をご覧ください。  
  
-   オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの機能を実行するには、 **の** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]固定サーバー ロールのメンバーであるアカウントの資格情報を使用するように構成する必要があります。 このアカウントには、次の Windows 権限が必要です。  
  
-   サービスとしてログオン (SeServiceLogonRight)  
  
-   プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)  
  
-   スキャン チェックを行わない (SeChangeNotifyPrivilege)  
  
-   プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービス アカウントに必要な Windows 権限の詳細については、「 [SQL Server エージェント サービスのアカウントの選択](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) 」および「 [Windows サービス アカウントと権限の構成](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014)」を参照してください。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-start-stop-or-restart-the-sql-server-agent-service"></a>SQL Server エージェント サービスを開始、停止、または一時停止するには  
  
1.  **オブジェクト エクスプ ローラー**で、プラス記号をクリックして、管理する SQL Server エージェント サービスを展開します。  
  
2.  **[SQL Server エージェント]**を右クリックし、 **[開始]**、 **[停止]**、または **[再起動]**を選択します。  
  
3.  **[ユーザー アカウント制御]** ダイアログ ボックスで、 **[はい]**をクリックします。  
  
4.  アクションを実行するかどうかを確認するメッセージが表示されたら、 **[はい]**をクリックします。  
  
詳細については、以下をご覧ください。  
  
-   [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](http://msdn.microsoft.com/en-us/32660a02-e5a1-411a-9e57-7066ca459df6)  
  
-   [SQL Server エージェントの自動起動 (SQL Server Management Studio)](../../ssms/agent/autostart-sql-server-agent-sql-server-management-studio.md)  
  

