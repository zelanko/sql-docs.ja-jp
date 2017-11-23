---
title: "backupfile (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- backupfile
- backupfile_TSQL
dev_langs: TSQL
helpviewer_keywords:
- file backups [SQL Server], backupfile system table
- backupfile system table
ms.assetid: f1a7fc0a-f4b4-47eb-9138-eebf930dc9ac
caps.latest.revision: "36"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f51eff63650e1cf3572b7b2e8ea77a89eb4a8265
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="backupfile-transact-sql"></a>backupfile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベースの各データまたは各ログ ファイルに対して 1 行のデータを格納します。 各列では、バックアップ作成時のファイル構成の詳細が示されます。 ファイルがバックアップに含まれているかどうかによって決まりますが、 **is_present**列です。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**backup_set_id**|**int**|バックアップ セットを格納するファイルの一意な識別番号。 参照**backupset (backup_set_id)**です。|  
|**first_family_number**|**tinyint**|バックアップ ファイルが保存されている先頭のメディアのファミリ番号。 NULL にすることができます。|  
|**first_media_number**|**smallint**|バックアップ ファイルが保存されている先頭のメディアのメディア番号。 NULL にすることができます。|  
|**filegroup_name**|**nvarchar (128)**|バックアップされたデータベース ファイルが含まれるファイル グループの名前。 NULL にすることができます。|  
|**page_size**|**int**|ページのサイズ (バイト単位)。|  
|**file_number が**|**numeric(10,0)**|ファイル識別番号をデータベース内で一意 (に対応する**sys.database_files**.**file_id**)。|  
|**backed_up_page_count**|**numeric(10,0)**|バックアップされたページ数。 NULL にすることができます。|  
|**file_type**|**char (1)**|バックアップされたファイル。次のいずれかです。<br /><br /> D = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ファイル<br /><br /> L =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログ ファイルです。<br /><br /> F = フルテキスト カタログ<br /><br /> NULL にすることができます。|  
|**source_file_block_size**|**numeric(10,0)**|バックアップ時に、元のデータまたはログ ファイルが保存されていたデバイス。 NULL にすることができます。|  
|**file_size**|**numeric(20,0)**|バックアップされたファイルの長さ (バイト単位)。 NULL にすることができます。|  
|**logical_name**|**nvarchar (128)**|バックアップされたファイルの論理名。 NULL にすることができます。|  
|**physical_drive**|**nvarchar (260)**|物理ドライブまたはパーティションの名前。 NULL にすることができます。|  
|**physical_name**|**nvarchar (260)**|残りの物理 (オペレーティング システム) ファイルの名前。 NULL にすることができます。|  
|**状態**|**tinyint**|ファイルの状態。次のいずれかです。<br /><br /> 0 = ONLINE<br /><br /> 1 = RESTORING<br /><br /> 2 = RECOVERING<br /><br /> 3 = RECOVERY PENDING <br /><br /> 4 = SUSPECT<br /><br /> 6 = OFFLINE <br /><br /> 7 = DEFUNCT<br /><br /> 8 = 削除<br /><br /> 注: これらの値がデータベースの状態の値に対応するように、値 5 はスキップされます。|  
|**state_desc**|**nvarchar(64)**|ファイルの状態の説明。次のいずれかです。<br /><br /> ONLINE RESTORING <br /><br /> RECOVERING<br /><br /> RECOVERY_PENDING <br /><br /> SUSPECT OFFLINE DEFUNCT|  
|**create_lsn**|**numeric(25,0)**|ファイルが作成されたときのログ シーケンス番号。|  
|**drop_lsn**|**numeric(25,0)**|ファイルが削除されたときのログ シーケンス番号。 NULL にすることができます。<br /><br /> ファイルが削除されていない場合、この値は NULL です。|  
|**file_guid**|**uniqueidentifier**|ファイルの一意識別子。|  
|**read_only_lsn**|**numeric(25,0)**|このファイルを含むファイル グループが、前回読み書き可能から読み取り専用に変更されたときのログ シーケンス番号。 NULL にすることができます。|  
|**read_write_lsn**|**numeric(25,0)**|このファイルを含むファイル グループが、前回読み取り専用から読み書き可能に変更されたときのログ シーケンス番号。 NULL にすることができます。|  
|**differential_base_lsn**|**numeric(25,0)**|差分バックアップのベース ログ シーケンス番号。 差分バックアップには、データ エクステントをログ シーケンス番号以上になるとだけが含まれています。 **differential_base_lsn**です。<br /><br /> その他の種類のバックアップの場合、この値は NULL です。|  
|**differential_base_guid**|**uniqueidentifier**|差分バックアップの場合、ファイルの差分ベースとなる最新のデータ バックアップの一意識別子。この値が NULL の場合、ファイルは差分バックアップに含まれますが、ベースの作成後に追加されています。<br /><br /> その他の種類のバックアップの場合、この値は NULL です。|  
|**backup_size**|**numeric(20,0)**|ファイルのバックアップ サイズ (バイト単位)。|  
|**filegroup_guid**|**uniqueidentifier**|ファイル グループの ID。 Backupfilegroup テーブルでのファイル グループ情報を見つけるには使用**filegroup_guid**で**backup_set_id**です。|  
|**is_readonly**|**bit**|1 = ファイルは読み取り専用。|  
|**is_present**|**bit**|1 = ファイルはバックアップ セットに含まれる。|  
  
## <a name="remarks"></a>解説  
 RESTORE VERIFYONLY FROM *backup_device* WITH LOADHISTORY の列に設定、 **backupmediaset**メディア セット ヘッダーから適切な値を持つテーブルです。  
  
 次の表では他のバックアップと履歴テーブルの行の数を減らすためには、実行、 [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)ストアド プロシージャです。  
  
## <a name="see-also"></a>参照  
 [バックアップと復元のテーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [システム テーブルと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
