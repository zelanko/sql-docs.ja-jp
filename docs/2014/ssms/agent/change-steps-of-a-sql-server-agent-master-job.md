---
title: SQL Server エージェントのマスター ジョブのステップの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 8f1a0ee6-49ff-4080-94ca-d661daeff2a6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f23c4817ff1a09c7d25b636049c22410003da002
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221162"
---
# <a name="change-steps-of-a-sql-server-agent-master-job"></a>Change Steps of a SQL Server Agent Master Job
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]で SQL Server エージェントのマスター ジョブのステップに変更を加える方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **以下を使用して SQL Server エージェントのマスター ジョブのステップに変更を加えるには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのマスター ジョブの対象サーバーを、ローカル サーバーとリモート サーバーの両方に設定することはできません。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 **sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか変更できません。 詳細については、「 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-make-changes-to-the-steps-of-a-sql-server-agent-master-job"></a>SQL Server エージェントのマスター ジョブのステップに変更を加えるには  
  
1.  **オブジェクト エクスプローラー** で、ステップを変更するジョブを含むサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]** を展開します。  
  
3.  プラス記号をクリックして **[ジョブ]** フォルダーを展開します。  
  
4.  ステップを変更するジョブを右クリックし、 **[プロパティ]** をクリックします。  
  
5.  *[ジョブのプロパティ - <ジョブ名>]* ダイアログ ボックスで、**[ページの選択]** の **[ステップ]** を選択します。  
  
6.  **[編集]** をクリックし、*[ジョブ ステップのプロパティ - <ジョブ ステップ名>]* ダイアログ ボックスを開きます。 このダイアログ ボックスで使用可能なオプションの詳細については、次を参照してください[ジョブ ステップのプロパティ: 新しいジョブ ステップ&#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)と[ジョブ ステップのプロパティ: 新しいジョブ ステップ&#40;高度なページ&#41;。](job-step-properties-new-job-step-advanced-page.md).  
  
7.  完了したら、 **[OK]** をクリックします。  
  
8.  *[ジョブのプロパティ - <ジョブ名>]* ダイアログ ボックスで、**[OK]** をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-make-changes-to-the-steps-of-a-sql-server-agent-master-job"></a>SQL Server エージェントのマスター ジョブのステップに変更を加えるには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- changes the number of retry attempts for the first step of the Weekly Sales Data Backup job.   
    -- After running this example, the number of retry attempts is 10   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 1,  
        @retry_attempts = 10 ;  
    GO  
    ```  
  
 詳細については、次を参照してください。 [sp_update_jobstep &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)します。  
  
  
