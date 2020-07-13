---
title: dm_exec_valid_use_hints (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 5bcc9db1f2ff0b4395a68025e54b719dc25c31cd
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053464"
---
# <a name="sysdm_exec_valid_use_hints-transact-sql"></a>dm_exec_valid_use_hints (Transact-sql)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

[使用ヒント](../../t-sql/queries/hints-transact-sql-query.md#use_hint)がサポートされているヒント名を返します。 行ごとに1つのヒント名が一覧表示されます。  
  
この DMV を使用して、サポートされているすべてのヒントの一覧を使用ヒント表記で表示します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|name|**sysname**|ヒントの名前。|

各ヒントの説明については、「[クエリヒント](../../t-sql/queries/hints-transact-sql-query.md#use_hint)」を参照してください。

SP1 で導入されました [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 。
  
## <a name="see-also"></a>参照  
    
 [Transact-sql&#41;&#40;の動的管理ビューおよび関数](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Transact-sql&#41;&#40;データベース関連の動的管理ビュー](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

