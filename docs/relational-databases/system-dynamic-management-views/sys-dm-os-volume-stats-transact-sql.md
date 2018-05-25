---
title: sys.dm_os_volume_stats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_volume_stats_TSQL
- dm_os_volume_stats
- sys.dm_os_volume_stats
- sys.dm_os_volume_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_volume_stats dynamic management function
ms.assetid: fa1c58ad-8487-42ad-956c-983f2229025f
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a5fcc94554408ed68988ddbdf34422078ca31dd4
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmosvolumestats-transact-sql"></a>sys.dm_os_volume_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたデータベースとファイルが格納されているでオペレーティング システムのボリューム (ディレクトリ) に関する情報を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 この動的管理関数は、物理ディスク ドライブの属性を確認する場合や、ディレクトリの使用可能な空き容量に関する情報を取得する場合に使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sys.dm_os_volume_stats (database_id, file_id)  
```  
  
##  <a name="Arguments"></a> 引数  
 *database_id*  
 データベースの ID です。 *database_id* は **int**, 、既定値はありません。 NULL 値は許容されません。  
  
 *file_id*  
 ファイルの ID です。 *file_id*は**int**、既定値はありません。 NULL 値は許容されません。  
  
## <a name="table-returned"></a>返されるテーブル  
  
||||  
|-|-|-|  
|**列**|**データ型**|**Description**|  
|**database_id**|**int**|データベースの ID です。 null にすることはできません。|  
|**file_id**|**int**|ファイルの ID です。 null にすることはできません。|  
|**volume_mount_point**|**nvarchar(512)**|ボリュームがルートとするマウント ポイント。 空の文字列を返すことができます。|  
|**volume_id**|**nvarchar(512)**|オペレーティング システム ボリューム ID。 空の文字列を返すことができます。|  
|**logical_volume_name**|**nvarchar(512)**|論理ボリューム名。 空の文字列を返すことができます。|  
|**file_system_type**|**nvarchar(512)**|ファイル システム ボリュームの種類 (NTFS、FAT、RAW など)。 空の文字列を返すことができます。|  
|**total_bytes**|**bigint**|ボリュームの合計サイズ (バイト単位)。 null にすることはできません。|  
|**available_bytes**|**bigint**|ボリューム上の使用可能な空き領域。 null にすることはできません。|  
|**supports_compression**|**bit**|ボリュームがオペレーティング システムによる圧縮をサポートするかどうかを示します。 null にすることはできません。|  
|**supports_alternate_streams**|**bit**|ボリュームが代替ストリームをサポートするかどうかを示します。 null にすることはできません。|  
|**supports_sparse_files**|**bit**|ボリュームがスパース ファイルをサポートするかどうかを示します。  null にすることはできません。|  
|**is_read_only**|**bit**|ボリュームが現在読み取り専用としてマークされているかどうかを示します。 null にすることはできません。|  
|**is_compressed**|**bit**|このボリュームが現在圧縮されているかどうかを示します。 null にすることはできません。|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-return-total-space-and-available-space-for-all-database-files"></a>A. すべてのデータベース ファイルの合計領域と使用可能な領域を返す  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにあるすべてのデータベース ファイルの合計領域と使用可能な領域 (バイト単位) を返します。  
  
```  
SELECT f.database_id, f.file_id, volume_mount_point, total_bytes, available_bytes  
FROM sys.master_files AS f  
CROSS APPLY sys.dm_os_volume_stats(f.database_id, f.file_id);  
```  
  
### <a name="b-return-total-space-and-available-space-for-the-current-database"></a>B. 現在のデータベースの合計領域と使用可能な領域を返す  
 次の例では、現在のデータベースにあるデータベース ファイルの合計領域と使用可能な領域 (バイト単位) を返します。  
  
```  
SELECT database_id, f.file_id, volume_mount_point, total_bytes, available_bytes  
FROM sys.database_files AS f  
CROSS APPLY sys.dm_os_volume_stats(DB_ID(f.name), f.file_id);  
```  
  
## <a name="see-also"></a>参照  
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
  
  
