---
title: sys.dm_pdw_network_credentials (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.component: dmv's
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f782d832dc5f3d962fcfc7aa72b1fa196159312d
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
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
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
