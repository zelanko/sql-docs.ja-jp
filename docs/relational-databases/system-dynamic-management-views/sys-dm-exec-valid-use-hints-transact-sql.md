---
title: sys.dm_exec_valid_use_hints (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
ms.openlocfilehash: d1fb0ffed04c77e280d02378429cf769107bdfbc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37987144"
---
# <a name="sysdmexecvalidusehints-transact-sql"></a>sys.dm_exec_valid_use_hints (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

返します[USE HINT](../../t-sql/queries/hints-transact-sql-query.md)ヒント名がサポートされています。 行ごとに 1 つのヒント名が一覧表示します。  
  
この DMV を使用して、USE HINT 表記法でサポートされているすべてのヒントの一覧を参照してください。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|NAME|**sysname**|ヒントの名前。|

参照してください[クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)の各ヒントについて説明します。

導入された[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]SP1。
  
## <a name="see-also"></a>参照  
    
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

