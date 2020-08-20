---
description: sys.dm_repl_tranhash (Transact-SQL)
title: dm_repl_tranhash (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_repl_tranhash
- sys.dm_repl_tranhash_TSQL
- dm_repl_tranhash_TSQL
- dm_repl_tranhash
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_tranhash dynamic management view
ms.assetid: 0cc52338-e805-4ed4-9835-b19bbf72448e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c38860b17b3d0b9530f4751c90cd61acf5212823
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481851"
---
# <a name="sysdm_repl_tranhash-transact-sql"></a>sys.dm_repl_tranhash (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  トランザクションパブリケーションでレプリケートされているトランザクションに関する情報を返します。  
  
|column_name|data_type|description|  
|------------------|----------------|-----------------|  
|**バケット**|**bigint**|ハッシュテーブル内のバケットの数。|  
|**hashed_trans**|**bigint**|現在のバッチでレプリケートされたコミット済みトランザクションの数。|  
|**completed_trans**|**bigint**|これまでに処理したトランザクションの数。|  
|**compensated_trans**|**bigint**|部分ロールバックを含むトランザクションの数。|  
|**first_begin_lsn**|**nvarchar (64)**|現在のバッチの最初の開始ログシーケンス番号 (LSN)。|  
|**last_commit_lsn**|**nvarchar (64)**|現在のバッチの最後のコミット LSN。|  
  
## <a name="permissions"></a>アクセス許可  
 **Dm_repl_tranhash**を呼び出すには、パブリケーションデータベースに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="remarks"></a>解説  
 情報は、レプリケーションアーティクルキャッシュに現在読み込まれているレプリケートされたデータベースオブジェクトに対してのみ返されます。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [レプリケーション関連の動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  
