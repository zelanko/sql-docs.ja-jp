---
title: "1 つのイベントの再生時 (SQL Server Profiler) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [SQL Server], replaying single event at a time
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 220fb192-9636-41a2-b15c-62af6cab8fff
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d920157a1e1b60b82952ba00a6afe4a4f30645e3
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="replay-a-single-event-at-a-time-sql-server-profiler"></a>一度に単一のイベントの再生 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]このトピックを使用して、再生トレース ファイルまたはトレース テーブルに一度に 1 つのイベントを再生する方法について説明[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]です。  
  
### <a name="to-replay-a-single-event-at-a-time"></a>一度に単一のイベントを再生するには  
  
1.  再生するトレース ファイルまたはトレース テーブルを開きます。 詳細については、「[トレース ファイルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)」または「[トレース テーブルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)」を参照してください。  
  
     開いたトレース ファイルまたはトレース テーブルに、再生に必要なイベント クラスが含まれていることを確認します。 詳細については、「 [再生を実行するための必要条件](../../tools/sql-server-profiler/replay-requirements.md)」を参照してください。  
  
2.  **[再生]** メニューの **[ステップ実行]**をクリックし、トレースを再生するサーバー インスタンスに接続します。  
  
3.  **[構成の再生]** ダイアログ ボックスで設定を確認し、**[OK]** をクリックします。 **[構成の再生]** ダイアログ ボックスで設定内容を指定する方法の詳細については、「[トレース ファイルの再生 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)」または「[トレース テーブルの再生 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)」を参照してください。  
  
4.  最初のイベントを再生するには、**[構成の再生]** ダイアログ ボックスで **[OK]** をクリックします。  
  
5.  後続のイベントを再生するには、 **[再生]** メニューの **[ステップ実行]**をクリックするか、F10 キーを押します。 各イベントに対して **[ステップ実行]** をクリックするか、または F10 キーを押す操作を繰り返します。  
  
## <a name="see-also"></a>参照  
 [トレースの再生](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
