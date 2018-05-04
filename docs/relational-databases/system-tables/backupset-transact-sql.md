---
title: バックアップ セット (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- backupset
- backupset_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backupset system table
- backup media [SQL Server], backupset system table
- backup sets [SQL Server]
ms.assetid: 6ff79bbf-4acf-4f75-926f-38637ca8a943
caps.latest.revision: 70
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 65d39eb0f4797ceb5e32c663cabbccfaeac12f23
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="backupset-transact-sql"></a>backupset (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  バックアップ セットごとに 1 行のデータを格納します。 *バックアップ セット* には、正常に終了した 1 つのバックアップ操作のバックアップが含まれます。 RESTORE、RESTORE FILELISTONLY、RESTORE HEADERONLY、および RESTORE VERIFYONLY ステートメントは、単一または複数の指定バックアップ デバイス上のメディア セット内にある単一のバックアップ セットに対して機能します。  
  
 次の表は、 **msdb**データベース。  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**backup_set_id**|**int**|バックアップ セットを識別する一意なバックアップ セット識別番号。 ID、主キー。|  
|**backup_set_uuid**|**uniqueidentifier**|バックアップ セットを識別する一意なバックアップ セット識別番号。|  
|**media_set_id**|**int**|バックアップ セットを含むメディア セットを識別する一意なメディア セット識別番号。 参照 **(media_set_id)** です。|  
|**first_family_number**|**tinyint**|バックアップ セットの先頭メディアのファミリ番号。 NULL を指定できます。|  
|**first_media_number**|**smallint**|バックアップ セットの先頭メディアのメディア番号。 NULL を指定できます。|  
|**last_family_number**|**tinyint**|バックアップ セットの最終メディアのファミリ番号。 NULL を指定できます。|  
|**last_media_number**|**smallint**|バックアップ セットの最終メディアのメディア番号。 NULL を指定できます。|  
|**catalog_family_number**|**tinyint**|バックアップ セット ディレクトリの先頭を含むメディアのファミリ番号。 NULL を指定できます。|  
|**catalog_media_number**|**smallint**|バックアップ セット ディレクトリの先頭を含むメディアのメディア番号。 NULL を指定できます。|  
|**position**|**int**|復元操作で、該当するバックアップ セットとファイルを検出するために使用されるバックアップ セットの位置。 NULL を指定できます。 詳細については、ファイルを参照して[バックアップ&#40;TRANSACT-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)です。|  
|**expiration_date**|**datetime**|バックアップ セットの期限が切れる日付と時刻。 NULL を指定できます。|  
|**software_vendor_id**|**int**|バックアップ メディア ヘッダーを記述するソフトウェア ベンダーの識別番号。 NULL を指定できます。|  
|**name**|**nvarchar(128)**|バックアップ セットの名前。 NULL を指定できます。|  
|**説明**|**nvarchar (255)**|バックアップ セットの説明です。 NULL を指定できます。|  
|**user_name**|**nvarchar(128)**|バックアップ操作を実行するユーザー名。 NULL を指定できます。|  
|**software_major_version**|**tinyint**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メジャー バージョン番号。 NULL を指定できます。|  
|**software_minor_version**|**tinyint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマイナー バージョン番号。 NULL を指定できます。|  
|**software_build_version**|**smallint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のビルド番号。 NULL を指定できます。|  
|**time_zone**|**smallint**|バックアップ操作が行われている現地時間と、協定世界時 (UTC) の差 (15 分間隔)。 値は、-48 ～ +48 の範囲になります。 値 127 は、不明な状態を表します。 たとえば、-20 は東部標準時刻 (EST) を表し、これは UTC の 5 時間前にあたります。 NULL を指定できます。|  
|**mtf_minor_version**|**tinyint**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Tape Format のマイナー バージョン番号。 NULL を指定できます。|  
|**first_lsn**|**numeric(25,0)**|バックアップ セット内の先頭または最も古いログ レコードのログ シーケンス番号。 NULL を指定できます。|  
|**last_lsn**|**numeric(25,0)**|バックアップ セットの次のログ レコードのログ シーケンス番号。 NULL を指定できます。|  
|**checkpoint_lsn**|**numeric(25,0)**|再実行を開始する必要があるログ レコードのログ シーケンス番号。 NULL を指定できます。|  
|**database_backup_lsn**|**numeric(25,0)**|データベース全体の最新バックアップのログ シーケンス番号。 NULL を指定できます。<br /><br /> **database_backup_lsn**は、"チェックポイントの先頭"、バックアップの開始時にトリガーされます。 この LSN は同時になる**first_lsn**場合は、データベースがアイドル状態で、レプリケーションが構成されていないときに、バックアップを実行します。|  
|**database_creation_date**|**datetime**|データベースが最初に作成された日付と時刻。 NULL を指定できます。|  
|**backup_start_date**|**datetime**|バックアップ操作が開始された日付と時刻。 NULL を指定できます。|  
|**backup_finish_date**|**datetime**|バックアップ操作が終了した日付と時刻。 NULL を指定できます。|  
|**type**|**char(1)**|バックアップの種類。 次の値をとります。<br /><br /> D = データベース<br /><br /> I = データベースの差分<br /><br /> L = ログ<br /><br /> F = ファイルまたはファイル グループ<br /><br /> G = ファイルの差分<br /><br /> P = 部分的<br /><br /> Q = 部分的な差分<br /><br /> NULL を指定できます。|  
|**sort_order**|**smallint**|バックアップ操作を実行するサーバーの並べ替え順。 NULL を指定できます。 並べ替え順序および照合順序の詳細については、次を参照してください。 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)です。|  
|**code_page**|**smallint**|バックアップ操作を実行するサーバーのコード ページ。 NULL を指定できます。 コード ページの詳細については、次を参照してください。 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)です。|  
|**compatibility_level**|**tinyint**|データベースに対する互換性レベルの設定。 次の値をとります。<br /><br /> 90 = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> 100 = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<br /><br /> 110 = [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]<br /><br /> 120 = [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]<br /><br /> NULL を指定できます。<br /><br /> 互換性レベルの詳細については、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」を参照してください。|  
|**database_version**|**int**|データベースのバージョン番号。 NULL を指定できます。|  
|**backup_size**|**numeric(20,0)**|バックアップ セットのサイズ (バイト単位)。 NULL を指定できます。 VSS バックアップ backup_size は推定値です。|  
|**database_name**|**nvarchar(128)**|バックアップ操作に関係するデータベース名。 NULL を指定できます。|  
|**server_name**|**nvarchar(128)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップ操作を実行しているサーバー名。 NULL を指定できます。|  
|**machine_name**|**nvarchar(128)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行しているコンピューターの名前。 NULL を指定できます。|  
|**flags**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、**フラグ**列は廃止されており、次のビット列で置き換えられます。<br /><br /> **has_bulk_logged_data** <br /> **is_snapshot** <br /> **is_readonly** <br /> **is_single_user** <br /> **has_backup_checksums** <br /> **is_damaged** <br /> **begins_log_chain** <br /> **has_incomplete_metadata** <br /> **is_force_offline** <br /> **is_copy_only**<br /><br /> NULL を指定できます。<br /><br /> 以前のバージョンからのバックアップ セットで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ビット フラグを設定します。<br />1 = バックアップには最小限のログ データが含まれている。 <br />2 = WITH SNAPSHOT が使用された。 <br />4 = データベースがバックアップ時に読み取り専用だった。<br />8 = バックアップ時、データベースはシングル ユーザー モードであった。|  
|**unicode_locale**|**int**|Unicode ロケール。 NULL を指定できます。|  
|**unicode_compare_style**|**int**|Unicode の比較形式。 NULL を指定できます。|  
|**collation_name**|**nvarchar(128)**|照合順序名。 NULL を指定できます。|  
|**Is_password_protected**|**bit**|バックアップ セット。<br /><br /> パスワードの保護は次のとおりです。<br /><br /> 0 = 保護されていない<br /><br /> 1 = 保護されている|  
|**recovery_model**|**nvarchar(60)**|データベースの復旧モデル。<br /><br /> FULL<br /><br /> BULK-LOGGED <br /><br /> SIMPLE|  
|**has_bulk_logged_data**|**bit**|1 = 一括ログ データを含むバックアップ。|  
|**is_snapshot**|**bit**|1 = バックアップは SNAPSHOT オプションで実行された。|  
|**is_readonly**|**bit**|1 = バックアップ時、データベースは読み取り専用であった。|  
|**is_single_user**|**bit**|1 = バックアップ時、データベースはシングル ユーザー モードであった。|  
|**has_backup_checksums**|**bit**|1 = バックアップ チェックサムを含むバックアップ。|  
|**is_damaged**|**bit**|1 = バックアップの作成時、データベースの損傷が検出された。 エラーに関係なくバックアップ操作の続行が要求されました。|  
|**begins_log_chain**|**bit**|1 = 連鎖的なログ バックアップの先頭。 データベースが作成された後、または単純復旧モデルが完全復旧モデルや一括ログ復旧モデルに切り替わった後、最初に行われるログ バックアップを先頭にして、ログ チェーンが形成されます。|  
|**has_incomplete_metadata**|**bit**|1 = 不完全なメタデータでのログ末尾のバックアップ。 詳細については、「[ログ末尾のバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/tail-log-backups-sql-server.md)」を参照してください。|  
|**is_force_offline**|**bit**|1 = バックアップ時、データベースが NORECOVERY オプションによってオフラインにされた。|  
|**is_copy_only**|**bit**|1 = コピーのみのバックアップ。 詳細については、「[コピーのみのバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md)」を参照してください。|  
|**first_recovery_fork_guid**|**uniqueidentifier**|最初の復旧分岐の ID。 これに対応して**FirstRecoveryForkID** RESTORE HEADERONLY のです。<br /><br /> データのバックアップ、 **first_recovery_fork_guid** equals **last_recovery_fork_guid**です。|  
|**last_recovery_fork_guid**|**uniqueidentifier**|最後の復旧分岐の ID。 これに対応して**RecoveryForkID** RESTORE HEADERONLY のです。<br /><br /> データのバックアップ、 **first_recovery_fork_guid** equals **last_recovery_fork_guid**です。|  
|**fork_point_lsn**|**numeric(25,0)**|場合**first_recovery_fork_guid**は等しくありません**last_recovery_fork_guid**、これは、分岐ポイントのログ シーケンス番号。 それ以外の場合は NULL になります。|  
|**database_guid**|**uniqueidentifier**|データベースに割り当てられた一意 ID。 これに対応して**BindingID** RESTORE HEADERONLY のです。 データベースを復元すると、新しい値が割り当てられます。|  
|**family_guid**|**uniqueidentifier**|作成時の元のデータベースの一意 ID。 この値は、データベースが別の名前で復元されても変更されません。|  
|**differential_base_lsn**|**numeric(25,0)**|差分バックアップのベース ログ シーケンス番号。 シングル ベースの差分バックアップです。Lsn に以上を使用して変更**differential_base_lsn**差分バックアップに含まれています。<br /><br /> マルチの差分バックアップ、値は NULL の場合と、ベース LSN は、ファイル レベルで決定する必要があります (を参照してください[backupfile &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md))。<br /><br /> 種類が差分バックアップ以外の場合は、常に NULL。|  
|**differential_base_guid**|**uniqueidentifier**|シングル ベースの差分バックアップの場合は、差分ベースの一意識別子。<br /><br /> マルチ ベースの差分バックアップの場合は NULL。差分のベースはファイル レベルで決定される必要があります。<br /><br /> 差分バックアップ以外の種類のバックアップの場合は NULL。|  
|**compressed_backup_size**|**numeric(20,0)**|ディスクに格納されたバックアップの総バイト数。<br /><br /> 圧縮比率を計算するには、使用**backup_size**と**backup_size**です。<br /><br /> 中に、 **msdb**アップグレードすると、この値は NULL に設定します。 これは圧縮されていないバックアップを示します。|  
|**key_algorithm**|**nvarchar(32)**|バックアップの暗号化に使用される暗号化アルゴリズム。 値が NO_Encryption である場合、バックアップが暗号化されていないことを示します。|  
|**encryptor_thumbprint**|**varbinary(20)**|データベースに保存されている証明書や非対称キーを検索するために使用される暗号化機能の拇印。 バックアップが暗号化されていない場合、この値は NULL です。|  
|**encryptor_type**|**nvarchar(32)**|使用される暗号化機能の種類 (証明書または非対称キー)。 」をご覧ください。 バックアップが暗号化されていない場合、この値は NULL です。|  
  
## <a name="remarks"></a>解説  
 RESTORE VERIFYONLY FROM *backup_device* WITH LOADHISTORY の列に設定します、 **backupmediaset**メディア セット ヘッダーから適切な値を持つテーブルです。  
  
 次の表では他のバックアップと履歴テーブルの行の数を減らすためには、実行、 [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)ストアド プロシージャです。  
  
## <a name="see-also"></a>参照  
 [バックアップし、復元テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [バックアップ中および復元中に発生する可能性があるメディア エラー &#40;SQL Server&#41;](../../relational-databases/backup-restore/possible-media-errors-during-backup-and-restore-sql-server.md)   
 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [復旧モデル &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)   
 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)   
 [バックアップし、復元テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)  
  
  
