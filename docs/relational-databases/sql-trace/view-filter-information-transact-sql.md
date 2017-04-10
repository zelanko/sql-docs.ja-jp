---
title: "フィルター情報の表示 (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フィルター情報の表示"
  - "フィルター [SQL Server]、表示"
  - "トレースのフィルター [SQL Server]"
  - "トレース [SQL Server]、フィルター"
  - "フィルター情報の確認"
ms.assetid: b7e52c13-8c83-47c2-8cd0-af7a49eceb5c
caps.latest.revision: 20
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 20
---
# フィルター情報の表示 (Transact-SQL)
  このトピックでは、組み込み関数を使用してトレース フィルター情報を表示する方法について説明します。  
  
### フィルター情報を表示するには  
  
1.  フィルター情報が必要なトレースの ID を指定して、**fn_trace_getfilterinfo** を実行します。 この関数は、フィルター、フィルターが適用されている列、およびフィルターで使用している値の一覧を返します。  
  
     この関数を呼び出すには、次のステートメントを実行します。  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getfilterinfo(trace_id)  
    ```  
  
## 参照  
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [SQL Server Profiler のストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  