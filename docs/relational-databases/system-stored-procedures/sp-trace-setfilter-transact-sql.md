---
title: "sp_trace_setfilter (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_trace_setfilter
- sp_trace_setfilter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_setfilter
ms.assetid: 11e7c7ac-a581-4a64-bb15-9272d5c1f7ac
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 82c7d580f8ff94e0d7fb4452d1608f93b776fe3b
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sptracesetfilter-transact-sql"></a>sp_trace_setfilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  トレースにフィルターを適用します。 **sp_trace_setfilter**停止している既存のトレースに対してのみ実行できます (*ステータス*は**0**)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]このストアド プロシージャが存在しないトレースまたはで実行される場合はエラーを返します*ステータス*は**0**します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 代わりに拡張イベントを使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_trace_setfilter [ @traceid = ] trace_id   
          , [ @columnid = ] column_id  
          , [ @logical_operator = ] logical_operator  
          , [ @comparison_operator = ] comparison_operator  
          , [ @value = ] value  
```  
  
## <a name="arguments"></a>引数  
 [ **@traceid=** ] *trace_id*  
 フィルターを適用するトレースの ID を指定します。 *trace_id*は**int**、既定値はありません。 ユーザーが使用してこの*trace_id*識別、変更、およびトレースを制御する値。  
  
 [ **@columnid=** ] *column_id*  
 フィルターが適用される列の ID を指定します。 *column_id*は**int**、既定値はありません。 場合*column_id* null、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指定されたトレースに対してすべてのフィルターをクリアします。  
  
 [ **@logical_operator** = ] *logical_operator*  
 指定するかどうか AND (**0**) または OR (**1**) 演算子を適用します。 *logical_operator*は**int**、既定値はありません。  
  
 [ **@comparison_operator=** ] *comparison_operator*  
 実行される比較の種類を示します。 *comparison_operator*は**int**、既定値はありません。 次の表は、比較演算子と各比較演算子に対応する値の一覧です。  
  
|[値]|比較演算子|  
|-----------|-------------------------|  
|**0**|= (等しい)|  
|**1**|<> (等しくない)|  
|**2**|> (より大きい)|  
|**3**|< (より小さい)|  
|**4**|> = (より大きいまたは等しい)|  
|**5**|< = (以下)|  
|**6**|LIKE|  
|**7**|パターンに一致しない|  
  
 [ **@value=** ] *value*  
 フィルターの対象となる値を指定します。 データ型*値*をフィルター選択するのには、列のデータ型に一致する必要があります。 たとえば、あるオブジェクトの ID 列にフィルターが設定されている場合、 **int**データ型、*値*する必要があります**int**です。場合*値*は**nvarchar**または**varbinary**8000 の最大長を持つことができます。  
  
 比較演算子が LIKE または NOT LIKE である場合、論理演算子には、"%" または LIKE 演算に適した他のフィルターを含めることができます。  
  
 NULL を指定することができます*値*NULL 列値を持つイベントを除外します。 のみ**0** (= 等号) と**1** (<> 不等号) 演算子は NULL で有効です。 この場合、これらの演算子は、[!INCLUDE[tsql](../../includes/tsql-md.md)] の IS NULL 演算子および IS NOT NULL 演算子と等価です。  
  
 列の値の範囲内のフィルターを適用する**sp_trace_setfilter**必要があります 2 回 - 1 回実行すると、大きい-よりも-または-equals ('> =') 比較演算子、および、小のよりも-または-equals で別の時間 ('< =') 演算子.  
  
 データ列のデータ型の詳細については、次を参照してください。、 [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md)です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 次の表は、このストアド プロシージャの完了時に返されるコード値を示しています。  
  
|リターン コード|Description|  
|-----------------|-----------------|  
|0|エラーなし。|  
|1|不明なエラーです。|  
|2|トレースは現在実行中です。 この結果、エラーが発生したときにトレースを変更します。|  
|4|指定された列が正しくありません。|  
|5|指定した列にはフィルターを適用できません。 この値がからのみ返されます**sp_trace_setfilter**です。|  
|6|指定した比較演算子は無効です。|  
|7|指定した論理演算子は無効です。|  
|9|指定したトレース ハンドルは無効です。|  
|13|メモリ不足。 指定した操作を実行するための十分なメモリがない場合に返されます。|  
|16|関数がこのトレースに対して無効です。|  
  
## <a name="remarks"></a>解説  
 **sp_trace_setfilter**は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の以前のバージョンで利用可能な拡張のストアド プロシージャで実行される操作の多くを実行するストアド プロシージャ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 使用して**sp_trace_setfilter**の代わりに、 **xp_trace_set\*フィルター**を作成するストアド プロシージャを拡張するには、適用、削除、またはトレースのフィルターを操作します。 詳細については、次を参照してください。[トレースをフィルター処理](../../relational-databases/sql-trace/filter-a-trace.md)です。  
  
 特定の列のすべてのフィルターは、の 1 つの実行で同時に有効にする必要があります**sp_trace_setfilter**です。 たとえば、ユーザーがアプリケーション名の列に 2 つのフィルターを適用し、ユーザー名の列に 1 つのフィルターを適用する場合は、アプリケーション名のフィルターを続けて指定する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーの場合、ユーザーが、1 つのストアド プロシージャ呼び出しでアプリケーション名でフィルターを指定しようとしています。 後にフィルターでユーザー名、アプリケーション名の別のフィルターを返します。  
  
 ストアド プロシージャのすべての SQL トレースのパラメーター (**sp_trace_xx**) は、厳密に型指定されています。 これらのパラメーターが、引数の説明で指定されている正しいデータ型で呼び出されないと、このストアド プロシージャではエラーが返されます。  
  
## <a name="permissions"></a>権限  
 ユーザーに ALTER TRACE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、3 つのフィルターを設定 trace`1`です。 フィルター`N'SQLT%'`と`N'MS%'`1 つの列を操作 (`AppName`、値`10`) を使用して、"`LIKE`"比較演算子です。 フィルター `N'joe'` は、"`UserName`" 比較演算子を使用して別の列 (`11`、値 `EQUAL`) に適用されます。  
  
```  
sp_trace_setfilter  1, 10, 0, 6, N'SQLT%';  
sp_trace_setfilter  1, 10, 0, 6, N'MS%';  
sp_trace_setfilter  1, 11, 0, 0, N'joe';  
```  
  
## <a name="see-also"></a>参照  
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [SQL トレース (SQL Trace)](../../relational-databases/sql-trace/sql-trace.md)  
  
  
