---
title: sys.trace_subclass_values (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.trace_subclass_values
- trace_subclass_values_TSQL
- sys.trace_subclass_values_TSQL
- trace_subclass_values
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trace_subclass_values catalog view
ms.assetid: 542b19ca-61c8-41ca-aa2e-0aba8906cc24
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 070327b43854e9b78f927e68ebfb1f20d607f5d9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37969635"
---
# <a name="systracesubclassvalues-transact-sql"></a>sys.trace_subclass_values (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sys.trace_subclass_values**カタログ ビューには、名前付きの列の値の一覧が含まれています。 これらのサブクラス値の指定したバージョンは変わりません、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]します。  
  
 サポートされているトレース イベントの完全な一覧を参照してください。 [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md)します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 拡張イベント カタログ ビューを代わりに使用します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**trace_event_id**|**smallint**|トレース イベントの ID。 このパラメーターもに、 **sys.trace_events**カタログ ビューです。|  
|**trace_column_id**|**smallint**|列挙に使用されるトレース列の ID。 このパラメーターもに、 **sys.trace_columns**カタログ ビューです。|  
|**subclass_name**|**nvarchar(128)**|列の値の意味。|  
|**subclass_value**|**smallint**|列の値。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.traces &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys.trace_categories &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys.trace_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [sys.trace_events &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [sys.trace_event_bindings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)  
  
  
