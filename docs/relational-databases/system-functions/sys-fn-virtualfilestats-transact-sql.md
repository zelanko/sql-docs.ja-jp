---
title: sys.fn_virtualfilestats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/16/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_virtualfilestats_TSQL
- fn_virtualfilestats
dev_langs:
- TSQL
helpviewer_keywords:
- I/O [SQL Server], statistics
- fn_virtualfilestats function
- sys.fn_virtualfilestats function
- statistical information [SQL Server], I/O
ms.assetid: 96b28abb-b059-48db-be2b-d60fe127f6aa
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f8e8bf556d721ac18af7fa552db558395bff76f2
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43090990"
---
# <a name="sysfnvirtualfilestats-transact-sql"></a>sys.fn_virtualfilestats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ログ ファイルを含む、データベース ファイルの I/O 統計を返します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からこの情報はまた、 [sys.dm_io_virtual_file_stats](../../relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql.md)動的管理ビュー。  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
fn_virtualfilestats ( { database_id | NULL } , { file_id | NULL } )  
```  
  
## <a name="arguments"></a>引数  
 *database_id* | NULL  
 データベースの ID です。 *database_id* は **int**, 、既定値はありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのすべてのデータベースに関する情報を返すには NULL を指定します。  
  
 *file_id* | NULL  
 ファイルの ID を指定します。 *file_id*は**int**、既定値はありません。 データベース内のすべてのファイルに関する情報を返すには NULL を指定します。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**DbId**|**smallint**|データベース ID。|  
|**FileId**|**smallint**|ファイル ID。|  
|**TimeStamp**|**bigint**|データが取り出されたデータベース タイムスタンプです。 **int**より前に、のバージョンで[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]します。 |  
|**NumberReads**|**bigint**|ファイルで実行された読み取りの数。|  
|**BytesRead**|**bigint**|そのファイルで実行された読み取りバイト数です。|  
|**IoStallReadMS**|**bigint**|そのファイルで、ユーザーが読み取り I/O の完了を待機した時間の合計 (ミリ秒単位) です。|  
|**NumberWrites**|**bigint**|そのファイルで実行された書き込みの数です。|  
|**BytesWritten**|**bigint**|そのファイルで実行された書き込みバイト数です。|  
|**IoStallWriteMS**|**bigint**|そのファイルで、ユーザーが書き込み I/O の完了を待機した時間の合計 (ミリ秒単位) です。|  
|**IoStallMS**|**bigint**|合計**IoStallReadMS**と**IoStallWriteMS**します。|  
|**FileHandle**|**bigint**|ファイル ハンドルの値です。|  
|**BytesOnDisk**|**bigint**|ディスク上の物理ファイル サイズ (バイト数) です。<br /><br /> データベース ファイルの場合と同じ値は、この**サイズ**で**sys.database_files**ページではなくバイトで表現されますが、します。<br /><br /> データベース スナップショット スパース ファイルの場合は、オペレーティング システムがこのファイル用に使用する領域です。|  
  
## <a name="remarks"></a>コメント  
 **fn_virtualfilestats**ファイルで I/o の合計数などの統計情報を提供するテーブル値関数は実行システムです。 この関数を使用して、ユーザーがファイルに対する読み取りまたは書き込みを待機する時間の長さを追跡できます。 また、この関数は、大量の I/O 利用量が生じたファイルを確認する場合にも役立ちます。  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-displaying-statistical-information-for-a-database"></a>A. データベースの統計情報を表示する  
 次の例の ID を使用してデータベース内のファイル ID 1 の統計情報を表示する`1`します。  
  
```sql  
SELECT *  
FROM fn_virtualfilestats(1, 1);  
GO  
```  
  
### <a name="b-displaying-statistical-information-for-a-named-database-and-file"></a>B. 指定されたデータベースおよびファイルの統計情報を表示する  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] サンプル データベースのログ ファイルの統計情報を表示します。 システム関数`DB_ID`を指定するために使用、 *database_id*パラメーター。  
  
```sql  
SELECT *  
FROM fn_virtualfilestats(DB_ID(N'AdventureWorks2012'), 2);  
GO  
```  
  
### <a name="c-displaying-statistical-information-for-all-databases-and-files"></a>C. すべてのデータベースおよびファイルの統計情報を表示する  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内のすべてのデータベースにあるすべてのファイルの統計情報を表示します。  
  
```sql  
SELECT *  
FROM fn_virtualfilestats(NULL,NULL);  
GO  
```  
  
## <a name="see-also"></a>参照  
 [DB_ID &#40;TRANSACT-SQL&#41;](../../t-sql/functions/db-id-transact-sql.md)   
 [FILE_IDEX &#40;Transact-SQL&#41;](../../t-sql/functions/file-idex-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
