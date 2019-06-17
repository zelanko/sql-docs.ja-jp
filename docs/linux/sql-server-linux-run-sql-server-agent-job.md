---
title: 作成し、Linux 上の SQL Server ジョブの実行 |Microsoft Docs
description: このチュートリアルでは、Linux 上の SQL Server エージェント ジョブを実行する方法を示します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1d93d95e-9c89-4274-9b3f-fa2608ec2792
ms.openlocfilehash: d7df0ed46d9ded592a8cebc6571c5ec1e1b1f486
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705117"
---
# <a name="create-and-run-sql-server-agent-jobs-on-linux"></a>作成し、Linux 上の SQL Server エージェント ジョブの実行

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server ジョブを使用して、定期的に SQL Server データベースで、同じ一連のコマンドを実行できます。 このチュートリアルでは、TRANSACT-SQL と SQL Server Management Studio (SSMS) の両方を使用して Linux 上の SQL Server エージェント ジョブを作成する方法の例を示します。

> [!div class="checklist"]
> * Linux 上の SQL Server エージェントをインストールします。
> * 日単位のデータベース バックアップを実行する新しいジョブを作成します。
> * スケジュールし、ジョブの実行
> * (省略可能) の SSMS で、同じ手順に従います

Linux 上の SQL Server エージェントに関する既知の問題を参照してください、[リリース ノート](sql-server-linux-release-notes.md)します。

## <a name="prerequisites"></a>前提条件

このチュートリアルを完了するには、次の前提条件が必要です。

* 次の前提条件を使用して Linux マシン:
  * SQL Server ([RHEL](quickstart-install-connect-red-hat.md)、 [SLES](quickstart-install-connect-suse.md)、または[Ubuntu](quickstart-install-connect-ubuntu.md)) コマンド ライン ツールを使用します。

次の前提条件はオプションです。

* SSMS を使用した Windows マシンの場合:
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) SSMS の省略可能な手順についてはします。

## <a name="enable-sql-server-agent"></a>SQL Server エージェントを有効にします。

Linux 上の SQL Server エージェントを使用して、既に SQL Server がインストールされているコンピューターで SQL Server エージェントをまず有効にする必要があります。

1. SQL Server エージェントを有効にするには、以下の手順に従います。
  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
  ```

1. 次のコマンドでは、SQL Server を再起動します。
  ```bash
  sudo systemctl restart mssql-server
  ```

> [!NOTE]
> SQL Server 2017 CU4 以降、SQL Server エージェントが付属、 **mssql server**パッケージ化し、既定で無効にします。 CU4 訪問する前に設定されたエージェント[Linux 上の SQL Server エージェントのインストール](sql-server-linux-setup-sql-agent.md)します。

## <a name="create-a-sample-database"></a>サンプル データベースの作成

次の手順を使用してという名前のサンプル データベースを作成する**SampleDB**します。 このデータベースは、毎日のバックアップ ジョブに使用されます。

1. Linux コンピューターでは、bash、ターミナル セッションを開きます。

1. 使用**sqlcmd** Transact SQL を実行する**CREATE DATABASE**コマンド。

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -Q 'CREATE DATABASE SampleDB'
   ```

1. データベースの作成、サーバー上のデータベースを一覧表示して確認します。

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -Q 'SELECT Name FROM sys.Databases'
   ```

## <a name="create-a-job-with-transact-sql"></a>Transact SQL を使用したジョブを作成します。

次の手順は、TRANSACT-SQL コマンドを使用して Linux 上の SQL Server エージェント ジョブを作成します。 ジョブの実行、サンプル データベースの日次バックアップ**SampleDB**します。

> [!TIP]
> T-SQL の任意のクライアントを使用すると、これらのコマンドを実行します。 たとえば、on Linux で使える[sqlcmd](sql-server-linux-setup-tools.md)または[Visual Studio Code](sql-server-linux-develop-use-vscode.md)します。 リモートの Windows サーバーからも SQL Server Management Studio (SSMS) でクエリを実行または、UI インターフェイスは、次のセクションで説明されているジョブの管理を使用できます。

1. 使用[sp_add_job](../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)という名前のジョブを作成する`Daily SampleDB Backup`します。

   ```sql
   -- Adds a new job executed by the SQLServerAgent service
   -- called 'Daily SampleDB Backup'
   USE msdb ;
   GO
   EXEC dbo.sp_add_job
      @job_name = N'Daily SampleDB Backup' ;
   GO
   ```

1. 呼び出す[sp_add_jobstep](../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)のバックアップを作成するジョブ ステップを作成する、`SampleDB`データベース。

   ```sql
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

