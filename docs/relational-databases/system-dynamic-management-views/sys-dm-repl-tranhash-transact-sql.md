---
title: sys.dm_repl_tranhash (TRANSACT-SQL) |Microsoft Docs
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7d10d4451071ac476b25fdfef00ab4a48d1c3f63
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47736589"
---
# <a name="sysdmrepltranhash-transact-sql"></a>sys.dm_repl_tranhash (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  トランザクション パブリケーションでレプリケートされるトランザクションに関する情報を返します。  
  
|column_name|data_type|description|  
|------------------|----------------|-----------------|  
|**buckets**|**bigint**|ハッシュ テーブルに含まれるバケット数。|  
|**hashed_trans**|**bigint**|現在のバッチでレプリケートされるコミット済みトランザクションの数。|  
|**completed_trans**|**bigint**|これまでに完了したトランザクションの数。|  
|**compensated_trans**|**bigint**|部分ロールバックを含むトランザクションの数。|  
|**first_begin_lsn**|**nvarchar(64)**|現在のバッチで最も早い開始ログ シーケンス番号 (LSN)。|  
|**last_commit_lsn**|**nvarchar(64)**|現在のバッチで最後にコミットされた LSN。|  
  
## <a name="permissions"></a>アクセス許可  
 呼び出すパブリケーション データベースに対する VIEW DATABASE STATE 権限が必要**dm_repl_tranhash**します。  
  
## <a name="remarks"></a>コメント  
 返される情報は、レプリケーション アーティクル キャッシュに現在読み込まれている、レプリケートされたデータベース オブジェクトの情報だけです。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [レプリケーション関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  
