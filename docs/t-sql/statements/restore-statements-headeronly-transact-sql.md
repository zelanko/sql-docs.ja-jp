---
title: "RESTORE HEADERONLY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/07/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- HEADERONLY
- RESTORE HEADERONLY
- RESTORE_HEADERONLY_TSQL
- HEADERONLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup sets [SQL Server], header information
- headers [SQL Server]
- RESTORE HEADERONLY statement
- backup header information [SQL Server]
ms.assetid: 4b88e98c-49c4-4388-ab0e-476cc956977c
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 840793c4bbfee8282676cf90d42d6e7a6c4d6b42
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="restore-statements---headeronly-transact-sql"></a>RESTORE ステートメントで HEADERONLY (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定のバックアップ デバイスのすべてのバックアップ セットのすべてのバックアップ ヘッダー情報を含む結果セットを返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
> [!NOTE]  
>  引数の説明については、次を参照してください。 [RESTORE の引数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
RESTORE HEADERONLY   
FROM <backup_device>   
[ WITH   
 {  
--Backup Set Options  
   FILE = { backup_set_file_number | @backup_set_file_number }   
 | PASSWORD = { password | @password_variable }   
  
--Media Set Options  
 | MEDIANAME = { media_name | @media_name_variable }   
 | MEDIAPASSWORD = { mediapassword | @mediapassword_variable }  
  
--Error Management Options  
 | { CHECKSUM | NO_CHECKSUM }   
 | { STOP_ON_ERROR | CONTINUE_AFTER_ERROR }  
  
--Tape Options  
 | { REWIND | NOREWIND }   
 | { UNLOAD | NOUNLOAD }    
 } [ ,...n ]  
]  
[;]  
  
<backup_device> ::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
   | { DISK | TAPE } = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}  
  
```  
  
## <a name="arguments"></a>引数  
 RESTORE HEADERONLY の引数の説明については、次を参照してください。 [RESTORE の引数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="result-sets"></a>結果セット  
 指定されたデバイス上にあるバックアップごとに、サーバーからヘッダー情報の行が送信されます。下に説明する列が含まれています。  
  
> [!NOTE]  
>  RESTORE HEADERONLY では、メディア上のすべてのバックアップ セットが確認されるため、 大容量のテープ ドライブを使用している場合は結果セットの生成に時間がかかることがあります。 すべてのバックアップ セットに関する情報を取得することがなく簡単に見て、メディアを取得する RESTORE LABELONLY を使用するか、ファイルを指定 **=**  *backup_set_file_number*です。  
  
> [!NOTE]  
>  性質の[!INCLUDE[msCoName](../../includes/msconame-md.md)]Tape Format の場合は、可能であれば同じメディア上の空き領域をバックアップが他のソフトウェア プログラムから設定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バックアップ セットです。 RESTORE HEADERONLY によって返される結果セットには、その他のバックアップ セットの情報も 1 件につき 1 行ずつ含まれます。  
  
|列名|データ型|SQL Server バックアップ セットの場合の説明|  
|-----------------|---------------|--------------------------------------------|  
|**BackupName**|**nvarchar(128)**|バックアップ セット名。|  
|**BackupDescription**|**nvarchar (255)**|バックアップ セットの説明。|  
|**BackupType**|**smallint**|バックアップの種類。<br /><br /> **1** = データベース<br /><br /> **2**トランザクション ログを =<br /><br /> **4**ファイルを =<br /><br /> **5**データベースの差分を =<br /><br /> **6**ファイルの差分を =<br /><br /> **7**部分を =<br /><br /> **8** = 部分的な差分|  
|**ExpirationDate**|**datetime**|バックアップ セットの失効日。|  
|**圧縮**|**BYTE(1)**|ソフトウェア ベースの圧縮によりバックアップ セットが圧縮されているかどうか。<br /><br /> **0** = なし<br /><br /> **1** = [はい]|  
|**[位置]**|**smallint**|ボリューム内でのバックアップ セットの位置 (FILE = のオプションで使用)。|  
|**DeviceType**|**tinyint**|バックアップ操作で使用するデバイスに対応する値。<br /><br /> ディスク:<br /><br /> **2** = 論理<br /><br /> **102** = 物理<br /><br /> テープ:<br /><br /> **5** = 論理<br /><br /> **105** = 物理<br /><br /> 仮想デバイス:<br /><br /> **7** = 論理<br /><br /> **107** = 物理<br /><br /> 論理デバイス名とデバイス番号は**sys.backup_devices**。 詳細については、を参照してください[sys.backup_devices &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md).|  
|**UserName**|**nvarchar(128)**|バックアップ操作を実行するユーザー名。|  
|**ServerName**|**nvarchar(128)**|バックアップ セットを作成したサーバーの名前。|  
|**DatabaseName**|**nvarchar(128)**|バックアップの作成元であるデータベースの名前。|  
|**DatabaseVersion**|**int**|バックアップの作成元であるデータベースのバージョン。|  
|**DatabaseCreationDate**|**datetime**|データベースが作成された日時。|  
|**BackupSize**|**numeric(20,0)**|バックアップのサイズ (バイト単位)。|  
|**FirstLSN**|**numeric(25,0)**|バックアップ セット内にある先頭のログ レコードのログ シーケンス番号。|  
|**LastLSN**|**numeric(25,0)**|バックアップ セットの次のログ レコードのログ シーケンス番号。|  
|**CheckpointLSN**|**numeric(25,0)**|バックアップが作成された時点における最新チェックポイントのログ シーケンス番号。|  
|**DatabaseBackupLSN**|**numeric(25,0)**|データベース全体の最新バックアップのログ シーケンス番号。<br /><br /> **DatabaseBackupLSN**は、"チェックポイントの先頭"、バックアップの開始時にトリガーされます。 この LSN は同時になる**FirstLSN**場合は、データベースがアイドル状態で、レプリケーションが構成されていないときに、バックアップを実行します。|  
|**BackupStartDate**|**datetime**|バックアップ操作が開始した日時。|  
|**BackupFinishDate**|**datetime**|バックアップ操作が終了した日時。|  
|**SortOrder**|**smallint**|サーバーの並べ替え順。 この列はデータベース バックアップのみで有効です。 これは旧バージョンとの互換性のために用意されています。|  
|**CodePage**|**smallint**|サーバーが使用するサーバー コード ページまたは文字セット。|  
|**UnicodeLocaleId**|**int**|Unicode 文字データの並べ替えに使用する、サーバー Unicode ロケール ID 構成オプション。 これは旧バージョンとの互換性のために用意されています。|  
|**UnicodeComparisonStyle**|**int**|Unicode データの並べ替えに詳細な設定を追加できる、サーバー Unicode 比較スタイル構成オプション。 これは旧バージョンとの互換性のために用意されています。|  
|**CompatibilityLevel**|**tinyint**|バックアップの作成元であるデータベースの互換性レベル設定。|  
|**SoftwareVendorId**|**int**|ソフトウェア ベンダーの識別番号。 この数は、SQL Server, **4608** (16 進数または**0x1200**)。|  
|**SoftwareVersionMajor**|**int**|バックアップ セットを作成したサーバーのメジャー バージョン番号。|  
|**SoftwareVersionMinor**|**int**|バックアップ セットを作成したサーバーのマイナー バージョン番号。|  
|**SoftwareVersionBuild**|**int**|バックアップ セットを作成したサーバーのビルド番号。|  
|**MachineName**|**nvarchar(128)**|バックアップ操作を実行したコンピューターの名前。|  
|**フラグ**|**int**|場合、個人がビットの意味をフラグに設定**1**:<br /><br /> **1** = ログ バックアップに一括ログ操作が含まれています。<br /><br /> **2** = スナップショット バックアップします。<br /><br /> **4** = データベースがバックアップ時に読み取り専用です。<br /><br /> **8** = データベースがシングル ユーザー モードのバックアップ時にします。<br /><br /> **16** = バックアップにバックアップ チェックサムが含まれています。<br /><br /> **32** = バックアップ時に、データベースが破損したが、バックアップ操作のエラーに関係なく続行が要求されました。<br /><br /> **64**ログ末尾のバックアップを = です。<br /><br /> **128**不完全なメタデータでログ末尾のバックアップを = です。<br /><br /> **256** = ログ末尾のバックアップ with norecovery を指定します。<br /><br /> **重要:**の代わりにことをお勧め**フラグ**個々 のブール型の列を使用する (以降で以下に示す**HasBulkLoggedData**で終わる**IsCopyOnly**)。|  
|**BindingID**|**uniqueidentifier**|データベースに割り当てられたバインド ID。 これに対応して**sys.database_recovery_status***database_guid**です。 データベースが復元されると、新しい値が割り当てられます。 参照してください**FamilyGUID** (下記)。|  
|**RecoveryForkID**|**uniqueidentifier**|終了の復旧分岐の ID。 この列に対応して**last_recovery_fork_guid**で、 [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)テーブル。<br /><br /> データのバックアップ、 **RecoveryForkID** equals **FirstRecoveryForkID**です。|  
|**[照合順序]**|**nvarchar(128)**|データベースで使用されている照合順序。|  
|**FamilyGUID**|**uniqueidentifier**|元のデータベースに関する作成時の ID。 この値は、データベースが復元されても変わりません。|  
|**HasBulkLoggedData**|**bit**|**1** = 一括ログ操作を含むログ バッグアップ。|  
|**IsSnapshot**|**bit**|**1** = スナップショット バックアップします。|  
|**IsReadOnly**|**bit**|**1** = データベースがバックアップ時に読み取り専用です。|  
|**IsSingleUser**|**bit**|**1** = データベースがシングル ユーザーのバックアップ時にします。|  
|**HasBackupChecksums**|**bit**|**1** = バックアップにバックアップ チェックサムが含まれています。|  
|**IsDamaged**|**bit**|**1** = バックアップ時に、データベースが破損したが、バックアップ操作のエラーに関係なく続行が要求されました。|  
|**BeginsLogChain**|**bit**|**1** = これは、最初のログ バックアップの連鎖的なです。 データベースを作成した後、または単純から完全または一括ログ復旧モデルに切り替えるときに、最初のログ バックアップ ログ チェーンを開始します。|  
|**HasIncompleteMetaData**|**bit**|**1** = ログ末尾のバックアップが不完全なメタデータを使用します。<br /><br /> 不完全なバックアップ メタデータでのログ末尾のバックアップについては、次を参照してください。[ログ末尾のバックアップ &#40;です。SQL Server &#41;](../../relational-databases/backup-restore/tail-log-backups-sql-server.md).|  
|**IsForceOffline**|**bit**|**1** = with norecovery を指定します。 作成したバックアップ、データベースによってオフラインにバックアップします。|  
|**IsCopyOnly**|**bit**|**1**コピーのみのバックアップを = です。<br /><br /> コピーのみのバックアップを行っても、データベースの全体的なバックアップと復元の手順に影響はありません。 詳細については、「[コピーのみのバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md)」を参照してください。|  
|**FirstRecoveryForkID**|**uniqueidentifier**|開始の復旧分岐の ID。 この列に対応して**first_recovery_fork_guid**で、 [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)テーブル。<br /><br /> データのバックアップ、 **FirstRecoveryForkID** equals **RecoveryForkID**です。|  
|**ForkPointLSN**|**numeric(25,0)** NULL|場合**FirstRecoveryForkID**は等しくありません**RecoveryForkID**、これは、分岐ポイントのログ シーケンス番号。 これらが同じである場合、この値は NULL になります。|  
|**RecoveryModel**|**nvarchar(60)**|データベースの復旧モデル。次のいずれかになります。<br /><br /> FULL<br /><br /> BULK-LOGGED <br /><br /> SIMPLE|  
|**DifferentialBaseLSN**|**numeric(25,0)** NULL|シングル ベースの差分バックアップと同じ値、 **FirstLSN** Lsn に以上で変更する、差分ベースの**DifferentialBaseLSN**差分に含まれています。<br /><br /> マルチ ベースの差分バックアップの場合、この値は NULL です。ベース ログ シーケンス番号はファイル レベルで決定される必要があります。 詳細については、[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md) を参照してください。<br /><br /> 差分バックアップ以外の種類のバックアップの場合は常に NULL。<br /><br /> 詳細については、「 [差分バックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/differential-backups-sql-server.md)」を参照してください。|  
|**DifferentialBaseGUID**|**uniqueidentifier**|シングル ベースの差分バックアップの場合は、差分ベースの一意識別子。<br /><br /> マルチ ベースの差分バックアップの場合は、NULL。差分のベースはファイルごとに決定する必要があります。<br /><br /> 差分バックアップ以外のバックアップの場合は NULL。|  
|**BackupTypeDescription**|**nvarchar(60)**|バックアップの種類を表す文字列。次のいずれかになります。<br /><br /> DATABASE<br /><br /> TRANSACTION LOG <br /><br /> FILE OR FILEGROUP<br /><br /> DATABASE DIFFERENTIAL<br /><br /> FILE DIFFERENTIAL PARTIAL<br /><br /> PARTIAL DIFFERENTIAL|  
|**BackupSetGUID**|**uniqueidentifier** NULL|メディア上のバックアップ セットを識別する、バックアップ セットの一意識別番号。|  
|**CompressedBackupSize**|**bigint**|バックアップ セットのバイト数。 圧縮されていないバックアップは、この値は同じ**BackupSize**です。<br /><br /> 圧縮比率を計算するには、使用**CompressedBackupSize**と**BackupSize**です。<br /><br /> 中に、 **msdb**アップグレードすると、この値は設定の値に一致する、 **BackupSize**列です。|  
|**containment**|**tinyint** not NULL|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> データベースの包含状態を示します。<br /><br /> 0 = データベースの包含がオフ<br /><br /> 1 = データベースは部分的な包含|  
|**KeyAlgorithm**|**nvarchar(32)**|**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (CU1) で現在のバージョン。<br /><br /> バックアップの暗号化に使用される暗号化アルゴリズム。 NO_Encryption では、バックアップが暗号化されていないことを示します。 システムに正しい値を特定できない場合、値は NULL になります。|  
|**EncryptorThumbprint**|**varbinary(20)**|**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (CU1) で現在のバージョン。<br /><br /> データベースに保存されている証明書や非対称キーを検索するために使用される暗号化機能の拇印。 バックアップが暗号化されていない、ときに、この値は NULL を使用します。|  
|**EncryptorType**|**nvarchar(32)**|**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] (CU1) で現在のバージョン。<br /><br /> 使用される暗号化機能の種類 (証明書または非対称キー)。 バックアップが暗号化されていない、ときに、この値は NULL を使用します。|  
  
> [!NOTE]  
>  バックアップ セットにパスワードが定義されている場合、RESTORE HEADERONLY によって完全な情報が返されるのは、コマンドの PASSWORD オプションと同じパスワードが指定されているバックアップ セットに対してのみです。 また保護されていないバックアップ セットについても、RESTORE HEADERONLY では完全な情報が返されます。 **バックアップ名**列、メディアの他のパスワードで保護されたバックアップ セットに設定されている ' * * * パスワードで保護された\*\*\*'、およびその他のすべての列は NULL です。  
  
## <a name="general-remarks"></a>全般的な解説  
 クライアントは RESTORE HEADERONLY を使用して、特定のバックアップ デバイス上のすべてのバックアップについて、バックアップ ヘッダーに関するすべての情報を取得できます。 バックアップ デバイス上にあるバックアップごとに、ヘッダー情報が 1 行のデータとしてサーバーから送信されます。  
  
## <a name="security"></a>セキュリティ  
 バックアップ操作では、オプションで、メディア セットとバックアップ セットにそれぞれパスワードを設定できます。 メディア セットまたはバックアップ セットにパスワードが設定されている場合は、RESTORE ステートメントで正しいパスワードを指定する必要があります。 これらのパスワードが不正に復元操作を防ぐため、不正なメディアを使用するバックアップ セットの追加[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ツールです。 ただし、BACKUP ステートメントで FORMAT オプションが使用された場合、メディアの上書きを防ぐことはできません。  
  
> [!IMPORTANT]  
>  パスワードによる保護は強力なものではありません。 使用して、正しくない復元を防止するものでは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ツールを承認またはユーザーです。 その他の手段によるバックアップ データの読み取りやパスワードの置き換えを防ぐわけではありません。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]バックアップを保護するためのベスト プラクティスでは、安全な場所に、または十分なアクセス制御リスト (Acl) によって保護されているディスク ファイルへのバックアップ、バックアップ テープを保存します。 ACL は、バックアップを作成するディレクトリのルートに設定する必要があります。  
  
### <a name="permissions"></a>権限  
 バックアップ セットやバックアップ デバイスに関する情報の取得には CREATE DATABASE 権限が必要になります。 詳細については、「[GRANT (データベースの権限の許可) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例では、ディスク ファイル `C:\AdventureWorks-FullBackup.bak` のヘッダー情報を返します。  
  
```  
RESTORE HEADERONLY   
FROM DISK = N'C:\AdventureWorks-FullBackup.bak'   
WITH NOUNLOAD;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [RESTORE REWINDONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [バックアップの履歴とヘッダーの情報 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)   
 [有効にするか、バックアップまたは復元 &#40; 中にバックアップ チェックサムを無効にします。SQL Server &#41;](../../relational-databases/backup-restore/enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)   
 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [復旧モデル &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)  
  
  
