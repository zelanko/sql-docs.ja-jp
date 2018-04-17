---
title: sys.dm_exec_valid_use_hints (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sys.dm_exec_valid_use_hints
- sys.dm_exec_valid_use_hints_TSQL
- dm_exec_valid_use_hints
- dm_exec_valid_use_hints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_valid_use_hints management view
ms.assetid: 65d50589-39c2-4046-92b6-0c4587d8c593
caps.latest.revision: 5
author: pmasl
ms.author: pelopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b3df254ec44164e88cf9ec801f92898bbdeeafc7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmexecvalidusehints-transact-sql"></a>sys.dm_exec_valid_use_hints (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

返します[USE ヒント](../../t-sql/queries/hints-transact-sql-query.md)ヒント名をサポートします。 行ごとに 1 つのヒント名が一覧表示します。  
  
USE ヒント表記法でサポートされているすべてのヒントの一覧を表示するのにには、この DMV を使用します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|name|**sysname**|ヒントの名前。|

参照してください[クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)のヒントごとの説明についてはします。

導入された[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]SP1。
  
## <a name="see-also"></a>参照  
    
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

