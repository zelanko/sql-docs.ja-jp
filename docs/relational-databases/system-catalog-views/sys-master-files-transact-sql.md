---
title: sys.master_files (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/10/2016
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 679a048a40c990c5c86c0c5a24f4f1c53fb9e0b3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68102390"
---
# <a name="sysmasterfiles-transact-sql"></a>sys.master_files (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  master データベースに格納されているデータベースのファイルごとに 1 行のデータを保持します。 これは、単一のシステム全体のビューです。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|database_id|**int**|このファイルを適用するデータベースの ID。 Masterdatabase_id は常に 1 です。|  
|file_id|**int**|データベース内のファイルの ID。 プライマリ ファイルの file_id は常に 1 です。|  
|file_guid|**uniqueidentifier**|ファイルの一意の識別子。<br /><br /> NULL = データベースは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の旧バージョンからアップグレードされています。|  
|type|**tinyint**|ファイルの種類です。<br /><br /> 0 = 行。<br /><br /> 1 = ログ<br /><br /> 2 = FILESTREAM<br /><br /> 3 = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> 4 = フルテキスト ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] より前のフルテキスト カタログです。[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降用にアップグレードまたは作成されたフルテキスト カタログの場合、ファイルの種類は 0 で報告されます。)|  
|type_desc|**nvarchar(60)**|ファイルの種類の説明です。<br /><br /> ROWS<br /><br /> LOG<br /><br /> FILESTREAM<br /><br /> FULLTEXT ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] より前のフルテキスト カタログです。)|  
|data_space_id|**int**|このファイルが所属するデータ領域の ID。 データ領域は、ファイル グループです。<br /><br /> 0 = ログ ファイル|  
|NAME|**sysname**|データベース内のファイルの論理名。|  
|physical_name|**nvarchar(260)**|オペレーティング システムのファイルの名前。|  
|state|**tinyint**|ファイルの状態です。<br /><br /> 0 = ONLINE<br /><br /> 1 = を復元します。<br /><br /> 2 = 回復<br /><br /> 3 = RECOVERY_PENDING<br /><br /> 4 = 問題あり<br /><br /> 5 = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> 6 = OFFLINE<br /><br /> 7 = DEFUNCT|  
|state_desc|**nvarchar(60)**|ファイルの状態の説明です。<br /><br /> ONLINE<br /><br /> RESTORING<br /><br /> RECOVERING<br /><br /> RECOVERY_PENDING<br /><br /> SUSPECT<br /><br /> OFFLINE<br /><br /> DEFUNCT<br /><br /> 詳しくは、「[ファイルの状態](../../relational-databases/databases/file-states.md)」をご覧ください。|  
|size|**int**|現在のファイル サイズ、8 KB ページ単位です。 データベース スナップショットの場合、size は、スナップショットがファイルに対して使用する中で最大の領域を表します。<br /><br /> 注:このフィールドは、FILESTREAM コンテナーに対して 0 として設定されます。 クエリ、 *sys.database_files*カタログ ビューの FILESTREAM コンテナーの実際のサイズ。|  
|max_size|**int**|8 KB ページ単位の最大ファイル サイズ:<br /><br /> 0 = 拡張は許可されません。<br /><br /> -1 = ディスクがいっぱいになるまでファイル サイズが拡張します。<br /><br /> 268435456 = ログ ファイルが 2 TB の最大サイズに拡張されます。<br /><br /> 注:無制限のログ ファイルのサイズにアップグレードしたデータベースは、ログ ファイルの最大サイズに達すると-1 に報告されます。|  
|成長|**int**|0 = ファイル サイズは固定されてし、なることはありません。<br /><br /> > 0 = ファイルは自動的に拡張されます。<br /><br /> is_percent_growth が 0 の場合、拡張増分は 8 KB ページ単位で表され、最も近い 64 KB 単位の値に切り上げられます。<br /><br /> is_percent_growth が 1 の場合、拡張増分は、整数のパーセンテージで表されます。|  
|is_media_read_onlyF|**bit**|1 = ファイルは読み取り専用メディア上です。<br /><br /> 0 = ファイルは読み取り/書き込みメディア上にあります。|  
|is_read_only|**bit**|1 = ファイルが読み取り専用としてマークします。<br /><br /> 0 = ファイルは読み取り/書き込みでマークされます。|  
|is_sparse|**bit**|1 = ファイルはスパース ファイルです。<br /><br /> 0 = ファイルはスパース ファイルではありません。<br /><br /> 詳細については、「[データベース スナップショットのスパース ファイルのサイズを表示する方法 &#40;Transact-SQL&#41;](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md)」を参照してください。|  
|is_percent_growth|**bit**|1 = ファイルの拡張はパーセンテージで表されます。<br /><br /> 0 = ページ単位の絶対拡張サイズです。|  
|is_name_reserved|**bit**|1 = 削除されたファイル名は再利用できます。 新しいファイル名に対して名前 (name または physical_name) を再使用するには、ログのバックアップを実行する必要があります。<br /><br /> 0 = ファイル名は再利用するために使用できません。|  
|create_lsn|**numeric(25,0)**|ファイルが作成されたログ シーケンス番号 (LSN) です。|  
|drop_lsn|**numeric(25,0)**|ファイルを削除した LSN です。|  
|read_only_lsn|**numeric(25,0)**|位置をファイルを含むファイル グループから読み取り/書き込みに変更読み取り専用 (最新の変更) LSN です。|  
|read_write_lsn|**numeric(25,0)**|読み取り専用読み取り/書き込み (最新の変更) してから、ファイルを含むファイル グループが変更された LSN。|  
|differential_base_lsn|**numeric(25,0)**|差分バックアップのベースです。 データ範囲を変更した後、この LSN は、差分バックアップに含まれます。|  
|differential_base_guid|**uniqueidentifier**|差分バックアップの基になるベース バックアップの一意の識別子。|  
|differential_base_time|**datetime**|differential_base_lsn に対応する時間です。|  
|redo_start_lsn|**numeric(25,0)**|次のロールフォワードを開始する必要がある LSN です。<br /><br /> state = RESTORING または state = RECOVERY_PENDING でない場合は NULL です。|  
|redo_start_fork_guid|**uniqueidentifier**|復旧分岐の一意識別子です。 復元される次のログ バックアップの first_fork_guid は、この値と一致する必要があります。 これは、コンテナーの現在の状態を表します。|  
|redo_target_lsn|**numeric(25,0)**|このファイルのオンライン ロール フォワードする LSN を停止できます。<br /><br /> state = RESTORING または state = RECOVERY_PENDING でない場合は NULL です。|  
|redo_target_fork_guid|**uniqueidentifier**|コンテナーを復旧できる復旧分岐。 redo_target_lsn と組み合わせて使用します。|  
|backup_lsn|**numeric(25,0)**|最新のデータまたはファイルの差分バックアップの LSN。|  
|credential_id|**int**|`credential_id`から`sys.credentials`ファイルを格納するために使用します。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]とデータベースの Azure 仮想マシンで実行しているファイルが Azure blob storage に格納されている、資格情報が記憶域の場所に、アクセス資格情報で構成されます。|  
  
> [!NOTE]  
>  ドロップまたは大きなインデックスを再構築または削除や、大規模なテーブルを切り捨てる、[!INCLUDE[ssDE](../../includes/ssde-md.md)]トランザクションがコミットされた後に、まで、実際のページの割り当て解除と、関連するロックを延期します。 遅延された削除操作では、割り当てられた領域をすぐに解放しません。 そのため、ラージ オブジェクトを削除または切り捨てた後すぐに sys.master_files から返される値は、実際の使用可能ディスク領域を表していない場合があります。  
  
## <a name="permissions"></a>アクセス許可  
 対応する行を表示するために必要な最小限のアクセス許可は、CREATE DATABASE、ALTER ANY DATABASE、または VIEW ANY DEFINITION です。  
  
## <a name="see-also"></a>関連項目  
 [データベースとファイルのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [ファイルの状態](../../relational-databases/databases/file-states.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [データベース ファイルとファイル グループ](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  
