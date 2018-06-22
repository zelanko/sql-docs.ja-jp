---
title: モニターの SQL Server Backup to Windows Azure の管理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cfb9e431-7d4c-457c-b090-6f2528b2f315
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 401b41399b7c62f7feeda6d83d2400dd4814d9d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077162"
---
# <a name="monitor-sql-server-managed-backup-to-windows-azure"></a>Windows Azure への SQL Server マネージ バックアップの監視
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]では、バックアップ プロセス中に問題やエラーを特定し、可能な限り修正措置によって解消するための方法が組み込まれています。  ただし、ユーザーの介入が必要になる場合もあります。 このトピックでは、バックアップの全体的な正常性状態を判定し、解決する必要があるエラーを特定するために使用できるツールについて説明します。  
  
## <a name="overview-of-includesssmartbackupincludesss-smartbackup-mdmd-built-in-debugging"></a>[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の組み込みデバッグの概要  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]は、スケジュールされたバックアップを定期的に確認して、失敗したバックアップのスケジュールを組み直します。 改ページ、データベースの復旧に影響するログ チェーンを識別するためには、定期的にストレージ アカウントをポーリングし、それに従って新しいバックアップをスケジュールします。 また、Windows Azure 調整ポリシーを考慮する共に、複数のデータベース バックアップを管理するためのメカニズムを保持しています。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]では、拡張イベントを使用してすべてのアクティビティを追跡します。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] エージェントで使用される拡張イベント チャネルには、管理、運用、分析、およびデバッグが含まれます。 管理カテゴリに分類されるイベントは、通常、エラーに関連しているため、ユーザーの介入を必要とし、既定で有効になっています。 分析イベントも既定で有効になっていますが、通常、ユーザーの介入を必要とするエラーには関連していません。 一般的に、運用イベントは情報イベントです。 たとえば、運用イベントには、バックアップのスケジュール、バックアップの正常な完了などがあります。デバッグは最も詳細なイベントで、問題を特定して必要に応じて修正するために [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]によって内部的に使用されます。  
  
### <a name="configure-monitoring-parameters-for-includesssmartbackupincludesss-smartbackup-mdmd"></a>[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の監視パラメーターの構成  
 **は smart_admin.sp_set_parameter**システム ストアド プロシージャでは、監視設定を指定することができます。 以下のセクションでは、拡張イベントの有効化、およびエラーと警告の電子メール通知の有効化の手順について説明します。  
  
 **Smart_admin.fn_get_parameter**関数を使用して、特定のパラメーターまたはすべての構成済みのパラメーターの現在の設定を取得することです。 パラメーターがまだ構成されていない場合は、この関数は何も値を返しません。  
  
