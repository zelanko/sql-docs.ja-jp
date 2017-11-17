---
title: "BACKUP (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/13/2017
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
- BACKUP_TSQL
- BACKUP
- BACKUP_DATABASE_TSQL
- BACKUP_LOG_TSQL
- BACKUP LOG
- BACKUP DATABASE
dev_langs:
- TSQL
helpviewer_keywords:
- backup media [SQL Server], BACKUP statement
- backing up filegroups [SQL Server]
- backup file formats [SQL Server]
- backups [SQL Server]
- database backups [SQL Server], BACKUP statement
- multifamily media sets [SQL Server]
- mirrored media sets [SQL Server]
- backing up files [SQL Server]
- backup sets [SQL Server], BACKUP statement
- backup compression [SQL Server], BACKUP statement
- BACKUP statement
- backups [SQL Server], BACKUP statement
- backup history tables [SQL Server]
- transaction log backups [SQL Server], BACKUP LOG statement
- READ_WRITE_FILEGROUPS option
- BACKUP DATABASE statement
- concurrency [SQL Server], backups
- backing up databases [SQL Server]
- passwords [SQL Server], backups
- security [SQL Server], backups
- media families [SQL Server]
- BACKUP LOG statement
- backing up transaction logs [SQL Server]
- stripe sets [SQL Server]
- cross-platform backups
ms.assetid: 89a4658a-62f1-4289-8982-f072229720a1
caps.latest.revision: 275
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 6e754198cf82a7ba0752fe8f20c3780a8ac551d7
ms.openlocfilehash: 3654be2e02163cd8069a95eb5e82d4649cec1ab5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/14/2017

---
# <a name="backup-transact-sql"></a>BACKUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  全体をバックアップ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースのバックアップ、または 1 つまたは複数ファイルまたはファイル グループ、データベースのファイル バックアップ (BACKUP DATABASE) を作成するを作成するデータベース。 完全復旧モデルまたは一括ログ復旧モデルの場合には、データベースのトランザクション ログをバックアップして、ログ バックアップを作成します (BACKUP LOG)。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
``` 
Backing Up a Whole Database   
BACKUP DATABASE { database_name | @database_name_var }   
  TO <backup_device> [ ,...n ]   
  [ <MIRROR TO clause> ] [ next-mirror-to ]  
  [ WITH { DIFFERENTIAL | <general_WITH_options> [ ,...n ] } ]  
[;]  
  
Backing Up Specific Files or Filegroups  
BACKUP DATABASE { database_name | @database_name_var }   
 <file_or_filegroup> [ ,...n ]   
  TO <backup_device> [ ,...n ]   
  [ <MIRROR TO clause> ] [ next-mirror-to ]  
  [ WITH { DIFFERENTIAL | <general_WITH_options> [ ,...n ] } ]  
[;]  
  
Creating a Partial Backup  
BACKUP DATABASE { database_name | @database_name_var }   
 READ_WRITE_FILEGROUPS [ , <read_only_filegroup> [ ,...n ] ]  
  TO <backup_device> [ ,...n ]   
  [ <MIRROR TO clause> ] [ next-mirror-to ]  
  [ WITH { DIFFERENTIAL | <general_WITH_options> [ ,...n ] } ]  
[;]  
  
Backing Up the Transaction Log (full and bulk-logged recovery models)  
BACKUP LOG { database_name | @database_name_var }   
  TO <backup_device> [ ,...n ]   
  [ <MIRROR TO clause> ] [ next-mirror-to ]  
  [ WITH { <general_WITH_options> | \<log-specific_optionspec> } [ ,...n ] ]  
[;]  
  
<backup_device>::=   
 {  
   { logical_device_name | @logical_device_name_var }   
 | { DISK | TAPE | URL} =   
     { 'physical_device_name' | @physical_device_name_var }  
 }   
  
<MIRROR TO clause>::=  
 MIRROR TO <backup_device> [ ,...n ]  
  
<file_or_filegroup>::=  
 {  
   FILE = { logical_file_name | @logical_file_name_var }   
 | FILEGROUP = { logical_filegroup_name | @logical_filegroup_name_var }  
 }   
  
<read_only_filegroup>::=  
FILEGROUP = { logical_filegroup_name | @logical_filegroup_name_var }  
  
<general_WITH_options> [ ,...n ]::=   
--Backup Set Options  
   COPY_ONLY   
 | { COMPRESSION | NO_COMPRESSION }   
 | DESCRIPTION = { 'text' | @text_variable }   
 | NAME = { backup_set_name | @backup_set_name_var }   
 | CREDENTIAL  
 | ENCRYPTION  
 | FILE_SNAPSHOT  
 | { EXPIREDATE = { 'date' | @date_var }   
        | RETAINDAYS = { days | @days_var } }   
  
--Media Set Options  
   { NOINIT | INIT }   
 | { NOSKIP | SKIP }   
 | { NOFORMAT | FORMAT }   
 | MEDIADESCRIPTION = { 'text' | @text_variable }   
 | MEDIANAME = { media_name | @media_name_variable }   
 | BLOCKSIZE = { blocksize | @blocksize_variable }   
  
--Data Transfer Options  
   BUFFERCOUNT = { buffercount | @buffercount_variable }   
 | MAXTRANSFERSIZE = { maxtransfersize | @maxtransfersize_variable }  
  
--Error Management Options  
   { NO_CHECKSUM | CHECKSUM }  
 | { STOP_ON_ERROR | CONTINUE_AFTER_ERROR }  
  
--Compatibility Options  
   RESTART   
  
--Monitoring Options  
   STATS [ = percentage ]   
  
--Tape Options  
   { REWIND | NOREWIND }   
 | { UNLOAD | NOUNLOAD }   
  
--Log-specific Options  
   { NORECOVERY | STANDBY = undo_file_name }  
 | NO_TRUNCATE  
  
--Encryption Options  
 ENCRYPTION (ALGORITHM = { AES_128 | AES_192 | AES_256 | TRIPLE_DES_3KEY } , encryptor_options ) <encryptor_options> ::=   
   SERVER CERTIFICATE = Encryptor_Name | SERVER ASYMMETRIC KEY = Encryptor_Name   
```  
  
## <a name="arguments"></a>引数  
 DATABASE  
 データベース全体のバックアップを指定します。 ファイルとファイル グループのリストを指定した場合、指定したファイルとファイル グループだけがバックアップされます。 完全または差分データベース バックアップ中は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のに十分なバックアップを復元すると、一貫性のあるデータベースを生成するトランザクション ログをバックアップします。  
  
 データベースのバックアップで作成されたバックアップを復元すると (、*データ バックアップ*)、全体のバックアップを復元します。 バックアップ内の特定の時点またはトランザクションに復元できるのは、ログ バックアップだけです。  
  
> [!NOTE]  
>  データベースの完全バックアップのみを実行できる、**マスター**データベース。  
  
 LOG  
 トランザクション ログのみのバックアップを指定します。 前回正しく実行されたログ バックアップの位置から、ログの現在の末尾まで、ログのバックアップが行われます。 最初のログ バックアップを作成するには、その前に完全バックアップを作成する必要があります。  
  
 特定の時刻またはバックアップ内のトランザクション ログ バックアップを復元するには WITH STOPAT、STOPATMARK、または stopbeforemark のいずれかで指定することによって、 [RESTORE LOG](../../t-sql/statements/restore-statements-transact-sql.md)ステートメントです。  
  
> [!NOTE]  
>  WITH NO_TRUNCATE または COPY_ONLY を指定する以外の標準的な方法でログ バックアップを行うと、一部のトランザクション ログ レコードはアクティブでなくなります。 1 つ以上の仮想ログ ファイル内ですべてのレコードがアクティブでなくなった場合、ログは切り捨てられます。 定期的なログ バックアップの後ログが切り捨てられない場合は、何らかの原因によりログの切り捨てが遅れている可能性があります。 詳細については、以下を参照してください。  
  
 { *database_name* | **@**database_name_var *}   
 トランザクション ログ、データベースの一部、またはデータベース全体をバックアップする場合の、バックアップ元となるデータベースを指定します。 変数として指定する場合 (**@***database_name_var*)、この名前を指定できます文字列定数として指定 (** @ ** *database_name_var***=***データベース名*) または文字の文字列データ型の変数として以外の**ntext**または**テキスト**データ型。  
  
