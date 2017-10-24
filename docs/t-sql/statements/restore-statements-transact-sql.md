---
title: "RESTORE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RESTORE DATABASE
- RESTORE_TSQL
- RESTORE_DATABASE_TSQL
- RESTORE
- RESTORE_LOG_TSQL
- RESTORE LOG
dev_langs:
- TSQL
helpviewer_keywords:
- RESTORE DATABASE, see RESTORE statement
- full backups [SQL Server]
- RECOVERY option
- database snapshots [SQL Server], reverting to
- STOPAT syntax
- differential backups, RESTORE statement
- point in time recovery [SQL Server]
- restoring [SQL Server]
- NORECOVERY option
- online restores [SQL Server], RESTORE statement
- moving databases
- RESTORE statement, syntax
- cross-platform restores
- restoring databases [SQL Server], options
- RESTORE statement
- snapshots [SQL Server database snapshots], reverting to
- reverting database snapshots
- transaction log backups [SQL Server], RESTORE statement
- RESTORE LOG, see RESTORE statement
ms.assetid: 877ecd57-3f2e-4237-890a-08f16e944ef1
caps.latest.revision: 248
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: e233de35336d5246c439c5dfb7b934cd2469b92c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="restore-statements-transact-sql"></a>RESTORE ステートメント (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  BACKUP コマンドで作成したバックアップを復元します。 このコマンドを使用すると、次の復元シナリオを実行できます。  
  
-   完全データベース バックアップからデータベース全体を復元する (完全復元)。  
  
-   データベースの一部を復元する (部分復元)。  
  
-   特定のファイルまたはファイル グループをデータベースに復元する (ファイル復元)。  
  
-   特定のページをデータベースに復元する (ページ復元)。  
  
-   トランザクション ログをデータベースに復元する (トランザクション ログ復元)。  
  
-   データベース スナップショットでキャプチャされた時点にデータベースを戻す。  
  
 詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]復元シナリオを参照してください[復元と復旧の概要 & #40 です。SQL Server & #41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md).  引数の説明の詳細については、次を参照してください。 [RESTORE の引数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-statements-arguments-transact-sql.md).   別のインスタンスからデータベースを復元するときは、「 [データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 (SQL Server)](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)」の情報を考慮してください。
  
> **注:** 、Windows Azure Blob ストレージ サービスからの復元に関する詳細については、次を参照してください。 [SQL Server のバックアップと Microsoft Azure Blob ストレージ サービスによる復元](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
--To Restore an Entire Database from a Full database backup (a Complete Restore):  
RESTORE DATABASE { database_name | @database_name_var }   
 [ FROM <backup_device> [ ,...n ] ]  
 [ WITH   
   {  
    [ RECOVERY | NORECOVERY | STANDBY =   
        {standby_file_name | @standby_file_name_var }   
       ]  
   | ,  <general_WITH_options> [ ,...n ]  
   | , <replication_WITH_option>  
   | , <change_data_capture_WITH_option>  
   | , <FILESTREAM_WITH_option>  
   | , <service_broker_WITH options>   
   | , \<point_in_time_WITH_options—RESTORE_DATABASE>   
   } [ ,...n ]  
 ]  
[;]  
  
--To perform the first step of the initial restore sequence  
-- of a piecemeal restore:  
RESTORE DATABASE { database_name | @database_name_var }   
   <files_or_filegroups> [ ,...n ]  
 [ FROM <backup_device> [ ,...n ] ]   
   WITH   
      PARTIAL, NORECOVERY   
      [  , <general_WITH_options> [ ,...n ]   
       | , \<point_in_time_WITH_options—RESTORE_DATABASE>   
      ] [ ,...n ]   
[;]  
  
--To Restore Specific Files or Filegroups:   
RESTORE DATABASE { database_name | @database_name_var }   
   <file_or_filegroup> [ ,...n ]  
 [ FROM <backup_device> [ ,...n ] ]   
   WITH   
   {  
      [ RECOVERY | NORECOVERY ]  
      [ , <general_WITH_options> [ ,...n ] ]  
   } [ ,...n ]   
[;]  
  
--To Restore Specific Pages:   
RESTORE DATABASE { database_name | @database_name_var }   
   PAGE = 'file:page [ ,...n ]'   
 [ , <file_or_filegroups> ] [ ,...n ]  
 [ FROM <backup_device> [ ,...n ] ]   
   WITH   
       NORECOVERY     
      [ , <general_WITH_options> [ ,...n ] ]  
[;]  
  
--To Restore a Transaction Log:  
RESTORE LOG { database_name | @database_name_var }   
 [ <file_or_filegroup_or_pages> [ ,...n ] ]  
 [ FROM <backup_device> [ ,...n ] ]   
 [ WITH   
   {  
     [ RECOVERY | NORECOVERY | STANDBY =   
        {standby_file_name | @standby_file_name_var }   
       ]  
    | ,  <general_WITH_options> [ ,...n ]  
    | , <replication_WITH_option>  
    | , \<point_in_time_WITH_options—RESTORE_LOG>   
   } [ ,...n ]  
 ]   
[;]  
  
--To Revert a Database to a Database Snapshot:     
RESTORE DATABASE { database_name | @database_name_var }   
FROM DATABASE_SNAPSHOT = database_snapshot_name   
  
<backup_device>::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
 | { DISK | TAPE | URL } = { 'physical_backup_device_name' |  
      @physical_backup_device_name_var }   
}   
Note: URL is the format used to specify the location and the file name for the Windows Azure Blob. Although Windows Azure storage is a service, the implementation is similar to disk and tape to allow for a consistent and seemless restore experince for all the three devices.  
<files_or_filegroups>::=   
{   
   FILE = { logical_file_name_in_backup | @logical_file_name_in_backup_var }   
 | FILEGROUP = { logical_filegroup_name | @logical_filegroup_name_var }   
 | READ_WRITE_FILEGROUPS  
}   
  
<general_WITH_options> [ ,...n ]::=   
--Restore Operation Options  
   MOVE 'logical_file_name_in_backup' TO 'operating_system_file_name'   
          [ ,...n ]   
 | REPLACE   
 | RESTART   
 | RESTRICTED_USER  | CREDENTIAL  
  
--Backup Set Options  
 | FILE = { backup_set_file_number | @backup_set_file_number }   
 | PASSWORD = { password | @password_variable }   
  
--Media Set Options  
 | MEDIANAME = { media_name | @media_name_variable }   
 | MEDIAPASSWORD = { mediapassword | @mediapassword_variable }   
 | BLOCKSIZE = { blocksize | @blocksize_variable }   
  
--Data Transfer Options  
 | BUFFERCOUNT = { buffercount | @buffercount_variable }   
 | MAXTRANSFERSIZE = { maxtransfersize | @maxtransfersize_variable }  
  
--Error Management Options  
 | { CHECKSUM | NO_CHECKSUM }   
 | { STOP_ON_ERROR | CONTINUE_AFTER_ERROR }   
  
--Monitoring Options  
 | STATS [ = percentage ]   
  
--Tape Options  
 | { REWIND | NOREWIND }   
 | { UNLOAD | NOUNLOAD }   
  
<replication_WITH_option>::=  
 | KEEP_REPLICATION   
  
<change_data_capture_WITH_option>::=  
 | KEEP_CDC  
  
<FILESTREAM_WITH_option>::=  
 | FILESTREAM ( DIRECTORY_NAME = directory_name )  
  
<service_broker_WITH_options>::=   
 | ENABLE_BROKER   
 | ERROR_BROKER_CONVERSATIONS   
 | NEW_BROKER  
  
\<point_in_time_WITH_options—RESTORE_DATABASE>::=   
 | {  
   STOPAT = { 'datetime'| @datetime_var }   
 | STOPATMARK = 'lsn:lsn_number'  
                 [ AFTER 'datetime']   
 | STOPBEFOREMARK = 'lsn:lsn_number'  
                 [ AFTER 'datetime']   
   }   
  
\<point_in_time_WITH_options—RESTORE_LOG>::=   
 | {  
   STOPAT = { 'datetime'| @datetime_var }   
 | STOPATMARK = { 'mark_name' | 'lsn:lsn_number' }  
                 [ AFTER 'datetime']   
 | STOPBEFOREMARK = { 'mark_name' | 'lsn:lsn_number' }  
                 [ AFTER 'datetime']   
   }  
  
```  
  
## <a name="arguments"></a>引数  
 引数の説明については、次を参照してください。 [RESTORE の引数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="about-restore-scenarios"></a>復元シナリオについて  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではさまざまな復元シナリオがサポートされています。  
  
-   データベースの全体復元  
  
     最初に完全データベース バックアップを行い、次に必要に応じて差分データベース バックアップ (およびログ バックアップ) の復元を行って、データベース全体を復元します。 詳細については、「[データベースの全体復元 &#40;単純復旧モデル&#41;](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)」または「[データベースの全体復元 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)」を参照してください。  
  
-   ファイル復元  
  
     マルチ ファイル グループ データベースのファイルまたはファイル グループを復元します。 単純復旧モデルでは、ファイルは読み取り専用のファイル グループに属している必要があります。 完全なファイル復元を行った後で、差分ファイル バックアップを復元できます。 詳細については、次を参照してください。[ファイルの復元 & #40 です。完全復旧モデル & #41;](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)と[ファイル復元 & #40;単純復旧モデル & #41;](../../relational-databases/backup-restore/file-restores-simple-recovery-model.md).  
  
-   ページ復元  
  
     個々のページを復元します。 ページ復元は、完全復旧モデルと一括ログ復旧モデルでのみ利用できます。 詳細については、「[ページ復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-pages-sql-server.md)」を参照してください。  
  
-   段階的な部分復元  
  
     プライマリ ファイル グループと、1 つ以上のセカンダリ ファイル グループの復元から始めて、データベースを段階的に復元します。 段階的な部分復元の最初の段階では、RESTORE DATABASE を PARTIAL オプションで実行し、このとき 1 つ以上のセカンダリ ファイル グループを指定します。 詳細については、「[段階的な部分復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)」を参照してください。  
  
-   復旧のみ  
  
     データベース内でデータの一貫性が保たれており、単にデータを使用可能にするだけの場合に行います。 詳細については、「[データを復元しないデータベースの復旧 &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md)」を参照してください。  
  
-   トランザクション ログの復元  
  
     完全復旧モデルまたは一括ログ復旧モデルで、目的の復旧ポイントに戻すには、ログ バックアップの復元が必要です。 ログ バックアップの復元の詳細については、次を参照してください。[トランザクション ログ バックアップの適用 & #40 です。SQL Server & #41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md).  
  
-   Always On 可用性グループの可用性データベースを準備します。  
  
     詳細については、「[可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)」を参照してください。  
  
-   データベース ミラーリングのためのミラー データベースの準備  
  
     詳細については、「 [ミラーリングのためのミラー データベースの準備 &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)を使用します。  
  
-   オンライン復元  
  
    > **注:**オンライン復元がの Enterprise edition でのみ許可されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
     オンライン復元がサポートされている場合、データベースがオンラインになっていると、ファイル復元とページ復元は自動的にオンライン復元になり、段階的な部分復元の最初の段階の後で行われるセカンダリ ファイル グループの復元もオンライン復元になります。  
  
    > **注:**オンライン復元を実行できる[遅延トランザクション](../../relational-databases/backup-restore/deferred-transactions-sql-server.md)です。  
  
     詳細については、次を参照してください。[オンライン復元 & #40 です。SQL Server & #41;](../../relational-databases/backup-restore/online-restore-sql-server.md).  
  
## <a name="additional-considerations-about-restore-options"></a>RESTORE のオプションに関するその他の注意点  
  
### <a name="discontinued-restore-keywords"></a>廃止された RESTORE キーワード  
 次のキーワードで廃止された[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]:  
  
|廃止されたキーワード|代替キーワード|代替キーワードの例|  
|--------------------------|------------------|------------------------------------|  
|LOAD|RESTORE|`RESTORE DATABASE`|  
|TRANSACTION|LOG|`RESTORE LOG`|  
|DBO_ONLY|RESTRICTED_USER|`RESTORE DATABASE ... WITH RESTRICTED_USER`|  
  
### <a name="restore-log"></a>RESTORE LOG  
 RESTORE LOG でファイル一覧を含めて、ロールフォワード中にファイルを作成することができます。 この機能は、データベースへファイルを追加するときに書き込まれたログ レコードが、ログ バックアップに含まれている場合に使用します。  
  
> **注:**完全または一括ログ復旧モデルを使用してデータベースをほとんどの場合必要がありますをバックアップするログの末尾、データベースを復元する前にします。 RESTORE DATABASE ステートメントに WITH REPLACE 句または WITH STOPAT 句が指定されていない場合、最初にログ末尾のバックアップを行わずに、データベースを復元しようとするとエラーが発生します。これらの句は、データのバックアップ終了後の時間またはトランザクションの指定が必要となる句です。 ログ末尾のバックアップの詳細については、「[ログ末尾のバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/tail-log-backups-sql-server.md)」を参照してください。  
  
### <a name="comparison-of-recovery-and-norecovery"></a>RECOVERY と NORECOVERY の比較  
 ロールバックは、RESTORE ステートメントの RECOVERY および NORECOVERY オプションで制御されます。  
  
-   NORECOVERY では、ロールバックを実行しないよう指定します。 こうすると、ロールフォワードしてそのままシーケンス内の次のステートメントを実行できます。  
  
     この場合、復元シーケンスでは他のバックアップを復元してそれらをロールフォワードできます。  
  
-   RECOVERY (既定) では、現在のバックアップのロールフォワードが完了した後ロールバックを実行するよう指定します。  
  
     データベースを復旧するには、復元されるデータのすべてのセットが必要です (、*ロール フォワード セット*) が、データベースと一致します。 ロール フォワード セットがロール フォワードされていない十分なデータベースと一致するようにして回復を指定して場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]エラーが発生します。  
  
## <a name="compatibility-support"></a>互換性サポート  
 バックアップ**マスター**、**モデル**と**msdb**の以前のバージョンを使用して作成された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で復元することはできません[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。  
  
> **注:**いいえ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の以前のバージョンに復元するバックアップ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バックアップが作成されているバージョンよりもします。  
  
 各バージョン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以前のバージョンと異なる既定パスを使用します。 そのため、以前のバージョンのバックアップが既定で保存されていた場所に作成されたデータベースを復元するには、MOVE オプションを使用する必要があります。 新しい既定パスの詳細については、次を参照してください。[既定と SQL Server のインスタンスをという名前のファイルの場所](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)です。  
  
 以前のバージョンのデータベースを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]に復元すると、データベースが自動的にアップグレードされます。 通常、データベースは直ちに使用可能になります。 ただし、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] データベースにフルテキスト インデックスがある場合、アップグレード プロセスでは、  **upgrade_option** サーバー プロパティの設定に応じて、インポート、リセット、または再構築が行われます。 アップグレード オプションがインポート (**upgrade_option** = 2) または再構築 (**upgrade_option** = 0) に設定されている場合、アップグレード中はフルテキスト インデックスを使用できなくなります。 インデックスを作成するデータ量によって、インポートには数時間、再構築には最大でその 10 倍の時間がかかることがあります。 また、アップグレード オプションがインポートに設定されており、フルテキスト カタログが使用できない場合は、関連付けられたフルテキスト インデックスが再構築されます。 **upgrade_option** サーバー プロパティの設定を変更するには、 [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)を使用します。  
  
 データベースが最初に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の新しいインスタンスにアタッチまたは復元されるとき、データベース マスター キー (サービス マスター キーにより暗号化されたもの) のコピーはまだサーバーに格納されていません。 **OPEN MASTER KEY** を使用して、データベース マスター キー (DMK) を暗号化解除する必要があります。 DMK の暗号化が解除されると、 **ALTER MASTER KEY REGENERATE** ステートメントを使用して、サービス マスター キー (SMK) で暗号化された DMK のコピーをサーバーに提供することにより、将来、自動的に暗号化解除することも可能となります。 データベースを以前のバージョンからアップグレードした場合、新しい AES アルゴリズムを使用するように DMK を再作成する必要があります。 DMK を再作成する方法については、「[ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md)」を参照してください。 DMK キーを再作成して AES にアップグレードするのに必要な時間は、DMK によって保護されているオブジェクトの数によって異なります。 DMK キーを再作成して AES にアップグレードする作業は、1 回限りで済み、今後のキー ローテーション方法には影響を与えません。  
  
## <a name="general-remarks"></a>全般的な解説  
 オフライン復元を実行しているときに、指定したデータベースが使用中の場合、RESTORE を実行してしばらくするとユーザーは強制的に切断されます。 プライマリ ファイル グループ以外のオンライン復元では、復元するファイル グループがオフラインにならなければ、データベースの使用を続けることができます。 指定したデータベース内のデータはすべて、復元されたデータに置き換えられます。  
  
 データベースの回復の詳細については、次を参照してください。[復元と復旧の概要 & #40 です。SQL Server & #41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md).  
  
 1 つのプラットフォームから別のプラットフォームへの復元操作は、異なる種類のプロセッサ間でも、オペレーティング システムでデータベースの照合順序がサポートされていれば実行できます。  
  
 エラーが発生した場合は RESTORE を再開できます。 また、エラーに関係なく RESTORE を続行することもできます。この場合は、復元可能なデータが復元されます (CONTINUE_AFTER_ERROR オプションを参照してください)。  
  
 RESTORE は、明示的または暗黙的なトランザクションでは使用できません。  
  
 復元、破損した**マスター**特別な手順を使用してデータベースを実行します。 詳細については、「[システム データベースのバックアップと復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)」を参照してください。  
  
 データベースを復元すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのプラン キャッシュが消去されます。 プラン キャッシュが消去されると、後続のすべての実行プランが再コンパイルされ、場合によっては、クエリ パフォーマンスが一時的に急激に低下します。 各キャッシュ ストアが消去、プラン キャッシュ内の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー ログには、次の情報メッセージが含まれています:"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]キャッシュ ストア フラッシュをいくつかのデータベースのため '%s' キャッシュ ストア (プラン キャッシュの一部) を %d 個検出が発生しましたメンテナンス操作または再構成操作"です。 このメッセージは、5 分以内にキャッシュがフラッシュされる限り、5 分間隔でログに記録されます。  
  
 可用性データベースを復元するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにデータベースを復元した後、そのデータベースを可用性グループに追加します。  
  
## <a name="interoperability"></a>相互運用性  
  
### <a name="database-settings-and-restoring"></a>データベースの設定と復元  
 復元を実行すると、ALTER DATABASE を使用して設定できるデータベース オプションの大半は、バックアップの終了時に有効となっていた値にリセットされます。  
  
 WITH RESTRICTED_USER オプションを使用すると、ユーザー アクセス オプションの設定の動作よりもこのオプションが優先されます。 ユーザー アクセス オプションの設定は、WITH RESTRICTED_USER オプションを含む RESTORE ステートメントの後で、常に設定されます。  
  
### <a name="restoring-an-encrypted-database"></a>暗号化されたデータベースの復元  
 暗号化されたデータベースを復元するには、データベースの暗号化に使用された証明書または非対称キーにアクセスできることが必要です。 証明書または非対称キーがないと、データベースは復元できません。 このため、バックアップが必要である間は、データベース暗号化キーの暗号化に使用する証明書を保持しておく必要があります。 詳細については、「 [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)」を参照してください。  
  
### <a name="restoring-a-database-enabled-for-vardecimal-storage"></a>vardecimal ストレージに対応したデータベースの復元  
 バックアップし、復元の正常に行う、 **vardecimal**ストレージ形式です。 詳細については**vardecimal**ストレージ形式を参照してください[sp_db_vardecimal_storage_format (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md).  
  
### <a name="restore-full-text-data"></a>フルテキスト データの復元  
 完全復元を実行すると、フルテキスト データは他のデータベース データと共に復元されます。 標準を使用して`RESTORE DATABASE database_name FROM backup_device`構文、フルテキスト ファイルは、データベース ファイルの復元の一部として復元されます。  
  
 RESTORE ステートメントでは、フルテキスト データに対し、代替位置への復元、差分復元、ファイルとファイル グループの復元、ファイルとファイル グループの差分復元を行うこともできます。 また、RESTORE ではデータベース データと同様にフルテキスト ファイルだけを復元することもできます。  
  
> **注:**からインポートされたフルテキスト カタログ[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]はデータベース ファイルとして扱われます。 これらの場合、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]は一時停止と再開、バックアップ操作中には必要なくする点を除いてにフルテキスト カタログをバックアップするための手順も、適用します。 詳細については、次を参照してください。[をバックアップおよび復元のフルテキスト カタログ](http://go.microsoft.com/fwlink/?LinkId=107381)です。  
  
## <a name="metadata"></a>メタデータ  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バックアップを追跡し、各サーバー インスタンスのアクティビティを復元するバックアップと復元の履歴テーブルが含まれます。 復元を実行すると、バックアップ履歴テーブルも変更されます。 これらのテーブルについては、次を参照してください。[バックアップ履歴とヘッダーの情報 & #40 です。SQL Server & #41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md).  
  
##  <a name="REPLACEoption"></a>REPLACE オプションによる影響  
 REPLACE は頻繁に使用すべきではありません。使用するのは十分に検討した後のみに限定してください。 通常、復元により、誤ってデータベースを別のデータベースで上書きしてしまうのを防ぐことができます。 RESTORE ステートメントで指定したデータベースが現在のサーバーに既に存在し、指定したデータベースのファミリ GUID がバックアップ セットに記録されているデータベースのファミリ GUID と異なる場合、そのデータベースは復元されません。 これは重要な保護機能です。  
  
 REPLACE オプションにより、通常は復元によって実行されるいくつかの重要な安全性チェックが無効になります。 無効になるチェックは次のとおりです。  
  
-   別のデータベースから取得したバックアップで既存のデータベースに復元することに対するチェック。  
  
     REPLACE オプションを使用すると、バックアップ セットに含まれているどのデータベースでも既存のデータベースを上書きできます。このことは、指定したデータベース名がバックアップ セットに記録されているデータベース名と異なる場合でも当てはまります。 これにより、誤ってデータベースを別のデータベースで上書きしてしまう可能性があります。  
  
-   ログ末尾のバックアップを行っておらず、STOPAT オプションを使用しない場合に、完全復旧モデルまたは一括ログ復旧モデルを使用してデータベースに復元することに対するチェック。  
  
     最近書き込まれたログをバックアップしていないので、REPLACE オプションを使用すると、コミットされた作業が失われる可能性があります。  
  
-   既存のファイルを上書きすることに対するチェック。  
  
     たとえば、間違った種類のファイル (.xls ファイルなど) や、別のデータベースによって使用されているオンラインになっていないファイルを誤って上書きしてしまう場合があります。 復元されたデータベースが完全であっても、既存のファイルが上書きされた場合はデータが失われている可能性があります。  
  
## <a name="redoing-a-restore"></a>復元の再実行  
 復元の結果を元に戻すことはできませんが、ファイル単位で最初からやり直して、データ コピーとロールフォワードの結果を取り消すことができます。 最初からやり直すには、目的のファイルを復元してもう一度ロールフォワードを実行します。 たとえば、間違って必要以上のログ バックアップを復元し、予定の停止ポイントを過ぎてしまった場合は、復元シーケンスを再開する必要があります。  
  
 復元シーケンスは途中で中断でき、影響があったファイルの内容全体を復元することで再開できます。  
  
## <a name="reverting-a-database-to-a-database-snapshot"></a>データベース スナップショットにデータベースを復帰させる  
 A*データベース操作を元に戻す*して時にソース データベース全体を受け取り (指定されたオプションを使用して、DATABASE_SNAPSHOT) ポイントからのデータとソース データベースの上書きは、データベース スナップショットの時間を戻すこと時点を指定したデータベース スナップショットで保持されています。 データベースを戻すスナップショットは、現時点で存在する唯一のスナップショットである必要があります。 その後、この操作ではログが再構成されます (したがって、後でこのデータベースをユーザー エラーの時点にロールフォワードすることはできません)。  
  
 失われるデータは、スナップショットの作成時点よりも後に行ったデータベースへの更新内容だけです。 この操作を行った後のデータベースのメタデータは、スナップショット作成時点のメタデータと同じになります。 ただし、スナップショットに戻すと、すべてのフルテキスト カタログが削除されます。  
  
 データベース スナップショットに戻す操作はメディアの復旧を目的としたものではありません。 標準的なバックアップ セットとは異なり、データベース スナップショットはデータベース ファイルの不完全なコピーです。 データベースまたはデータベース スナップショットが壊れた場合、スナップショットに戻すことはほぼ不可能です。 戻すことができても、データベースまたはデータベース スナップショットが壊れている場合は、問題が解決しない可能性が高くなります。  
  
### <a name="restrictions-on-reverting"></a>元に戻す操作の制限  
 元に戻す操作は、次の状況ではサポートされません。  
  
-   ソース データベースに読み取り専用のファイル グループまたは圧縮されたファイル グループがある。  
  
-   スナップショットの作成時にオンラインだったファイルがオフラインとなっている。  
  
-   現在、複数のデータベース スナップショットが存在する。  
  
 詳細については、次を参照してください。[データベース スナップショットにデータベースを元に戻す](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md)です。  
  
## <a name="security"></a>セキュリティ  
 バックアップ操作では、オプションで、メディア セットとバックアップ セットにそれぞれパスワードを設定できます。 メディア セットまたはバックアップ セットにパスワードが設定されている場合は、RESTORE ステートメントで正しいパスワードを指定する必要があります。 これらのパスワードが不正に復元操作を防ぐため、不正なメディアを使用するバックアップ セットの追加[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ツールです。 ただし、パスワードで保護されたメディアは、BACKUP ステートメントの形式オプションで上書きできます。  
  
> [!IMPORTANT]  
>  パスワードによる保護は強力なものではありません。 使用して、正しくない復元を防止するものでは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ツールを承認またはユーザーです。 その他の手段によるバックアップ データの読み取りやパスワードの置き換えを防ぐわけではありません。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]バックアップを保護するためのベスト プラクティスでは、安全な場所に、または十分なアクセス制御リスト (Acl) によって保護されているディスク ファイルへのバックアップ、バックアップ テープを保存します。 ACL は、バックアップを作成するディレクトリのルートに設定する必要があります。  
>   
>  SQL Server のバックアップと復元、Windows Azure Blob ストレージに固有の情報を参照してください。 [SQL Server Backup and Restore with Microsoft Azure Blob Storage Service](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)です。  
  
### <a name="permissions"></a>Permissions  
 復元するデータベースが存在しない場合、ユーザーは RESTORE を実行できる CREATE DATABASE 権限を使用する必要があります。 データベースが存在する場合、既定では、RESTORE 権限は **sysadmin** 固定サーバー ロールおよび **dbcreator** 固定サーバー ロールのメンバーと、データベースの所有者 (**dbo**) に与えられています (FROM DATABASE_SNAPSHOT オプションを使用する場合、データベースは常に存在します)。  
  
 RESTORE 権限は、サーバーでメンバーシップ情報を常に確認できるロールに与えられます。 固定データベース ロールのメンバーシップは、データベースがアクセス可能で破損していない場合にのみ確認することができますが、RESTORE の実行時にはデータベースがアクセス可能で損傷していないことが必ずしも保証されないため、 **db_owner** 固定データベース ロールのメンバーには RESTORE 権限は与えられません。  
  
##  <a name="examples"></a> 使用例  
 次の例ではすべて、データベース全体のバックアップが既に実行されていることが前提です。  
  
 RESTORE の例を次に示します。  
  
-   A. [データベース全体を復元します。](#restoring_full_db)  
  
-   B. [データベースの完全および差分バックアップを復元します。](#restoring_full_n_differential_db_backups)  
  
-   C. [RESTART 構文を使用してデータベースを復元します。](#restoring_db_using_RESTART)  
  
-   D. [データベースと移動のファイルを復元します。](#restoring_db_n_move_files)  
  
-   E. [バックアップと復元によるデータベースのコピー](#copying_db_using_bnr)  
  
-   F. [STOPAT を使って特定の時点の状態に復元する](#restoring_to_pit_using_STOPAT)  
  
-   G. [トランザクション ログにマークを復元します。](#restoring_transaction_log_to_mark)  
  
-   H. [TAPE 構文を使用して復元します。](#restoring_using_TAPE)  
  
-   I. [FILE および FILEGROUP 構文を使用して復元します。](#restoring_using_FILE_n_FG)  
  
-   J. [データベース スナップショットに戻す](#reverting_from_db_snapshot)  
  
-   K. [Microsoft Azure Blob ストレージ サービスからの復元](#Azure_Blob)  
  
> **注:**例についてに記載されている復元方法に関するトピックを参照してください。[復元と復旧の概要 & #40 です。SQL Server & #41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md).  
  
###  <a name="restoring_full_db"></a> A. データベース全体を復元する  
 次の例では、`AdventureWorksBackups` 論理バックアップ デバイスからデータベース バックアップ全体を復元します。 このデバイスの作成の例は、次を参照してください。[バックアップ デバイス](../../relational-databases/backup-restore/backup-devices-sql-server.md)です。  
  
```  
RESTORE DATABASE AdventureWorks2012   
   FROM AdventureWorks2012Backups;  
```  
  
> **注:**完全または一括ログ復旧モデルを使用してデータベースの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ほとんどの場合、データベースを復元する前に、ログの末尾をバックアップすることが必要です。 詳細については、「[ログ末尾のバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/tail-log-backups-sql-server.md)」を参照してください。  
  
 [& #91。上部の例 & #93;](#examples)  
  
###  <a name="restoring_full_n_differential_db_backups"></a> B. データベースの完全および差分バックアップの復元  
 次の例は、後から差分バックアップをデータベースの完全バックアップを復元、`Z:\SQLServerBackups\AdventureWorks2012.bak`バックアップ デバイスは、両方のバックアップが含まれています。 復元するデータベース全体のバックアップはデバイス上の 6 番目のバックアップ セット (`FILE = 6`) で、差分データベース バックアップはデバイス上の 9 番目のバックアップ セット (`FILE = 9`) です。 差分バックアップからの復元が終わると、データベースは完全に復元されたことになります。  
  
```  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'  
   WITH FILE = 6  
      NORECOVERY;  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'  
   WITH FILE = 9  
      RECOVERY;  
```  
  
 [& #91。上部の例 & #93;](#examples)  
  
###  <a name="restoring_db_using_RESTART"></a> C. RESTART 構文を使用してデータベースを復元する  
 次の例では、サーバーの電源異常による割り込みを受けた `RESTART` 操作を、`RESTORE` オプションで再起動します。  
  
```  
-- This database RESTORE halted prematurely due to power failure.  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorksBackups;  
-- Here is the RESTORE RESTART operation.  
RESTORE DATABASE AdventureWorks2012   
   FROM AdventureWorksBackups WITH RESTART;  
```  
  
 [& #91。上部の例 & #93;](#examples)  
  
###  <a name="restoring_db_n_move_files"></a> D. データベースを復元しファイルを移動する  
 次の例では、データベース全体とトランザクション ログを復元し、復元したデータベースを `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data` ディレクトリに移動します。  
  
```  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorksBackups  
   WITH NORECOVERY,   
      MOVE 'AdventureWorks2012_Data' TO   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\NewAdvWorks.mdf',   
      MOVE 'AdventureWorks2012_Log'   
TO 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\NewAdvWorks.ldf';  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorksBackups  
   WITH RECOVERY;  
```  
  
 [& #91。上部の例 & #93;](#examples)  
  
###  <a name="copying_db_using_bnr"></a> E. BACKUP および RESTORE を使用してデータベースのコピーを作成する  
 次の例では、`BACKUP` および `RESTORE` の両方のステートメントを使用して、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] のコピーを作成します。 `MOVE`ステートメントにより、指定された場所に復元するデータとログ ファイルです。 `RESTORE FILELISTONLY`数と復元するデータベース内のファイルの名前を決定するステートメントを使用します。 データベースの新しいコピーは、`TestDB` という名前になります。 詳細については、[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md) を参照してください。  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO AdventureWorksBackups ;  
  
RESTORE FILELISTONLY   
   FROM AdventureWorksBackups ;  
  
RESTORE DATABASE TestDB   
   FROM AdventureWorksBackups   
   WITH MOVE 'AdventureWorks2012_Data' TO 'C:\MySQLServer\testdb.mdf',  
   MOVE 'AdventureWorks2012_Log' TO 'C:\MySQLServer\testdb.ldf';  
GO  
```  
  
 [& #91。上部の例 & #93;](#examples)  
  
###  <a name="restoring_to_pit_using_STOPAT"></a> F. STOPAT を使って特定の時点の状態に復元する  
 次の例では、データベースを `12:00 AM` `April 15, 2020` の状態に復元し、複数のログ バックアップが関連する復元操作を行います。 バックアップ デバイス `AdventureWorksBackups`において、復元するデータベース全体のバックアップはデバイス上の 3 番目のバックアップ セット (`FILE = 3`)、最初のログ バックアップは 4 番目のバックアップ セット (`FILE = 4`)、2 番目のログ バックアップは 5 番目のバックアップ セット (`FILE = 5`) です。  
  
```  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorksBackups  
   WITH FILE=3, NORECOVERY;  
  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorksBackups  
   WITH FILE=4, NORECOVERY, STOPAT = 'Apr 15, 2020 12:00 AM';  
  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorksBackups  
   WITH FILE=5, NORECOVERY, STOPAT = 'Apr 15, 2020 12:00 AM';  
RESTORE DATABASE AdventureWorks2012 WITH RECOVERY;  
  
```  
  
 [& #91。上部の例 & #93;](#examples)  
  
###  <a name="restoring_transaction_log_to_mark"></a>G. トランザクション ログをマークまで復元する  
 次の例では、トランザクション ログを `ListPriceUpdate`というマーク付きトランザクションのマークまで復元します。  
  
```  
USE AdventureWorks2012  
GO  
BEGIN TRANSACTION ListPriceUpdate  
   WITH MARK 'UPDATE Product list prices';  
GO  
  
UPDATE Production.Product  
   SET ListPrice = ListPrice * 1.10  
   WHERE ProductNumber LIKE 'BK-%';  
GO  
  
COMMIT TRANSACTION ListPriceUpdate;  
GO  
  
-- Time passes. Regular database   
-- and log backups are taken.  
-- An error occurs in the database.  
USE master;  
GO  
  
RESTORE DATABASE AdventureWorks2012  
FROM AdventureWorksBackups  
WITH FILE = 3, NORECOVERY;  
GO  
  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorksBackups   
   WITH FILE = 4,  
   RECOVERY,   
   STOPATMARK = 'UPDATE Product list prices';  
```  
  
 [& #91。上部の例 & #93;](#examples)  
  
###  <a name="restoring_using_TAPE"></a>H. TAPE 構文を使用して復元する  
 次の例からデータベースの完全バックアップの復元、`TAPE`バックアップ デバイス。  
  
```  
RESTORE DATABASE AdventureWorks2012   
   FROM TAPE = '\\.\tape0';  
```  
  
 [& #91。上部の例 & #93;](#examples)  
  
###  <a name="restoring_using_FILE_n_FG"></a>私。 FILE および FILEGROUP 構文を使用して復元する  
 次の例は、という名前のデータベースを復元`MyDatabase`を持つ 2 つのファイル、1 つのセカンダリ ファイル グループ、および 1 つのトランザクション ログです。 このデータベースは、完全復旧モデルを使用しています。  
  
 データベースのバックアップは、という名前の論理バックアップ デバイス上のメディア セットで、9 番目のバックアップ`MyDatabaseBackups`です。 次に、3 つのログ バックアップは、次の 3 つのバックアップ セット (`10`、 `11`、および`12`) で、`MyDatabaseBackups`デバイスを使用して復元`WITH NORECOVERY`です。 最後のログ バックアップを復元した後、データベースを復旧します。  
  
> **注:**を復旧してしまわないの可能性を減らすために別のステップとして回復が実行される、前にすべてのログ バックアップが復元されました。  
  
 `RESTORE DATABASE`、次の 2 種類があることに注意してください。`FILE`オプション。 `FILE` のように、バックアップ デバイス名より前の `FILE = 'MyDatabase_data_1'` オプションでは、バックアップ セットから復元するデータベース ファイルの論理ファイル名を指定します。 このバックアップ セットが、メディア セット内の最初のデータベース バックアップではありません。使用して、メディア セット内の位置が示されているため、`FILE`オプション、`WITH`句、`FILE=9`です。  
  
```  
RESTORE DATABASE MyDatabase  
   FILE = 'MyDatabase_data_1',  
   FILE = 'MyDatabase_data_2',  
   FILEGROUP = 'new_customers'  
   FROM MyDatabaseBackups  
   WITH   
      FILE = 9,  
      NORECOVERY;  
GO  
-- Restore the log backups.  
RESTORE LOG MyDatabase  
   FROM MyDatabaseBackups  
   WITH FILE = 10,   
      NORECOVERY;  
GO  
RESTORE LOG MyDatabase  
   FROM MyDatabaseBackups  
   WITH FILE = 11,   
      NORECOVERY;  
GO  
RESTORE LOG MyDatabase  
   FROM MyDatabaseBackups  
   WITH FILE = 12,   
      NORECOVERY;  
GO  
--Recover the database:  
RESTORE DATABASE MyDatabase WITH RECOVERY;  
GO  
```  
  
 [& #91。上部の例 & #93;](#examples)  
  
###  <a name="reverting_from_db_snapshot"></a>J. データベース スナップショットに戻す  
 次の例では、データベースをデータベース スナップショットに戻します。 この例では、現在、データベースに 1 つだけスナップショットが存在することを想定しています。 このデータベース スナップショットを作成する方法の例は、次を参照してください[データベース スナップショット & #40; を作成しますTRANSACT-SQL と #41 です。](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md).  
  
> **注:**スナップショットに戻す際は、すべてのフルテキスト カタログを削除します。  
  
```  
USE master;    
RESTORE DATABASE AdventureWorks2012 FROM DATABASE_SNAPSHOT = 'AdventureWorks_dbss1800';  
GO  
```  
 詳細については、次を参照してください。[データベース スナップショットにデータベースを元に戻す](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md)です。  

 [& #91。上部の例 & #93;](#examples)  
  
###  <a name="Azure_Blob"></a>K. Microsoft Azure Blob ストレージ サービスからの復元  
次の 3 つの例には、Microsoft Azure ストレージ サービスの使用が含まれます。  ストレージ アカウント名は `mystorageaccount`です。  データ ファイル用のコンテナーが呼び出された`myfirstcontainer`です。  バックアップ ファイルのコンテナーが呼び出された`mysecondcontainer`です。  各コンテナーの読み取り、書き込み、削除、および一覧は、権限を持つは、保存されているアクセス ポリシーが用意されています。  SQL Server 資格情報は、格納されているアクセス ポリシーに関連付けられている Shared Access Signature を使用して作成されました。  SQL Server のバックアップと復元、Microsoft Azure Blob ストレージに固有の情報を参照してください。 [SQL Server Backup and Restore with Microsoft Azure Blob Storage Service](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)です。  

**K1 です。Microsoft Azure ストレージ サービスからのデータベースの完全バックアップを復元します。**  
データベースの完全バックアップがある`mysecondcontainer`の`Sales`に復元されます`myfirstcontainer`です。  `Sales`サーバーに現在存在しません。 
```
RESTORE DATABASE Sales
  FROM URL = 'https://mystorageaccount.blob.core.windows.net/mysecondcontainer/Sales.bak'   
  WITH  MOVE 'Sales_Data1' to 'https://mystorageaccount.blob.core.windows.net/myfirstcontainer/Sales_Data1.mdf', 
  MOVE 'Sales_log' to 'https://mystorageaccount.blob.core.windows.net/myfirstcontainer/Sales_log.ldf', 
  STATS = 10;
```

**K2 です。Microsoft Azure ストレージ サービスからローカル ストレージにデータベースの完全バックアップを復元します。**  
データベースの完全バックアップがある`mysecondcontainer`の`Sales`はローカル ストレージに復元されます。  `Sales`サーバーに現在存在しません。
```
RESTORE DATABASE Sales
  FROM URL = 'https://mystorageaccount.blob.core.windows.net/mysecondcontainer/Sales.bak'   
  WITH  MOVE 'Sales_Data1' to 'H:\DATA\Sales_Data1.mdf', 
  MOVE 'Sales_log' to 'O:\LOG\Sales_log.ldf', 
  STATS = 10;
```
  
**K3 です。Microsoft Azure ストレージ サービスへのローカル ストレージからデータベースの完全バックアップを復元します。**  
```
RESTORE DATABASE Sales
  FROM DISK = 'E:\BAK\Sales.bak'
  WITH  MOVE 'Sales_Data1' to 'https://mystorageaccount.blob.core.windows.net/myfirstcontainer/Sales_Data1.mdf', 
  MOVE 'Sales_log' to 'https://mystorageaccount.blob.core.windows.net/myfirstcontainer/Sales_log.ldf', 
  STATS = 10;
```  
  

  
 [& #91。上部の例 & #93;](#examples)  
  
## <a name="much-more-information"></a>!! の詳細については  
 - [SQL Server データベースのバックアップと復元](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md) 
- [バックアップし、復元のシステム データベース (SQL Server)](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md) 
 - [SSMS を使用してデータベース バックアップを復元する](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)
 - [フルテキスト カタログとフルテキスト インデックスのバックアップおよび復元](../../relational-databases/search/back-up-and-restore-full-text-catalogs-and-indexes.md)   
 - [レプリケートされたデータベースのバックアップと復元](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 - [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 - [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 - [RESTORE REWINDONLY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 - [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 - [RESTORE FILELISTONLY (TRANSACT-SQL)](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)  
 - [RESTORE HEADERONLY (TRANSACT-SQL)](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)  
 - [バックアップの履歴とヘッダーの情報 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  

