---
title: dm_fts_memory_buffers (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: pmasl
ms.author: pelopes
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fed15fbcfa685bde5d408e799bb605a40380ab5a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68265924"
---
# <a name="sysdm_fts_memory_buffers-transact-sql"></a>dm_fts_memory_buffers (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  フルテキスト クロールまたはフルテキスト クロール範囲の一部として使用される、特定のメモリ プールのメモリ バッファーに関する情報を返します。  
  
> [!NOTE]
> 次の列は、の今後の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]リリースで削除される予定です: **row_count**。 新しい開発作業ではこの列の使用を避け、現在この列を使用しているアプリケーションの変更を検討してください。  

  
|列|データ型|説明|  
|------------|---------------|-----------------|  
|**pool_id**|**int**|割り当てられたメモリプールの ID。<br /><br /> 0 = 小さいバッファー<br /><br /> 1 = 大きいバッファー|  
|**memory_address**|**varbinary (8)**|割り当てられたメモリバッファーのアドレス。|  
|**name**|**nvarchar (4000)**|この割り当てが行われた共有メモリバッファーの名前。|  
|**is_free**|**bit**|メモリバッファーの現在の状態。<br /><br /> 0 = 空き<br /><br /> 1 = ビジー状態|  
|**row_count**|**int**|このバッファーが現在処理している行の数。|  
|**bytes_used**|**int**|バッファーで使用されているメモリ サイズ (バイト単位)。|  
|**percent_used**|**int**|割り当てられたメモリの使用パーセンテージ。|  
  
## <a name="permissions"></a>アクセス許可  

で[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]は、 `VIEW SERVER STATE`権限が必要です。   
Premium [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルでは、データベース`VIEW DATABASE STATE`の権限が必要です。 Standard [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルおよび Basic レベルでは、**サーバー管理**者または**Azure Active Directory 管理者**アカウントが必要です。   
  
## <a name="physical-joins"></a>物理結合  
 ![この動的管理ビューの重要な結合](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-memory-buffers-1.gif "この動的管理ビューの重要な結合")  
  
## <a name="relationship-cardinalities"></a>リレーションシップ基数  
  
|ソース|終了|リレーションシップ|  
|----------|--------|------------------|  
|dm_fts_memory_buffers。 pool_id|dm_fts_memory_pools.pool_id|多対一|  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;の動的管理ビューおよび関数](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Transact-sql&#41;&#40;のフルテキスト検索とセマンティック検索の動的管理ビューおよび関数](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

