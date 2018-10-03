---
title: SQL Server Managed Backup to Windows Azure の設定 |Microsoft Docs
ms.custom: ''
ms.date: 08/04/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 68ebb53e-d5ad-4622-af68-1e150b94516e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a80190c7a10ade3994fb9e12690b64b2e0e1b4df
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124072"
---
# <a name="setting-up-sql-server-managed-backup-to-windows-azure"></a>Windows Azure への SQL Server マネージド バックアップの設定
  このトピックには、次の 2 つのチュートリアルが含まれています。  
  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]をデータベース レベルで設定し、電子メール通知を有効にして、バックアップ処理を監視します。  
  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]をインスタンス レベルで設定し、電子メール通知を有効にして、バックアップ処理を監視します。  
  
 設定に関するチュートリアルについては[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]可用性グループの場合は、次を参照してください。[可用性グループを設定する SQL Server Managed Backup to Microsoft Azure](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)します。  
  
## <a name="setting-up-includesssmartbackupincludesss-smartbackup-mdmd"></a>[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の設定  
  
### <a name="enable-and-configure-includesssmartbackupincludesss-smartbackup-mdmd-for-a-database"></a>有効にして構成[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]データベース  
 このチュートリアルでは、データベース (TestDB) に対して [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を有効にして構成するために必要な手順の後、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の正常性状態の監視を有効にする手順について説明します。  
  
 **アクセス許可:**  
  
-   メンバーシップが必要です**db_backupoperator**データベース ロール、 **ALTER ANY CREDENTIAL**アクセス許可、および`EXECUTE`に対する**sp_delete_backuphistory**ストアド プロシージャ。  
  
-   必要があります**選択**に対するアクセス許可、 **smart_admin.fn_get_current_xevent_settings**関数。  
  
-   必要があります`EXECUTE`に対するアクセス許可、 **smart_admin.sp_get_backup_diagnostics**ストアド プロシージャ。 さらに、`VIEW SERVER STATE` 権限も必要です (この権限を必要とする他のシステム オブジェクトを内部的に呼び出すため)。  
  
-   必要があります`EXECUTE`に対するアクセス許可、`smart_admin.sp_set_instance_backup`と`smart_admin.sp_backup_master_switch`ストアド プロシージャ。  


1.  **Microsoft Azure ストレージ アカウントの作成:** バックアップは、Microsoft Azure ストレージ サービスに格納されます。 アカウントを既に持っていない場合、Microsoft Azure ストレージ アカウントを作成する必要があります。
    - SQL Server 2014 では、これは、ブロックとは異なる追加 blob、ページ blob を使用します。 そのため、汎用アカウントと blob のアカウントではなくを作成する必要があります。 詳細については、次を参照してください。 [Azure ストレージ アカウントについて](http://azure.microsoft.com/documentation/articles/storage-create-storage-account/)します。
    - ストレージ アカウント名およびアクセス キーをメモしておきます。 ストレージ アカウント名およびアクセス キー情報は、SQL 資格情報の作成に使用します。 SQL 資格情報は、ストレージ アカウントへの認証に使用されます。  
 
2.  **SQL 資格情報の作成:** Id、およびストレージ アクセス キーをパスワードとしてストレージ アカウントの名前を使用して SQL 資格情報を作成します。  
  
3.  **SQL Server エージェント サービスが開始され実行されていることを確認します。** SQL Server エージェントの開始が現在実行されていない場合。  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] でバックアップ操作を実行するには、SQL Server エージェントがインスタンスで実行されている必要があります。  バックアップ操作を定期的に実行できるように、SQL Server エージェントの自動的な実行を設定できます。  
  
4.  **保有期間を決定する:** バックアップ ファイルに必要な保有期間を決定します。 保有期間は日数で指定し、その範囲は 1 ～ 30 になります。  
  
5.  **有効にして構成[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]:** SQL Server Management Studio を起動し、データベースがインストールされているインスタンスに接続します。 要件に合わせて、データベース名、SQL 資格情報、保有期間、および暗号化オプションの値を変更した後、クエリ ウィンドウから次のステートメントを実行します。  
  
     暗号化の証明書を作成する方法の詳細については、次を参照してください。、**バックアップ証明書を作成する**ステップ[Create an Encrypted Backup](create-an-encrypted-backup.md)します。  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] は、指定したデータベースで有効になります。 データベースでのバックアップ操作の実行が開始されるまで最大 15 分かかる場合があります。  
  
