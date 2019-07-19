---
title: sys.database_files (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 09/19/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.database_files
- sys.database_files_TSQL
- database_files
- database_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_files catalog view
ms.assetid: 0f5b0aac-c17d-4e99-b8f7-d04efc9edf44
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 37ec05a27421b8b55fb0085dbac97ab564bc5bff
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915093"
---
# <a name="sysdatabasefiles-transact-sql"></a>sys.database_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベース自体に保存されているデータベースのファイルごとに 1 行のデータを格納します。 これはデータベース単位のビューです。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**file_id**|**int**|データベース内のファイルの ID。|  
|**file_guid**|**uniqueidentifier**|ファイルの GUID。<br /><br /> NULL = データベースは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の旧バージョンからアップグレードされています。|  
|**type**|**tinyint**|ファイルの種類です。<br /><br /> 0 = 行 (にアップグレードまたはで作成されたフルテキスト カタログのファイルが含まれます[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])。<br /><br /> 1 = ログ<br /><br /> 2 = FILESTREAM<br /><br /> 3 = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> 4 = フルテキスト ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] より前のフルテキスト カタログです。[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 用にアップグレードまたは作成されたフルテキスト カタログの場合、ファイルの種類は 0 で報告されます。)|  
|**type_desc**|**nvarchar(60)**|ファイルの種類の説明です。<br /><br /> 行 (にアップグレードまたはで作成されたフルテキスト カタログのファイルが含まれます[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])。<br /><br /> LOG<br /><br /> FILESTREAM<br /><br /> FULLTEXT ([!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] より前のフルテキスト カタログです。)|  
|**data_space_id**|**int**|値は、0 または 0 より大きい値を指定できます。 値 0 は、データベース ログ ファイルを表し、0 より大きい値は、このデータ ファイルが格納されているファイル グループの ID を表します。|  
|**name**|**sysname**|データベース内のファイルの論理名。|  
|**physical_name**|**nvarchar(260)**|オペレーティング システムのファイルの名前。 データベースが AlwaysOn によってホストされている場合[読み取り可能セカンダリ レプリカ](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)、 **physical_name**プライマリ レプリカ データベースのファイルの場所を示します。 読み取り可能なセカンダリ データベースの適切なファイルの場所、クエリ[sys.sysaltfiles](../../relational-databases/system-compatibility-views/sys-sysaltfiles-transact-sql.md)します。|  
|**state**|**tinyint**|ファイルの状態です。<br /><br /> 0 = ONLINE<br /><br /> 1 = を復元します。<br /><br /> 2 = 回復<br /><br /> 3 = RECOVERY_PENDING<br /><br /> 4 = 問題あり<br /><br /> 5 = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> 6 = OFFLINE<br /><br /> 7 = DEFUNCT|  
|**state_desc**|**nvarchar(60)**|ファイルの状態の説明です。<br /><br /> ONLINE<br /><br /> RESTORING<br /><br /> RECOVERING<br /><br /> RECOVERY_PENDING<br /><br /> SUSPECT<br /><br /> OFFLINE<br /><br /> DEFUNCT<br /><br /> 詳しくは、「[ファイルの状態](../../relational-databases/databases/file-states.md)」をご覧ください。|  
|**size**|**int**|8 KB のページで、ファイルの現在のサイズ。<br /><br /> 0 = 適用なし<br /><br /> データベース スナップショットの場合、size は、スナップショットがファイルに対して使用する中で最大の領域を表します。<br /><br /> FILESTREAM ファイル グループ コンテナーでは、現在、コンテナーのサイズの使用済みサイズが反映されます。|  
|**max_size**|**int**|8 KB ページ単位の最大ファイル サイズ:<br /><br /> 0 = 拡張は許可されません。<br /><br /> -1 = ディスクがいっぱいになるまでファイル サイズが拡張します。<br /><br /> 268435456 = ログ ファイルが 2 TB の最大サイズに拡張されます。<br /><br /> FILESTREAM ファイル グループ コンテナーでは、max_size コンテナーの最大サイズが反映されます。<br /><br /> ログ ファイルの最大サイズに達すると-1 を無制限のログ ファイルのサイズにアップグレードしたデータベースに報告することに注意してください。|  
|**growth**|**int**|0 = ファイル サイズは固定されてし、なることはありません。<br /><br /> > 0 = ファイルは自動的に拡張されます。<br /><br /> is_percent_growth = 0 の場合、ファイルは 8 KB ページ単位で拡張され、最も近い 64 KB 単位の値に丸められます。<br /><br /> is_percent_growth が 1 の場合、拡張増分は、整数のパーセンテージで表されます。|  
|**is_media_read_only**|**bit**|1 = ファイルは読み取り専用メディア上です。<br /><br /> 0 = ファイルは読み取り/書き込みメディア上です。|  
|**is_read_only**|**bit**|1 = ファイルが読み取り専用としてマークします。<br /><br /> 0 = ファイルは読み取り/書き込み用としてマークされています。|  
|**is_sparse**|**bit**|1 = ファイルはスパース ファイルです。<br /><br /> 0 = ファイルはスパース ファイルではありません。<br /><br /> 詳細については、「[データベース スナップショットのスパース ファイルのサイズを表示する方法 &#40;Transact-SQL&#41;](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md)」を参照してください。|  
|**is_percent_growth**|**bit**|1 = ファイルの拡張はパーセンテージで表されます。<br /><br /> 0 = ページ単位の絶対拡張サイズです。|  
|**is_name_reserved**|**bit**|1 = 削除されたファイルの名前 (name または physical_name) は、次のログ バックアップ後にのみ再利用可能な。 ファイルがデータベースから削除されると、ファイルの論理名は次回のログ バックアップまで予約された状態になります。 この列は完全復旧モデルと一括ログ復旧モデルにのみ関係します。|  
|**create_lsn**|**numeric(25,0)**|ファイルが作成されたログ シーケンス番号 (LSN) です。|  
|**drop_lsn**|**numeric(25,0)**|ファイルを削除した LSN です。<br /><br /> 0 = ファイル名は再利用するために使用できません。|  
|**read_only_lsn**|**numeric(25,0)**|位置をファイルを含むファイル グループから読み取り/書き込みに変更読み取り専用 (最新の変更) LSN です。|  
|**read_write_lsn**|**numeric(25,0)**|読み取り専用読み取り/書き込み (最新の変更) してから、ファイルを含むファイル グループが変更された LSN。|  
|**differential_base_lsn**|**numeric(25,0)**|差分バックアップのベースです。 データ範囲を変更した後、この LSN は、差分バックアップに含まれます。|  
|**differential_base_guid**|**uniqueidentifier**|差分バックアップの基になるベース バックアップの一意の識別子。|  
|**differential_base_time**|**datetime**|differential_base_lsn に対応する時間です。|  
|**redo_start_lsn**|**numeric(25,0)**|次のロールフォワードを開始する必要がある LSN です。<br /><br /> state = RESTORING または state = RECOVERY_PENDING でない場合は NULL です。|  
|**redo_start_fork_guid**|**uniqueidentifier**|復旧分岐の一意識別子です。 復元される次のログ バックアップの first_fork_guid は、この値と一致する必要があります。 これは、ファイルの現在の状態を表します。|  
|**redo_target_lsn**|**numeric(25,0)**|このファイルのオンライン ロール フォワードする LSN を停止できます。<br /><br /> state = RESTORING または state = RECOVERY_PENDING でない場合は NULL です。|  
|**redo_target_fork_guid**|**uniqueidentifier**|復旧分岐は、ファイルを回復できます。 redo_target_lsn と組み合わせて使用します。|  
|**backup_lsn**|**numeric(25,0)**|最新のデータまたはファイルの差分バックアップの LSN。|  
  
> [!NOTE]  
>  ドロップまたは大きなインデックスを再構築または削除や、大規模なテーブルを切り捨てる、[!INCLUDE[ssDE](../../includes/ssde-md.md)]トランザクションがコミットされた後に、まで、実際のページの割り当て解除と、関連するロックを延期します。 遅延された削除操作では、割り当てられた領域をすぐに解放しません。 したがって、削除するか、ラージ オブジェクトを切り捨てた直後に sys.database_files を実行して返される値は使用可能な実際のディスク領域を反映可能性があります。  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  

## <a name="examples"></a>使用例  
次のステートメントは、名、ファイルのサイズ、および各データベース ファイルの空き領域の量を返します。

```
SELECT name, size/128.0 FileSizeInMB,
size/128.0 - CAST(FILEPROPERTY(name, 'SpaceUsed') AS int)/128.0 
   AS EmptySpaceInMB
FROM sys.database_files;
```
使用する場合の詳細については[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]を参照してください[Azure SQL Database V12 でデータベースのサイズを決定する](https://blogs.msdn.microsoft.com/sqlcat/2016/09/21/determining-database-size-in-azure-sql-database-v12/)SQL Customer Advisory Team ブログ。
  
## <a name="see-also"></a>関連項目  
 [データベースとファイルのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [ファイルの状態](../../relational-databases/databases/file-states.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md)   
 [sys.data_spaces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)  
  
  
