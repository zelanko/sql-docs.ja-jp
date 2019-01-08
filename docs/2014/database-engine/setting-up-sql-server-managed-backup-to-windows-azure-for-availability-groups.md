---
title: 可用性グループの SQL Server Managed Backup to Windows Azure の設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 0c4553cd-d8e4-4691-963a-4e414cc0f1ba
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6a67b2331959dbc3087f6282be05de90b42443c5
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52416833"
---
# <a name="setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups"></a>可用性グループに対する Windows Azure への SQL Server マネージド バックアップの設定
  このトピックは、AlwaysOn 可用性グループに参加しているデータベースの [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の構成に関するチュートリアルです。  
  
## <a name="availability-group-configurations"></a>可用性グループの構成  
 レプリカがいずれも内部設置型として構成されているか、全体が Windows Azure 上で構成されているか、または内部設置型と 1 つ以上の Windows Azure 仮想マシンの間のハイブリッド実装であるかにかかわりなく、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] は可用性グループ データベースでサポートされています。 ただし、1 つ以上の実装に関して、次のことを考慮する必要が生じる可能性があります。  
  
-   ログ バックアップ頻度: ログ バックアップ頻度に応じて、時間とログの両方が増加します。 たとえば、2 時間という期間で使用されるログ領域が 5 MB に達しない場合は、2 時間ごとにログ バックアップを作成するとします。 この方針を、内部設置型、クラウド、またはハイブリッドというすべての実装に適用します。  
  
-   ネットワーク帯域幅: これは、レプリカのどこ物理的に異なる場所のようなハイブリッド クラウド、またはクラウドのみの構成で別の Windows Azure リージョン間での実装に適用されます。 ネットワーク帯域幅は、セカンダリの待機時間に影響する可能性があります。セカンダリが同期レプリケーションに設定されている場合は、プライマリ ログの増加が引き起こされる可能性があります。 セカンダリ レプリカが同期レプリケーションに設定されている場合は、ネットワーク待機時間が原因でセカンダリは同期を維持できない可能性があり、その結果、セカンダリ レプリカへのフェールオーバー イベントが発生したときにデータが失われる可能性があります。  
  
### <a name="configuring-includesssmartbackupincludesss-smartbackup-mdmd-for-availability-databases"></a>可用性データベースに対する [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の構成  
 **アクセス許可:**  
  
-   メンバーシップが必要です**db_backupoperator**データベース ロール、 **ALTER ANY CREDENTIAL**アクセス許可、および`EXECUTE`に対する**sp_delete_backuphistory**ストアド プロシージャ。  
  
-   必要があります**選択**に対するアクセス許可、 **smart_admin.fn_get_current_xevent_settings**関数。  
  
-   必要があります`EXECUTE`に対するアクセス許可、 **smart_admin.sp_get_backup_diagnostics**ストアド プロシージャ。 さらに、`VIEW SERVER STATE` 権限も必要です (この権限を必要とする他のシステム オブジェクトを内部的に呼び出すため)。  
  
-   必要があります`EXECUTE`に対するアクセス許可、`smart_admin.sp_set_instance_backup`と`smart_admin.sp_backup_master_switch`ストアド プロシージャ。  
  
 次に、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]で AlwaysOn 可用性グループを設定する基本的な手順を説明します。 詳細手順のチュートリアルについては、このトピックの後半で説明します。  
  