> [!NOTE]  
>  データベース ミラーリング パートナーシップ内のミラー データベースは、バックアップできません。  
  
\<file_or_filegroup > [ **、**.*n* ]  
 BACKUP DATABASE でのみ使用できます。ファイル バックアップに含めるデータベース ファイルまたはファイル グループを指定するか、部分バックアップに含める読み取り専用ファイルまたはファイル グループを指定します。  
  
 ファイル** = ** { *logical_file_name*| **@***logical_file_name_var* }  
 バックアップに含めるファイルの論理名、またはこの論理名を値として保持する変数を指定します。  
  
 ファイル グループ** = ** { *logical_filegroup_name*| **@***logical_filegroup_name_var* }  
 バックアップに含めるファイル グループの論理名、またはこの論理名を値として保持する変数を指定します。 単純復旧モデルでは、ファイル グループのバックアップは、読み取り専用のファイル グループに対してのみ使用できます。  
  
> [!NOTE]  
>  データベースのサイズやパフォーマンス要件によりデータベース バックアップの実行が難しい場合は、ファイル単位のバックアップを検討してください。  
  
 *n*  
 複数のファイルおよびファイル グループを、コンマで区切ったリストで指定できることを示すプレースホルダーです。 数値の制限はありません。 
  
 詳細についてを参照してください:[ファイルの完全バックアップ & #40 です。SQL Server &#41;](../../relational-databases/backup-restore/full-file-backups-sql-server.md)と[ファイルおよびファイル グループ &#40; バックアップSQL Server &#41;](../../relational-databases/backup-restore/back-up-files-and-filegroups-sql-server.md).  
  
 READ_WRITE_FILEGROUPS [ **、**ファイル グループ = { *logical_filegroup_name*| **@***logical_filegroup_name_var* }[ **,**...*n* ] ]  
 部分バックアップを指定します。 部分バックアップには、データベース内のすべての読み取り/書き込みファイル (プライマリ ファイル グループ、存在する場合は読み取り/書き込みセカンダリ ファイル グループ、および指定の読み取り専用ファイルまたはファイル グループ) が含まれます。  
  
 READ_WRITE_FILEGROUPS  
 部分バックアップで、すべての読み取り/書き込みファイル グループをバックアップすることを指定します。 データベースが読み取り専用の場合、READ_WRITE_FILEGROUPS にはプライマリ ファイル グループのみが含まれます。  
  
> [!IMPORTANT]  
>  READ_WRITE_FILEGROUPS の代わりに FILEGROUP を使用して、読み取り/書き込みファイル グループのリストを明示的に指定すると、ファイル バックアップが作成されます。  
  
 ファイル グループ = { *logical_filegroup_name*| **@***logical_filegroup_name_var* }  
部分バックアップに含める読み取り専用ファイル グループの論理名、またはこの論理名を値として保持する変数を指定します。 詳細については、次を参照してください。"\<file_or_filegroup >、"このトピックで前述しました。
  
 *n*  
 複数の読み取り専用ファイル グループを、コンマで区切ったリストで指定できることを示すプレースホルダーです。  
  
 部分バックアップの詳細については、次を参照してください。[部分バックアップ & #40 です。SQL Server &#41;](../../relational-databases/backup-restore/partial-backups-sql-server.md).  
  
\<Backup_device > [ **、**.* n * ] の設定に付属していることを示します[バックアップ デバイス](../../relational-databases/backup-restore/backup-devices-sql-server.md)はミラー化されていないメディア セットまたはミラー化メディア セット (用を 1 つまたは複数のミラーに内にあるミラーのうちの最初のいずれか句が宣言されている)。  
  
\<backup_device >、バックアップ操作に使用する論理または物理バックアップ デバイスを指定します。  
  
 { *logical_device_name* | **@***logical_device_name_var* }  
 データベースのバックアップが作成されるバックアップ デバイスの論理名を指定します。 論理名は、識別子のルールに従う必要があります。 変数として指定する場合 (@*logical_device_name_var*)、バックアップ デバイス名を指定できます文字列定数として指定 (@*logical_device_name_var* ** = **論理バックアップ デバイス名)、または任意の文字の文字列データ型以外の変数として、 **ntext**または**テキスト**データ型。  
  
 {ディスク |テープ |URL} ** = ** { **'***physical_device_name***'**  |  ** @ ***physical_device_name_var* }  
 ディスク ファイルまたはテープ デバイス、あるいは Windows Azure BLOB ストレージ サービスを指定します。 URL の形式は、Windows Azure ストレージ サービスへのバックアップを作成するために使用されます。 詳細と例については、次を参照してください。 [SQL Server のバックアップと Microsoft Azure Blob ストレージ サービスによる復元](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)です。 チュートリアルについては、次を参照してください。[チュートリアル: SQL Server のバックアップと Windows Azure Blob ストレージ サービスへの復元](~/relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]まで SP1 CU2 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]URL にバックアップする場合のみ 1 台のデバイスにバックアップすることができます。 URL にバックアップする場合は、複数のデバイスにバックアップをするために使用する必要があります[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]し Shared Access Signature (SAS) トークンを使用する必要があります。 共有アクセス署名を作成する例については、次を参照してください。 [SQL Server Backup to URL](../../relational-databases/backup-restore/sql-server-backup-to-url.md)と[Powershell による Azure Storage に Shared Access Signature (SAS) トークンで、SQL 資格情報の作成を簡素化](http://blogs.msdn.com/b/sqlcat/archive/2015/03/21/simplifying-creation-sql-credentials-with-shared-access-signature-sas-keys-on-azure-storage-containers-with-powershell.aspx)です。  
  
**URL が対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 CU2 から[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])。  
  
 ディスク デバイスは、BACKUP ステートメントで指定するときにまだ存在していなくてもかまいません。 物理デバイスが既に存在し、BACKUP ステートメントに INIT オプションが指定されていない場合、バックアップはデバイスに追加されます。  
  
 詳細については、「 [バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)の別のインスタンスで作成された場合、これは必須です。  
  
> [!NOTE]  
>  TAPE オプションは将来のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。  
  
 *n*  
 最大 64 個のバックアップ デバイスをコンマ区切りリストに指定できることを示すプレースホルダーです。  
  
MIRROR TO \<backup_device > [ **、**.* n * ]、バックアップ デバイスが、TO 句で指定された各なるミラー、最大 3 つのセカンダリ バックアップ デバイスのセットを指定します。 MIRROR TO 句では、TO 句と同じの型とバックアップ デバイスの数を指定する必要があります。 MIRROR TO 句の最大数は 3 です。  
  
 このオプションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の Enterprise Edition でのみ使用できます。  
  
> [!NOTE]  
>  MIRROR TO = DISK の場合、BACKUP によって、ディスク デバイスに応じた適切なブロック サイズが自動的に決まります。 ブロック サイズの詳細については、後の「BLOCKSIZE」の説明を参照してください。  
  
\<backup_device > を参照してください"\<backup_device >、"このセクションで前述しました。
  
 *n*  
 最大 64 個のバックアップ デバイスをコンマ区切りリストに指定できることを示すプレースホルダーです。 各 MIRROR TO 句内のデバイス数は、TO 句内のデバイス数と同じである必要があります。  
  
 詳細については、後の「解説」の「ミラー化されたメディア セットのメディア ファミリ」を参照してください。  
  
 [*次でミラーを*]  
 単一の BACKUP ステートメントに、1 つの TO 句と 3 つまでの MIRROR TO 句を含めることができることを示すプレースホルダーです。  
  
### <a name="with-options"></a>WITH オプション  
 バックアップ操作で使用するオプションを指定します。  
  
 CREDENTIAL  
 Windows Azure BLOB ストレージ サービスにバックアップを作成する場合にのみ使用します。  
  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 CU2 から[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])。  
  
 FILE_SNAPSHOT  
 Azure Blob ストレージ サービスを使用してすべての SQL Server データベース ファイルが格納される場合は、データベース ファイルの Azure のスナップショットを作成するために使用します。 詳細については、次を参照してください。 [Microsoft Azure で SQL Server データ ファイル](../../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md)です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スナップショット バックアップでは、一貫性のある状態にデータベース ファイル (データとログ ファイル) の Azure のスナップショットを取得します。 Azure のスナップショットの一貫性のあるセットでは、バックアップを構成し、バックアップ ファイルに記録されます。 唯一の違い**バックアップ データベースを URL で FILE_SNAPSHOT**と**バックアップ ログを URL で FILE_SNAPSHOT**こと、後者もトランザクション ログを切り捨て、以前ではありませんが、します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スナップショット バックアップで必要とされる最初の完全バックアップの後に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]だけを 1 つのトランザクション ログのバックアップは、トランザクション ログ バックアップの時間内のポイントにデータベースを復元するために、バックアップのチェーンを確立するためにします。 さらに、次の 2 つのトランザクション ログ バックアップの期間の間のポイントにデータベースを復元するだけの 2 つのトランザクション ログ バックアップが必要です。  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]まで)。  
  
 DIFFERENTIAL  
 BACKUP DATABASE でのみ使用できます。前回の完全バックアップ以降に変更が加えられたデータベースやファイルだけをバックアップすることを指定します。 完全バックアップに比べ、差分バックアップの方が使用領域が少なくてすみます。 前回の完全バックアップ以降に実行された各ログ バックアップをすべて適用する必要がない場合に、このオプションを使用します。  
  
