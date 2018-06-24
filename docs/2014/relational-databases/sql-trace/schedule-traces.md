---
title: トレースのスケジュール設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], events
- traces [SQL Server]
- traces [SQL Server], stopping
- events [SQL Server], filters
- scheduling traces [SQL Server]
- traces [SQL Server], scheduling
- stopping traces
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3017f239b024bcab3d19b589be1ec189187a5d09
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075685"
---
# <a name="schedule-traces"></a>トレースのスケジュール設定
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でトレースのスケジュールを設定するには、次の 2 つの方法があります。 可能な代替手段としては以下の方法があります。  
  
-   トレース停止時刻を有効にする。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用してトレースのスケジュールを設定する。  
  
## <a name="specifying-a-stop-time"></a>トレース停止時刻の指定  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャまたは [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用する場合は、トレース停止時刻を指定できます。 停止時刻は、トレースを最初に構成する際に設定する必要があります。  
  
## <a name="scheduling-traces-by-using-sql-server-agent"></a>SQL Server エージェントを使用したトレースのスケジュール設定  
 トレースのスケジュールを設定する最善の方法は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用してトレースを開始してから、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャ **sp_trace_setstatus**または [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用してトレース停止時刻を指定する方法です。  
  
 **トレースの終了時刻フィルターを設定するには**  
  
 [イベントの終了時刻に基づいたフィルターでのイベントの選択 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)  
  
## <a name="see-also"></a>参照  
 [管理タスクの自動化 &#40;SQL Server エージェント&#41;](../../ssms/agent/sql-server-agent.md)  
  
  
