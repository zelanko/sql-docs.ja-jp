---
title: "sys.dm_fts_memory_buffers (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_memory_buffers
- dm_fts_memory_buffers_TSQL
- dm_fts_memory_buffers
- sys.dm_fts_memory_buffers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_memory_buffers dynamic management view
ms.assetid: 56895fe5-e8df-4d75-9adc-c1f7757cdef8
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 190d564ec27cf7921fbfbd9d6e85fc594b77c2d6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmftsmemorybuffers-transact-sql"></a>sys.dm_fts_memory_buffers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  フルテキスト クロールまたはフルテキスト クロール範囲の一部として使用される、特定のメモリ プールのメモリ バッファーに関する情報を返します。  
  
> [!NOTE]
> 次の列は、の将来のリリースで削除される予定[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **row_count**です。 新しい開発作業では、この列の使用は避け、現在この列を使用しているアプリケーションは修正するようにしてください。  

  
|列|データ型|Description|  
|------------|---------------|-----------------|  
|**pool_id**|**int**|割り当てられたメモリ プールの ID。<br /><br /> 0 = 小さいバッファー<br /><br /> 1 = 大きいバッファー|  
|**memory_address**|**varbinary(8)**|割り当てられたメモリ バッファーのアドレス。|  
|**name**|**nvarchar (4000)**|この割り当ての対象となっている共有メモリ バッファーの名前。|  
|**is_free**|**bit**|メモリ バッファーの現在の状態。<br /><br /> 0 = 空き<br /><br /> 1 = ビジー|  
|**row_count**|**int**|バッファーで現在処理されている行の数。|  
|**bytes_used**|**int**|バッファーで使用されているメモリ サイズ (バイト単位)。|  
|**percent_used**|**int**|割り当てられたメモリの使用パーセンテージ。|  
  
## <a name="permissions"></a>権限  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。  
 
## <a name="physical-joins"></a>物理結合  
 ![この動的管理ビューの重要な結合](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-memory-buffers-1.gif "この動的管理ビューの重要な結合")  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|dm_fts_memory_buffers.pool_id|dm_fts_memory_pools.pool_id|多対一|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [フルテキスト検索およびセマンティック検索の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

