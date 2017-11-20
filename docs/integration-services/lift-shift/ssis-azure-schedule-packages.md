---
title: "Azure での SSIS パッケージの実行がスケジュール |Microsoft ドキュメント"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2f28400200105e8e63f787cbcda58c183ba00da5
ms.openlocfilehash: 2130e68d5e29671a2881d8762666cf852ff51259
ms.contentlocale: ja-jp
ms.lasthandoff: 10/18/2017

---
# <a name="schedule-the-execution-of-an-ssis-package-on-azure"></a>Azure で SSIS パッケージの実行をスケジュールします。
次のスケジュールのオプションのいずれかを選択して、Azure SQL Database サーバー上の SSISDB カタログ データベースに格納されたパッケージの実行をスケジュールすることができます。
-   [SQL Server エージェント](#agent)
-   [SQL データベース elastic ジョブ](#elastic)
-   [Azure データ ファクトリ SQL Server ストアド プロシージャ アクティビティ](#sproc)

## <a name="agent"></a>SQL Server エージェントを使用してパッケージのスケジュール

### <a name="prerequisite"></a>前提条件

内部設置型 SQL Server エージェントを使用するには、Azure SQL Database サーバーに格納されたパッケージの実行をスケジュールする、前に、リンク サーバーとして SQL データベース サーバーを追加する必要があります。 詳細については、次を参照してください。[リンク サーバーの作成](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md)と[リンク サーバー](../../relational-databases/linked-servers/linked-servers-database-engine.md)です。

### <a name="create-a-sql-server-agent-job"></a>SQL Server エージェント ジョブを作成します。

内部設置型 SQL Server エージェントを使用してパッケージのスケジュールを SSIS カタログを呼び出すジョブ ステップでジョブを作成するストアド プロシージャ`[catalog].[create_execution]`し`[catalog].[start_execution]`です。 詳細については、次を参照してください。[パッケージの SQL Server エージェント ジョブ](../packages/sql-server-agent-jobs-for-packages.md)です。

1.  SQL Server Management Studio では、ジョブを作成する内部設置型 SQL Server データベースに接続します。

2.  右クリックし、 **SQL Server エージェント**ノード、**新規**、し、**ジョブ**を開くには、**新しいジョブ** ダイアログ ボックス。

3.  **新しいジョブ**ダイアログ ボックスで、**手順**ページし、[**新規**を開くには、**新しいジョブ ステップ**] ダイアログ ボックス。

4.  **新しいジョブ ステップ**ダイアログ ボックスで、`SSISDB`として、**データベース。**

5.  コマンド フィールドでは、次の例に示すように、スクリプトのような TRANSACT-SQL スクリプトを入力します。

    ```sql
    DECLARE @return_value int, @exe_id bigint 

    EXEC @return_value = [YourLinkedServer].[SSISDB].[catalog].[create_execution] 
    @folder_name=N'folderName', @project_name=N'projectName', 
    @package_name=N'packageName', @use32bitruntime=0, 
    @runinscaleout=1, @useanyworker=1, @execution_id=@exe_id OUTPUT 
 
    EXEC [YourLinkedServer].[SSISDB].[catalog].[start_execution] @execution_id=@exe_id

    GO
    ```

6.  構成して、ジョブのスケジュール設定を完了します。

## <a name="elastic"></a>SQL Database の弾力性ジョブを使用してパッケージのスケジュール

SQL データベースでエラスティック ジョブに関する詳細については、次を参照してください。[管理するスケール アウト クラウド データベース](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-overview)です。

### <a name="prerequisites"></a>前提条件

弾力性ジョブを使用して、Azure SQL データベース サーバー上の SSISDB カタログ データベースに格納されている SSIS パッケージをスケジュールすることができます、前に、次の作業を行う必要があります。

1.  インストールし、弾力性データベース ジョブ コンポーネントを構成します。 詳細については、次を参照してください。[弾力性データベースをインストールするジョブの概要](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-service-installation)です。

2. ジョブを使用して、SSIS カタログ データベースにコマンドを送信するデータベース スコープ資格情報を作成します。 詳細については、次を参照してください。 [CREATE DATABASE SCOPED CREDENTIAL (TRANSACT-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)です。

### <a name="create-an-elastic-job"></a>弾力性ジョブを作成します。

ジョブを作成するには、次の例に示すように、スクリプトのような TRANSACT-SQL スクリプトを使用します。

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

## <a name="sproc"></a>Azure データ ファクトリ SQL Server ストアド プロシージャ アクティビティを使用してパッケージのスケジュール

> [!IMPORTANT]
> Azure Data Factory バージョン 1 で次の例で JSON スクリプトを使用してストアド プロシージャ アクティビティ。

Azure データ ファクトリ SQL Server ストアド プロシージャ アクティビティを使用してパッケージをスケジュールするには、次の作業を行います。

1.  データ ファクトリを作成します。

2.  SSISDB をホストする SQL データベースのリンクされたサービスを作成します。

3.  ドライブのスケジュール設定を出力データセットを作成します。

4.  SSIS パッケージを実行する SQL Server ストアド プロシージャ アクティビティを使用する Data Factory パイプラインを作成します。

このセクションでは、これらの手順の概要を示します。 データ ファクトリの完全なチュートリアルは、この記事の範囲外です。 詳細については、次を参照してください。 [SQL Server ストアド プロシージャ アクティビティ](https://docs.microsoft.com/en-us/azure/data-factory/data-factory-stored-proc-activity)です。

### <a name="created-a-linked-service-for-the-sql-database-that-hosts-ssisdb"></a>SQL データベースのリンクされたサービスをホストする SSISDB の作成
リンクされたサービスには、SSISDB に接続するデータ ファクトリことができます。

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

### <a name="create-an-output-dataset"></a>出力データセットを作成します。
出力データセットには、スケジューリング情報が含まれています。

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
### <a name="create-a-data-factory-pipeline"></a>Data Factory パイプラインを作成します。
パイプラインでは、SQL Server ストアド プロシージャ アクティビティを使用して、SSIS パッケージを実行します。

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

作成して SSIS パッケージの実行を開始するために必要な TRANSACT-SQL コマンドをカプセル化する新しいストアド プロシージャを作成する必要はありません。 スクリプト全体の値として使用できる、`stmt`上記の JSON サンプル内のパラメーターです。 スクリプトの例を次に示します。

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

このスクリプトでコードの詳細については、次を参照してください。[ストアド プロシージャを使用して、実行 SSIS パッケージの配置および](../packages/deploy-integration-services-ssis-projects-and-packages.md#deploy-and-execute-ssis-packages-using-stored-procedures)です。

## <a name="next-steps"></a>次の手順
SQL Server エージェントに関する詳細については、次を参照してください。[パッケージの SQL Server エージェント ジョブ](../packages/sql-server-agent-jobs-for-packages.md)です。

SQL データベースでエラスティック ジョブに関する詳細については、次を参照してください。[管理するスケール アウト クラウド データベース](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-overview)です。

