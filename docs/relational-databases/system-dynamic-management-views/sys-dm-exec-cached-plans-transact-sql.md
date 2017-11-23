---
title: "sys.dm_exec_cached_plans (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_cached_plans
- dm_exec_cached_plans
- dm_exec_cached_plans_TSQL
- sys.dm_exec_cached_plans_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_cached_plans dynamic management view
ms.assetid: 95b707d3-3a93-407f-8e88-4515d4f2039d
caps.latest.revision: "44"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 816fcb7a7fbf362f2f531b93629508ab3ab2b76f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexeccachedplans-transact-sql"></a>sys.dm_exec_cached_plans (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  クエリ実行を高速化するため [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でキャッシュされた各クエリ プランについての行を返します。 この動的管理ビューを使用して、キャッシュされたクエリ プラン、キャッシュされたクエリ テキスト、キャッシュされたプランが確保するメモリの量、およびキャッシュされたプランの再利用回数を参照できます。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、動的管理ビューは、データベースの包含に影響を与えるまたはユーザーがアクセスを他のデータベースに関する情報が公開される情報を公開できません。 この情報が公開されないように、接続されたテナントに属していないデータを含む行はすべてフィルターで除外されます。さらに、列の値**memory_object_address**と**pool_id**フィルター処理され、列の値は NULL に設定します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_exec_cached_plans**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|bucketid|**int**|エントリをキャッシュするハッシュ バケットの ID。 値の範囲は、0 からキャッシュの種類によって決まっているハッシュ テーブルのサイズまでです。<br /><br /> SQL プランおよびオブジェクト プランのキャッシュでは、ハッシュ テーブルのサイズが 32 ビット システムで最大 10007、64 ビット システムで最大 40009 です。 Bound Trees のキャッシュでは、ハッシュ テーブルのサイズが 32 ビット システムで最大 1009、64 ビット システムで最大 4001 です。 拡張ストアド プロシージャのキャッシュでは、ハッシュ テーブルのサイズが 32 ビット システムでも 64 ビット システムでも 127 です。|  
|refcounts|**int**|このキャッシュ オブジェクトを参照しているキャッシュ オブジェクトの数。 **Refcounts**キャッシュ内にあるエントリを 1 以上にする必要があります。|  
|usecounts|**int**|キャッシュ オブジェクトが検索された回数。 パラメーター化クエリがキャッシュ内のプランを検索したときは増加しません。 プラン表示を使用しているときは複数回増加できます。|  
|size_in_bytes|**int**|キャッシュ オブジェクトによって使用されたバイト数。|  
|memory_object_address|**varbinary (8)**|キャッシュ エントリのメモリ アドレス。 この値で使用できる[sys.dm_os_memory_objects](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md)を使用して、キャッシュされたプランのメモリ内訳を取得する[sys.dm_os_memory_cache_entries](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-entries-transact-sql.md)とエントリをキャッシュするコストを取得します。|  
|cacheobjtype|**nvarchar (34)**|キャッシュ内のオブジェクトの種類。 値は、次のいずれかです。<br /><br /> Compiled Plan<br /><br /> Compiled Plan Stub<br /><br /> Parse Tree<br /><br /> Extended Proc<br /><br /> CLR Compiled Func<br /><br /> CLR Compiled Proc|  
|objtype|**nvarchar (16)**|オブジェクトの種類。 使用可能な値とその対応する説明のとおりです。<br /><br /> Proc: ストアド プロシージャ<br />準備されたステートメントの準備:<br />Adhoc: アドホック クエリです。 指す[!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して言語イベントとして送信された**osql**または**sqlcmd**の代わりにリモート プロシージャ呼び出しとして。<br />ReplProc: レプリケーション フィルター プロシージャ<br />トリガー: トリガー<br />ビュー: 表示<br />Default: 既定<br />UsrTab: ユーザー テーブル<br />SysTab: システム テーブル<br />CHECK 制約をチェックします。<br />ルール: ルール|  
|plan_handle|**varbinary (64)**|インメモリ プランの識別子。 この識別子は一時的なもので、プランがキャッシュに残っている間だけ一定の値になります。 この値は、次の動的管理関数で使用できます。<br /><br /> [sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)<br /><br /> [sys.dm_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)<br /><br /> [sys.dm_exec_plan_attributes](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md)|  
|pool_id|**int**|このプランのメモリ使用量の大部分を占めるリソース プールの ID。|  
|pdw_node_id|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
 <sup>1</sup>  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Premium 階層には、データベースの VIEW DATABASE STATE 権限が必要です。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard および Basic 階層が必要です、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]管理者アカウントです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-the-batch-text-of-cached-entries-that-are-reused"></a>A. 再利用されたキャッシュ エントリのバッチ テキストを取得する  
 次の例は、複数回使用されたすべてのキャッシュ エントリの SQL テキストを返します。  
  
```  
SELECT usecounts, cacheobjtype, objtype, text   
FROM sys.dm_exec_cached_plans   
CROSS APPLY sys.dm_exec_sql_text(plan_handle)   
WHERE usecounts > 1   
ORDER BY usecounts DESC;  
GO  
```  
  
### <a name="b-returning-query-plans-for-all-cached-triggers"></a>B. キャッシュされたすべてのトリガーのクエリ プランを取得する  
 次の例は、キャッシュされたすべてのトリガーのクエリ プランを返します。  
  
```  
SELECT plan_handle, query_plan, objtype   
FROM sys.dm_exec_cached_plans   
CROSS APPLY sys.dm_exec_query_plan(plan_handle)   
WHERE objtype ='Trigger';  
GO  
```  
  
### <a name="c-returning-the-set-options-with-which-the-plan-was-compiled"></a>C. プランをコンパイルした SET オプションを取得する  
 次の例は、プランをコンパイルした SET オプションを返します。 `sql_handle`計画も返されます。 PIVOT 演算子が使用される出力を`set_options`と`sql_handle`属性の行ではなく列として。 戻り値の詳細については`set_options`を参照してください[sys.dm_exec_plan_attributes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md).  
  
```  
SELECT plan_handle, pvt.set_options, pvt.sql_handle  
FROM (  
      SELECT plan_handle, epa.attribute, epa.value   
      FROM sys.dm_exec_cached_plans   
      OUTER APPLY sys.dm_exec_plan_attributes(plan_handle) AS epa  
      WHERE cacheobjtype = 'Compiled Plan'  
      ) AS ecpa   
PIVOT (MAX(ecpa.value) FOR ecpa.attribute IN ("set_options", "sql_handle")) AS pvt;  
GO  
```  
  
### <a name="d-returning-the-memory-breakdown-of-all-cached-compiled-plans"></a>D. キャッシュされたすべてのコンパイル済みプランのメモリ内訳を取得する  
 次の例は、キャッシュにあるすべてのコンパイル済みプランのメモリ内訳を返します。  
  
```  
SELECT plan_handle, ecp.memory_object_address AS CompiledPlan_MemoryObject,   
    omo.memory_object_address, pages_allocated_count, type, page_size_in_bytes   
FROM sys.dm_exec_cached_plans AS ecp   
JOIN sys.dm_os_memory_objects AS omo   
    ON ecp.memory_object_address = omo.memory_object_address   
    OR ecp.memory_object_address = omo.parent_address  
WHERE cacheobjtype = 'Compiled Plan';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_query_plan &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)   
 [sys.dm_exec_plan_attributes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_os_memory_objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md)   
 [sys.dm_os_memory_cache_entries &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-entries-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)  
  
  


