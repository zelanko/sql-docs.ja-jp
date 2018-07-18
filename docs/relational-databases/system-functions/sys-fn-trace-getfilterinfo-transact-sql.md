---
title: sys.fn_trace_getfilterinfo (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_trace_getfilterinfo
- fn_trace_getfilterinfo_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server], filters
- sys.fn_trace_getfilterinfo function
- filters [SQL Server], traces
- fn_trace_getfilterinfo function
ms.assetid: 09fe4a28-ff8a-4655-9da1-4654d5bc514d
caps.latest.revision: 36
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1f55c02dfd91edbb964b87e74e2d413f9066501d
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37971877"
---
# <a name="sysfntracegetfilterinfo-transact-sql"></a>sys.fn_trace_getfilterinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したトレースに適用されるフィルターの情報を返します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 代わりに拡張イベントを使用します。  
  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
fn_trace_getfilterinfo ( trace_id )  
```  
  
## <a name="arguments"></a>引数  
 *trace_id*  
 トレースの ID を指定します。 *trace_id*は**int**、既定値はありません。  
  
## <a name="tables-returned"></a>返されるテーブル  
 次の情報を返します。 列に関する詳細については、次を参照してください。 [sp_trace_setfilter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**columnid**|**int**|フィルターが適用される列の ID。|  
|**logical_operator**|**int**|AND または OR 演算子が適用されるかどうかを示します。|  
|**comparison_operator**|**int**|実行される比較の種類を示します。次の種類があります。<br /><br /> 0 = 等しい<br /><br /> 1 = 等しくない<br /><br /> 2 = より大きい<br /><br /> 3 = より小さい<br /><br /> 4 = 以上<br /><br /> 5 = 以下<br /><br /> 6 = 一致<br /><br /> 7 = 一致しない|  
|**value**|**sql_variant**|フィルターを適用するときに使用する値を示します。|  
  
## <a name="remarks"></a>コメント  
 ユーザーのセット*trace_id*識別、変更、およびトレースを制御する値。 特定のトレースの ID が渡されたときに**fn_trace_getfilterinfo**そのトレースに関するすべてのフィルターに関する情報を返します。 指定されたトレースにフィルターがない場合、空の行セットが返されます。 無効な ID が渡された場合、空の行セットが返されます。 トレースに関する同様の情報を参照してください。 [sys.fn_trace_getinfo &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 サーバーの ALTER TRACE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、トレース番号 2 のすべてのフィルターに関する情報を返します。  
  
```  
SELECT * FROM fn_trace_getfilterinfo(2) ;  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [トレースの作成 &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [sp_trace_generateevent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [sys.fn_trace_geteventinfo &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [sys.fn_trace_gettable &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md)  
  
  