1. 使用するジョブの毎日のスケジュールを作成し、 [sp_add_schedule](../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md)します。

   ```sql
   -- Creates a schedule called 'Daily'
   EXEC dbo.sp_add_schedule
      @schedule_name = N'Daily SampleDB',
      @freq_type = 4,
      @freq_interval = 1,
      @active_start_time = 233000 ;
   USE msdb ;
   GO
   ```

1. ジョブのスケジュールを使用してジョブにアタッチ[sp_attach_schedule](../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)します。

   ```sql
   -- Sets the 'Daily' schedule to the 'Daily SampleDB Backup' Job
   EXEC sp_attach_schedule
      @job_name = N'Daily SampleDB Backup',
      @schedule_name = N'Daily SampleDB';
   GO
   ```

1. 使用[sp_add_jobserver](../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)ターゲット サーバーにジョブを割り当てます。 この例では、ターゲットは、ローカル サーバーです。

   ```sql
   EXEC dbo.sp_add_jobserver
      @job_name = N'Daily SampleDB Backup',
      @server_name = N'(LOCAL)';
   GO
   ```
1. 使用してジョブを開始[sp_start_job](../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)します。

   ```sql
   EXEC dbo.sp_start_job N' Daily SampleDB Backup' ;
   GO
   ```

## <a name="create-a-job-with-ssms"></a>SSMS を使用したジョブを作成します。

作成し、Windows 上の SQL Server Management Studio (SSMS) を使用してリモートでジョブを管理することができますも。

1. Windows で SSMS を起動し、Linux の SQL Server インスタンスに接続します。 詳細については、次を参照してください。 [SSMS を使用した Linux 上の SQL Server の管理](sql-server-linux-manage-ssms.md)します。

1. という名前のサンプル データベースを作成することを確認**SampleDB**します。

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-0.png" alt="Create a SampleDB database" style="width: 550px;"/>

1. SQL エージェントがしたことを確認[インストール](sql-server-linux-setup-sql-agent.md)正しく構成されているとします。 オブジェクト エクスプ ローラーで SQL Server エージェントの横にあるプラス記号を探します。 SQL Server エージェントが有効でない場合は、再起動してみてください、 **mssql server** Linux 上のサービスです。

   ![SQL Server エージェントがインストールされていることを確認します。](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-1.png)

1. 新しいジョブを作成します。

   ![新しいジョブを作成します。](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-2.png)

1. ジョブの名前し、ジョブ ステップを作成します。

   ![ジョブ ステップを作成します。](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-3.png)

1. どのようなサブシステムを使用して、ジョブ ステップで行う必要がありますを指定します。

   ![ジョブのサブシステム](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-4.png)

   ![ジョブのステップ アクション](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-5.png)

1. 新しいジョブ スケジュールを作成します。

   ![ジョブ スケジュール](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-6.png)

   ![ジョブ スケジュール](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-8.png)

1. ジョブを開始します。

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-9.png" alt="Start the SQL Server Agent job" style="width: 550px;"/>

## <a name="next-steps"></a>次の手順

このチュートリアルでは、以下の使用方法を学習しました:

> [!div class="checklist"]
> * Linux 上の SQL Server エージェントをインストールします。
> * TRANSACT-SQL の使用とシステム ストアド プロシージャのジョブを作成するには
> * 日単位のデータベース バックアップを実行するジョブを作成します。
> * SSMS UI を使用して作成し、ジョブの管理

次に、その他の機能を作成すると、ジョブの管理の詳細します。

> [!div class="nextstepaction"]
>[SQL Server エージェントのドキュメント](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent)
