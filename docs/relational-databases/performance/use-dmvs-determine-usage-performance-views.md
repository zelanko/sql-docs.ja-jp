---
title: DMV を使用してビューの使用統計とパフォーマンスを確認する
description: DMV を使用してビューの使用統計とパフォーマンスを確認する
manager: craigg
author: MashaMSFT
ms.author: mathoma
ms.date: 09/27/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.openlocfilehash: 1ac9c72ecee9beee66ea190b3acf233a0e4bc753
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47618410"
---
# <a name="use-dmvs-to-determine-usage-statistics-and-performance-of-views"></a>DMV を使用してビューの使用統計とパフォーマンスを確認する

この記事では、データベース オブジェクトで**ビューを使用するクエリのパフォーマンス**に関する情報を取得するために使用する方法とスクリプトについて説明します。 これらのスクリプトの目的は、データベース内のさまざまなビューの使用とパフォーマンスのインジケーターを提供することです。 

## <a name="sysdmexecqueryoptimizerinfo"></a>Sys.dm_exec_query_optimizer_info

DMV [sys.dm_exec_query_optimizer_info](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-optimizer-info-transact-sql) では、SQL Server クエリ オプティマイザーによって行われた最適化に関する統計情報が公開されます。 これらの値は累積的であり、SQL Server の起動時に記録を開始します。  

次の common_table_expression (CTE) では、この DMV を使用して、ビューを参照するクエリの割合など、ワークロードに関する情報を提供します。 このクエリによって返される結果では、パフォーマンスの問題自体は示されませんが、クエリのパフォーマンスが悪いというユーザーの不満と組み合わせることで、基になる問題が明らかになります。 


```SQL
WITH CTE_QO AS
(
  SELECT
    occurrence
  FROM
    sys.dm_exec_query_optimizer_info
  WHERE
    ([counter] = 'optimizations')
),
QOInfo AS
(
  SELECT
    [counter]
    ,[%] = CAST((occurrence * 100.00)/(SELECT occurrence FROM CTE_QO) AS DECIMAL(5, 2))
  FROM
    sys.dm_exec_query_optimizer_info
  WHERE
    [counter] IN ('optimizations'
                  ,'trivial plan'
                  ,'no plan'
                  ,'search 0'
                  ,'search 1'
                  ,'search 2'
                  ,'timeout'
                  ,'memory limit exceeded'
                  ,'insert stmt'
                  ,'delete stmt'
                  ,'update stmt'
                  ,'merge stmt'
                  ,'contains subquery'
                  ,'view reference'
                  ,'remote query'
                  ,'dynamic cursor request'
                  ,'fast forward cursor request'
             )
)
SELECT
  [optimizations] AS [optimizations %]
  ,[trivial plan] AS [trivial plan %]
  ,[no plan] AS [no plan %]
  ,[search 0] AS [search 0 %]
  ,[search 1] AS [search 1 %]
  ,[search 2] AS [search 2 %]
  ,[timeout] AS [timeout %]
  ,[memory limit exceeded] AS [memory limit exceeded %]
  ,[insert stmt] AS [insert stmt %]
  ,[delete stmt] AS [delete stmt]
  ,[update stmt] AS [update stmt]
  ,[merge stmt] AS [merge stmt]
  ,[contains subquery] AS [contains subquery %]
  ,[view reference] AS [view reference %]
  ,[remote query] AS [remote query %]
  ,[dynamic cursor request] AS [dynamic cursor request %]
  ,[fast forward cursor request] AS [fast forward cursor request %]
FROM
  QOInfo
PIVOT (MAX([%]) FOR [counter] 
  IN ([optimizations]
      ,[trivial plan]
      ,[no plan]
      ,[search 0]
      ,[search 1]
      ,[search 2]
      ,[timeout]
      ,[memory limit exceeded]
      ,[insert stmt]
      ,[delete stmt]
      ,[update stmt]
      ,[merge stmt]
      ,[contains subquery]
      ,[view reference]
      ,[remote query]
      ,[dynamic cursor request]
      ,[fast forward cursor request])) AS p;
GO
```
このクエリの結果と、システム ビュー [sys.views](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-views-transact-sql) の結果を組み合わせて、クエリ統計、クエリ テキスト、およびキャッシュされた実行プランを識別します。 

