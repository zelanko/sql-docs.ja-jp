---
title: SQL Server エージェントのマスター ジョブのステップの変更 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1a0ee6-49ff-4080-94ca-d661daeff2a6
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8e6604550fd8d34e6a1beeff7734eb67344d1e5c
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="change-steps-of-a-sql-server-agent-master-job"></a>Change Steps of a SQL Server Agent Master Job
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database マネージ インスタンスと SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql_md.md)]で SQL Server エージェントのマスター ジョブのステップに変更を加える方法について説明します。  
  
**このトピックの内容**  
  
-   **開始する前に。**  
  
    [制限事項と制約](#Restrictions)  
  
    [セキュリティ](#Security)  
  
-   **以下を使用して SQL Server エージェントのマスター ジョブのステップに変更を加えるには:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのマスター ジョブの対象サーバーを、ローカル サーバーとリモート サーバーの両方に設定することはできません。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
**sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか変更できません。 詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-make-changes-to-the-steps-of-a-sql-server-agent-master-job"></a>SQL Server エージェントのマスター ジョブのステップに変更を加えるには  
  
1.  **オブジェクト エクスプローラー** で、ステップを変更するジョブを含むサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]**を展開します。  
  
3.  プラス記号をクリックして **[ジョブ]** フォルダーを展開します。  
  
4.  ステップを変更するジョブを右クリックし、 **[プロパティ]**をクリックします。  
  
5.  *[ジョブのプロパティ - <ジョブ名>]* ダイアログ ボックスで、**[ページの選択]** の **[ステップ]** を選択します。  
  
6.  **[編集]** をクリックし、*[ジョブ ステップのプロパティ - <ジョブ ステップ名>]* ダイアログ ボックスを開きます。 このダイアログ ボックスで利用できるオプションの詳細については、「[[ジョブ ステップのプロパティ] - [新しいジョブ ステップ] ([全般] ページ)](../../ssms/agent/job-step-properties-new-job-step-general-page.md)」と「[[ジョブ ステップのプロパティ]/[新しいジョブ ステップ] ([詳細設定] ページ)](../../ssms/agent/job-step-properties-new-job-step-advanced-page.md)」を参照してください。  
  
7.  完了したら、 **[OK]**をクリックします。  
  
8.  *[ジョブのプロパティ - <ジョブ名>]* ダイアログ ボックスで、**[OK]** をクリックします。  
  
## <a name="TsqlProcedure"></a>Transact-SQL の使用  
  
#### <a name="to-make-changes-to-the-steps-of-a-sql-server-agent-master-job"></a>SQL Server エージェントのマスター ジョブのステップに変更を加えるには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    -- changes the number of retry attempts for the first step
    -- of the Weekly Sales Data Backup job.   
    -- After running this example, the number of retry attempts is 10   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 1,  
        @retry_attempts = 10 ;  
    GO  
    ```  
  
詳細については、「 [sp_update_jobstep (Transact-SQL)](http://msdn.microsoft.com/en-us/e158802c-c347-4a5d-bf75-c03e5ae56e6b)」を参照してください。  
  