> [!NOTE]  
>  BACKUP DATABASE では、既定で完全バックアップが作成されます。  
  
 詳細については、「 [差分バックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/differential-backups-sql-server.md)」を参照してください。  
  
 ENCRYPTION  
 バックアップの暗号化を指定するために使用します。 バックアップを暗号化するための暗号化アルゴリズムを指定するか、バックアップを暗号化しない場合は "NO_ENCRYPION" を指定できます。 暗号化は、セキュリティで保護されたバックアップ ファイルを作成する場合に推奨される方法です。 指定できるアルゴリズムを次に示します。  
  
-   AES_128  
  
-   AES_192  
  
-   AES_256  
  
-   TRIPLE_DES_3KEY  
  
-   NO_ENCRYPTION  
  
 暗号化することを選択した場合、次の暗号化機能のオプションを使用して、暗号化機能も指定する必要があります。  
  
-   SERVER CERTIFICATE = Encryptor_Name  
  
-   SERVER ASYMMETRIC KEY = Encryptor_Name  
  
    > [!WARNING]  
    >  暗号化が FILE_SNAPSHOT 引数と組み合わせて使用し、指定した暗号化アルゴリズムを使用して、メタデータ ファイル自体が暗号化されて、システムでは、データベース用に TDE が完了したことを確認します。 データ自体の追加の暗号化が行われない。 データベースが暗号化されていないまたは backup ステートメントが発行された場合は、暗号化をする前に完了していない場合、バックアップは失敗します。  
  
**バックアップ セットのオプション**  
  
以下のオプションは、このバックアップ操作で作成されるバックアップ セットに対して有効なオプションです。  
  
> [!NOTE]  
>  復元操作用のバックアップ セットを指定するファイルを使用して** = ** * \<backup_set_file_number >*オプション。 バックアップ セットを指定する方法の詳細についてを参照してください「バックアップ セットの指定" [RESTORE の引数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-statements-arguments-transact-sql.md).
  
 COPY_ONLY  
 バックアップがあるを指定します、*コピーのみのバックアップ*、これは通常のバックアップ シーケンスには影響しません。 コピーのみのバックアップは定期的に行われる従来のバックアップとは別に作成するもので、 コピーのみのバックアップはありません、全体的なバックアップと復元、データベースのプロシージャです。  
  
 コピーのみのバックアップは、オンラインでファイルを復元する前にログをバックアップするなど、特殊な目的でバックアップを作成する場合にのみ使用してください。 通常、コピーのみのログ バックアップは 1 回だけ使用して、その後削除します。  
  
-   BACKUP DATABASE で COPY_ONLY オプションを使用した場合、作成される完全バックアップは差分ベースとして使用できません。 差分ビットマップは更新されず、後に実行する差分バックアップではコピーのみのバックアップは無視され、 従来のバックアップで作成された最新の完全バックアップがベースとして使用されます。  
  
    > [!IMPORTANT]  
    >  COPY_ONLY を DIFFERENTIAL と共に使用した場合、COPY_ONLY は無視され、差分バックアップが作成されます。  
  
-   ログのバックアップに使用する場合、COPY_ONLY オプションを作成、*コピーのみのログ バックアップ*、これは、トランザクション ログを切り捨てられません。 コピーのみのログ バックアップはログ チェーンに影響せず、他のログ バックアップはコピーのみのバックアップが存在しない場合と同様に動作します。  
  
詳細については、「[コピーのみのバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md)」を参照してください。  
  
{ COMPRESSION | NO_COMPRESSION }  
[!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)]し、それ以降のバージョンを指定するだけ、かどうか[バックアップの圧縮](../../relational-databases/backup-restore/backup-compression-sql-server.md)はこのバックアップは、サーバー レベルの既定値のオーバーライドで実行します。  
  
インストール時の既定の動作では、バックアップの圧縮は行われません。 この既定値を設定して変更できますが、[バックアップの圧縮の既定](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)サーバー構成オプション。 このオプションの現在の値を表示する方法については、次を参照してください。[ビューまたはサーバー プロパティの変更 & #40 です。SQL Server &#41;](../../database-engine/configure-windows/view-or-change-server-properties-sql-server.md).  
  
COMPRESSION  
バックアップの圧縮を明示的に有効にします。  
  
NO_COMPRESSION  
バックアップの圧縮を明示的に無効にします。  
  
DESCRIPTION **=** { **'***text***'** | **@***text_variable* }  
バックアップ セットを記述したテキストを自由な形式で指定します。 文字列の長さは最大 255 文字です。  
  
名前** = ** { *backup_set_name*| **@***backup_set_var* }  
バックアップ セットの名前を指定します。 名前の長さは最大 128 文字です。 NAME を指定しないと、名前は空白になります。  
  
{EXPIREDATE **='***日付***'**|RETAINDAYS ** = ** *日数*}  
このバックアップのバックアップ セットがいつ上書きできるようになるかを指定します。 オプションを両方とも使用した場合は、RETAINDAYS が EXPIREDATE よりも優先されます。  
  
有効期限の日付がによって決まりますがどちらのオプションが指定されている場合、 **mediaretention**構成設定。 詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)サーバー構成オプションを構成する方法について説明します。  
  
> [!IMPORTANT]  
>  これらのオプションを防ぐだけ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ファイルを上書きするからです。 テープは別の方法で消去することができ、ディスク ファイルはオペレーティング システムで削除できます。 有効期限の確認の詳細については、このトピックの「SKIP」および「FORMAT」を参照してください。  
  
EXPIREDATE ** = ** { **'***日付***'** |  ** @ ***date_var* }  
 バックアップ セットが失効して上書きできるようになる日を指定します。 変数として指定する場合 (@*date_var*)、この日付が構成されたシステムに従う必要があります**datetime**書式設定し、次のいずれかとして指定します。  
  
-   文字列定数 (@*date_var* ** = **日付)  
-   文字列データ型の変数 (を除き、 **ntext**または**テキスト**データ型)  
-   A **smalldatetime**  
-   A **datetime**変数  
  
例:  
  
-   `'Dec 31, 2020 11:59 PM'`  
-   `'1/1/2021'`  
  
指定する方法については**datetime**値を参照してください[日付と時刻型](../../t-sql/data-types/date-and-time-types.md)です。  
  
> [!NOTE]  
>  失効日を無視するには、SKIP オプションを使用します。  
  
RETAINDAYS ** = ** {*日数*| **@***days_var* }  
 このバックアップ メディア セットに上書きできるようになるまでの経過日数を指定します。 変数として指定する場合 (**@***days_var*)、整数として指定する必要があります。  
  
**メディア セットのオプション**  
  
