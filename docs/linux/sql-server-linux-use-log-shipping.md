---
title: SQL Server on Linux のログ配布の構成 |Microsoft ドキュメント
description: このチュートリアルでは、Linux 上の SQL Server インスタンスをログ配布を使用してセカンダリ インスタンスにレプリケートする方法の基本的な例を示します。
author: meet-bhagdev
ms.author: meetb
manager: craigg
ms.date: 04/19/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.openlocfilehash: 7d4e66937372c690949d1c15bedf6c39ed4f6f45
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="get-started-with-log-shipping-on-linux"></a>Linux 上のログ配布の概要します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server ログ配布は、1 つ以上のセカンダリ サーバー上にプライマリ サーバーからデータベースがレプリケートされる HA 構成です。 簡単に言うと、ソース データベースのバックアップはセカンダリ サーバー上に復元されます。 トランザクション ログ バックアップの作成、プライマリ サーバー、定期的にし、セカンダリ サーバーに復元、データベースのセカンダリ コピーを更新します。 

  ![ログ配布](https://preview.ibb.co/hr5Ri5/logshipping.png)


この」の説明に従って画像、ログ配布セッションでは、次の手順。

- プライマリ SQL Server インスタンスでトランザクション ログ ファイルをバックアップします。
- ネットワーク経由で 1 つまたは複数のセカンダリ SQL Server インスタンスにトランザクション ログのバックアップ ファイルをコピー
- セカンダリ SQL Server インスタンスでトランザクション ログ バックアップ ファイルを復元します。

## <a name="prerequisites"></a>前提条件
- [Linux 上の SQL Server エージェントをインストールします。](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-setup-sql-agent)

## <a name="setup-a-network-share-for-log-shipping-using-cifs"></a>ログ配布の CIFS を使用して、ネットワーク共有のセットアップ 

> [!NOTE] 
> このチュートリアルでは、CIFS + Samba を使用して、ネットワーク共有を設定します。 NFS を使用する場合は、コメントのままにし、ドキュメントに追加されます。       

### <a name="configure-primary-server"></a>プライマリ サーバーを構成します。
-   Samba をインストールするには、次を実行します。

    ```bash
    sudo apt-get install samba #For Ubuntu
    sudo yum -y install samba #For RHEL/CentOS
    ```
-   ログ配布のログを保存し、mssql に必要なアクセス許可を付与するディレクトリを作成します。

    ```bash
    mkdir /var/opt/mssql/tlogs
    chown mssql:mssql /var/opt/mssql/tlogs
    chmod 0700 /var/opt/mssql/tlogs
    ```

-   (ルートのアクセス許可は必要です)/etc/samba/smb.conf ファイルを編集し、次のセクションを追加します。

    ```bash
    [tlogs]
    path=/var/opt/mssql/tlogs
    available=yes
    read only=yes
    browsable=yes
    public=yes
    writable=no
    ```

-   Samba mssql ユーザーを作成します。

    ```bash
    sudo smbpasswd -a mssql
    ```

-   Samba サービスを再起動します。
    ```bash
    sudo systemctl restart smbd.service nmbd.service
    ```
 
### <a name="configure-secondary-server"></a>セカンダリ サーバーを構成します。

-   CIFS クライアントをインストールするには、次を実行します。
    ```bash   
    sudo apt-get install cifs-utils #For Ubuntu
    sudo yum -y install cifs-utils #For RHEL/CentOS
    ```

-   資格情報を格納するファイルを作成します。 最近、mssql Samba アカウントに対して設定するパスワードを使用します。 

        vim /var/opt/mssql/.tlogcreds
        #Paste the following in .tlogcreds
        username=mssql
        domain=<domain>
        password=<password>

-   マウントの空のディレクトリを作成し、アクセス許可と所有権を正しく設定するには、次のコマンドを実行します。
    ```bash   
    mkdir /var/opt/mssql/tlogs
    sudo chown root:root /var/opt/mssql/tlogs
    sudo chmod 0550 /var/opt/mssql/tlogs
    sudo chown root:root /var/opt/mssql/.tlogcreds
    sudo chmod 0660 /var/opt/mssql/.tlogcreds
    ```

-   共有を永続化するには、等/fstab に行を追加します。 

        //<ip_address_of_primary_server>/tlogs /var/opt/mssql/tlogs cifs credentials=/var/opt/mssql/.tlogcreds,ro,uid=mssql,gid=mssql 0 0
        
-   共有をマウントします。
    ```bash   
    sudo mount -a
    ```
       
## <a name="setup-log-shipping-via-t-sql"></a>ログ配布の T-SQL を使用してのセットアップします。

- プライマリ サーバーからこのスクリプトを実行します。

    ```tsql
    BACKUP DATABASE SampleDB
    TO DISK = '/var/opt/mssql/tlogs/SampleDB.bak'
    GO
    ```
    ```tsql
    DECLARE @LS_BackupJobId AS uniqueidentifier 
    DECLARE @LS_PrimaryId   AS uniqueidentifier 
    DECLARE @SP_Add_RetCode As int 
    EXEC @SP_Add_RetCode = master.dbo.sp_add_log_shipping_primary_database 
             @database = N'SampleDB' 
            ,@backup_directory = N'/var/opt/mssql/tlogs' 
            ,@backup_share = N'/var/opt/mssql/tlogs' 
            ,@backup_job_name = N'LSBackup_SampleDB' 
            ,@backup_retention_period = 4320
            ,@backup_compression = 2
            ,@backup_threshold = 60 
            ,@threshold_alert_enabled = 1
            ,@history_retention_period = 5760 
            ,@backup_job_id = @LS_BackupJobId OUTPUT 
            ,@primary_id = @LS_PrimaryId OUTPUT 
            ,@overwrite = 1 

    IF (@@ERROR = 0 AND @SP_Add_RetCode = 0) 
    BEGIN 

    DECLARE @LS_BackUpScheduleUID   As uniqueidentifier 
    DECLARE @LS_BackUpScheduleID    AS int 

    EXEC msdb.dbo.sp_add_schedule 
            @schedule_name =N'LSBackupSchedule' 
            ,@enabled = 1 
            ,@freq_type = 4 
            ,@freq_interval = 1 
            ,@freq_subday_type = 4 
            ,@freq_subday_interval = 15 
            ,@freq_recurrence_factor = 0 
            ,@active_start_date = 20170418 
            ,@active_end_date = 99991231 
            ,@active_start_time = 0 
            ,@active_end_time = 235900 
            ,@schedule_uid = @LS_BackUpScheduleUID OUTPUT 
            ,@schedule_id = @LS_BackUpScheduleID OUTPUT 

    EXEC msdb.dbo.sp_attach_schedule 
            @job_id = @LS_BackupJobId 
            ,@schedule_id = @LS_BackUpScheduleID  

    EXEC msdb.dbo.sp_update_job 
            @job_id = @LS_BackupJobId 
            ,@enabled = 1 
            
    END 

    EXEC master.dbo.sp_add_log_shipping_alert_job 

    EXEC master.dbo.sp_add_log_shipping_primary_secondary 
            @primary_database = N'SampleDB' 
            ,@secondary_server = N'<ip_address_of_secondary_server>' 
            ,@secondary_database = N'SampleDB' 
            ,@overwrite = 1 
    ```


- セカンダリ サーバーからこのスクリプトを実行します。

    ```tsql
    RESTORE DATABASE SampleDB FROM DISK = '/var/opt/mssql/tlogs/SampleDB.bak'
    WITH NORECOVERY;
    ```
    
    ```tsql
    DECLARE @LS_Secondary__CopyJobId    AS uniqueidentifier 
    DECLARE @LS_Secondary__RestoreJobId AS uniqueidentifier 
    DECLARE @LS_Secondary__SecondaryId  AS uniqueidentifier 
    DECLARE @LS_Add_RetCode As int 

    EXEC @LS_Add_RetCode = master.dbo.sp_add_log_shipping_secondary_primary 
            @primary_server = N'<ip_address_of_primary_server>' 
            ,@primary_database = N'SampleDB' 
            ,@backup_source_directory = N'/var/opt/mssql/tlogs/' 
            ,@backup_destination_directory = N'/var/opt/mssql/tlogs/' 
            ,@copy_job_name = N'LSCopy_SampleDB' 
            ,@restore_job_name = N'LSRestore_SampleDB' 
            ,@file_retention_period = 4320 
            ,@overwrite = 1 
            ,@copy_job_id = @LS_Secondary__CopyJobId OUTPUT 
            ,@restore_job_id = @LS_Secondary__RestoreJobId OUTPUT 
            ,@secondary_id = @LS_Secondary__SecondaryId OUTPUT 

    IF (@@ERROR = 0 AND @LS_Add_RetCode = 0) 
    BEGIN 

    DECLARE @LS_SecondaryCopyJobScheduleUID As uniqueidentifier 
    DECLARE @LS_SecondaryCopyJobScheduleID  AS int 

    EXEC msdb.dbo.sp_add_schedule 
            @schedule_name =N'DefaultCopyJobSchedule' 
            ,@enabled = 1 
            ,@freq_type = 4 
            ,@freq_interval = 1 
            ,@freq_subday_type = 4 
            ,@freq_subday_interval = 15 
            ,@freq_recurrence_factor = 0 
            ,@active_start_date = 20170418 
            ,@active_end_date = 99991231 
            ,@active_start_time = 0 
            ,@active_end_time = 235900 
            ,@schedule_uid = @LS_SecondaryCopyJobScheduleUID OUTPUT 
            ,@schedule_id = @LS_SecondaryCopyJobScheduleID OUTPUT 

    EXEC msdb.dbo.sp_attach_schedule 
            @job_id = @LS_Secondary__CopyJobId 
            ,@schedule_id = @LS_SecondaryCopyJobScheduleID  

    DECLARE @LS_SecondaryRestoreJobScheduleUID  As uniqueidentifier 
    DECLARE @LS_SecondaryRestoreJobScheduleID   AS int 

    EXEC msdb.dbo.sp_add_schedule 
            @schedule_name =N'DefaultRestoreJobSchedule' 
            ,@enabled = 1 
            ,@freq_type = 4 
            ,@freq_interval = 1 
            ,@freq_subday_type = 4 
            ,@freq_subday_interval = 15 
            ,@freq_recurrence_factor = 0 
            ,@active_start_date = 20170418 
            ,@active_end_date = 99991231 
            ,@active_start_time = 0 
            ,@active_end_time = 235900 
            ,@schedule_uid = @LS_SecondaryRestoreJobScheduleUID OUTPUT 
            ,@schedule_id = @LS_SecondaryRestoreJobScheduleID OUTPUT 

    EXEC msdb.dbo.sp_attach_schedule 
            @job_id = @LS_Secondary__RestoreJobId 
            ,@schedule_id = @LS_SecondaryRestoreJobScheduleID  
            
    END 
    DECLARE @LS_Add_RetCode2    As int 
    IF (@@ERROR = 0 AND @LS_Add_RetCode = 0) 
    BEGIN 

    EXEC @LS_Add_RetCode2 = master.dbo.sp_add_log_shipping_secondary_database 
            @secondary_database = N'SampleDB' 
            ,@primary_server = N'<ip_address_of_primary_server>' 
            ,@primary_database = N'SampleDB' 
            ,@restore_delay = 0 
            ,@restore_mode = 0 
            ,@disconnect_users  = 0 
            ,@restore_threshold = 45   
            ,@threshold_alert_enabled = 1 
            ,@history_retention_period  = 5760 
            ,@overwrite = 1 

    END 

    IF (@@error = 0 AND @LS_Add_RetCode = 0) 
    BEGIN 

    EXEC msdb.dbo.sp_update_job 
            @job_id = @LS_Secondary__CopyJobId 
            ,@enabled = 1 

    EXEC msdb.dbo.sp_update_job 
            @job_id = @LS_Secondary__RestoreJobId 
            ,@enabled = 1 

    END 
    ```

## <a name="verify-log-shipping-works"></a>ログ配布の動作を確認します。

- プライマリ サーバーで次のジョブを開始してログ配布が機能することを確認します。

    ```tsql
    USE msdb ;  
    GO  

    EXEC dbo.sp_start_job N'LSBackup_SampleDB' ;  
    GO  
    ```

- セカンダリ サーバーで次のジョブを開始してログ配布が機能することを確認します。
 
    ```tsql
    USE msdb ;  
    GO  

    EXEC dbo.sp_start_job N'LSCopy_SampleDB' ;  
    GO  
    EXEC dbo.sp_start_job N'LSRestore_SampleDB' ;  
    GO  
    RESTORE DATABASE SampleDB WITH RECOVERY;
    ```


