---
title: Linux 上の SQL Server レプリケーションの構成 |Microsoft Docs
description: このチュートリアルでは、Linux 上の SQL Server スナップショット レプリケーションを構成する方法を示します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 88fa1c1be8e6506f947fc300b2f26bd865d77622
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715241"
---
# <a name="configure-replication-with-t-sql"></a>T-SQL でレプリケーションを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)] 

このチュートリアルでは、TRANSACT-SQL を使用して SQL Server の 2 つのインスタンスを使った Linux 上に SQL Server スナップショット レプリケーションを構成します。 パブリッシャーとディストリビューターに、同じインスタンスをして、サブスクライバーが別のインスタンスになります。

> [!div class="checklist"]
> * Linux 上の SQL Server レプリケーション エージェントを有効にします。
> * サンプル データベースの作成
> * SQL Server エージェントのアクセスのスナップショット フォルダーを構成します。
> * ディストリビューターの構成
> * パブリッシャーを構成します
> * パブリケーションとアーティクルを構成します。
> * サブスクライバーを構成します。 
> * レプリケーション ジョブを実行します。

すべてのレプリケーション構成で構成できます[レプリケーション ストアド プロシージャ](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)します。

## <a name="prerequisites"></a>前提条件  
このチュートリアルを完了するには、必要があります。

- SQL Server on Linux の最新バージョンの SQL Server の 2 つのインスタンス
- SQLCMD または SSMS などのレプリケーションを設定する問題の T-SQL クエリするためのツール

  参照してください[SSMS を使用して、SQL Server on Linux を管理する](./sql-server-linux-manage-ssms.md)します。

## <a name="detailed-steps"></a>詳細な手順

