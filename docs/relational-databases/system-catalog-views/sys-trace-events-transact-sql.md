---
title: "sys.trace_events (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- trace_events_TSQL
- trace_events
- sys.trace_events
- sys.trace_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trace_events catalog view
ms.assetid: e7d2c5df-0e17-4e94-9d41-d36c7ee60662
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1d067dc13fbaeecac2b20ee771b8fd9bd2e283b0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="systraceevents-transact-sql"></a>sys.trace_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sys.trace_events**カタログ ビューには、すべての SQL トレース イベントの一覧が含まれています。 これらのトレース イベントは、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]によって異なることはありません。  
  
> **重要:** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]拡張イベント カタログ ビューを代わりに使用します。  
  
 これらのトレース イベントの詳細については、次を参照してください。 [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md)です。  
  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**trace_event_id**|**smallint**|イベントの一意な ID。 この列にではまた、 **sys.trace_event_bindings**と**sys.trace_subclass_values**カタログ ビューです。|  
|**category_id**|**smallint**|イベントのカテゴリ ID。 この列にではまた、 **sys.trace_categories**カタログ ビューです。|  
|**name**|**nvarchar(128)**|このイベントの一意な名前。 このパラメーターはローカライズされません。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.traces &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys.trace_categories &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys.trace_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [sys.trace_event_bindings &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [sys.trace_subclass_values &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