## <a name="sysviews"></a>Sys.views

次の CTE では、実行の数、合計実行時間、メモリから読み取られたページ数に関する情報が提供されます。 結果を使用して、最適化の候補となる可能性のあるクエリを識別できます。 
  
  >[!NOTE]
  > このクエリの結果は、SQL Server のバージョンによって異なることがあります。  


```SQL
WITH CTE_VW_STATS AS
(
  SELECT
    SCHEMA_NAME(vw.schema_id) AS schemaname
    ,vw.name AS viewname
    ,vw.object_id AS viewid
  FROM
    sys.views AS vw
  WHERE
    (vw.is_ms_shipped = 0)
  INTERSECT
  SELECT
    SCHEMA_NAME(o.schema_id) AS schemaname
    ,o.Name AS name
    ,st.objectid AS viewid
  FROM
    sys.dm_exec_cached_plans cp
  CROSS APPLY
    sys.dm_exec_sql_text(cp.plan_handle) st
  INNER JOIN
    sys.objects o ON st.[objectid] = o.[object_id]
  WHERE
    st.dbid = DB_ID()
)
SELECT
  vw.schemaname
  ,vw.viewname
  ,vw.viewid
  ,DB_NAME(t.databaseid) AS databasename
  ,t.databaseid
  ,t.*
FROM
  CTE_VW_STATS AS vw
CROSS APPLY
  (
    SELECT
      st.dbid AS databaseid
      ,st.text
      ,qp.query_plan
      ,qs.*
    FROM
      sys.dm_exec_query_stats AS qs
    CROSS APPLY
      sys.dm_exec_sql_text(qs.plan_handle) AS st
    CROSS APPLY
      sys.dm_exec_query_plan(qs.plan_handle) AS qp
    WHERE
      (CHARINDEX(vw.schemaname, st.text, 1) > 0)
      AND (st.dbid = DB_ID())
  ) AS t;
GO
```

## <a name="sysdmvexeccachedplans"></a>Sys.dmv_exec_cached_plans

最後のクエリでは、DMV [sys.dmv_exec_cached_plans](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql) を使用して、未使用のビューに関する情報が提供されます。 ただし、実行プランのキャッシュは動的であり、結果は異なることがあります。 そのため、ある程度の期間についてこのクエリを使用し、ビューが実際に使用されているかどうかを判断します。 


```SQL
SELECT
  SCHEMA_NAME(vw.schema_id) AS schemaname
  ,vw.name AS name
  ,vw.object_id AS viewid
FROM
  sys.views AS vw
WHERE
  (vw.is_ms_shipped = 0)
EXCEPT
SELECT
  SCHEMA_NAME(o.schema_id) AS schemaname
  ,o.name AS name
  ,st.objectid AS viewid
FROM
  sys.dm_exec_cached_plans cp
CROSS APPLY
  sys.dm_exec_sql_text(cp.plan_handle) st
INNER JOIN
  sys.objects o ON st.[objectid] = o.[object_id]
WHERE
  st.dbid = DB_ID();
GO
```

## <a name="related-external-resources"></a>関連する外部リソース

- [パフォーマンス チューニングのための DMV (動画 - SQL Saturday Pordenone)](https://www.youtube.com/watch?v=9FQaFwpt3-k)
- [パフォーマンス チューニングのための DMV (スライドとデモ - SQL Saturday Pordenone)](http://www.sqlsaturday.com/589/Sessions/Details.aspx?sid=57409)
- [カプセル形式での SQL Server チューニング (動画 - SQL Saturday Parma)](https://vimeo.com/200980883)
- [SQL Server のチューニングの概要 (スライドとデモ - SQL Saturday Parma)](http://www.sqlsaturday.com/566/Sessions/Details.aspx?sid=53988)
- [SQL Server 動的管理ビューでのパフォーマンス チューニング](https://www.red-gate.com/library/performance-tuning-with-sql-server-dynamic-management-views)
- [SQL Server 2016 の最も顕著な待機の種類](https://channel9.msdn.com/Blogs/MVP-Data-Platform/The-Most-Prominent-Wait-Types-of-your-SQL-Server-2016)
