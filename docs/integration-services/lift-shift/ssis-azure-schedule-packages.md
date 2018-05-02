---
title: Azure で SSIS パッケージの実行をスケジュールする | Microsoft Docs
ms.date: 04/17/2018
ms.topic: article
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c946055e7579478d65de31f737b1c265b2a38eba
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="schedule-the-execution-of-an-ssis-package-on-azure"></a>Azure で SSIS パッケージの実行をスケジュールする
次のスケジュール設定のオプションのいずれかを選択して、Azure SQL Database サーバー上の SSISDB カタログ データベースに格納されているパッケージの実行をスケジュール設定することができます。
-   [SQL Server エージェント](#agent)
-   [SQL Database エラスティック ジョブ](#elastic)
-   [Azure Data Factory での SSIS パッケージ アクティビティの実行](#activities)
-   [Azure Data Factory SQL Server ストアド プロシージャ アクティビティ](#activities)

## <a name="agent"></a> SQL Server エージェントを使用してパッケージのスケジュールを設定する

### <a name="prerequisite---create-a-linked-server"></a>前提条件 - リンク サーバーを作成する

オンプレミスの SQL Server エージェントを使用して、Azure SQL Database サーバーに格納されているパッケージの実行をスケジュール設定するには、事前に SQL Database サーバーをリンク サーバーとしてオンプレミス SQL Server に追加する必要があります。

1.  **リンク サーバーを設定する**

    ```sql
    -- Add the SSISDB database on your Azure SQL Database as a linked server to your SQL Server on premises
    EXEC sp_addlinkedserver
        @server='myLinkedServer', -- Name your linked server
        @srvproduct='',     
        @provider='sqlncli', -- Use SQL Server native client
        @datasrc='<server_name>.database.windows.net', -- Add your Azure SQL Database server endpoint
        @location=‘’,
        @provstr=‘’,
        @catalog='SSISDB'  -- Add SSISDB as the initial catalog
    ```

2.  **リンク サーバーの資格情報を設定する**

    ```sql
    -- Add your Azure SQL DB server admin credentials
    EXEC sp_addlinkedsrvlogin
        @rmtsrvname = 'myLinkedServer’,
        @useself = 'false’,
        @rmtuser = 'myUsername', -- Add your server admin username
        @rmtpassword = 'myPassword' -- Add your server admin password
    ```

3.  **リンク サーバーのオプションを設定する**

    ```sql
    EXEC sp_serveroption 'myLinkedServer', 'rpc out', true;
    ```

詳細については、「[リンク サーバーの作成](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md)」と「[リンク サーバー](../../relational-databases/linked-servers/linked-servers-database-engine.md)」を参照してください。

### <a name="create-a-sql-server-agent-job"></a>SQL Server エージェント ジョブを作成する

オンプレミスの SQL Server エージェントを使用してパッケージのスケジュールを設定するには、SSIS カタログ ストアド プロシージャ `[catalog].[create_execution]` と `[catalog].[start_execution]` を順に呼び出すジョブ ステップでジョブを作成します。 詳細については、「[パッケージに対する SQL Server エージェント ジョブ](../packages/sql-server-agent-jobs-for-packages.md)」を参照してください。

1.  SQL Server Management Studio では、ジョブを作成するオンプレミスの SQL Server データベースに接続します。

2.  **SQL Server エージェント** ノードを右クリックし、**[新規]**、**[ジョブ]** の順に選択し、**[新しいジョブ]** ダイアログ ボックスを開きます。

3.  **[新しいジョブ]** ダイアログ ボックスで、**[手順]** ページを選択し、**[新規]** を選択して、**[新しいジョブ ステップ]** ダイアログ ボックスを開きます。

4.  **[新しいジョブ ステップ]** ダイアログ ボックスで、`SSISDB` を**データベース**として選択します。

5.  **[コマンド]** フィールドで、次の例に示されたスクリプトのような Transact-SQL スクリプトを入力します。

    ```sql
    -- T-SQL script to create and start SSIS package execution using SSISDB stored procedures
    DECLARE @return_value int, @exe_id bigint 

    EXEC @return_value = [YourLinkedServer].[SSISDB].[catalog].[create_execution] 
        @folder_name=N'folderName', @project_name=N'projectName', 
        @package_name=N'packageName', @use32bitruntime=0, @runincluster=1, @useanyworker=1,
        @execution_id=@exe_id OUTPUT 

    EXEC [YourLinkedServer].[SSISDB].[catalog].[set_execution_parameter_value] @exe_id,
        @object_type=50, @parameter_name=N'SYNCHRONIZED', @parameter_value=1

    EXEC [YourLinkedServer].[SSISDB].[catalog].[start_execution] @execution_id=@exe_id
    ```

6.  ジョブの構成とスケジュール設定を完了します。

## <a name="elastic"></a> SQL Database エラスティック ジョブを使用してパッケージをスケジュールする

SQL Database のエラスティック ジョブに関する詳細については、「[スケールアウトされたクラウド データベースの管理](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-overview)」を参照してください。

### <a name="prerequisites"></a>Prerequisites

エラスティック ジョブを使用して、Azure SQL Database サーバー上の SSISDB カタログ データベースに格納されている SSIS パッケージをスケジュール設定するには、事前に次の作業を行う必要があります。

1.  Elastic Database ジョブ コンポーネントをインストールして構成します。 詳細については、「[Elastic Database ジョブのインストールの概要](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-service-installation)」を参照してください。

2. ジョブで SSIS カタログ データベースにコマンドを送信するために使用できるデータベース スコープの資格情報を作成します。 詳細については、「[CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)」 (データベース スコープの資格情報を作成する (Transact-SQL)) を参照してください。

### <a name="create-an-elastic-job"></a>エラスティック ジョブの作成

次の例に示されているスクリプトと同じような Transact-SQL スクリプトを使用して、ジョブを作成します。

```sql
-- Create Elastic Jobs target group 
EXEC jobs.sp_add_target_group 'TargetGroup' 

-- Add Elastic Jobs target group member 
EXEC jobs.sp_add_target_group_member @target_group_name='TargetGroup', 
    @target_type='SqlDatabase', @server_name='YourSQLDBServer.database.windows.net',
    @database_name='SSISDB' 

-- Add a job to schedule SSIS package execution
EXEC jobs.sp_add_job @job_name='ExecutePackageJob', @description='Description', 
    @schedule_interval_type='Minutes', @schedule_interval_count=60

-- Add a job step to create/start SSIS package execution using SSISDB catalog stored procedures
EXEC jobs.sp_add_jobstep @job_name='ExecutePackageJob', 
    @command=N'DECLARE @exe_id bigint 
        EXEC [SSISDB].[catalog].[create_execution]
            @folder_name=N''folderName'', @project_name=N''projectName'',
            @package_name=N''packageName'', @use32bitruntime=0,
            @runinscaleout=1, @useanyworker=1, 
            @execution_id=@exe_id OUTPUT         
        EXEC [SSISDB].[catalog].[start_execution] @exe_id, @retry_count=0', 
    @credential_name='YourDBScopedCredentials', 
    @target_group_name='TargetGroup' 

-- Enable the job schedule 
EXEC jobs.sp_update_job @job_name='ExecutePackageJob', @enabled=1, 
    @schedule_interval_type='Minutes', @schedule_interval_count=60 
```

## <a name="activities"></a> Azure Data Factory を使用したパッケージのスケジュール

Azure Data Factory アクティビティを使用して、SSIS パッケージをスケジュールする方法の詳細については、次の記事を参照してください。

-   Data Factory バージョン 2 の場合: [Azure Data Factory での SSIS アクティビティを使用した SSIS パッケージの実行](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity)

-   Data Factory バージョン 2 の場合: [Azure Data Factory でのストアド プロシージャ アクティビティを使用した SSIS パッケージの実行](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-stored-procedure-activity)

-   Data Factory バージョン 1 の場合: [Azure Data Factory でのストアド プロシージャ アクティビティを使用した SSIS パッケージの実行](https://docs.microsoft.com/azure/data-factory/v1/how-to-invoke-ssis-package-stored-procedure-activity)

## <a name="next-steps"></a>次の手順
SQL Server エージェントの詳細については、「[パッケージに対する SQL Server エージェント ジョブ](../packages/sql-server-agent-jobs-for-packages.md)」を参照してください。

SQL Database のエラスティック ジョブに関する詳細については、「[スケールアウトされたクラウド データベースの管理](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-overview)」を参照してください。
