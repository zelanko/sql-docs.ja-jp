---
title: SQL Server エージェント サービスの開始、停止、または一時停止 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- SQL Server Agent, pausing
- SQL Server Agent, stopping
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
author: stevestein
ms.author: sstein
ms.openlocfilehash: f11ef36d72a029a906da29467fd9e4fe3a0cf8ee
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067537"
---
# <a name="start-stop-or-pause-the-sql-server-agent-service"></a>Start, Stop, or Pause the SQL Server Agent Service
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の SQL Server エージェント サービスを開始、停止、または一時停止する方法について説明します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスは、オペレーティング システムの起動時に自動的に開始するよう構成したり、ジョブの完了が必要なときに手動で開始できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを停止または一時停止して、ジョブ、オペレーターへの通知、および警告を中断できます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   [SQL Server Management Studio を使用して SQL Server エージェント サービスを開始、停止、または一時停止するには](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントは、管理タスクを自動化するためにサービスとして実行されている必要があります。 詳細については、「 [Configure SQL Server Agent](configure-sql-server-agent.md)」をご覧ください。  
  
-   オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの機能を実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定サーバー ロールの **sysadmin** のメンバーであるアカウントの資格情報を使用するように構成する必要があります。 このアカウントには、次の Windows 権限が必要です。  
  
-   サービスとしてログオン (SeServiceLogonRight)  
  
-   プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)  
  
-   スキャン チェックを行わない (SeChangeNotifyPrivilege)  
  
-   プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)  
  
 エージェントサービスアカウントに必要な Windows アクセス許可の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server エージェントサービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」および「 [Windows サービスアカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-start-stop-or-restart-the-sql-server-agent-service"></a>SQL Server エージェント サービスを開始、停止、または一時停止するには  
  
1.  **オブジェクト エクスプ ローラー**で、プラス記号をクリックして、管理する SQL Server エージェント サービスを展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、 **[開始]**、 **[停止]**、または **[再起動]** を選択します。  
  
3.  **[ユーザー アカウント制御]** ダイアログ ボックスで、 **[はい]** をクリックします。  
  
4.  アクションを実行するかどうかを確認するメッセージが表示されたら、 **[はい]** をクリックします。  
  
 詳細については、次を参照してください。  
  
-   [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
-   [SQL Server エージェントの自動起動 (SQL Server Management Studio)](autostart-sql-server-agent-sql-server-management-studio.md)  
  
  
