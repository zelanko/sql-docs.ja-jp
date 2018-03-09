---
title: "sys.master_files (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.master_files
- master_files_TSQL
- sys.master_files_TSQL
- master_files
dev_langs:
- TSQL
helpviewer_keywords:
- sys.master_files catalog view
ms.assetid: 803b22f2-0016-436b-a561-ce6f023d6b6a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1c0ee418f8b04c8a549fb107698bd1f2df5648b2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysmasterfiles-transact-sql"></a>sys.master_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  master データベースに格納されているデータベースのファイルごとに 1 行のデータを保持します。 これは、単一のシステム全体のビューです。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|このファイルが適用されるデータベースの ID です。 Masterdatabase_id は常に 1 です。|  
|file_id|**int**|データベース内のファイルの ID です。 プライマリ ファイルの file_id は常に 1 です。|  
|file_guid|**uniqueidentifier**|ファイルの一意識別子。<br /><br /> NULL = データベースは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の旧バージョンからアップグレードされています。|  
|型|**tinyint**|ファイルの種類です。<br /><br /> 0 = 行 <br /><br /> 1 = ログ<br /><br /> 2 = FILESTREAM<br /><br /> 3 = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> 4 = フルテキスト ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] より前のフルテキスト カタログです。[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降用にアップグレードまたは作成されたフルテキスト カタログの場合、ファイルの種類は 0 で報告されます。)|  
|type_desc|**nvarchar (60)**|ファイルの種類の説明です。<br /><br /> ROWS<br /><br /> LOG<br /><br /> FILESTREAM<br /><br /> FULLTEXT ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] より前のフルテキスト カタログです。)|  
|data_space_id|**int**|このファイルが属するデータ領域の ID です。 データ領域はファイル グループです。<br /><br /> 0 = ログ ファイル|  
|name|**sysname**|データベース内のファイルの論理名です。|  
|physical_name|**nvarchar (260)**|オペレーティング システム ファイル名です。|  
|state|**tinyint**|ファイルの状態です。<br /><br /> 0 = ONLINE<br /><br /> 1 = RESTORING<br /><br /> 2 = RECOVERING<br /><br /> 3 = RECOVERY_PENDING<br /><br /> 4 = SUSPECT<br /><br /> 5 = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> 6 = OFFLINE <br /><br /> 7 = DEFUNCT|  
|state_desc|**nvarchar (60)**|ファイルの状態の説明です。<br /><br /> ONLINE<br /><br /> RESTORING<br /><br /> RECOVERING<br /><br /> RECOVERY_PENDING <br /><br /> SUSPECT<br /><br /> OFFLINE<br /><br /> DEFUNCT<br /><br /> 詳細については、次を参照してください。[ファイルの状態](../../relational-databases/databases/file-states.md)です。|  
|サイズ|**int**|現在のファイル サイズ (8 KB ページ単位) です。 データベース スナップショットの場合、size は、スナップショットがファイルに対して使用する中で最大の領域を表します。<br /><br /> 注: このフィールドは、FILESTREAM コンテナーに対して 0 として設定されます。 クエリ、 *sys.database_files*カタログ ビューの FILESTREAM コンテナーの実際のサイズの詳細。|  
|max_size|**int**|8 KB ページ単位の最大ファイル サイズ:<br /><br /> 0 = 拡張は許可されません。<br /><br /> -1 = ディスクがいっぱいになるまでファイル サイズが拡張します。<br /><br /> 268435456 = ログ ファイルが最大 2 TB まで拡張することを表します。<br /><br /> 注: が無制限のログ ファイル サイズとアップグレードされたデータベースは、ログ ファイルの最大サイズに達すると-1 に報告されます。|  
|growth|**int**|0 = ファイル サイズは固定されてし、なることはありません。<br /><br /> >0 = ファイルは自動的に拡張されます。<br /><br /> is_percent_growth が 0 の場合、拡張増分は 8 KB ページ単位で表され、最も近い 64 KB 単位の値に切り上げられます。<br /><br /> is_percent_growth が 1 の場合、拡張増分は、整数のパーセンテージで表されます。|  
|is_media_read_onlyF|**bit**|1 = ファイルは読み取り専用メディア上にあります。<br /><br /> 0 = ファイルは読み取り/書き込みメディア上にあります。|  
|is_read_only|**bit**|1 = ファイルは読み取り専用としてマークされます。<br /><br /> 0 = ファイルは読み取り/書き込みとしてマークされます。|  
|is_sparse|**bit**|1 = ファイルはスパース ファイルです。<br /><br /> 0 = ファイルはスパース ファイルではありません。<br /><br /> 詳細については、「[データベース スナップショットのスパース ファイルのサイズを表示する方法 &#40;Transact-SQL&#41;](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md)」を参照してください。|  
|is_percent_growth|**bit**|1 = ファイルの拡張はパーセンテージで表されます。<br /><br /> 0 = ページ単位の絶対拡張サイズです。|  
|is_name_reserved|**bit**|1 = 削除されたファイル名を再使用できます。 新しいファイル名に対して名前 (name または physical_name) を再使用するには、ログのバックアップを実行する必要があります。<br /><br /> 0 = ファイル名は再利用するため使用できません。|  
|create_lsn|**numeric(25,0)**|ファイルが作成されたログ シーケンス番号 (LSN) です。|  
|drop_lsn|**numeric(25,0)**|ファイルが削除された LSN です。|  
|read_only_lsn|**numeric(25,0)**|ファイルを含むファイル グループが読み取り/書き込みから読み取り専用へ変更された (最新の変更) LSN です。|  
|read_write_lsn|**numeric(25,0)**|ファイルを含むファイル グループが読み取り専用から読み取り/書き込みへ変更された (最新の変更) LSN です。|  
|differential_base_lsn|**numeric(25,0)**|差分バックアップのベースです。 この LSN の後に変更されたデータ エクステントが差分バックアップに含まれます。|  
|differential_base_guid|**uniqueidentifier**|差分バックアップの基になるベース バックアップの一意識別子です。|  
|differential_base_time|**datetime**|differential_base_lsn に対応する時間です。|  
|redo_start_lsn|**numeric(25,0)**|次のロールフォワードを開始する必要がある LSN です。<br /><br /> state = RESTORING または state = RECOVERY_PENDING でない場合は NULL です。|  
|redo_start_fork_guid|**uniqueidentifier**|復旧分岐の一意識別子です。 復元される次のログ バックアップの first_fork_guid は、この値と一致する必要があります。 これは、コンテナーの現在の状態を表します。|  
|redo_target_lsn|**numeric(25,0)**|このファイルでのオンライン ロールフォワードが停止できる LSN です。<br /><br /> state = RESTORING または state = RECOVERY_PENDING でない場合は NULL です。|  
|redo_target_fork_guid|**uniqueidentifier**|コンテナーを復元できる復旧分岐です。 redo_target_lsn と組み合わせて使用します。|  
|backup_lsn|**numeric(25,0)**|ファイルの最新データまたは差分バックアップの LSN です。|  
|credential_id|**int**|`credential_id`から`sys.credentials`ファイルを格納するために使用します。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]とデータベースの Azure の仮想マシンで実行しているファイルが Azure blob ストレージに格納されている、記憶域の場所へのアクセス資格情報を使用する資格情報が構成されています。|  
  
> [!NOTE]  
>  ドロップまたは大規模なインデックスを再構築またはドロップまたは大規模なテーブルを切り捨てるしたときに、[!INCLUDE[ssDE](../../includes/ssde-md.md)]トランザクションがコミットされた後に、まで、実際のページの割り当て解除と、関連するロックを延期します。 削除操作が延期された場合、割り当てられた領域は、すぐには解放されません。 そのため、ラージ オブジェクトを削除または切り捨てた後すぐに sys.master_files から返される値は、実際の使用可能ディスク領域を表していない場合があります。  
  
## <a name="permissions"></a>Permissions  
 対応する行を参照するには、少なくとも CREATE DATABASE、ALTER ANY DATABASE、または VIEW ANY DEFINITION 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [データベースとファイルのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [ファイルの状態](../../relational-databases/databases/file-states.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [データベース ファイルとファイル グループ](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  