以下のオプションはメディア セット全般に適用されます。  
  
{ **NOINIT** |INIT}  
 バックアップ操作で、バックアップ メディア上の既存のバックアップ セットに追加するか、上書きするかを制御します。 既定では、メディア上の最新のバックアップ セットに追加します (NOINIT)。  
  
> [!NOTE]  
>  間の相互作用について { **NOINIT** |INIT} と { **NOSKIP** |SKIP} では、このトピックの「解説」を参照してください。  
  
NOINIT  
 バックアップ セットを指定のメディア セットに追加します。この場合、既存のバックアップ セットは維持されます。 メディア セットのメディア パスワードが定義されている場合は、パスワードを指定する必要があります。 既定値は NOINIT です。  
  
詳細については、「 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。  
  
INIT  
 すべてのバックアップ セットを上書きします。ただし、メディア ヘッダーは維持されます。 INIT を指定した場合は、条件が満たされる限り、そのデバイス上にある既存のすべてのバックアップ セットが上書きされます。 既定では、BACKUP によって次の状況が確認され、いずれかの状況に該当する場合はバックアップ メディアは上書きされません。  
  
-   バックアップ セットがまだ期限切れではない。 詳細については、EXPIREDATE オプションおよび RETAINDAYS オプションの説明を参照してください。  
-   BACKUP ステートメントにバックアップ セットの名前が指定されていて、その名前がバックアップ メディア上の名前と一致していない。 詳細については、前の NAME オプションを参照してください。  
  
これらのチェックを無効にするには、SKIP オプションを使用します。  
  
詳細については、「 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。  
  
{ **NOSKIP** |SKIP}  
バックアップ操作で、上書き前にメディア上のバックアップ セットの失効日と失効時刻を確認するかどうかを制御します。  
  
> [!NOTE]  
>  間の相互作用について { **NOINIT** |INIT} と { **NOSKIP** |SKIP} では、このトピックの「解説」を参照してください。  
  
NOSKIP  
上書きを許可する前に、メディア上のすべてのバックアップ セットの有効期限を確認することを BACKUP ステートメントに指示します。 これは既定の動作です。  
  
SKIP  
バックアップ セットの有効期限と名前の確認を無効にします。この確認は、通常、バックアップ セットの上書きを防止するために BACKUP ステートメントによって実行されます。 { INIT | NOINIT } と { NOSKIP | SKIP } の相関関係については、後の「解説」を参照してください。  
バックアップ セットの有効期限の日付を表示するには、クエリ、 **expiration_date**の列、 [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)履歴テーブルです。  
  
{ **NOFORMAT** |形式}  
このバックアップ操作で使用するボリュームに新しいメディア ヘッダーを書き込み、既存のメディア ヘッダーとバックアップ セットを上書きするかどうかを指定します。  
  
NOFORMAT  
このバックアップ操作に使用するメディア ボリューム上の、既存のメディア ヘッダーとバックアップ セットを保持するよう指定します。 これは既定の動作です。  
  
FORMAT  
新しいメディア セットを作成するよう指定します。 FORMAT を指定した場合、バックアップ操作に使用するすべてのメディア ボリュームに、新しいメディア ヘッダーを書き込みます。 この場合、ボリューム上の既存のメディア ヘッダーとバックアップ セットは上書きされるので、それまであった内容は無効になります。  
  
> [!IMPORTANT]  
>  FORMAT の使用には注意が必要です。 メディア セットに属するボリュームを 1 つでも初期化すると、メディア セット全体が使用できなくなります。 たとえば、既存のストライプ メディア セットに属するテープを 1 つ初期化すると、このメディア セット全体が使用できなくなります。  
  
FORMAT を指定することは SKIP を実行することを意味します。SKIP を明示的に指定する必要はありません。  
  
MEDIADESCRIPTION ** = ** {*テキスト* | **@***text_variable* }  
メディア セットを記述した自由形式のテキストを最大 255 文字で指定します。  
  
MEDIANAME ** = ** { *media_name* | **@***media_name_variable* }  
バックアップ メディア セット全体に対するメディア名を指定します。 メディア名は最長 128 文字まで入力できます。MEDIANAME を指定する場合、バックアップ ボリュームに既に存在する、前回指定したメディア名と一致する必要があります。 MEDIANAME を指定しない場合、または SKIP オプションを指定した場合、メディア名の照合チェックは行われません。  
  
BLOCKSIZE ** = ** { *blocksize* | **@***blocksize_variable* }  
物理ブロック サイズをバイト単位で指定します。 サポートされるサイズは、512、1024、2048、4096、8192、16384、32768、および 65536 (64 KB) バイトです。 テープ デバイスの場合の既定値は 65536 バイトで、他のデバイスの場合の既定値は 512 バイトです。 通常は、BACKUP でデバイスに適したブロック サイズが自動的に選択されるので、このオプションは不要です。 ブロック サイズは、自動的に選択された値よりも明示的に指定された値が優先されます。  
  
バックアップを作成して CD-ROM に格納したり、CD-ROM からバックアップを復元する場合は、BLOCKSIZE=2048 と指定します。  
  
> [!NOTE]  
>  このオプションがパフォーマンスに影響するのは、通常、テープ デバイスに書き込むときだけです。  
  
**データ転送オプション**  
  
BUFFERCOUNT ** = ** { *buffercount* | **@***buffercount_variable* }  
バックアップ操作に使用される I/O バッファーの総数を指定します。 任意の正の整数を指定できますが、バッファー数が多いと Sqlservr.exe プロセスで仮想アドレス空間が不足し、"メモリ不足" エラーの原因となる場合があります。  
  
バッファーで使用される領域の合計はによって決定されます。 *buffercount***\****maxtransfersize*です。  
  
> [!NOTE]  
>  BUFFERCOUNT オプションを使用してに関する重要な情報は、次を参照してください。、 [OOM の状態につながる可能性が不適切な BufferCount データ転送オプション](http://blogs.msdn.com/b/sqlserverfaq/archive/2010/05/06/incorrect-buffercount-data-transfer-option-can-lead-to-oom-condition.aspx)ブログ。  
  
MAXTRANSFERSIZE ** = ** { *maxtransfersize* | **@***maxtransfersize_variable* }  
 間で使用できるをバイト単位で最大転送単位を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]とバックアップ メディア。 有効値は 65536 バイト (64 KB) の倍数で、最大有効値は 4194304 バイト (4 MB) です。  
> [!NOTE]  
>  データベースで構成されて FILESTREAM、か、インメモリ OLTP ファイル グループが含まれます場合に、SQL ライター サービスを使用してバックアップを作成するときに、`MAXTRANSFERSIZE`時的な部分復元のより大きいか等しくなければなりませんを`MAXTRANSFERSIZE`となった際に使用される、バックアップが作成されました。 
  
**エラー管理オプション**  
  
これらのオプションを使用すると、バックアップ操作でバックアップ チェックサムが有効にするかどうかと、エラー発生時に、操作を停止するかどうかを決定できます。  
  
{ **NO_CHECKSUM** |チェックサム}  
 バックアップのチェックサムを有効にするかどうかを制御します。  
  
NO_CHECKSUM  
バックアップ チェックサムの生成 (およびページ チェックサムの検証) を明示的に無効にします。 これは既定の動作です。  
  
CHECKSUM  
バックアップ操作が有効になっており、使用可能な場合は、各ページのチェックサムおよび破損ページをことを確認し、バックアップ全体のチェックサムを生成を指定します。  
  
バックアップ チェックサムを使用すると、ワークロードとバックアップのスループットに影響する場合があります。  
  