6.  **拡張イベントの既定の構成を確認する:** 次の Transact-SQL ステートメントを実行して、拡張イベントの設定を確認します。  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     管理、運用、および分析のチャネル イベントは既定で有効になっていて、無効にできないことに注意してください。 手動の介入を必要とするイベントを監視するには、これで十分です。  デバッグ イベントを有効にすることはできますが、デバッグ チャネルには、 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] が問題の検出および解決に使用する情報イベントとデバッグ イベントが含まれています。 詳細については、次を参照してください。[モニター SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)します。  
  
7.  **正常性状態の通知を有効化し、構成する:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] には、注意を要するエラーまたは警告の電子メール通知を送信するためにエージェント ジョブを作成するストアド プロシージャがあります。 次の手順では、電子メール通知を有効にして構成するためのプロセスを示します。  
  
    1.  データベース メールがインスタンス上でまだ有効になっていない場合は設定します。 詳細については、「 [Configure Database Mail](../database-mail/configure-database-mail.md)」を参照してください。  
  
    2.  データベース メールを使用するように SQL Server エージェント通知を構成します。 詳細については、「 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)」を参照してください。  
  
    3.  **電子メール通知を有効にして、バックアップ エラーおよび警告を受け取る:** クエリ ウィンドウから、次の Transact-SQL ステートメントを実行します。  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email1;email2>'  
  
        ```  
  
         詳細についてと完全なサンプル スクリプトを参照してください。[モニター SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)します。  
  
8.  **Microsoft Azure ストレージ アカウントでバックアップ ファイルを表示する:** SQL Server Management Studio または Azure 管理ポータルから、ストレージ アカウントに接続します。 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を使用するように構成したデータベースをホストする SQL Server インスタンスのコンテナーが表示されます。 また、データベースに対して [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を有効にしてから 15 分以内のデータベースとログ バックアップも表示される場合があります。  
  
9. **正常性状態を監視する:**  前の手順で構成した電子メール通知から監視するか、ログに記録されているイベントをアクティブに監視することができます。 イベントを表示するための Transact-SQL ステートメントのいくつかの例を示します。  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    -- to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 このセクションで説明した手順は、データベースで初めて [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] を構成するための特別な手順です。 同じシステム ストアド プロシージャを使用して既存の構成を変更する**smart_admin.sp_set_db_backup**新しい値を指定します。 詳細については、次を参照してください。 [SQL Server Managed Backup to Microsoft Azure - 保有期間とストレージ設定](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)します。  
  
### <a name="enable-includesssmartbackupincludesss-smartbackup-mdmd-for-the-instance-with-default-settings"></a>既定の設定を使用してインスタンスの [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を有効にする  
 このチュートリアルでは、有効にして構成する手順を説明します。[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]インスタンスについて、"MyInstance"\\します。 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] の正常性状態の監視を有効にするための手順も含まれています。  
  
 **アクセス許可:**  
  
-   メンバーシップが必要です**db_backupoperator**データベース ロール、 **ALTER ANY CREDENTIAL**アクセス許可、および`EXECUTE`に対する**sp_delete_backuphistory**ストアド プロシージャ。  
  
-   必要があります**選択**に対するアクセス許可、 **smart_admin.fn_get_current_xevent_settings**関数。  
  
-   必要があります`EXECUTE`に対するアクセス許可、 **smart_admin.sp_get_backup_diagnostics**ストアド プロシージャ。 さらに、`VIEW SERVER STATE` 権限も必要です (この権限を必要とする他のシステム オブジェクトを内部的に呼び出すため)。  


1.  **Microsoft Azure ストレージ アカウントの作成:** バックアップは、Microsoft Azure ストレージ サービスに格納されます。 アカウントを既に持っていない場合、Microsoft Azure ストレージ アカウントを作成する必要があります。
    - SQL Server 2014 では、これは、ブロックとは異なる追加 blob、ページ blob を使用します。 そのため、汎用アカウントと blob のアカウントではなくを作成する必要があります。 詳細については、次を参照してください。 [Azure ストレージ アカウントについて](http://azure.microsoft.com/documentation/articles/storage-create-storage-account/)します。
    - ストレージ アカウント名およびアクセス キーをメモしておきます。 ストレージ アカウント名およびアクセス キー情報は、SQL 資格情報の作成に使用します。 SQL 資格情報は、ストレージ アカウントへの認証に使用されます。  
  
2.  **SQL 資格情報の作成:** Id、およびストレージ アクセス キーをパスワードとしてストレージ アカウントの名前を使用して SQL 資格情報を作成します。  
  
3.  **SQL Server エージェント サービスが開始され、実行されていることを確認する:** SQL Server エージェントを開始します (現在実行されていない場合)。 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] でバックアップ操作を実行するには、SQL Server エージェントがインスタンスで実行されている必要があります。  バックアップ操作を定期的に実行できるように、SQL Server エージェントの自動的な実行を設定できます。  
  
4.  **保有期間を決定する:** バックアップ ファイルに必要な保有期間を決定します。 保有期間は日数で指定し、その範囲は 1 ～ 30 になります。 インスタンス レベルで既定値を使用して [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を有効にすると、その後作成されたすべての新しいデータベースに、設定が継承されます。 完全または一括ログ復旧モデルに設定されているデータベースのみがサポートされており、自動的に構成されます。 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を構成する必要がなければ、特定のデータベースの [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]をいつでも無効にすることができます。 また、データベース レベルで [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を構成することで、特定のデータベースの構成を変更することもできます。  
  
5.  **有効にして構成[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]:** SQL Server Management Studio を起動し、SQL Server のインスタンスに接続します。 クエリ ウィンドウからは、要件に合わせて、データベース名、SQL 資格情報、保有期間、および暗号化のオプションの値を変更した後、次のステートメントを実行します。  
  
     暗号化の証明書を作成する方法の詳細については、次を参照してください。、**バックアップ証明書を作成する**ステップ[Create an Encrypted Backup](create-an-encrypted-backup.md)します。  
  
    ```  
    Use msdb;  
    Go  
       EXEC smart_admin.sp_set_instance_backup  
                     @enable_backup=1  
                    ,@retention_days=30   
                    ,@credential_name='sqlbackuptoURL'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert';  
    GO  
  
    ```  
  
     これで、インスタンス上で [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]が有効になります。  
  
6.  次の Transact-SQL ステートメントを実行して、構成設定を確認します。  
  
    ```  
    Use msdb;  
    GO  
    SELECT * FROM smart_admin.fn_backup_instance_config ();  
  
    ```  
  
7.  インスタンス上に新しいデータベースを作成します。 次の Transact-SQL ステートメントを実行して、データベースの [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の構成設定を表示します。  
  
    ```  
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('NewDB')  
    ```  
  
     設定が表示され、データベースでのバックアップ操作の実行が開始されるまで最大 15 分かかる場合があります。  
  
8.  **正常性状態の通知を有効化し、構成する:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] には、注意を要するエラーまたは警告の電子メール通知を送信するためにエージェント ジョブを作成するストアド プロシージャがあります。  このような通知を受信するには、SQL Server エージェント ジョブを作成するストアド プロシージャの実行を有効にする必要があります。 次の手順では、電子メール通知を有効にして構成するためのプロセスを示します。  
  
    1.  データベース メールがインスタンス上でまだ有効になっていない場合は設定します。 詳細については、「 [Configure Database Mail](../database-mail/configure-database-mail.md)」を参照してください。  
  
    2.  データベース メールを使用するように SQL Server エージェント通知を構成します。 詳細については、「 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)」を参照してください。  
  
    3.  **電子メール通知を有効にして、バックアップ エラーおよび警告を受け取る:** クエリ ウィンドウから、次の Transact-SQL ステートメントを実行します。  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email address>'  
  
        ```  
  
         完全なサンプル スクリプトとを監視する方法の詳細については、次を参照してください。[モニター SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)します。  
  
9. **Microsoft Azure ストレージ アカウントでバックアップ ファイルを表示する:** SQL Server Management Studio または Azure 管理ポータルから、ストレージ アカウントに接続します。 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]を使用するように構成したデータベースをホストする SQL Server インスタンスのコンテナーが表示されます。 また、新しいデータベースを作成してから 15 分以内のデータベースとログ バックアップも表示される場合があります。  
  
10. **正常性状態を監視する:**  前の手順で構成した電子メール通知から監視するか、ログに記録されているイベントをアクティブに監視することができます。 イベントを表示するための Transact-SQL ステートメントのいくつかの例を示します。  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    --  to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の既定の設定は、明示的にデータベース レベルで設定を構成することで、特定のデータベースに対してオーバーライドすることができます。 また、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] サービスを一時停止および再開することもできます。 詳細については、次を参照してください[SQL Server Managed Backup to Microsoft Azure - リテンション期間とストレージの設定。](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)  
  
  
