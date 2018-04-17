---
title: sp_trace_setstatus (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_trace_setstatus_TSQL
- sp_trace_setstatus
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_setstatus
ms.assetid: 29e7a7d7-b9c1-414a-968a-fc247769750d
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a6f6aacf619df24477528b4d39ad9551be321e61
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sptracesetstatus-transact-sql"></a>sp_trace_setstatus (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したトレースの現在の状態を変更します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 代わりに拡張イベントを使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_trace_setstatus [ @traceid = ] trace_id , [ @status = ] status  
```  
  
## <a name="arguments"></a>引数  
 [ **@traceid=** ] *trace_id*  
 変更するトレースの ID を指定します。 *trace_id*は**int**、既定値はありません。 ユーザーが使用してこの*trace_id*識別、変更、およびトレースを制御する値。 取得する方法について、 *trace_id*を参照してください[sys.fn_trace_getinfo &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)です。  
  
 [  **@status=** ]*ステータス*  
 トレースに実装する操作を指定します。 *ステータス*は**int**、既定値はありません。  
  
 次の表は、指定できる状態の一覧です。  
  
|[状態]|Description|  
|------------|-----------------|  
|**0**|指定されたトレースを停止します。|  
|**1**|指定されたトレースを開始します。|  
|**2**|指定されたトレースを閉じて、その定義をサーバーから削除します。|  
  
> [!NOTE]  
>  トレースを閉じるには、最初にそのトレースを停止する必要があります。 トレースを表示するには、最初にそのトレースを停止して閉じる必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 次の表は、このストアド プロシージャの完了時に返されるコード値を示しています。  
  
|リターン コード|Description|  
|-----------------|-----------------|  
|**0**|エラーなし。|  
|**1**|不明なエラーです。|  
|**8**|指定した状態は無効です。|  
|**9**|指定したトレース ハンドルは無効です。|  
|**13**|メモリ不足。 指定した操作を実行するための十分なメモリがない場合に返されます。|  
  
 場合は、トレースが、指定した状態で既に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]戻ります**0**します。  
  
## <a name="remarks"></a>解説  
 ストアド プロシージャのすべての SQL トレースのパラメーター (**sp_trace_xx**) は、厳密に型指定されています。 これらのパラメーターを、引数の説明で指定されている正しいデータ型で指定しないと、このストアド プロシージャではエラーが返されます。  
  
 トレース ストアド プロシージャを使用した例については、「[トレースの作成 &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>権限  
 ユーザーに ALTER TRACE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sys.fn_trace_geteventinfo &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sp_trace_generateevent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [SQL トレース (SQL Trace)](../../relational-databases/sql-trace/sql-trace.md)  
  
  
