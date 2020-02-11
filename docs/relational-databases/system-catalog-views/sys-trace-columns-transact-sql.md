---
title: trace_columns (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.trace_columns
- trace_columns
- trace_columns_TSQL
- sys.trace_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trace_columns catalog view
ms.assetid: 5c48eb09-9e9b-45dd-b151-ca39b026ece5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bda45d55505356594f23a8bb1ece2e95153206a7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68022656"
---
# <a name="systrace_columns-transact-sql"></a>sys.trace_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Trace_columns**カタログビューには、すべてのトレースイベント列の一覧が含まれています。 これらの列は、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の特定のバージョンでは変更されません。  
  
 サポートされているトレースイベントの完全な一覧については、「 [SQL Server イベントクラスのリファレンス](../../relational-databases/event-classes/sql-server-event-class-reference.md)」を参照してください。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに拡張イベントカタログビューを使用します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**trace_column_id**|**smallint**|この列の一意の ID。|  
|**name**|**nvarchar(128**|この列の一意な名前。 このパラメーターはローカライズされていません。|  
|**type_name**|**nvarchar(128**|この列のデータ型名です。|  
|**max_size**|**int**|この列の最大データサイズ (バイト単位)。|  
|**is_filterable**|**bit**|フィルターの指定に列を使用できるかどうか。<br /><br /> 0 = false<br /><br /> 1 = true|  
|**is_repeatable**|**bit**|"繰り返し列" のデータで列を参照できるかどうか。<br /><br /> 0 = false<br /><br /> 1 = true|  
|**is_repeated_base**|**bit**|繰り返しデータを参照する一意のキーとして、この列を使用できるかどうか。<br /><br /> 0 = false<br /><br /> 1 = true|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Transact-sql&#41;&#40;のトレース](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [trace_categories &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [trace_events &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [trace_event_bindings &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [trace_subclass_values &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
