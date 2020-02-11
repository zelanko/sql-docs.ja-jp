---
title: トレース フィルターの設定 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
ms.assetid: 7b976a84-7381-43a6-a828-ba83ada71cbe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e6e3ecc4b125d226fc2cdf6dbe241e0ce017eae6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63245939"
---
# <a name="set-a-trace-filter-transact-sql"></a>トレース フィルターの設定 (Transact-SQL)
  このトピックでは、ストアド プロシージャを使用して、トレース中のイベントに関して必要な情報のみを取得するフィルターを作成する方法について説明します。  
  
### <a name="to-set-a-trace-filter"></a>トレース フィルターを設定するには  
  
1.  トレースが既に実行中の場合は、**** = 0** を指定して @statussp_trace_setstatus** を実行し、トレースを停止します。  
  
2.  
  **sp_trace_setfilter** を実行して、トレース中のイベントに関して取得する情報の種類を構成します。  
  
> [!IMPORTANT]
>  通常のストアドプロシージャとは異なり、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]すべてのストアドプロシージャ (<strong>sp_trace_*xx*</strong>) のパラメーターは厳密に型指定されており、データ型の自動変換はサポートされていません。 これらのパラメーターを、引数の説明で指定されている正しいデータ型で指定しないと、このストアド プロシージャではエラーが返されます。  
  
## <a name="see-also"></a>参照  
 [トレースのフィルター処理](../../relational-databases/sql-trace/filter-a-trace.md)   
 [sp_trace_setfilter &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)   
 [sp_trace_setstatus &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [Transact-sql&#41;&#40;のストアドプロシージャの SQL Server プロファイラー](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
