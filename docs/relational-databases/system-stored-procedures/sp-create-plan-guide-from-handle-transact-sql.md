---
title: sp_create_plan_guide_from_handle (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_create_plan_guide_from_handle_TSQL
- sp_create_plan_guide_from_handle
dev_langs:
- TSQL
helpviewer_keywords:
- sp_create_plan_guide_from_handle
ms.assetid: 02cfb76f-a0f9-4b42-a880-1c3e7d64fe41
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 78d466a6860eb145c409f32735c812f17a051e44
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032972"
---
# <a name="spcreateplanguidefromhandle-transact-sql"></a>sp_create_plan_guide_from_handle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  プラン キャッシュ内のクエリ プランから 1 つ以上のプラン ガイドを作成します。 このストアド プロシージャを使用すると、クエリ オプティマイザーが指定のクエリに対して常に特定のクエリ プランを使用するように設定できます。 プラン ガイドの詳細については、「 [Plan Guides](../../relational-databases/performance/plan-guides.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_create_plan_guide_from_handle [ @name = ] N'plan_guide_name'  
    , [ @plan_handle = ] plan_handle  
    , [ [ @statement_start_offset = ] { statement_start_offset | NULL } ]  
```  
  
## <a name="arguments"></a>引数  
 [ @name =] N'*plan_guide_name*'  
 プラン ガイドの名前を指定します。 プラン ガイド名は現在のデータベースに対して有効です。 *plan_guide_name*の規則に従っている必要があります[識別子](../../relational-databases/databases/database-identifiers.md)番号記号で始めることはできません (#)。 最大長*plan_guide_name*は 124 文字です。  
  
 [ @plan_handle =] *plan_handle*  
 プラン キャッシュのバッチを識別します。 *plan_handle*は**varbinary (64)** します。 *plan_handle*から取得できます、 [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)動的管理ビュー。  
  
 [ @statement_start_offset =] { *statement_start_offset* |NULL}]  
 指定したバッチ内のステートメントの開始位置を識別する*plan_handle*します。 *statement_start_offset*は**int**、既定値は NULL です。  
  
 ステートメント オフセットは statement_start_offset 列に対応する、 [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)動的管理ビュー。  
  
 NULL を指定した場合や、ステートメント オフセットを指定しない場合は、指定したプラン ハンドルのクエリ プランを使用してバッチ内の各ステートメントに対してプラン ガイドが作成されます。 結果のプラン ガイドは、USE PLAN クエリ ヒントを使用して特定のプランを強制的に使用させるプラン ガイドと同等になります。  
  
## <a name="remarks"></a>コメント  
 すべての種類のステートメントに対してプラン ガイドを作成できるわけではありません。 プラン ガイドを作成できないステートメントがバッチ内にあった場合、そのステートメントは無視されて、バッチ内の次のステートメントが処理されます。 同じバッチ内に複数回出現するステートメントがあった場合は、最後に出現した箇所のプランが有効になり、それより前のプランは無効になります。 プラン ガイドで使用できるステートメントがバッチ内になかった場合は、エラー 10532 が発生してステートメントが失敗します。 このエラーを回避するため、常に sys.dm_exec_query_stats 動的管理ビューからプラン ハンドルを取得することをお勧めします。  
  
> [!IMPORTANT]  
>  sp_create_plan_guide_from_handle では、プラン キャッシュに含まれているとおりのプランに基づいてプラン ガイドが作成されます。 したがって、バッチ テキスト、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント、および XML プラン表示が、プラン キャッシュから結果のプラン ガイドに文字単位で (クエリに渡されたリテラル値も含め) 取り込まれます。 これらのテキスト文字列に機密情報が含まれていた場合、それらはデータベースのメタデータに格納されます。 適切なアクセス許可を持つユーザーは、sys.plan_guides カタログ ビューを使用してこの情報を表示することができます、**プラン ガイド プロパティ** ダイアログ ボックスで[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。 プラン ガイドから機密情報が漏洩しないように、プラン キャッシュから作成されたプラン ガイドを確認することをお勧めします。  
  
## <a name="creating-plan-guides-for-multiple-statements-within-a-query-plan"></a>クエリ プラン内の複数のステートメントに対するプラン ガイドの作成  
 sp_create_plan_guide_from_handle では、sp_create_plan_guide と同様に、対象となるバッチやモジュールのクエリ プランがプラン キャッシュから削除されます。 これは、新しいプラン ガイドがすべてのユーザーによって使用されるようにするための措置です。 1 つのクエリ プラン内の複数のステートメントに対してプラン ガイドを作成する場合は、すべてのプラン ガイドを明示的なトランザクションの中で作成することによって、キャッシュからプランが削除されるのを遅らせることができます。 これにより、そのトランザクションが完了して、指定した各ステートメントのプラン ガイドが作成されるまで、プランがキャッシュに保持されます。 例 B を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 VIEW SERVER STATE 権限が必要です。 その他、sp_create_plan_guide_from_handle を使用して作成するプラン ガイドごとに必要な個々の権限があります。 型のプラン ガイドを作成するには、オブジェクトには、参照先オブジェクトに対する ALTER 権限が必要です。 SQL または TEMPLATE 型のプラン ガイドを作成するには、現在のデータベースに対する ALTER 権限が必要です。 作成されるプラン ガイドの型を特定するには、次のクエリを実行します。  
  
```  
SELECT cp.plan_handle, sql_handle, st.text, objtype   
FROM sys.dm_exec_cached_plans AS cp  
JOIN sys.dm_exec_query_stats AS qs ON cp.plan_handle = qs.plan_handle  
CROSS APPLY sys.dm_exec_sql_text(sql_handle) AS st;  
```  
  
 プラン ガイドを作成するステートメントを含む行を調べて、`objtype`結果セット内の列。 値`Proc`プラン ガイドは OBJECT 型を示します。 その他の値など`AdHoc`または`Prepared`SQL 型のプラン ガイドを示します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-plan-guide-from-a-query-plan-in-the-plan-cache"></a>A. プラン キャッシュ内のクエリ プランからプラン ガイドを作成する  
 次の例では、プラン キャッシュ内のクエリ プランを指定して 1 つの SELECT ステートメントのプラン ガイドを作成します。 まず、プラン ガイドを作成する単純な `SELECT` ステートメントを実行します。 次に、動的管理ビューの `sys.dm_exec_sql_text` および `sys.dm_exec_text_query_plan` を使用してこのクエリのプランを調べます。 その後、クエリに関連付けられているプラン キャッシュ内のクエリ プランを指定して、クエリのプラン ガイドを作成します。 この例の最後のステートメントは、プラン ガイドが存在することを確認します。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT WorkOrderID, p.Name, OrderQty, DueDate  
FROM Production.WorkOrder AS w   
JOIN Production.Product AS p ON w.ProductID = p.ProductID  
WHERE p.ProductSubcategoryID > 4  
ORDER BY p.Name, DueDate;  
GO  
-- Inspect the query plan by using dynamic management views.  
SELECT * FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_sql_text(sql_handle)  
CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, qs.statement_start_offset, qs.statement_end_offset) AS qp  
WHERE text LIKE N'SELECT WorkOrderID, p.Name, OrderQty, DueDate%';  
GO  
-- Create a plan guide for the query by specifying the query plan in the plan cache.  
DECLARE @plan_handle varbinary(64);  
DECLARE @offset int;  
SELECT @plan_handle = plan_handle, @offset = qs.statement_start_offset  
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_sql_text(sql_handle) AS st  
CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, qs.statement_start_offset, qs.statement_end_offset) AS qp  
WHERE text LIKE N'SELECT WorkOrderID, p.Name, OrderQty, DueDate%';  
  
EXECUTE sp_create_plan_guide_from_handle   
    @name =  N'Guide1',  
    @plan_handle = @plan_handle,  
    @statement_start_offset = @offset;  
GO  
-- Verify that the plan guide is created.  
SELECT * FROM sys.plan_guides  
WHERE scope_batch LIKE N'SELECT WorkOrderID, p.Name, OrderQty, DueDate%';  
GO  
```  
  
### <a name="b-creating-multiple-plan-guides-for-a-multistatement-batch"></a>B. 複数のステートメントで構成されるバッチに対して複数のプラン ガイドを作成する  
 次の例では、複数のステートメントで構成されるバッチ内の 2 つのステートメントに対してプラン ガイドを作成します。 最初のプラン ガイドの作成後にバッチのクエリ プランがプラン キャッシュから削除されないように、明示的なトランザクションの中でプラン ガイドを作成します。 まず、複数のステートメントで構成されるバッチを実行します。 次に、動的管理ビューを使用してバッチのプランを調べます。 バッチ内の各ステートメントに対して行が返されていることに注目してください。 指定して、バッチ内の最初と 3 番目のステートメントのプラン ガイドが作成し、`@statement_start_offset`パラメーター。 最後のステートメントの例では、プラン ガイドが存在することを確認します。  
  
 [!code-sql[PlanGuides#Create_From_Handle2](../../relational-databases/system-stored-procedures/codesnippet/tsql/sp-create-plan-guide-fro_1.sql)]  
  
## <a name="see-also"></a>参照  
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 [プラン ガイド](../../relational-databases/performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_text_query_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql.md)   
 [sp_control_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql.md)  
  
  
