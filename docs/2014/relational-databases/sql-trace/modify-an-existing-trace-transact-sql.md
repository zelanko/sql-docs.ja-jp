---
title: 既存のトレースの変更 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], modifying
- modifying traces
ms.assetid: 8792b43f-2510-44e3-9239-e73ad8227b89
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4d5308b708e32a1e886aadc2c78d3f504c3a6640
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163572"
---
# <a name="modify-an-existing-trace-transact-sql"></a>既存のトレースの変更 (Transact-SQL)
  このトピックでは、ストアド プロシージャを使用して既存のトレースを変更する方法について説明します。  
  
### <a name="to-modify-an-existing-trace"></a>既存のトレースを変更するには  
  
1.  トレースが既に実行中の場合は、**@status = 0** を指定して **sp_trace_setstatus** を実行し、トレースを停止します。  
  
2.  トレース イベントを変更するには、パラメーターを使用して変更を指定し、 **sp_trace_setevent** を実行します。 パラメーターは次の順序で指定します。  
  
    -   **@traceid** (トレース ID)  
  
    -   **@eventid** (イベント ID)  
  
    -   **@columnid** (列 ID)  
  
    -   **@on** (ON)  
  
     **@on** パラメーターを変更する場合は、**@columnid** パラメーターとの相互作用を考慮してください。  
  
    |ON|列 ID|結果|  
    |--------|---------------|------------|  
    |ON (**1**)|NULL|イベントはオンになります。 すべての列は消去されます。|  
    ||NOT NULL|指定されたイベントに対して列はオンになります。|  
    |OFF (**0**)|NULL|イベントはオフになります。 すべての列は消去されます。|  
    ||NOT NULL|指定されたイベントに対して列はオフになります。|  
  
> [!IMPORTANT]  
>  通常のストアド プロシージャとは異なり、すべての [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ストアド プロシージャ (**sp_trace_* xx***) で、パラメーターのデータ型が厳密に定義されており、データ型の自動変換はサポートしていません。 これらのパラメーターが、引数の説明で指定されている正しいデータ型で呼び出されないと、このストアド プロシージャではエラーが返されます。  
  
## <a name="see-also"></a>参照  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [SQL Server Profiler のストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
