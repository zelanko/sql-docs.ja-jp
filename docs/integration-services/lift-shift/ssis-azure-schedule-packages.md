---
title: "Azure で SSIS パッケージの実行をスケジュールする | Microsoft Docs"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 80fac355ad3ecc1486257651999be9d3f6ad30e6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="schedule-the-execution-of-an-ssis-package-on-azure"></a>Azure で SSIS パッケージの実行をスケジュールする
次のスケジュール設定のオプションのいずれかを選択して、Azure SQL Database サーバー上の SSISDB カタログ データベースに格納されているパッケージの実行をスケジュール設定することができます。
-   [SQL Server エージェント](#agent)
-   [SQL Database エラスティック ジョブ](#elastic)
-   [Azure Data Factory SQL Server ストアド プロシージャ アクティビティ](#sproc)

## <a name="agent"></a> SQL Server エージェントを使用してパッケージのスケジュールを設定する

### <a name="prerequisite"></a>前提条件

オンプレミスの SQL Server エージェントを使用して、Azure SQL Database サーバーに格納されているパッケージの実行をスケジュール設定するには、事前に SQL Database サーバーをリンク サーバーとして追加する必要があります。 詳細については、「[リンク サーバーの作成](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md)」と「[リンク サーバー](../../relational-databases/linked-servers/linked-servers-database-engine.md)」を参照してください。

### <a name="create-a-sql-server-agent-job"></a>SQL Server エージェント ジョブを作成する

オンプレミスの SQL Server エージェントを使用してパッケージのスケジュールを設定するには、SSIS カタログ ストアド プロシージャ `[catalog].[create_execution]` と `[catalog].[start_execution]` を順に呼び出すジョブ ステップでジョブを作成します。 詳細については、「[パッケージに対する SQL Server エージェント ジョブ](../packages/sql-server-agent-jobs-for-packages.md)」を参照してください。

1.  SQL Server Management Studio では、ジョブを作成するオンプレミスの SQL Server データベースに接続します。

2.  **SQL Server エージェント** ノードを右クリックし、**[新規]**、**[ジョブ]** の順に選択し、**[新しいジョブ]** ダイアログ ボックスを開きます。

3.  **[新しいジョブ]** ダイアログ ボックスで、**[手順]** ページを選択し、**[新規]** を選択して、**[新しいジョブ ステップ]** ダイアログ ボックスを開きます。

4.  **[新しいジョブ ステップ]** ダイアログ ボックスで、`SSISDB` を**データベース**として選択します。

5.  コマンド フィールドで、次の例に示されたスクリプトのような Transact-SQL スクリプトを入力します。

    ```sql
    DECLARE @return_value int, @exe_id bigint 

    EXEC @return_value = [YourLinkedServer].[SSISDB].[catalog].[create_execution] 
    @folder_name=N'folderName', @project_name=N'projectName', 
    @package_name=N'packageName', @use32bitruntime=0, 
    @runinscaleout=1, @useanyworker=1, @execution_id=@exe_id OUTPUT 
 
    EXEC [YourLinkedServer].[SSISDB].[catalog].[start_execution] @execution_id=@exe_id

    GO
    ```

6.  ジョブの構成とスケジュール設定を完了します。

## <a name="elastic"></a> SQL Database エラスティック ジョブを使用してパッケージをスケジュールする

SQL Database のエラスティック ジョブに関する詳細については、「[スケールアウトされたクラウド データベースの管理](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-overview)」を参照してください。

### <a name="prerequisites"></a>前提条件

エラスティック ジョブを使用して、Azure SQL Database サーバー上の SSISDB カタログ データベースに格納されている SSIS パッケージをスケジュール設定するには、事前に次の作業を行う必要があります。

1.  Elastic Database ジョブ コンポーネントをインストールして構成します。 詳細については、「[Elastic Database ジョブのインストールの概要](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-service-installation)」を参照してください。

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

## <a name="sproc"></a> Azure Data Factory SQL Server ストアド プロシージャ アクティビティを使用してパッケージをスケジュール設定する

> [!IMPORTANT]
> 次の例では、Azure Data Factory バージョン 1 ストアド プロシージャ アクティビティで JSON スクリプトを使用します。

Azure Data Factory SQL Server ストアド プロシージャ アクティビティを使用してパッケージをスケジュール設定するには、次の作業を行います。

1.  データ ファクトリを作成する。

2.  SSISDB をホストする SQL Database のリンク サービスを作成する。

3.  スケジュール設定を駆動する出力データセットを作成する。

4.  SSIS パッケージを実行する SQL Server ストアド プロシージャ アクティビティを使用するデータ ファクトリ パイプラインを作成する。

このセクションでは、これらの手順の概要を説明します。 データ ファクトリの完全なチュートリアルは、この記事の範囲外です。 詳細については、「[SQL Server ストアド プロシージャ アクティビティ](https://docs.microsoft.com/en-us/azure/data-factory/data-factory-stored-proc-activity)」を参照してください。

### <a name="created-a-linked-service-for-the-sql-database-that-hosts-ssisdb"></a>SSISDB をホストする SQL Database のリンク サービスを作成する
リンク サービスは、データ ファクトリを SSISDB に接続することができます。

```json
{
    "name": "AzureSqlLinkedService",
    "properties": {
        "description": "",
        "type": "AzureSqlDatabase",
        "typeProperties": {
            "connectionString": "Data Source = tcp: YourSQLDBServer.database.windows.net, 1433; Initial Catalog = SSISDB; User ID = YourUsername; Password = YourPassword; Integrated Security = False; Encrypt = True; Connect Timeout = 30"
        }
    }
}
```

### <a name="create-an-output-dataset"></a>出力データセットを作成する
出力データセットには、スケジューリング情報が含まれます。

```json
{
    "name": "sprocsampleout",
    "properties": {
        "type": "AzureSqlTable",
        "linkedServiceName": "AzureSqlLinkedService",
        "typeProperties": {
            "tableName": "sampletable"
        },
        "availability": {
            "frequency": "Hour",
            "interval": 1
        }
    }
}
```
### <a name="create-a-data-factory-pipeline"></a>データ ファクトリ パイプラインを作成する
パイプラインは、SQL Server ストアド プロシージャ アクティビティを使用して SSIS パッケージを実行します。

```json
{
    "name": "SprocActivitySamplePipeline",
    "properties": {
        "activities": [{
            "name": "SprocActivitySample",
            "type": "SqlServerStoredProcedure",
            "typeProperties": {
                "storedProcedureName": "sp_executesql",
                "storedProcedureParameters": {
                    "stmt": "Transact-SQL script to create and start SSIS package execution using SSISDB catalog stored procedures"
                }
            },
            "outputs": [{
                "name": "sprocsampleout"
            }],
            "scheduler": {
                "frequency": "Hour",
                "interval": 1
            }
        }],
        "start": "2017-10-01T00:00:00Z",
        "end": "2017-10-01T05:00:00Z",
        "isPaused": false
    }
}
```

SSIS パッケージの実行を作成および開始するために必要な Transact-SQL コマンドをカプセル化するため、新しいストアド プロシージャを作成する必要はありません。 スクリプト全体を前出の JSON サンプル内の `stmt` パラメーターの値として提供できます。 次にサンプル スクリプトを示します。

```sql
-- T-SQL script to create and start SSIS package execution using SSISDB catalog stored procedures
DECLARE @return_value INT,@exe_id BIGINT,@err_msg NVARCHAR(150)

-- Create the exectuion
EXEC @return_value=[SSISDB].[catalog].[create_execution] @folder_name=N'folderName', @project_name=N'projectName', @package_name=N'packageName', @use32bitruntime=0, @runinscaleout=1,@useanyworker=1, @execution_id=@exe_id OUTPUT

-- To synchronize SSIS package execution, set the SYNCHRONIZED execution parameter
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @exe_id, @object_type=50, @parameter_name=N'SYNCHRONIZED', @parameter_value=1

-- Start the execution                                                         
EXEC [SSISDB].[catalog].[start_execution] @execution_id=@exe_id,@retry_count=0
                                          
-- Raise an error for unsuccessful package execution
-- Execution status values include the following:
-- created (1)
-- running (2)
-- canceled (3)
-- failed (4)
-- pending (5)
-- ended unexpectedly (6)
-- succeeded (7)
-- stopping (8)
-- completed (9) 
IF(SELECT [status]
   FROM [SSISDB].[catalog].[executions]
   WHERE execution_id=@exe_id)<>7
BEGIN
    SET @err_msg=N'Your package execution did not succeed for execution ID: ' + CAST(@exe_id AS NVARCHAR(20))
    RAISERROR(@err_msg,15,1)
END
GO
```

このスクリプトのコードの詳細については、「[ストアド プロシージャを使用した SSIS パッケージの配置と実行](../packages/deploy-integration-services-ssis-projects-and-packages.md#deploy-and-execute-ssis-packages-using-stored-procedures)」を参照してください。

## <a name="next-steps"></a>次の手順
SQL Server エージェントの詳細については、「[パッケージに対する SQL Server エージェント ジョブ](../packages/sql-server-agent-jobs-for-packages.md)」を参照してください。

SQL Database のエラスティック ジョブに関する詳細については、「[スケールアウトされたクラウド データベースの管理](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-overview)」を参照してください。
