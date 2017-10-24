---
title: "(SQL Server Profiler) カーソルを再生 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- replaying cursors
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 775216d4634aced69ecc3248064b9539599fe54c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="replay-to-a-cursor-sql-server-profiler"></a>カーソルまでの再生 (SQL Server Profiler)
  このトピックでは、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して、カーソルに到達したときに一時停止するトレース ファイルまたはトレース テーブルの再生方法について説明します。 カーソル到達時点でトレースを一時停止することでデバッグがサポートされることになります。これは、長いトレース スクリプトの再生を、順番に分析できる短いセグメントに分割できるためです。  
  
### <a name="to-replay-to-the-cursor"></a>カーソルまで再生するには  
  
1.  再生するトレース ファイルまたはトレース テーブルを開きます。 詳細については、「[トレース ファイルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)」または「[トレース テーブルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)」を参照してください。  
  
     開いたトレース ファイルまたはトレース テーブルに、再生に必要なイベント クラスが含まれていることを確認します。 詳細については、「 [再生を実行するための必要条件](../../tools/sql-server-profiler/replay-requirements.md)」を参照してください。  
  
2.  トレース ウィンドウで、イベントを 1 つクリックします。  
  
3.  **[再生]** メニューの **[カーソルまで実行]**をクリックし、トレースを再生するサーバーに接続します。  
  
4.  **[構成の再生]** ダイアログ ボックスで設定を確認し、 **[OK]**をクリックします。  
  
     再生が開始され、最初のカーソルに到達した時点で一時停止されます。  
  
5.  F5 キーを押してトレースを再開します。  
  
6.  手順 5. をトレースの最後まで繰り返します。  
  
## <a name="see-also"></a>参照  
 [ブレークポイント &#40; までの再生します。SQL Server Profiler &#41;](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)   
 [トレースを再生します。](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  

