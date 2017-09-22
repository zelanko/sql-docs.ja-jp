---
title: "作成し、Linux での SQL Server のジョブを実行 |Microsoft ドキュメント"
description: "このチュートリアルでは、Linux 上の SQL Server エージェント ジョブを実行する方法を示します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1d93d95e-9c89-4274-9b3f-fa2608ec2792
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 8d05ec1ae3be89b7a087938c44b356ccc9dbca43
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="create-and-run-sql-server-agent-jobs-on-linux"></a>作成し、Linux 上の SQL Server エージェント ジョブの実行

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

SQL Server ジョブを使用して、定期的に、SQL Server データベースで同じ一連のコマンドを実行できます。 このトピックでは、TRANSACT-SQL および SQL Server Management Studio (SSMS) の両方を使用して Linux に SQL Server エージェント ジョブを作成する方法の例を示します。

このリリースの SQL Server エージェントで既知の問題を参照してください、 [Release Notes](sql-server-linux-release-notes.md)です。

## <a name="prerequisites"></a>前提条件 
作成し、ジョブを実行するのには、まず、SQL Server エージェント サービスをインストールする必要があります。 インストール手順については、次を参照してください。、 [SQL Server エージェントのインストールに関するトピック](sql-server-linux-setup-sql-agent.md)です。

## <a name="create-a-job-with-transact-sql"></a>Transact SQL を使用したジョブを作成します。

次の手順では、TRANSACT-SQL コマンドを Linux 上の SQL Server エージェント ジョブを作成する方法の例を提供します。 この例ではこれらのジョブは、サンプル データベースに、毎日バックアップを実行`SampleDB`です。 


> [!TIP]
> 任意の T-SQL でクライアントを使用して、これらのコマンドを実行することができます。 たとえば、Linux で行うこともできます[sqlcmd](sql-server-linux-setup-tools.md)または[Visual Studio Code](sql-server-linux-develop-use-vscode.md)です。 リモートの Windows Server からもクエリを実行して SQL Server Management Studio (SSMS) または、次のセクションで説明されているジョブの管理用 UI インターフェイスを使用できます。

1. **ジョブを作成**です。 次の例で[sp_add_job](/sql-docs/docs/relational-databases/system-stored-procedures/sp-add-job-transact-sql)という名前のジョブを作成する`Daily AdventureWorks Backup`です。

    ```tsql
     -- Adds a new job executed by the SQLServerAgent service 
     -- called 'Daily SampleDB Backup'  
     CREATE DATABASE SampleDB
     USE msdb ;  
     GO  
     EXEC dbo.sp_add_job  
         @job_name = N'Daily SampleDB Backup' ;  
     GO

    ```

2. **1 つまたは複数のジョブ ステップを追加**です。 次の TRANSACT-SQL スクリプトを使用して[sp_add_jobstep](/sql-docs/docs/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)のバックアップを作成するジョブ ステップを作成、`AdventureWlorks2014`データベース。

    ```tsql
    -- Adds a step (operation) to the job  
    EXEC sp_add_jobstep  
      @job_name = N'Daily SampleDB Backup',  
      @step_name = N'Backup database',  
      @subsystem = N'TSQL',  
      @command = N'BACKUP DATABASE SampleDB TO DISK = \
      N''/var/opt/mssql/data/SampleDB.bak'' WITH NOFORMAT, NOINIT, \
              NAME = ''SampleDB-full'', SKIP, NOREWIND, NOUNLOAD, STATS = 10',   
      @retry_attempts = 5,  
      @retry_interval = 5 ;  
    GO
    ```

3. **ジョブ スケジュールを作成する**です。 この例では[sp_add_schedule](/sql-docs/docs/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql)ジョブの毎日のスケジュールを作成します。

    ```tsql
    -- Creates a schedule called 'Daily'  
    EXEC dbo.sp_add_schedule  
     @schedule_name = N'Daily SampleDB',  
     @freq_type = 4,  
     @freq_interval = 1,
     @active_start_time = 233000 ;  
   USE msdb ;  
   GO
    ```

4. **ジョブのスケジュールをジョブにアタッチ**です。 使用して[sp_attach_schedule](/sql-docs/docs/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)ジョブにジョブ スケジュールをアタッチします。

    ```tsql
    -- Sets the 'Daily' schedule to the 'Daily AdventureWorks Backup' Job  
    EXEC sp_attach_schedule  
     @job_name = N'Daily SampleDB Backup',  
     @schedule_name = N'Daily SampleDB';  
    GO
    ```

5. **対象サーバーにジョブを割り当てます**です。 ターゲット サーバーにジョブを割り当てる[sp_add_jobserver](/sql-docs/docs/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)です。 この例では、ローカル サーバーは、対象です。

    ```tsql
    EXEC dbo.sp_add_jobserver  
     @job_name = N'Daily SampleDB Backup',  
     @server_name = N'(LOCAL)';  
    GO
    ```
6. **ジョブを開始**です。 

    ```tsql
    EXEC dbo.sp_start_job N' Daily SampleDB Backup' ;
    GO
    ```
## <a name="create-a-job-with-ssms"></a>SSMS でジョブを作成します。

作成および Windows 上でのリモート SQL Server Management Studio (SSMS) を使用してジョブを管理することもできます。

1. **Windows で SSMS を起動し、Linux の SQL Server インスタンスに接続します。** 詳細については、次を参照してください。 [SSMS での Linux 上の SQL Server の管理](sql-server-linux-develop-use-ssms.md)です。

1. **SampleDB という名前の新しいデータベースを作成**です。

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-0.png" alt="Create a SampleDB database" style="width: 550px;"/>

2. **SQL エージェントがインストールされ、正しく構成されていることを確認します。** オブジェクト エクスプ ローラーで SQL Server エージェントの横にあるプラス記号を探します。 SQL Server エージェントがインストールされていない場合は、次を参照してください。 [Linux 上の SQL Server エージェントのインストール](sql-server-linux-setup-sql-agent.md)です。

    ![SQL Server エージェントがインストールされていることを確認します。](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-1.png)


3. **新しいジョブを作成します。**

    ![新しいジョブを作成します。](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-2.png)


4. **ジョブに名前を付けて、ジョブ ステップを作成します。**

    ![ジョブ ステップを作成します。](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-3.png)


5. **どのようなサブシステムを使用して、ジョブ ステップで行う必要がありますを指定します。**

    ![ジョブのサブシステム](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-4.png)

    ![ジョブ ステップの操作](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-5.png)

6. **新しいジョブ スケジュールを作成します。**

    ![ジョブ スケジュール](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-6.png)
  
    ![ジョブ スケジュール](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-8.png)

7. **ジョブを開始します。**

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-9.png" alt="Start the SQL Server Agent job" style="width: 550px;"/>

## <a name="next-steps"></a>次の手順

作成して、SQL Server エージェント ジョブの管理に関する詳細については、次を参照してください。 [SQL Server エージェント](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent)です。