1.  [!INCLUDE[ssDE](../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。 これにより、拡張イベントの現在の構成、および電子メール通知が返されます。  
  
```  
Use msdb  
Go  
SELECT * FROM smart_admin.fn_get_parameter (NULL)  
GO  
```  
  
 詳細については、次を参照してください[smart_admin.fn_get_parameter &#40;TRANSACT-SQL。&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)  
  
### <a name="extended-events-for-monitoring"></a>監視のための拡張イベント  
 既定では、管理、運用、および分析イベントが有効になっています。 問題を解決するために手動による介入が必要なエラーを特定する場合は、管理イベントが最も重大かつ有用です。 運用イベントおよびデバッグ イベントを有効にすることもできますが、これらのイベントは詳細で、フィルターの適用が必要になる可能性がある点に注意してください。 次の手順では、拡張イベントを使用してログに記録されたイベントを監視する方法について説明します。  
  
> [!IMPORTANT]  
>  SQL エンジンの拡張イベントとは異なり、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]では、拡張イベント セッションの概念がサポートされていません。 拡張イベントとの対話には、ツールとしてシステム ストアド プロシージャおよびシステム関数を使用します。 また、ログ ディレクトリから拡張イベント ログを表示することもできます。  
  
##### <a name="to-configure-and-view-extended-events"></a>拡張イベントを構成および表示するには  
  
1.  使用可能な拡張イベント チャネルとその現在の状態を表示するには、次のクエリを実行します。  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     このクエリの出力には、イベント名、イベントが構成可能かどうか、およびイベントが現在有効になっているかどうかが表示されます。  詳細については、次を参照してください。 [smart_admin.fn_get_current_xevent_settings &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql)です。  
  
2.  デバッグ イベントを有効にするには、次のクエリを実行します。  
  
    ```  
    --  to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
     ストアド プロシージャの詳細については、次を参照してください。[は smart_admin.sp_set_parameter &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql)です。  
  
3.  ログに記録されたイベントを表示するには、次のクエリを実行します。  
  
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
  
### <a name="aggregated-error-countshealth-status"></a>集計されたエラー数/正常性状態  
 **Smart_admin.fn_get_health_status**の正常性状態の監視に使用できるカテゴリごとに集計されたエラー数のテーブルを返す関数[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]です。 この関数は、このトピックの後半で説明する、システムで構成された電子メール通知メカニズムでも使用されます。   
このような集計されたカウントは、システム正常性の監視に使用できます。 たとえば、number_of_retention_loops 列が 30 分間 0 だった場合、保有期間の管理に長時間がかかる可能性や保有期間の管理が正常に動作しない可能性があります。 エラー列が 0 以外の場合は問題を示す可能性があるため、拡張イベント ログで問題がないかどうかをチェックする必要があります。 代わりに、呼び出す**smart_admin.sp_get_backup_diagnostics**ストアド プロシージャをエラーの詳細を検索します。  
  
### <a name="using-agent-notification-for-assessing-backup-status-and-health"></a>バックアップ状態と正常性の評価にエージェント通知を使用する  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]には、SQL Server ポリシー ベースの管理ポリシーに基づく通知メカニズムが含まれています。  
  
 **前提条件:**  
  
-   この機能を使用するには、データベース メールが必要です。 詳細については、SQL Server のインスタンスのデータベース メールを有効にする方法についてを参照してください。 [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md)です。  
  
-   SQL Server エージェントの警告システムのプロパティは、データベース メールを使用するように設定する必要があります。  
  
 **通知のアーキテクチャ:**  
  
-   **ポリシー ベースの管理:** バックアップの正常性を監視する 2 つのポリシーが設定されている: **Smart Admin システム正常性ポリシー**、および**Smart Admin ユーザー操作ヘルス ポリシー**です。 Smart Admin システム正常性ポリシーは、重大なエラー (SQL 資格情報が存在しない、無効な SQL 資格情報、接続エラーなど) を評価して、システムの正常性を報告します。 これらは、通常、根本的な問題を修正するために手動による操作を必要とします。 Smart Admin ユーザー操作正常性ポリシーは、バックアップの破損などの警告を評価します。  これらは、操作を必要とせず、単なる警告だけの場合もあります。 このような問題は [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] エージェントによって自動的に対処されることが予想されます。  
  
-   **SQL Server エージェント**ジョブ: 次の 3 つのジョブ ステップを含む SQL Server エージェント ジョブを使用して、通知を実行します。 最初のジョブ ステップでは、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]がデータベースまたはインスタンスに対して構成されているかどうかが検出されます。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]が有効であり構成済みであることが検出されると、2 番目のステップが実行されます。これにより、SQL Server ポリシー ベースの管理ポリシーを評価して正常性状態を判断する PowerShell コマンドレットが実行されます。 エラーまたは警告が検出されると失敗になり、これによって 3 番目の手順が開始されます。3 番目の手順では、エラー/警告レポートが含まれた電子メール通知が送信されます。  ただし、この SQL Server エージェント ジョブは、既定では有効になっていません。 電子メール通知ジョブを有効にするを使用して、 **smart_admin.sp_set_backup_parameter**システム ストアド プロシージャです。  手順については、次で詳しく説明します。  
  
##### <a name="enabling-email-notification"></a>電子メール通知を有効にする  
  
1.  データベース メールが構成されていない場合に記載の手順を使用して[Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md)です。  
  
2.  SQL Server 警告システム用のメール システムとしてデータベース: を右クリックして**SQL Server エージェント**を選択**警告システム**、確認、**メール プロファイルを有効にする**ボックス、選択**データベース メール**として、**メール システム**、以前に作成したメール プロファイルを選択します。  
  
3.  クエリ ウィンドウで次のクエリを実行し、通知の送信先となる電子メール アドレスを指定します。  
  
    ```  
    Use msdb  
    Go  
    EXEC smart_admin.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'  
  
    ```  
  
     これにより、SQL Server エージェント ジョブが作成されます。このジョブは、正常性状態を収集し、バックアップでエラーまたは問題が発生しているときに通知を送信するために使用されます。  
  
 データベース メールを有効にして、SQL Server エージェント ジョブによる電子メール通知を設定するサンプル スクリプトを次に示します。  
  
```  
-- Prereq: Make sure that SQL Server service runs in a service account that has  
--  access to SMTP Server   
-- set SQL Server service account as domain account   
  
EXEC sp_configure 'show advanced', 1  
RECONFIGURE  
GO  
  
-- Enable DBMail  
EXEC sp_configure 'Database Mail XPs',1  
GO  
RECONFIGURE  
GO  
  
-- Configure DBMail  
DECLARE @emailid NVARCHAR(255)  
-- Note: change this email to your own email id  
SET @emailid = N'emailalias@mycompany.com'  
  
DECLARE @smtpserver NVARCHAR(255)  
SET @smtpserver = N'smtphost.domainname.com'  
  
DECLARE @mailprofile NVARCHAR(255)  
SET @mailprofile = N'my_profile'  
  
EXEC msdb.dbo.sysmail_add_account_sp @account_name=N'myaccount',  
                @email_address = @emailid,  
                @replyto_address = @emailid,  
                @mailserver_name = @smtpserver,  
                @use_default_credentials = 1  
  
EXEC msdb.dbo.sysmail_add_profile_sp @profile_name=@mailprofile  
EXEC msdb.dbo.sysmail_add_profileaccount_sp @profile_name=@mailprofile, @account_name=N'myaccount', @sequence_number=1  
  
-- Set SQL Agent to use DBMail profile  
EXEC msdb.dbo.sp_set_sqlagent_properties @databasemail_profile = @mailprofile  
  
-- Configure Notifications   
EXEC msdb.smart_admin.sp_set_parameter  
@parameter_name = 'SSMBackup2WANotificationEmailIds',  
@parameter_value = @emailid  
  
-- To test is you are receiving notifications  
-- delete few backup files from your storage container, Wait for 15 minutes & see if you get any email notification  
  
```  
  
### <a name="using-powershell-to-setup-custom-health-monitoring"></a>PowerShell を使用してカスタムの正常性状態の監視を設定する  
 **Test-sqlsmartadmin**コマンドレットは、カスタムの正常性の監視を作成するために使用できます。 たとえば、前のセクションで説明した通知オプションは、インスタンス レベルで構成できます。  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を使用するよう構成された SQL Server インスタンスが複数ある場合は、PowerShell コマンドレットを使用して、すべてのインスタンスのバックアップの状態と正常性を収集するためのスクリプトを作成できます。  
  
 **Test-sqlsmartadmin**コマンドレットは、SQL Server ポリシー ベースの管理ポリシーによって返された警告とエラーを評価し、ロール アップされたステータスを報告します。  既定では、このコマンドレットはシステム ポリシーを使用します。 カスタム ポリシーを含めるには、`–AllowUserPolicies` パラメーターを使用します。  
  
 システム ポリシーと作成されたユーザー ポリシーに基づいてエラーと警告のレポートを返す PowerShell のサンプル スクリプトを次に示します。  
  
```  
$policyResults = get-sqlsmartadmin | test-sqlsmartadmin -AllowUserPolicies  
$policyResults.PolicyEvaluationDetails | select Name, Category, Expression, Result, Exception | fl  
  
```  
  
 次のスクリプトでは、既定のインスタンスのエラーと警告の詳細なレポートが返されます。  
  
```  
PS C:\>PS SQLSERVER:\SQL\COMPUTER\DEFAULT> (get-sqlsmartadmin ).EnumHealthStatus()  
```  
  
### <a name="objects-in-msdb-database"></a>MSDB データベース内のオブジェクト  
 機能を実装するためにインストールされているオブジェクトがあります。 これらのオブジェクトは内部使用のために予約されています。 ただし、バックアップの状態を監視する際に役立つ smart_backup_files というシステム テーブルが 1 つあります。 バックアップ、データベースの型と同様に監視に関連するこのテーブルに格納されている情報の大部分が名、最初と最後の lsn、バックアップの有効期限の日付は、システム関数を通じて公開される[smart_admin.fn_available_backups &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql). ただし、この関数を使用して、バックアップ ファイルの状態を示す smart_backup_files テーブルの状態列を利用することはできません。 状態などの一部の情報は、次に示すサンプル クエリを使用してシステム テーブルから取得できます。  
  
```  
USE msdb  
GO  
SELECT  
 database_name AS [Database Name]  
,backup_path AS [Backup Destination and File]  
,[Backup Type] =  
CASE backup_type  
WHEN 1 THEN 'FULL'  
WHEN 2 THEN 'LOG'  
END  
,[Backup Status] =  
CASE [status]  
WHEN 'A' THEN 'Available'  
WHEN 'B' THEN 'Copy In Progress'  
WHEN 'C' THEN 'Corrupted'  
WHEN 'D' THEN 'Deleted'  
WHEN 'F' THEN 'Copy Failed'  
WHEN 'U' THEN 'Unknown'  
END  
,first_lsn AS [First LSN]  
,last_lsn AS [Last LSN]  
,backup_start_date AS [Backup Start Time]  
,backup_finish_date AS [Backup Completion Time]  
,expiration_date AS [Backup Expiry Date/Time]  
FROM  
smart_backup_files;  
  
```  
  
 返される各種状態の詳細を以下に示します。  
  
-   **利用可能 - a:** これは、通常のバックアップ ファイル。 バックアップが完了し、Windows Azure ストレージで利用できることが確認されました。  
  
-   **進行中のコピー-b:** この状態は、可用性グループ データベース専用にします。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]は、バックアップ ログ チェーンの中断を検出すると、バックアップ チェーンの中断の原因になったと考えられるバックアップの特定をまず試みます。 バックアップ ファイルが見つかると、Windows Azure ストレージにファイルがコピーされます。 コピー プロセスの実行中にこの状態が表示されます。  
  
-   **失敗 – f: をコピー**と似ています Copy In Progress にこれは、可用性グループのデータベースを特定できません。 コピー プロセスが失敗した場合、状態は F としてマークされます。  
  
-   **破損しています – c:** 場合[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]はも複数回試行後 RESTORE HEADER_ONLY コマンドを実行することによって、記憶域内のバックアップ ファイルを確認できません。 は、マークこのファイルが破損しているとします。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]は、破損したファイルによってバックアップ チェーンが中断されないように、バックアップをスケジュールします。  
  
-   **削除する – d:** Windows Azure ストレージに対応するファイルが見つかりません。 ファイルの削除によってバックアップ チェーンが中断された場合、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]はバックアップをスケジュールします。  
  
-   **不明な – u:** をこの状態が示される[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]されていないファイルの存在と Windows Azure ストレージでは、そのプロパティを確認できません。 プロセスが次回実行されたときに (約 15 分間隔)、この状態が更新されます。  
  
  
