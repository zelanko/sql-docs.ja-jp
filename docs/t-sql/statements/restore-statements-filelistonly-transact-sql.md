---
title: "RESTORE FILELISTONLY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RESTORE FILELISTONLY
- RESTORE_FILELISTONLY_TSQL
- FILELISTONLY
- FILELISTONLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backups [SQL Server], file lists
- RESTORE FILELISTONLY statement
- listing backed up files
ms.assetid: 0b4b4d11-eb9d-4f3e-9629-6c79cec7a81a
caps.latest.revision: 83
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bdae49bd22b5398d120530db150bc9628e34d92a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="restore-statements---filelistonly-transact-sql"></a>RESTORE ステートメントで FILELISTONLY (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバックアップ セットに保存されているデータベースとログ ファイルのリストを含んだ結果セットを返します。  
  
> [!NOTE]  
>  引数の説明については、次を参照してください。 [RESTORE の引数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
RESTORE FILELISTONLY   
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
 RESTORE FILELISTONLY の引数の説明については、次を参照してください。 [RESTORE の引数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="result-sets"></a>結果セット  
 クライアントでは、RESTORE FILELISTONLY を使用して、バックアップ セットに含まれるファイルの一覧を取得できます。 この情報は、ファイル 1 件あたり 1 行のデータで構成される結果セットとして返されます。  
  
|列名|データ型|Description|  
|-|-|-|  
|LogicalName|**nvarchar (128)**|ファイルの論理名です。|  
|PhysicalName|**nvarchar (260)**|ファイルの物理名またはオペレーティング システム名。|  
|型|**char (1)**|ファイルの種類。次のいずれかになります。<br /><br /> **L** = Microsoft[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログ ファイル<br /><br /> **D**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ファイル<br /><br /> **F**フル テキスト カタログを =<br /><br /> **S** = FileStream、FileTable、または[!INCLUDE[hek_2](../../includes/hek-2-md.md)]コンテナー|  
|FileGroupName|**nvarchar (128)**|このファイルを含むファイル グループの名前。|  
|サイズ|**numeric(20,0)**|現在のサイズ (バイト単位)。|  
|MaxSize|**numeric(20,0)**|最大許容サイズ (バイト単位)。|  
|FileID|**bigint**|データベース内で一意なファイル識別子。|  
|CreateLSN|**numeric(25,0)**|ファイルが作成されたときのログ シーケンス番号。|  
|DropLSN|**numeric(25,0)** NULL|ファイルを削除したログ シーケンス番号。 ファイルが削除されていない場合、この値は NULL です。|  
|UniqueID|**uniqueidentifier**|ファイルのグローバル一意識別子。|  
|ReadOnlyLSN|**numeric(25,0) NULL**|このファイルを含むファイル グループが、前回読み書き可能から読み取り専用に変更されたときのログ シーケンス番号。|  
|ReadWriteLSN|**numeric(25,0)** NULL|このファイルを含むファイル グループが、前回読み取り専用から読み書き可能に変更されたときのログ シーケンス番号。|  
|BackupSizeInBytes|**bigint**|ファイルのバックアップ サイズ (バイト単位)。|  
|SourceBlockSize|**int**|ファイルが格納されている物理デバイス (バックアップ デバイス以外) のバイト単位のブロック サイズ。|  
|FileGroupID|**int**|ファイル グループの ID。|  
|LogGroupGUID|**NULL で一意識別子**|NULL。|  
|DifferentialBaseLSN|**numeric(25,0)** NULL|差分バックアップは、ログ シーケンス番号より大きいか等しいを持つ変更**DifferentialBaseLSN**差分に含まれます。<br /><br /> その他の種類のバックアップの場合、この値は NULL です。|  
|DifferentialBaseGUID|**uniqueidentifier**|差分ベースの一意識別子 (差分バックアップの場合)。<br /><br /> その他の種類のバックアップの場合、この値は NULL です。|  
|IsReadOnly|**bit**|**1** = ファイルは読み取り専用です。|  
|IsPresent|**bit**|**1** = バックアップに、ファイルが存在します。|  
|TDEThumbprint|**varbinary (32)**|データベース暗号化キーの拇印を表示します。 暗号化の拇印とは、キーの暗号化で使用された証明書の SHA-1 ハッシュです。 データベースの暗号化については、次を参照してください。 [Transparent Data Encryption & #40 です。TDE &#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).|  
|SnapshotURL|**nvarchar(360)**|FILE_SNAPSHOT バックアップに含まれているデータベース ファイルの Azure のスナップショットの URL。 FILE_SNAPSHOT バックアップがない場合は、NULL を返します。|  
  
## <a name="security"></a>セキュリティ  
 バックアップ操作では、オプションで、メディア セットとバックアップ セットにそれぞれパスワードを設定できます。 メディア セットまたはバックアップ セットにパスワードが設定されている場合は、RESTORE ステートメントで正しいパスワードを指定する必要があります。 これらのパスワードが不正に復元操作を防ぐため、不正なメディアを使用するバックアップ セットの追加[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ツールです。 ただし、BACKUP ステートメントで FORMAT オプションが使用された場合、メディアの上書きを防ぐことはできません。  
  
> [!IMPORTANT]  
>  パスワードによる保護は強力なものではありません。 使用して、正しくない復元を防止するものでは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ツールを承認またはユーザーです。 その他の手段によるバックアップ データの読み取りやパスワードの置き換えを防ぐわけではありません。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]バックアップを保護するためのベスト プラクティスでは、安全な場所に、または十分なアクセス制御リスト (Acl) によって保護されているディスク ファイルへのバックアップ、バックアップ テープを保存します。 ACL は、バックアップを作成するディレクトリのルートに設定する必要があります。  
  
### <a name="permissions"></a>Permissions  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、バックアップ セットやバックアップ デバイスに関する情報の取得には CREATE DATABASE 権限が必要になります。 詳細については、「[GRANT (データベースの権限の許可) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例では、情報を返しますというバックアップ デバイスから`AdventureWorksBackups`です。 この例では `FILE` オプションを使用して、デバイスで 2 番目のバックアップ セットを指定しています。  
  
```  
RESTORE FILELISTONLY FROM AdventureWorksBackups   
   WITH FILE=2;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE REWINDONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [バックアップの履歴とヘッダーの情報 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  

