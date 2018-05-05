---
title: sys.dm_fts_fdhosts (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_fts_fdhosts
- dm_fts_fdhosts_TSQL
- sys.dm_fts_fdhosts
- sys.dm_fts_fdhosts_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_fdhosts dynamic management view
- troubleshooting [SQL Server], full-text search
ms.assetid: d42a6334-4362-4361-83da-f8324fe55ec7
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b4bc446dbcf3b896dca1b33789cfd1f0f1e89ff9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmftsfdhosts-transact-sql"></a>sys.dm_fts_fdhosts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  サーバー インスタンス上のフィルター デーモン ホストの現在のアクティビティに関する情報を返します。  
  
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**fdhost_id**|**int**|フィルター デーモン ホストの ID。|  
|**fdhost_name**|**nvarchar(120)**|フィルター デーモン ホストの名前。|  
|**fdhost_process_id**|**int**|フィルター デーモン ホストの Windows プロセス ID。|  
|**fdhost_type**|**nvarchar(120)**|フィルター デーモン ホストで処理されるドキュメントの種類。次のいずれかです。<br /><br /> シングルスレッド<br /><br /> マルチスレッド<br /><br /> 巨大なドキュメント|  
|**max_thread**|**int**|フィルター デーモン ホストのスレッドの最大数。|  
|**batch_count**|**int**|フィルター デーモン ホストで処理中のバッチ数。|  
  
## <a name="permissions"></a>権限  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   

## <a name="examples"></a>使用例  
 次の例では、フィルター デーモン ホストの名前とフィルター デーモン ホストのスレッドの最大数を返します。 また、フィルター デーモン ホストで現在処理されているバッチの数も監視します。 この情報はパフォーマンスの診断に使用できます。  
  
```  
SELECT fdhost_name, batch_count, max_thread FROM sys.dm_fts_fdhosts;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索とセマンティック検索の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)  
  
  