1. レプリケーション エージェントを使用する SQL Server エージェントを有効にする Linux 上の SQL Server レプリケーション エージェントを有効にします。 両方のホスト コンピューターで、ターミナルで次のコマンドを実行します。 

  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
  sudo systemctl restart mssql-server
  ```

1. SQL Server レプリケーションに参加している各 CTP1.5 インスタンスの msdb データベースに、SQL Server インスタンスを次のストアド プロシージャのレプリケーションの実行のために構成します。

  ```sql
  USE msdb
  GO
  exec sys.sp_MSrepl_createdatatypemappings;
  GO
  ```

1. サンプル データベースとテーブルで、パブリッシャーの作成、サンプル データベースとパブリケーションのアーティクルとして機能するテーブルを作成します。

  ```sql
  CREATE DATABASE Sales
  GO
  USE [SALES]
  GO 
  CREATE TABLE CUSTOMER([CustomerID] [int] NOT NULL, [SalesAmount] [decimal] NOT NULL)
  GO 
  INSERT INTO CUSTOMER (CustomerID, SalesAmount) VALUES (1,100),(2,200),(3,300)
  ```

  その他の SQL Server インスタンスで、サブスクライバーのアーティクルを受信するデータベースを作成します。

  ```sql
  CREATE DATABASE Sales
  GO
  ```

1. 読み取り/書き込みをディストリビューターでスナップショット フォルダーを作成し、'mssql' ユーザーにアクセスを許可する SQL Server エージェントのスナップショット フォルダーを作成します。 

  ```bash
  sudo mkdir /var/opt/mssql/data/ReplData/
  sudo chown mssql /var/opt/mssql/data/ReplData/
  sudo chgrp mssql /var/opt/mssql/data/ReplData/
  ```

1. この例では、ディストリビューターを構成、発行元は、ディストリビューターにもなります。 配布もインスタンスを構成するパブリッシャーで、次のコマンドを実行します。

  ```sql
  DECLARE @distributor AS sysname
  DECLARE @distributorlogin AS sysname
  DECLARE @distributorpassword AS sysname
  -- Specify the distributor name. Use 'hostname' command on in terminal to find the hostname
  SET @distributor = N'<distributor instance name>'--in this example, it will be the name of the publisher
  SET @distributorlogin = N'<distributor login>'
  SET @distributorpassword = N'<distributor password>'
  -- Specify the distribution database. 
  
  use master
  exec sp_adddistributor @distributor = @distributor -- this should be the hostname

  -- Log into distributor and create Distribution Database. In this example, our publisher and distributor is on the same host
  exec sp_adddistributiondb @database = N'distribution', @log_file_size = 2, @deletebatchsize_xact = 5000, @deletebatchsize_cmd = 2000, @security_mode = 0, @login = @distributorlogin, @password = @distributorpassword
  GO

  DECLARE @snapshotdirectory AS nvarchar(500)
  SET @snapshotdirectory = N'/var/opt/mssql/data/ReplData/'

  -- Log into distributor and create Distribution Database. In this example, our publisher and distributor is on the same host
  use [distribution] 
  if (not exists (select * from sysobjects where name = 'UIProperties' and type = 'U ')) 
         create table UIProperties(id int) 
  if (exists (select * from ::fn_listextendedproperty('SnapshotFolder', 'user', 'dbo', 'table', 'UIProperties', null, null))) 
         EXEC sp_updateextendedproperty N'SnapshotFolder', @snapshotdirectory, 'user', dbo, 'table', 'UIProperties' 
  else 
         EXEC sp_addextendedproperty N'SnapshotFolder', @snapshotdirectory, 'user', dbo, 'table', 'UIProperties'
  GO
  ```

1. パブリッシャーで、次の TSQL コマンドを実行するパブリッシャーを構成します。

  ```sql
  DECLARE @publisher AS sysname
  DECLARE @distributorlogin AS sysname
  DECLARE @distributorpassword AS sysname
  -- Specify the distributor name. Use 'hostname' command on in terminal to find the hostname
  SET @publisher = N'<instance name>' 
  SET @distributorlogin = N'<distributor login>'
  SET @distributorpassword = N'<distributor password>'
  -- Specify the distribution database. 

  -- Adding the distribution publishers
  exec sp_adddistpublisher @publisher = @publisher, 
  @distribution_db = N'distribution', 
  @security_mode = 0, 
  @login = @distributorlogin, 
  @password = @distributorpassword, 
  @working_directory = N'/var/opt/mssql/data/ReplData', 
  @trusted = N'false', 
  @thirdparty_flag = 0, 
  @publisher_type = N'MSSQLSERVER'
  GO
  ```

1. パブリッシャーのパブリケーションがジョブの実行、次の TSQL コマンドを構成します。

  ```sql
  DECLARE @replicationdb AS sysname
  DECLARE @publisherlogin AS sysname
  DECLARE @publisherpassword AS sysname
  SET @replicationdb = N'Sales'
  SET @publisherlogin = N'<Publisher login>'
  SET @publisherpassword = N'<Publisher Password>'

  use [Sales]
  exec sp_replicationdboption @dbname = N'Sales', @optname = N'publish', @value = N'true'
  
  -- Add the snapshot publication
  exec sp_addpublication 
  @publication = N'SnapshotRepl', 
  @description = N'Snapshot publication of database ''Sales'' from Publisher ''<PUBLISHER HOSTNAME>''.',
  @retention = 0, 
  @allow_push = N'true', 
  @repl_freq = N'snapshot', 
  @status = N'active', 
  @independent_agent = N'true'

  exec sp_addpublication_snapshot @publication = N'SnapshotRepl', 
  @frequency_type = 1, 
  @frequency_interval = 1, 
  @frequency_relative_interval = 1, 
  @frequency_recurrence_factor = 0, 
  @frequency_subday = 8, 
  @frequency_subday_interval = 1, 
  @active_start_time_of_day = 0,
  @active_end_time_of_day = 235959, 
  @active_start_date = 0, 
  @active_end_date = 0, 
  @publisher_security_mode = 0, 
  @publisher_login = @publisherlogin, 
  @publisher_password = @publisherpassword
  ```

1. パブリッシャーで、アーティクルを次の TSQL コマンド実行 sales テーブルからに作成します。

  ```sql
  use [Sales]
  exec sp_addarticle 
  @publication = N'SnapshotRepl', 
  @article = N'customer', 
  @source_owner = N'dbo', 
  @source_object = N'customer', 
  @type = N'logbased', 
  @description = null, 
  @creation_script = null, 
  @pre_creation_cmd = N'drop', 
  @schema_option = 0x000000000803509D,
  @identityrangemanagementoption = N'manual', 
  @destination_table = N'customer', 
  @destination_owner = N'dbo', 
  @vertical_partition = N'false'
  ```

1. サブスクリプションの実行、パブリッシャーで、次の TSQL コマンドを構成します。

  ```sql
  DECLARE @subscriber AS sysname
  DECLARE @subscriber_db AS sysname
  DECLARE @subscriberLogin AS sysname
  DECLARE @subscriberPassword AS sysname
  SET @subscriber = N'<Instance Name>' -- for example, MSSQLSERVER
  SET @subscriber_db = N'Sales'
  SET @subscriberLogin = N'<Subscriber Login>'
  SET @subscriberPassword = N'<Subscriber Password>'

  use [Sales]
  exec sp_addsubscription 
  @publication = N'SnapshotRepl', 
  @subscriber = @subscriber,
  @destination_db = @subscriber_db, 
  @subscription_type = N'Push', 
  @sync_type = N'automatic', 
  @article = N'all', 
  @update_mode = N'read only', 
  @subscriber_type = 0

  exec sp_addpushsubscription_agent 
  @publication = N'SnapshotRepl', 
  @subscriber = @subscriber,
  @subscriber_db = @subscriber_db, 
  @subscriber_security_mode = 0, 
  @subscriber_login =  @subscriberLogin,
  @subscriber_password =  @subscriberPassword,
  @frequency_type = 1,
  @frequency_interval = 0, 
  @frequency_relative_interval = 0, 
  @frequency_recurrence_factor = 0, 
  @frequency_subday = 0, 
  @frequency_subday_interval = 0, 
  @active_start_time_of_day = 0, 
  @active_end_time_of_day = 0, 
  @active_start_date = 0, 
  @active_end_date = 19950101
  GO
  ```

1. レプリケーション エージェント ジョブを実行します。

  ジョブの一覧を取得する次のクエリを実行します。

  ```sql
  SELECT name, date_modified FROM msdb.dbo.sysjobs order by date_modified desc
  ```

  スナップショットを生成するスナップショットのレプリケーション ジョブを実行します。

  ```sql
  USE msdb;  
  --generate snapshot of publications, for example
  EXEC dbo.sp_start_job N'PUBLISHER-PUBLICATION-SnapshotRepl-1'
  GO
  ```

  スナップショットを生成するスナップショットのレプリケーション ジョブを実行します。

  ```sql
  USE msdb;  
  --distribute the publication to subscriber, for example
  EXEC dbo.sp_start_job N'DISTRIBUTOR-PUBLICATION-SnapshotRepl-SUBSCRIBER'
  GO
  ```

1. サブスクライバーを接続し、レプリケートされたデータのクエリ 

  サブスクライバーでは、次のクエリを実行して、レプリケーションが動作しているを確認します。

  ```sql
  SELECT * from [Sales].[dbo].[CUSTOMER]
  ```

このチュートリアルでは、SQL Server スナップショット レプリケーションを構成して、TRANSACT-SQL を使用して SQL Server の 2 つのインスタンスを使った Linux 上。

> [!div class="checklist"]
> * Linux 上の SQL Server レプリケーション エージェントを有効にします。
> * サンプル データベースの作成
> * SQL Server エージェントのアクセスのスナップショット フォルダーを構成します。
> * ディストリビューターの構成
> * パブリッシャーを構成します
> * パブリケーションとアーティクルを構成します。
> * サブスクライバーを構成します。 
> * レプリケーション ジョブを実行します。

## <a name="see-also"></a>関連項目

レプリケーションの詳細については、次を参照してください。 [SQL Server レプリケーションのドキュメント](../relational-databases/replication/sql-server-replication.md)します。

## <a name="next-steps"></a>次の手順

[Linux 上の概念: SQL Server レプリケーション](sql-server-linux-replication.md)

[レプリケーション ストアド プロシージャ](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)します。