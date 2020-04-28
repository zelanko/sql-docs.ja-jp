---
title: ジョブの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: b35af2b6-6594-40d1-9861-4d5dd906048c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7126b01fcaee1a0ab3f7776cc54e6eb0dbe2774d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "72798310"
---
# <a name="create-a-job"></a>ジョブを作成する
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または SQL Server 管理オブジェクト (SMO) を使用して、[!INCLUDE[tsql](../../includes/tsql-md.md)] で SQL Server エージェント ジョブを作成する方法について説明します。  
  
 オペレーターに送信できるジョブ ステップ、スケジュール、警告、および通知を追加するには、「参照」セクションのトピックをご覧ください。  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **ジョブを作成する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)、  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SQL Server 管理オブジェクト](#SMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
  
-   ジョブを作成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールか **sysadmin** 固定サーバー ロールのメンバーである必要があります。 ジョブの編集は、ジョブの所有者または **sysadmin** ロールのメンバーのみが行うことができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールの詳細については、「 [SQL Server エージェントの固定データベース ロール](sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
-   別のログインにジョブを割り当てた場合に、新しい所有者がそのジョブを正常に実行できる十分な権限を持っていないこともあります。  
  
-   ローカル ジョブはローカル [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによってキャッシュに格納されます。 したがって、ジョブを変更すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは暗黙的にジョブをキャッシュに再登録します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_add_jobserver **が呼び出されるまで** エージェントはジョブをキャッシュに格納しないので、 **sp_add_jobserver** を最後に呼び出す方が効率的です。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
-   ジョブの所有者を変更するには、システム管理者でなければなりません。  
  
-   セキュリティを確保するため、ジョブの所有者または **sysadmin** ロールのメンバーだけがジョブの定義を変更できます。 **sysadmin** 固定サーバー ロールのメンバーのみが別のユーザーにジョブの所有権を割り当てることができ、ジョブの所有者とは無関係にジョブを実行できます。  
  
    > [!NOTE]  
    >  ジョブの所有権を **sysadmin** 固定サーバー ロールのメンバーでないユーザーに変更し、そのジョブがプロキシ アカウントを必要とするジョブ ステップを実行する ( [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの実行など) 場合は、ユーザーがそのプロキシ アカウントにアクセスできることを確認してください。アクセスできない場合、ジョブは失敗します。  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-create-a-sql-server-agent-job"></a>SQL Server エージェントのジョブを作成するには  
  
1.  **オブジェクト エクスプローラー**で、SQL Server エージェント ジョブを作成するサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]** を展開します。  
  
3.  **[ジョブ]** フォルダーを右クリックし、**[新しいジョブ]** を選択します。  
  
4.  **[新しいジョブ]** ダイアログ ボックスの **[全般]** ページで、ジョブの全般的なプロパティを変更します。 このページで利用可能なオプションの詳細については、「[ジョブのプロパティ」および「[新しいジョブ &#40;全般] ページ](../../integration-services/general-page-of-integration-services-designers-options.md)」を参照してください&#41;  
  
5.  **[ステップ]** ページで、ジョブ ステップを編成します。 このページで使用可能なオプションの詳細については、「[ジョブのプロパティ: 新しいジョブ &#40;ステップ」ページ](job-properties-new-job-steps-page.md)を参照してください&#41;  
  
6.  **[スケジュール** ] ページで、ジョブのスケジュールを編成します。 このページで使用可能なオプションの詳細については、「[ジョブのプロパティ: [新しいジョブ &#40;スケジュール] ページ](job-properties-new-job-schedules-page.md)」を参照してください&#41;  
  
7.  **[警告]** ページで、ジョブの警告を編成します。 このページで利用可能なオプションの詳細については、「[ジョブのプロパティ: 新しいジョブ &#40;アラート」ページ](job-properties-new-job-alerts-page.md)を参照してください&#41;  
  
8.  **[通知]** ページで、ジョブの完了時に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行するアクションを設定します。 このページで利用可能なオプションの詳細については、「[ジョブのプロパティ: 新しいジョブ &#40;通知」ページ&#41;](job-properties-new-job-notifications-page.md)を参照してください。  
  
9. **[ターゲット]** ページで、ジョブのターゲット サーバーを管理します。 このページで使用可能なオプションの詳細については、「[ジョブのプロパティ: 新しいジョブ &#40;ターゲットページ&#41;](job-properties-new-job-targets-page.md)」を参照してください。  
  
10. 完了したら、[**OK**] をクリックします。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-create-a-sql-server-agent-job"></a>SQL Server エージェントのジョブを作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```sql
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_job  
        @job_name = N'Weekly Sales Data Backup' ;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
    USE msdb ;  
    GO  
    EXEC sp_attach_schedule  
       @job_name = N'Weekly Sales Data Backup',  
       @schedule_name = N'RunOnce';  
    GO  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Data Backup';  
    GO  
    ```  
  
 詳細については次を参照してください:  
  
-   [sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [sp_attach_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [sp_add_jobserver &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMOProcedure"></a>SQL Server 管理オブジェクトの使用  
 **SQL Server エージェントのジョブを作成するには**  
  
 Visual Basic、Visual C#、PowerShell などのプログラミング言語で `Create` クラスの `Job` メソッドを呼び出します。 コード例については、「 [SQL Server エージェントでの自動管理タスクのスケジュール設定](sql-server-agent.md)」を参照してください。  
  
##  <a name="SSMSProc2"></a>  
