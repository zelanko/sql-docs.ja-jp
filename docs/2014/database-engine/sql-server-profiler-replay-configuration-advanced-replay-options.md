---
title: SQL Server プロファイラー-[構成の再生] ([再生オプションの詳細設定]) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.advanced.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: b4eb34f7-3af6-4a44-ba7e-2b8430ec3cd7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0bf91032c1514037c754fd489ac266cf68063fa4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66089729"
---
# <a name="sql-server-profiler---replay-configuration-advanced-replay-options"></a>[SQL Server Profiler] - [構成の再生] ([再生オプションの詳細設定])
  
  **[構成の再生]** ダイアログ ボックスの **[再生オプションの詳細設定]** タブを使用すると、トレース ファイルの再生方法を指定できます。  
  
 このウィンドウを表示するには、 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] を使用して、再生するイベントを含むトレース ファイルまたはテーブルを開きます。 詳細については、「 [再生を実行するための必要条件](../tools/sql-server-profiler/replay-requirements.md)」を参照してください。 トレース ファイルまたはテーブルを開いているときに、 **[再生]** メニューの **[開始]** をクリックして、トレースを再生する SQL Server インスタンスに接続してから、 **[再生オプションの詳細設定]** タブをクリックします。  
  
## <a name="options"></a>オプション  
 **[システム SPID を再生する]**  
 
  [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] でシステム プロセス識別子 (SPID) を再生するかどうかを指定します。  
  
 **[1 つの SPID のみ再生する]**  
 ソース トレース ファイルで、選択した SPID に関連する操作だけを再生します。  
  
 **再生する SPID**  
 再生する SPID を指定します。  
  
 **[日時により再生を制限する]**  
 オンにすると、ソース トレース ファイルの一部だけを再生します。  
  
 **開始時刻**  
 ソース トレース ファイル内の再生の開始位置を示す日付と時刻です。  
  
 **終了時刻**  
 ソース トレース ファイル内の再生の終了位置を示す日付と時刻です。  
  
 **ヘルスモニターの待機間隔 (秒)**  
 再生の待機間隔を秒単位で指定します。 既定値は 3,600 秒 (1 時間) です。 この設定値によって、プロセスがヘルス モニターにより終了されるまでの実行時間の長さが決まります。  
  
 **ヘルスモニターのポーリング間隔 (秒)**  
 再生中のヘルス モニターのポーリング間隔を秒単位で指定します。 既定値は 60 秒です。 ユーザーはこの値を指定することで、終了するプロセスを決定するためにヘルス モニターがポーリングする頻度を設定できます。  
  
 **[SQL Server のブロックされるプロセスの監視を有効にする]**  
 ブロックされるプロセス、またはブロックするプロセスを検索するプロセスを有効にします。  
  
 **ブロックされたプロセスの監視の待機間隔 (秒)**  
 ブロックされるプロセス モニターで、ブロックされるプロセスまたはブロックするプロセスを検索する頻度を設定します。  
  
## <a name="see-also"></a>参照  
 [トレーステーブル &#40;SQL Server プロファイラーの再生&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)   
 [トレースファイル &#40;SQL Server プロファイラーを再生する&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)   
 [トレースの再生](../tools/sql-server-profiler/replay-traces.md)  
  
  
