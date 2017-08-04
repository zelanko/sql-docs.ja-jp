---
title: "トレースの再生 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Profiler, replaying traces
- Run to Cursor option
- Toggle Breakpoint option
- traces [SQL Server], replaying
- replaying traces
- playback engine [SQL Server Profiler]
- events [SQL Server], replaying traces
- Profiler [SQL Server Profiler], replaying traces
ms.assetid: da958d3c-7f3e-44c9-aecc-8a9493bea7c0
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 09eb93462d990d374c4e38ecdaea1918cb832f11
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="replay-traces"></a>トレースの再生
  再生とは、トレースでキャプチャされたアクティビティを再現する機能です。 トレースの作成または編集を行うときに、そのトレースをファイルに保存して後で再生できます。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して、1 つのコンピューターからのトレース アクティビティを再生できます。 ワークロードが大きい場合、Distributed Replay Utility を使用して複数のコンピューターからのトレース データを再生できます。  
  
 このセクションでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]の再生機能の使用方法について説明します。 Distributed Replay Utility の詳細については、「 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)」を参照してください。  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] には、ユーザー接続と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証をシミュレートできるマルチスレッド再生エンジンが備わっています。 再生は、アプリケーションまたはプロセスに関する問題のトラブルシューティングを行う際に役立ちます。 問題を特定して修正を実装したら、発生する可能性がある問題を検出したトレースを、修正されたアプリケーションまたはプロセスに対して実行します。 その後、元のトレースを再生し、結果を比較します。  
  
 トレースの再生では、 **の** [再生] **メニューの** [ブレークポイントの設定/解除] [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **[カーソルまで実行]** オプションを使用したデバッグがサポートされます。 これらのオプションでは、長いスクリプトを段階的に分析できるように、トレースの再生を短いセグメントに分割できるので、長いスクリプトの分析が特に強化されます。  
  
 トレースの再生に必要な権限については、「 [SQL Server Profiler の実行に必要な権限](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[再生の要件](../../tools/sql-server-profiler/replay-requirements.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] で再生できるようにトレース定義に含める必要があるイベントについて説明します。|  
|[Replay オプション & #40 です。SQL Server Profiler &#41;](../../tools/sql-server-profiler/replay-options-sql-server-profiler.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] の **[構成の再生]** ダイアログ ボックスで設定できるオプションについて説明します。|  
|[トレース &#40; の再生に関する注意点SQL Server Profiler &#41;](../../tools/sql-server-profiler/considerations-for-replaying-traces-sql-server-profiler.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] で再生できないトレース イベント、およびトレースの再生によるサーバー パフォーマンスへの影響について説明します。|  
  
## <a name="see-also"></a>参照  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  