詳細については、次を参照してください[可能なメディア エラー時にバックアップと復元 &#40;。SQL Server &#41;](../../relational-databases/backup-restore/possible-media-errors-during-backup-and-restore-sql-server.md).  
  
{**場合は STOP_ON_ERROR** |CONTINUE_AFTER_ERROR}  
ページ チェックサム エラーの発生時、バックアップ操作を停止するか続行するかを制御します。  
  
STOP_ON_ERROR  
ページ チェックサムが正しくない場合、BACKUP を失敗させます。 これは既定の動作です。  
  
CONTINUE_AFTER_ERROR  
無効なチェックサム、ページの破損などのエラーが検出されても、BACKUP を継続します。  
  
末尾をバックアップできない場合、NO_TRUNCATE を使用してログ オプションのデータベースが破損している場合に試みることができます、[ログのログ末尾のバックアップ](../../relational-databases/backup-restore/tail-log-backups-sql-server.md)NO_TRUNCATE の代わりに CONTINUE_AFTER_ERROR を指定しています。  
  
詳細については、次を参照してください[可能なメディア エラー時にバックアップと復元 &#40;。SQL Server &#41;](../../relational-databases/backup-restore/possible-media-errors-during-backup-and-restore-sql-server.md).  
  
**互換性オプション**  
  
RESTART  
以降で[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]影響を与えません。 このオプションは、以前のバージョンの互換性のため、バージョンによって承認された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
**監視オプション**  
  
統計情報 [ ** = ***割合*]  
 ごとにメッセージが表示されます*割合*が完了し、進行状況の測定に使用されます。 場合*割合*を省略すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]各 10% が完了した後、メッセージが表示されます。  
  
STATS オプションでは、次のパーセンテージをレポートするためのしきい値に達した時点で、完了したパーセンテージがレポートされます。 このしきい値は、指定したパーセンテージを正確に反映するものではありません。たとえば STATS=10 の場合、40% が完了しても、43% の時点でメッセージが表示されることがあります。 大きいバックアップ セットの場合、これは重要な問題にはなりません。これは、完了した I/O 呼び出し間で、完了パーセンテージの変化が非常に遅くなるためです。  
  
**テープのオプション**  
  
このオプションはテープ デバイスにのみ適用されます。 テープ以外のデバイスが使用されている場合は、これらのオプションは無視されます。  
  
{ **REWIND** | NOREWIND }  
REWIND  
 指定する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を解放し、テープを巻き戻します。 既定値は REWIND です。  
  
NOREWIND  
指定する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はテープを開いたまま、バックアップ操作の後にします。 このオプションを使用すると、1 つのテープに複数のバックアップ操作を実行する場合のパフォーマンスを向上できます。  
  
NOREWIND は暗黙的に NOUNLOAD も意味しています。この 2 つのオプションを同一 BACKUP ステートメント内で同時に使用することはできません。  
  
> [!NOTE]  
>  NOREWIND を使用する場合、テープ ドライブの所有権は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスによって保持されます。同じプロセス内で実行される BACKUP ステートメントや RESTORE ステートメントで REWIND オプションまたは UNLOAD オプションが使用されるか、サーバー インスタンスがシャットダウンすると、所有権は解放されます。 テープを開いたままにすると、他のプロセスはそのテープにアクセスできません。 開いているテープの一覧を表示して、開いているテープを閉じる方法については、次を参照してください。[バックアップ デバイス & #40 です。SQL Server &#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
{**アンロード**|NOUNLOAD}  
> [!NOTE]  
>  UNLOAD または NOUNLOAD はセッションの設定であり、セッションが終了するまで、または代わりとなるオプションの指定によりリセットされるまで有効です。  
  
UNLOAD  
 バックアップ完了後、テープの巻き戻しおよびアンロードを自動的に行います。 UNLOAD はセッション開始時の既定の設定です。 
  
NOUNLOAD  
 テープのバックアップ処理は、テープ ドライブに読み込まれたまま後を指定します。  
  
> [!NOTE]  
>  テープ バックアップ デバイスへのバックアップの場合、BLOCKSIZE オプションはバックアップ操作のパフォーマンスに影響します。 このオプションがパフォーマンスに影響するのは、通常、テープ デバイスに書き込むときだけです。  
  
**ログに固有のオプション**  
  
以下のオプションは、BACKUP LOG でのみ使用するオプションです。  
  
> [!NOTE]  
>  ログ バックアップを作成しない場合は、単純復旧モデルを使用します。 詳細については、「[復旧モデル &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)」を参照してください。  
  
{NORECOVERY |スタンバイ** = ** *undo_file_name* }  
  NORECOVERY  
  ログの末尾をバックアップし、データベースを RESTORING の状態のままにします。 NORECOVERY は、セカンダリ データベースにフェールオーバーする場合、または RESTORE 操作の前にログの末尾を保存する場合に便利です。  
  
  ログの切り捨てをスキップするベストエフォートのログ バックアップを実行して、データベースを自動的に RESTORING 状態にするには、NO_TRUNCATE および NORECOVERY オプションを同時に使用します。  
  
  スタンバイ** = ** *standby_file_name*  
  ログの末尾をバックアップし、データベースを読み取り専用および STANDBY 状態のままにします。 STANDBY 句では、スタンバイ データが書き込まれます。ロールバックが実行されますが、追加の復元を行うこともできます。 STANDBY オプションの使用は、BACKUP LOG WITH NORECOVERY の後に RESTORE WITH STANDBY を使用する場合と同じ効果があります。  
  
  指定した、スタンバイ ファイルをスタンバイ モードを使用する必要があります*standby_file_name*、ある場所は、データベースのログに格納します。 指定したファイルが既に存在する場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]が上書きされます。 ファイルが存在しない場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]によって作成されます。 スタンバイ ファイルはデータベースの一部となります。  
  
  このファイルには、ロールバックされた変更内容が含まれています。RESTORE LOG 操作を後で適用する場合、これらの変更内容の順序を逆にする必要があります。 スタンバイ ファイルでは、ファイル サイズが増加するので、ディスクに十分な空き容量が必要です。これは、コミットされていないトランザクションのロールバックによって変更が加えられた、データベース内にあるすべてのページを保存できるようにするためです。  
  
NO_TRUNCATE  
指定、ログの切り捨ては、原因、[!INCLUDE[ssDE](../../includes/ssde-md.md)]データベースの状態に関係なくバックアップが行われる。 その結果、NO_TRUNCATE で実行されるバックアップに不完全なメタデータが含まれる場合があります。 このオプションを使用すると、データベースが破損している場合でもログをバックアップできます。  
  
BACKUP LOG の NO_TRUNCATE オプションを指定すると、COPY_ONLY と CONTINUE_AFTER_ERROR の両方を指定する場合と同じ結果が得られます。  
  
NO_TRUNCATE オプションを使用しない場合は、データベースが ONLINE 状態である必要があります。 データベースが SUSPENDED 状態の場合は、NO_TRUNCATE を指定することによってバックアップを作成できる可能性がありますが、 データベースが OFFLINE または EMERGENCY 状態の場合、NO_TRUNCATE を使用しても BACKUP を実行できません。 データベースの状態については、次を参照してください。[データベースの状態](../../relational-databases/databases/database-states.md)です。  
  
