---
title: "sys.dm_fts_population_ranges (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sys.dm_fts_population_ranges
- sys.dm_fts_population_ranges_TSQL
- dm_fts_population_ranges_TSQL
- dm_fts_population_ranges
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_population_ranges dynamic management view
ms.assetid: 58d8564b-9c43-4965-a31c-2893890334ef
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ca071232727b71306f6490b10284a8b33a9a655d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmftspopulationranges-transact-sql"></a>sys.dm_fts_population_ranges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在進行中のフルテキスト インデックスの作成に関連する特定の範囲についての情報を返します。  
   
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**memory_address**|**varbinary(8)**|対象となるフルテキスト インデックス設定の範囲に関連する動作に割り当てられたメモリ バッファーのアドレス。|  
|**parent_memory_address**|**varbinary(8)**|フルテキスト インデックス設定に関連するすべての範囲の親オブジェクトを表すメモリ バッファーのアドレス。|  
|**is_retry**|**bit**|値が 1 の場合、対象となる範囲でエラーが発生した行を再試行します。|  
|**session_id**|**smallint**|現在、このタスクを処理中のセッションの ID。|  
|**processed_row_count**|**int**|対象となる範囲で処理された行の数。 進行情報は保存されます。カウントは、バッチがコミットされるたびではなく 5 分ごとに行われます。|  
|**error_count**|**int**|対象となる範囲でエラーが発生した行の数。 進行情報は保存されます。カウントは、バッチがコミットされるたびではなく 5 分ごとに行われます。|  
  
## <a name="permissions"></a>権限  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。  

## <a name="physical-joins"></a>物理結合  
 ![この動的管理ビューの重要な結合](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-population-ranges-1.gif "この動的管理ビューの重要な結合")  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|dm_fts_population_ranges.parent_memory_address|dm_fts_index_population.memory_address|多対一|  
  
## <a name="see-also"></a>参照  
  [フルテキスト検索およびセマンティック検索の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

