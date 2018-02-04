---
title: "sys.dm_pdw_network_credentials (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.reviewer: 
ms.service: 
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4bddbdd676ab829f1468866c09d745919d1fe97d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwnetworkcredentials-transact-sql"></a>sys.dm_pdw_network_credentials (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  格納されているすべてのネットワーク資格情報の一覧を返します、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]アプライアンスのすべての対象サーバーです。 結果は、コントロールのノード、およびすべてのコンピューティング ノードの一覧に表示されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|ノードに関連付けられている一意の数値 id です。|  
|target_server_name|**nvarchar(32)**|対象サーバーの IP アドレスを[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]はユーザー名とパスワード資格情報を使用してアクセスします。|  
|username|**nvarchar(32)**|ユーザー名が、パスワードが保存されます。|  
|last_modified|**datetime**|資格情報を変更する最後の操作の日付と時刻。|  
  
## <a name="permissions"></a>権限  
 VIEW SERVER STATE が必要です。  
  
## <a name="general-remarks"></a>全般的な解説  
 この動的管理ビューのキーは*pdw_node_id* plus *target_server_name*です。  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
