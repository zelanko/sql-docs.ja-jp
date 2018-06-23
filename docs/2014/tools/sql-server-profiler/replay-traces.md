---
title: トレースの再生 |Microsoft ドキュメント
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
- SQL Server Profiler, replaying traces
- Run to Cursor option
- Toggle Breakpoint option
- traces [SQL Server], replaying
- replaying traces
- playback engine [SQL Server Profiler]
- events [SQL Server], replaying traces
- Profiler [SQL Server Profiler], replaying traces
ms.assetid: da958d3c-7f3e-44c9-aecc-8a9493bea7c0
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4e6f0b2068faf1fb5282eb0effd348cb01d4ac91
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177896"
---
# <a name="replay-traces"></a>トレースの再生
  再生とは、トレースでキャプチャされたアクティビティを再現する機能です。 トレースの作成または編集を行うときに、そのトレースをファイルに保存して後で再生できます。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して、1 つのコンピューターからのトレース アクティビティを再生できます。 ワークロードが大きい場合、Distributed Replay Utility を使用して複数のコンピューターからのトレース データを再生できます。  
  
 このセクションでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]の再生機能の使用方法について説明します。 Distributed Replay Utility の詳細については、「 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)」を参照してください。  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] には、ユーザー接続と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証をシミュレートできるマルチスレッド再生エンジンが備わっています。 再生は、アプリケーションまたはプロセスに関する問題のトラブルシューティングを行う際に役立ちます。 問題を特定して修正を実装したら、発生する可能性がある問題を検出したトレースを、修正されたアプリケーションまたはプロセスに対して実行します。 その後、元のトレースを再生し、結果を比較します。  
  
 トレースの再生では、 **の** [再生] **メニューの** [ブレークポイントの設定/解除] [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Replay** menu. これらのオプションでは、長いスクリプトを段階的に分析できるように、トレースの再生を短いセグメントに分割できるので、長いスクリプトの分析が特に強化されます。  
  
 トレースの再生に必要な権限については、「 [SQL Server Profiler の実行に必要な権限](permissions-required-to-run-sql-server-profiler.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[再生を実行するための必要条件](replay-requirements.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]で再生できるようにトレース定義に含める必要があるイベントについて説明します。|  
|[[再生オプション] &#40;SQL Server Profiler&#41;](replay-options-sql-server-profiler.md)|**の** [構成の再生] [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]ダイアログ ボックスで設定できるオプションについて説明します。|  
|[トレースの再生に関する注意点&#40;SQL Server Profiler&#41;](considerations-for-replaying-traces-sql-server-profiler.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] で再生できないトレース イベント、およびトレースの再生によるサーバー パフォーマンスへの影響について説明します。|  
  
## <a name="see-also"></a>参照  
 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)  
  
  