1.  可用性グループを作成したら、優先されるバックアップ レプリカを構成します。 可用性グループに対するこの設定は、バックアップに使用するレプリカを決定するために [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]でも使用されます。 バックアップの設定を設定する方法についてステップ バイ ステップ手順については、次を参照してください。[可用性レプリカでバックアップの構成&#40;SQL Server&#41;](availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)します。  新しい AlwaysOn 可用性グループを作成する場合は、次を参照してください。 [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](availability-groups/windows/getting-started-with-always-on-availability-groups-sql-server.md)します。  
  
2.  セカンダリ レプリカへの読み取り専用接続アクセスを構成します。 読み取り専用アクセスを構成する方法についてステップ バイ ステップの手順を参照してください[可用性レプリカの読み取り専用アクセスを構成する&#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
3.  バックアップ レプリカを指定します。 優先されるバックアップ レプリカの設定は、バックアップのスケジュール設定に使用するデータベースを決定するために [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]で使用されます。  現在のレプリカが優先されるバックアップ レプリカであるかどうかを調べるには、 [sys.fn_hadr_backup_is_preferred_replica &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)関数。  
  
4.  各レプリカで[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を使用して、データベースの構成、**スマート admin.sp_set_db_backup**ストアド プロシージャ。  
  
     **[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] フェールオーバー後の動作:** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]は引き続き動作し、フェールオーバー後にバックアップ コピーと回復性を維持します。 フェールオーバー後に特別な操作は必要ありません。  
  
#### <a name="considerations-and-requirements"></a>注意点と要件:  
 AlwaysOn 可用性グループに参加しているデータベースに対して [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を構成する場合は、特定の注意点と要件があります。 考慮事項と要件の一覧を次に示します。  
  
-   [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の構成設定は、同じ可用性グループに参加している [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のすべてのノード上にあるすべてのデータベースに対して同じである必要があります。 これを実現するには、データベース レベルでプライマリとすべてのレプリカに対して同じ [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]構成を設定するか、可用性グループに参加しているすべてのノードで同じ既定の [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]設定を使用します。 データベース レベルで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を設定することをお勧めします。データベース レベルで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を構成すると、データベースに対する設定を分離でき、既定の設定に対する変更は、インスタンス上の他のデータベースすべてに反映されます。  
  
-   バックアップ レプリカを指定します。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]では、優先されるバックアップ レプリカの設定がバックアップのスケジュール設定に使用されます。 現在のレプリカが優先されるバックアップ レプリカであるかどうかを調べるには、 [sys.fn_hadr_backup_is_preferred_replica &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)関数。  
  
-   優先されるレプリカとしてセカンダリ レプリカが構成されている場合は、少なくとも読み取り専用接続アクセスを持つように構成する必要があります。 セカンダリ データベースへの接続アクセスがない可用性グループはサポートされません。  詳細については、「 [可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)が存在する必要があります。  
  
-   可用性グループの構成後に [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を構成すると、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]は、構成に基づいて既存のバックアップをコピーし、それをストレージ コンテナーに格納することを試みます。  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]は、既存のバックアップが見つからない場合や既存のバックアップにアクセスできない場合に、データベースの完全バックアップをスケジュールします。 この処理は、特に、可用性グループのデータベースのバックアップ操作を最適化するために行われます。  
  
-   新しい可用性データベースを作成して、データベースにインスタンス レベルの設定を適用する予定がない場合は、インスタンス レベルの設定を無効にすることを検討したい場合があります。  
  
-   暗号化を使用する場合は、すべてのレプリカで同じ証明書を使用します。 この結果、フェールオーバー イベントが発生した場合や、別のレプリカへの復元を行う場合に、継続的で途切れることのないバックアップ操作が容易になります。  
  
#### <a name="enable-and-configure-includesssmartbackupincludesss-smartbackup-mdmd-for-an-availability-database"></a>可用性データベースに対する [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の有効化と構成  
 このチュートリアルでは、有効にして構成する手順を説明します。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Node1 と Node2 コンピューター上のデータベース (AGTestDB)、続いて監視を有効にする手順、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]正常性状態。  
  
1.  **Windows Azure ストレージ アカウントを作成します。** バックアップは、Microsoft Azure BLOB ストレージ サービスに格納されます。 Windows Azure ストレージ アカウントを持っていない場合は、最初にそのアカウントを作成する必要があります。 詳細については、次を参照してください。 [Windows Azure ストレージ アカウントを作成する](http://www.windowsazure.com/manage/services/storage/how-to-create-a-storage-account/)します。 ストレージ アカウントの名前、アクセス キー、および URL をメモしておきます。 ストレージ アカウント名およびアクセス キー情報は、SQL 資格情報の作成に使用します。 SQL 資格情報は、バックアップ操作中にストレージ アカウントへの認証を行うために [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]によって使用されます。  
  
2.  **SQL 資格情報を作成します。** Id、およびストレージ アクセス キーをパスワードとしてストレージ アカウントの名前を使用して SQL 資格情報を作成します。  
  
3.  **SQL Server エージェント サービスが開始され実行されていることを確認します。** 現在実行されていない場合は、SQL Server エージェントを開始します。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] でバックアップ操作を実行するには、SQL Server エージェントがインスタンスで実行されている必要があります。  バックアップ操作を定期的に実行できるように、SQL エージェントの自動的な実行を設定できます。  
  
4.  **保有期間を決定します。** バックアップ ファイルに必要な保有期間を決定します。 保有期間は日数で指定し、その範囲は 1 ～ 30 になります。 保有期間は、データベースの回復性の期間を決定します。  
  
5.  **バックアップ中の暗号化を使用する証明書または非対称キーを作成します。** Node1 で、最初のノードで、証明書を作成しを使用してファイルにエクスポートして[BACKUP CERTIFICATE &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql). Node 2 で、Node 1 からエクスポートしたファイルを使用して証明書を作成します。 ファイルから証明書を作成する方法の詳細については、例を参照してください。[証明書の作成&#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)します。  
  
6.  **有効にして構成[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]Node1 で agtestdb に対しての。** SQL Server Management Studio を起動し、可用性データベースがインストールされている Node1 上のインスタンスに接続します。 要件に合わせて、データベース名、ストレージ URL、SQL 資格情報、および保有期間の値を変更した後、クエリ ウィンドウから次のステートメントを実行します。  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='AGTestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     暗号化の証明書を作成する方法の詳細については、次を参照してください。、**バックアップ証明書を作成する**ステップ[Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md)します。  
  
7.  **有効にして構成[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]Node2 で agtestdb に対しての。** SQL Server Management Studio を起動し、可用性データベースがインストールされている Node2 上のインスタンスに接続します。 要件に合わせて、データベース名、ストレージ URL、SQL 資格情報、および保有期間の値を変更した後、クエリ ウィンドウから次のステートメントを実行します。  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='AGTestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] は、指定したデータベースで有効になります。 データベースでのバックアップ操作の実行が開始されるまで最大 15 分かかる場合があります。 バックアップは、優先されるバックアップ レプリカに対して実行されます。  
  
8.  **拡張イベントの既定の構成を確認します。** レプリカで次の TRANSACT-SQL ステートメントを実行して拡張イベントの構成を確認[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]はバックアップのスケジュールを使用しています。 これは、通常、データベースが属している可用性グループの優先されるバックアップ レプリカの設定です。  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     管理、運用、および分析のチャネル イベントは既定で有効になっていて、無効にできないことに注意してください。 手動の介入を必要とするイベントを監視するには、これで十分です。  デバッグ イベントを有効にすることはできますが、これらのチャネルには、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]が問題の検出および解決に使用する情報イベントとデバッグ イベントが含まれています。 詳細については、次を参照してください。[モニター SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)します。  
  
9. **正常性状態の通知を有効化し、構成する:** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] には、注意を要するエラーまたは警告の電子メール通知を送信するためにエージェント ジョブを作成するストアド プロシージャがあります。  このような通知を受信するには、SQL Server エージェント ジョブを作成するストアド プロシージャの実行を有効にする必要があります。 次の手順では、電子メール通知を有効にして構成するためのプロセスを示します。  
  
    1.  データベース メールがインスタンス上でまだ有効になっていない場合は設定します。 詳細については、「 [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md)」を参照してください。  
  
    2.  データベース メールを使用するように SQL Server エージェント通知を構成します。 詳細については、「 [Configure SQL Server Agent Mail to Use Database Mail](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)」を参照してください。  
  
    3.  **バックアップ エラーおよび警告を受信する電子メール通知を有効にします。** クエリ ウィンドウから、次の Transact-SQL ステートメントを実行します。  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email>'  
  
        ```  
  
         詳細と完全なサンプル スクリプトについてを参照してください。[モニター SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)します。  
  
10. **Windows Azure ストレージ アカウントでバックアップ ファイルを表示します。** SQL Server Management Studio または Azure 管理ポータルから、ストレージ アカウントに接続します。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を使用するように構成したデータベースをホストする SQL Server インスタンスのコンテナーが表示されます。 また、データベースに対して [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を有効にしてから 15 分以内のデータベースとログ バックアップも表示される場合があります。  
  
11. **正常性状態を監視するには。** 以前は、構成した電子メール通知から監視または記録されたイベントを積極的に監視できます。 イベントを表示するための Transact-SQL ステートメントのいくつかの例を示します。  
  
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
    event varchar (512),  
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
  
 このセクションで説明した手順は、データベースで初めて [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を構成するための特別な手順です。 同じシステム ストアド プロシージャを使用して既存の構成を変更する**smart_admin.sp_set_db_backup**新しい値を指定します。 詳細については、次を参照してください。 [SQL Server Managed Backup to Windows Azure - 保有期間とストレージ設定](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)します。  
  
### <a name="considerations-when-removing-a-database-from-alwayson-availability-group-configuration"></a>AlwaysOn 可用性グループの構成からデータベースを削除する際の注意点  
 使用したバックアップの実行をお勧めデータベースが AlwaysOn 可用性グループの構成から削除されますが、スタンドアロンのデータベース場合[smart_admin.sp_backup_on_demand &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql)します。 データベースのバックアップをこのように作成すると、新しいバックアップ チェーンが確立され、データベースが可用性グループに含まれていたときにバックアップが格納された可用性コンテナーではなく、インスタンス固有のコンテナーにファイルが配置されます。  
  
> [!WARNING]  
>  このシナリオのデータベースについては、可用性グループの状態が変更される前のバックアップからの復旧性は保証されません。  
  
  