## <a name="about-working-with-sql-server-backups"></a>SQL Server バックアップの操作について  
 このセクションでは、次の基本的なバックアップの概念について説明します。  
  
 [バックアップの種類](#Backup_Types)  
 [トランザクション ログの切り捨て](#Tlog_Truncation)  
 [バックアップ メディアを書式設定](#Formatting_Media)  
 [バックアップ デバイスとメディア セットの操作](#Backup_Devices_and_Media_Sets)  
 [SQL Server のバックアップを復元します。](#Restoring_Backups)  
  
> [!NOTE]  
>  バックアップの概要について[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[バックアップの概要 & #40 です。SQL Server &#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md).  
  
###  <a name="Backup_Types"></a>バックアップの種類  
 実行できるバックアップの種類は、次のようにデータベースの復旧モデルに依存します。  
  
-   データの完全バックアップと差分バックアップはすべての復旧モデルで実行できます。  
  
    |バックアップの範囲|バックアップの種類|  
    |---------------------|------------------|  
    |データベース全体|[データベース バックアップ](../../relational-databases/backup-restore/full-database-backups-sql-server.md)データベース全体をカバーします。<br /><br /> 各データベースのバックアップを一連の 1 つまたは複数のベースとして使用できます必要に応じて、[データベースの差分バックアップ](../../relational-databases/backup-restore/differential-backups-sql-server.md)です。|  
    |データベースの部分バックアップ|[部分バックアップ](../../relational-databases/backup-restore/partial-backups-sql-server.md)カバーの読み取り/書き込みファイル グループと、場合によっては 1 つ以上読み取り専用のファイルまたはファイル グループ。<br /><br /> 各部分バックアップを一連の 1 つまたは複数のベースとして使用できます必要に応じて、[部分的な差分バックアップ](../../relational-databases/backup-restore/differential-backups-sql-server.md)です。|  
    |ファイルまたはファイル グループ|[ファイル バックアップ](../../relational-databases/backup-restore/full-file-backups-sql-server.md)1 つ以上のファイルまたはファイル グループ、カバー、複数のファイル グループを含むデータベースだけに関するものです。 単純復旧モデルでは、ファイル バックアップは原則として読み取り専用セカンダリ ファイル グループに限定されます。<br /> 各ファイルのバックアップを一連の 1 つまたは複数のベースとして使用できます必要に応じて、[ファイルの差分バックアップ](../../relational-databases/backup-restore/differential-backups-sql-server.md)です。|  
  
-   完全復旧モデルまたは一括ログ復旧モデルでは、従来のバックアップも含めるシーケンシャル*トランザクション ログ バックアップ*(または*ログ バックアップ*)、これが必要です。 各ログ バックアップでは、トランザクション ログのうち、バックアップが作成された時点でアクティブだった部分と、前回のログ バックアップでバックアップされなかったすべてのログ レコードが対象となります。  
  
     作業損失の可能性を最小に抑えるには、管理のオーバーヘッドが発生するという犠牲を払っても、ログ バックアップを頻繁に行うようスケジュールする必要があります。 完全バックアップの合間に差分バックアップを行うようにスケジュールすると、データを復元した後で復元する必要のあるログ バックアップの数が減るので、復元時間を短縮することができます。  
  
     ログ バックアップは、データベースのバックアップとは別のボリュームに配置することをお勧めします。  
  
    > [!NOTE]  
    >  最初のログ バックアップを作成するには、その前に完全バックアップを作成する必要があります。  
  
-   A*コピーのみのバックアップ*は特殊な用途の完全バックアップまたはログ バックアップの従来のバックアップの通常のシーケンスから独立しました。 コピーのみのバックアップを作成するには、BACKUP ステートメントで COPY_ONLY オプションを指定します。 詳細については、「[コピーのみのバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md)」を参照してください。  
  
###  <a name="Tlog_Truncation"></a>トランザクション ログの切り捨て  
 データベースのトランザクション ログがいっぱいにならないように、トランザクション ログを定期的にバックアップする必要があります。 ログの切り捨ては、単純復旧モデルではデータベースのバックアップ後に、完全復旧モデルではトランザクション ログのバックアップ後に自動的に行われます。 ただし、切り捨ての処理が遅れる場合もあります。 ログの切り捨てが遅れる要因については、「[トランザクション ログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)」を参照してください。  
  
> [!NOTE]  
>  BACKUP LOG WITH NO_LOG オプションと WITH TRUNCATE_ONLY オプションは廃止されました。 完全復旧モデルまたは一括ログ復旧モデルの復旧を使用している場合に、ログ バックアップ チェーンをデータベースから削除するには、単純復旧モデルに切り替える必要があります。 詳細については、「[データベースの復旧モデルの表示または変更 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)」を参照してください。  
  
###  <a name="Formatting_Media"></a>バックアップ メディアを書式設定  
 次の条件のいずれか 1 つでも該当する場合は、BACKUP ステートメントでバックアップ メディアがフォーマットされます。  
  
-   FORMAT オプションが指定されている。  
-   メディアが空である。  
-   連続するテープに書き込んでいる。  
  
###  <a name="Backup_Devices_and_Media_Sets"></a>バックアップ デバイスとメディア セットの操作  
  
#### <a name="backup-devices-in-a-striped-media-set-a-stripe-set"></a>ストライプ メディア セット (ストライプ セット) 内のバックアップ デバイス  
 A*セットをストライピング*は、一連のディスク ファイル データのブロックに分割され、一定の順序で分散します。 ストライプ セットで使用されるバックアップ デバイスの数は、(FORMAT でメディアを最初期化する場合を除いて) 常に同じである必要があります。  
  
 次の例では、バックアップ、 [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 3 つのディスク ファイルを使用する新しいストライプ メディア セットへのデータベースです。  
  
```sql  
BACKUP DATABASE AdventureWorks2012  
TO DISK='X:\SQLServerBackups\AdventureWorks1.bak',   
DISK='Y:\SQLServerBackups\AdventureWorks2.bak',   
DISK='Z:\SQLServerBackups\AdventureWorks3.bak'  
WITH FORMAT,  
   MEDIANAME = 'AdventureWorksStripedSet0',  
   MEDIADESCRIPTION = 'Striped media set for AdventureWorks2012 database;  
GO  
```  
  
 バックアップ デバイスをいったんストライプ セットの一部として定義すると、FORMAT を指定しない限り、ファイル単位のバックアップに使用することはできません。 同様に、非ストライプ バックアップを含むバックアップ デバイスは、FORMAT を指定しない限り、ストライプ セットでは使用できません。 ストライプ バックアップ セットを分割するには、FORMAT を使用します。  
  
 MEDIANAME と MEDIADESCRIPTION のどちらも指定すると、メディア ヘッダーが書き込まれるときに、空のアイテムに対応するメディアのヘッダー フィールドが空です。  
  
#### <a name="working-with-a-mirrored-media-set"></a>ミラー化されたメディア セットの操作  
 通常、バックアップはミラー化せず、BACKUP ステートメントには TO 句のみを指定しますが、 メディア セットあたり 4 つまでミラーを指定できます。 ミラー化されたメディア セットの場合、バックアップ操作では、バックアップ デバイスの複数のグループに書き込みが行われます。 このバックアップ デバイスの各グループが、ミラー化されたメディア セット内の 1 つのミラーとなります。 それぞれのミラーでは同じ容量および種類の物理バックアップ デバイスを使用する必要があり、プロパティがすべて同じである必要があります。  
  
 ミラー化されたメディア セットにバックアップを作成するには、ミラーがすべて存在している必要があります。 ミラー化されたメディア セットにバックアップするには、TO 句に 1 つ目のミラーを指定し、MIRROR TO 句にその他のミラーをそれぞれ指定します。  
  
 ミラー化されたメディア セットの場合、各 MIRROR TO 句では、TO 句と同じ数および種類のデバイスのリストを指定する必要があります。 次の例では、ミラー化されたメディア セットに書き込みます。このメディア セットには 2 つのミラーが含まれ、それぞれで 3 つのデバイスが使用されています。  
  
```sql  
BACKUP DATABASE AdventureWorks2012  
TO DISK='X:\SQLServerBackups\AdventureWorks1a.bak',   
DISK='Y:\SQLServerBackups\AdventureWorks2a.bak',   
DISK='Z:\SQLServerBackups\AdventureWorks3a.bak'  
MIRROR TO DISK='X:\SQLServerBackups\AdventureWorks1b.bak',   
DISK='Y:\SQLServerBackups\AdventureWorks2b.bak',   
DISK='Z:\SQLServerBackups\AdventureWorks3b.bak';  
GO  
```  
  
> [!IMPORTANT]  
>  この例は、ローカル システム上でテストできるように設計されています。 実際には同じドライブ上にある複数のデバイスにバックアップすると、パフォーマンスが低下するおそれがあり、ミラー化されたメディア セットの設計目的でもある冗長性が損なわれる可能性があります。  
  
##### <a name="media-families-in-mirrored-media-sets"></a>ミラー化されたメディア セットのメディア ファミリ  
 BACKUP ステートメントの TO 句で指定する各バックアップ デバイスは、1 つのメディア ファミリとなります。 たとえば、TO 句で 3 つのデバイスのリストを指定する場合、BACKUP では 3 つのメディア ファミリにデータが書き込まれます。 ミラー化されたメディア セットでは、各ミラーにすべてのメディア ファミリのコピーが含まれている必要があります。 このため、各ミラーでデバイス数が一致する必要があります。  
  
 各ミラーに対し複数のデバイスのリストを指定する順番によって、どのメディア ファミリがどのデバイスに書き込まれるかが決まります。 たとえば、各デバイスのリストで、2 番目のデバイスは 2 番目のメディア ファミリに対応します。 先に示した例のデバイスでは、デバイスとメディア ファミリの対応は次の表のようになります。  
  
|ミラー|メディア ファミリ 1|メディア ファミリ 2|メディア ファミリ 3|  
|------------|--------------------|--------------------|--------------------|  
|0|`Z:\AdventureWorks1a.bak`|`Z:\AdventureWorks2a.bak`|`Z:\AdventureWorks3a.bak`|  
|1|`Z:\AdventureWorks1b.bak`|`Z:\AdventureWorks2b.bak`|`Z:\AdventureWorks3b.bak`|  
  
 1 つのメディア ファミリは常に、特定のミラー内の同じデバイス上にバックアップされる必要があります。 したがって、既存のメディア セットを使用するときは毎回、メディア セットを作成したときと同じ順序で各ミラーのデバイスを列挙してください。  
  
 ミラー化メディア セットの詳細については、 [Mirrored Backup Media Sets &#40;SQL Server&#41;](../../relational-databases/backup-restore/mirrored-backup-media-sets-sql-server.md)のバックアップと復元で使用する基本的なバックアップ メディア用語を紹介します。 メディア セットおよび一般内のメディア ファミリに関する詳細については、次を参照してください。[メディア セット、メディア ファミリ、およびバックアップ セット (&) #40 です。SQL Server &#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md).  
  
###  <a name="Restoring_Backups"></a>SQL Server のバックアップを復元します。  
 データベースを復元し、必要に応じて、オンライン、または、ファイルまたはファイル グループを復元することを復旧するには、いずれかの操作を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)] [復元](../../t-sql/statements/restore-statements-transact-sql.md)ステートメントまたは[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**復元**タスク。 詳細については、次を参照してください。[復元と復旧の概要 & #40 です。SQL Server &#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md).  
  
##  <a name="Additional_Considerations"></a>バックアップ オプションに関する追加の考慮事項  
  
###  <a name="Interactions_SKIP_etc"></a>SKIP、NOSKIP、INIT、および NOINIT の相互作用  
 次の表の間のやり取り、{ **NOINIT** |INIT} と { **NOSKIP** |SKIP} オプションです。  
  
> [!NOTE]  
>  テープ メディアが空の場合、またはディスクのバックアップ ファイルが存在しない場合は、これらすべての相関関係に基づいて、メディア ヘッダーが記述され、操作が継続します。 ただしメディアが空でなく、有効なメディア ヘッダーが含まれない場合、これらの操作では有効な MTF メディアでないことが返され、バックアップ操作は中断されます。  
  
||NOINIT|INIT|  
|------|------------|----------|  
|NOSKIP|ボリュームに有効なメディア ヘッダーが含まれる場合は、MEDIANAME が指定されていれば、その値とメディア名が一致していることを確認します。 メディア名が一致した場合は、すべての既存のバックアップ セットはそのままにして、バックアップ セットを追加します。<br /> ボリュームに有効なメディア ヘッダーが含まれない場合は、エラーが発生します。|ボリュームに有効なメディア ヘッダーが含まれている場合は、次のチェックを実行します。<br /> -MEDIANAME が指定されている場合は、特定のメディア名と一致しているメディア ヘッダーのメディア name.* * ことを確認します。<br /> -メディアには既に期限が切れていないバックアップ セットがないことを確認します。 存在している場合は、バックアップを中断します。<br /> 上のチェックにパスした場合は、メディア ヘッダーだけをそのままにして、メディア上のすべてのバックアップ セットを上書きします。<br /> ボリュームに有効なメディア ヘッダーが含まれない場合は、MEDIANAME および MEDIADESCRIPTION が指定されていれば、これらのオプションを使用してメディア ヘッダーを生成します。|  
|SKIP|ボリュームに有効なメディア ヘッダーが含まれる場合は、すべての既存のバックアップ セットをそのままにして、バックアップ セットを追加します。|ボリュームが含まれていますが、有効な場合 * メディア ヘッダーが、メディア ヘッダーだけをそのまま、メディア上のすべてのバックアップ セットが上書きされます。<br /> メディアが空の場合は、MEDIANAME および MEDIADESCRIPTION が指定されていれば、これらのオプションを使用してメディア ヘッダーを生成します。|  
  
 * 有効性には、MTF のバージョン番号とその他のヘッダー情報が含まれています。 指定されたバージョンがサポートされていないか、予期しない値の場合、エラーが発生します。  
  
 * *、ユーザーは、バックアップ操作を実行する適切な固定データベースまたはサーバー ロールに属している必要があります。  
  
## <a name="compatibility"></a>互換性  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって作成されたバックアップは、それより前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では復元できません。  
  
 バックアップの以前のバージョンとの下位互換性を提供するのには、再起動オプションをサポートしている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 ただし、RESTART は無効です。  
  
## <a name="general-remarks"></a>全般的な解説  
 データベースやログのバックアップは、任意のディスクまたはテープ デバイスに追加できます。これによって、データベースとそのトランザクション ログをすべて 1 つの物理位置に格納できます。  
  
 BACKUP ステートメントは、明示的または暗黙的なトランザクションでは使用できません。  
  
 オペレーティング システムがデータベースの照合順序をサポートしている場合は、プロセッサの種類が違っていても、1 つのプラットフォームから別のプラットフォームにわたるバックアップ操作を実行できます。  
  
> [!NOTE]  
>  既定では、バックアップ操作が成功するたびに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログおよびシステム イベント ログにエントリが 1 つ追加されます。 ログを頻繁にバックアップすると、これらの成功メッセージがすぐに蓄積され、他のメッセージを探すのが困難になるほどエラー ログが大きくなることがあります。 そのような場合、これらのエントリに依存するスクリプトがなければ、トレース フラグ 3226 を使用することによってこれらのログ エントリを除外できます。 詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)」を参照してください。  
  
## <a name="interoperability"></a>相互運用性  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースが使用されているときに、データベースのバックアップを許可するのにには、オンラインのバックアップ プロセスを使用します。 バックアップ中はほとんどの操作が可能です。たとえば、INSERT、UPDATE、または DELETE ステートメントはバックアップ操作中でも使用できます。  
  
 データベース バックアップやトランザクション ログ バックアップ中に実行できない操作には次のものがあります。  
  
-   ADD FILE または REMOVE FILE オプションのいずれかで ALTER DATABASE ステートメントなどの管理操作をファイルです。  
  
-   データベースまたはファイルの圧縮操作。 これには自動圧縮操作も含まれます。  
  
バックアップ操作がファイル管理または圧縮操作と重複すると、競合が発生します。 どの競合操作が最初に始まったかに関係なく、最初の操作によって設定されたロックがタイムアウトになるまで、2 番目の操作は待機します (タイムアウト時間はセッション タイムアウト設定で制御されます)。 ロックがタイムアウト期間内に解放されると、2 番目の操作が開始されます。 ロックがタイムアウトになると、2 番目の操作は実行されません。  
  
## <a name="metadata"></a>メタデータ  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バックアップのアクティビティを追跡する次のバックアップ履歴テーブルが含まれています。  
  
-   [backupfile & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/backupfile-transact-sql.md)  
-   [backupfilegroup & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
-   [backupmediafamily & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
-   [backupmediaset & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
-   [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
復元が行われる場合、バックアップ セットがまだに記録されていない場合、 **msdb**データベース、バックアップ履歴テーブルを変更する可能性があります。  
  
## <a name="security"></a>セキュリティ  
 以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、**パスワード**と**MEDIAPASSWORD**バックアップを作成するオプションが廃止されました。 これは、パスワード付きで作成されたバックアップを復元することも可能です。  
  
### <a name="permissions"></a>Permissions  
 BACKUP DATABASE 権限と BACKUP LOG 権限は、既定では、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_backupoperator** 固定データベース ロールのメンバーに与えられています。  
  
 バックアップ デバイスの物理ファイルに対する所有と許可の問題によって、バックアップ操作が妨げられることがあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、デバイスに対して読み書きを実行できる必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されているアカウントには書き込み権限が必要です。 ただし、システム テーブルにバックアップ デバイスのエントリを追加する [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)では、ファイル アクセスの権限は確認されません。 バックアップ デバイスの物理ファイルに関するこのような問題は、バックアップや復元が試行され、物理リソースがアクセスされるまで、表面化しない可能性があります。  
  
##  <a name="examples"></a> 使用例  
 ここでは、次の例について説明します。  
  
-   A. [データベース全体をバックアップする](#backing_up_db)  
-   B. [データベースおよびログをバックアップします。](#backing_up_db_and_log)  
-   C. [セカンダリ ファイル グループのファイルの完全バックアップを作成します。](#full_file_backup)  
-   D. [セカンダリ ファイル グループのファイルの差分バックアップを作成します。](#differential_file_backup)  
-   E. [セットを作成し、ファミリ ミラー化メディアへのバックアップ](#create_single_family_mirrored_media_set)  
-   F. [セットを作成し、マルチファミリ ミラー化メディアへのバックアップ](#create_multifamily_mirrored_media_set)  
-   G[ミラー化メディア セットの既存のバックアップ](#existing_mirrored_media_set)  
-   H. [新しいメディア セットに圧縮されたバックアップを作成します。](#creating_compressed_backup_new_media_set)  
-   I.  [Microsoft Azure Blob ストレージ サービスへのバックアップ](#url)  
  
> [!NOTE]  
>  バックアップ方法に関するトピックで、さらに例を記載しています。 詳細については、「 [バックアップの概要 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)」を参照してください。  
  
###  <a name="backing_up_db"></a> A. データベース全体をバックアップする  
 次の例でをバックアップ、[!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)]データベースをディスク ファイル。  
  
```sql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH FORMAT;  
GO  
```  
  
###  <a name="backing_up_db_and_log"></a> B. データベースおよびログをバックアップする  
 次の例では、既定により単純復旧モデルを使用する [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースをバックアップします。 ここではまず、ログをバックアップするため、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを修正して完全復旧モデルを使用するようにします。  
  
 例を使用して次に、 [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)論理を作成する[バックアップ デバイス](../../relational-databases/backup-restore/backup-devices-sql-server.md)、データをバックアップする`AdvWorksData`、し、ログをバックアップするための別の論理バックアップ デバイスを作成`AdvWorksLog`です。  
  
 データベースの完全バックアップを作成し`AdvWorksData`、更新操作の期間後に、ログ バックアップと`AdvWorksLog`です。  
  
```sql  
-- To permit log backups, before the full database backup, modify the database   
-- to use the full recovery model.  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
   SET RECOVERY FULL;  
GO  
-- Create AdvWorksData and AdvWorksLog logical backup devices.   
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'AdvWorksData',   
'Z:\SQLServerBackups\AdvWorksData.bak';  
GO  
EXEC sp_addumpdevice 'disk', 'AdvWorksLog',   
'X:\SQLServerBackups\AdvWorksLog.bak';  
GO  
  
-- Back up the full AdventureWorks2012 database.  
BACKUP DATABASE AdventureWorks2012 TO AdvWorksData;  
GO  
-- Back up the AdventureWorks2012 log.  
BACKUP LOG AdventureWorks2012  
   TO AdvWorksLog;  
GO  
```  
  
> [!NOTE]  
>  運用データベースでは、ログを定期的にバックアップしてください。 ログのバックアップは、データ損失を防ぐため、頻繁に行ってください。  
  
###  <a name="full_file_backup"></a> C. セカンダリ ファイル グループの完全ファイル バックアップを作成する  
 次の例では、両方のセカンダリ ファイル グループ内のすべてのファイルについて、完全ファイル バックアップを作成します。  
  
```sql  
--Back up the files in SalesGroup1:  
BACKUP DATABASE Sales  
   FILEGROUP = 'SalesGroup1',  
   FILEGROUP = 'SalesGroup2'  
   TO DISK = 'Z:\SQLServerBackups\SalesFiles.bck';  
GO  
```  
  
###  <a name="differential_file_backup"></a> D. セカンダリ ファイル グループの差分ファイル バックアップを作成する  
 次の例では、両方のセカンダリ ファイル グループ内のすべてのファイルについて、差分ファイル バックアップを作成します。  
  
```sql  
--Back up the files in SalesGroup1:  
BACKUP DATABASE Sales  
   FILEGROUP = 'SalesGroup1',  
   FILEGROUP = 'SalesGroup2'  
   TO DISK = 'Z:\SQLServerBackups\SalesFiles.bck'  
   WITH   
      DIFFERENTIAL;  
GO  
```  
  
###  <a name="create_single_family_mirrored_media_set"></a> E. 単一ファミリ ミラー化メディア セットを作成し、そこにバックアップを作成する  
 次の例は、ミラー化メディア セットを含む 1 つのメディア ファミリと 4 つのミラーを作成し、バックアップ、[!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)]データベースにします。  
  
```sql  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0'  
MIRROR TO TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2'  
MIRROR TO TAPE = '\\.\tape3'  
WITH  
   FORMAT,  
   MEDIANAME = 'AdventureWorksSet0';  
```  
  
###  <a name="create_multifamily_mirrored_media_set"></a> F. マルチファミリ ミラー化メディア セットを作成し、そこにバックアップを作成する  
 次の例では、各ミラーが 2 つのメディア ファミリで構成されているミラー化メディア セットを作成します。 例では、バックアップし、[!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)]を両方のミラー データベース。  
  
```sql  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
   FORMAT,  
   MEDIANAME = 'AdventureWorksSet1';  
```  
  
###  <a name="existing_mirrored_media_set"></a>G. 既存のミラー化メディア セットにバックアップを作成する  
 次の例では、前の例で作成されたメディア セットにバックアップ セットを追加します。  
  
```sql  
BACKUP LOG AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH   
   NOINIT,  
   MEDIANAME = 'AdventureWorksSet1';  
```  
  
> [!NOTE]  
>  NOINIT は既定値ですが、ここではわかりやすくするために記載しています。  
  
###  <a name="creating_compressed_backup_new_media_set"></a>H. 新しいメディア セットに圧縮されたバックアップを作成する  
 次の例形式に新しいメディアを作成して、メディア セットにしの圧縮された完全バックアップを実行、[!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)]データベース。  
  
```sql  
BACKUP DATABASE AdventureWorks2012 TO DISK='Z:\SQLServerBackups\AdvWorksData.bak'   
WITH   
   FORMAT,   
   COMPRESSION;  
```  

###  <a name="url"></a>私。 Microsoft Azure BLOB ストレージ サービスへのバックアップ 
データベースの完全バックアップを実行する例では、 `Sales` Microsoft Azure Blob ストレージ サービスにします。  ストレージ アカウント名は `mystorageaccount`です。  コンテナーは `myfirstcontainer`と呼ばれます。  保存されたアクセス ポリシーは読み取り、書き込み、削除および一覧表示権で作成されています。  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資格情報、 `https://mystorageaccount.blob.core.windows.net/myfirstcontainer`、保存されたアクセス ポリシーに関連付けられている共有アクセス署名を使用して作成されました。  について[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows Azure Blob ストレージ サービスへのバックアップ、参照[SQL Server Backup and Restore with Microsoft Azure Blob Storage Service](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)と[SQL Server Backup to URL](../../relational-databases/backup-restore/sql-server-backup-to-url.md)です。

```sql  
BACKUP DATABASE Sales
TO URL = 'https://mystorageaccount.blob.core.windows.net/myfirstcontainer/Sales_20160726.bak'
WITH STATS = 5;
```

  
## <a name="see-also"></a>参照  
 [バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [ログ末尾のバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/tail-log-backups-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [DBCC SQLPERF & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)   
 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)   
 [RESTORE LABELONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [sp_helpfile を実行 & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sp_helpfilegroup & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpfilegroup-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [メモリ最適化テーブルを持つデータベースの段階的な部分復元](../../relational-databases/in-memory-oltp/piecemeal-restore-of-databases-with-memory-optimized-tables.md)  
  
  

