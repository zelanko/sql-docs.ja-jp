---
title: 一度に単一のイベントの再生 (SQL Server Profiler) | Microsoft Docs
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
- events [SQL Server], replaying single event at a time
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 220fb192-9636-41a2-b15c-62af6cab8fff
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e4383fa52200bbf9cd302adff230239df14fcb4a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163986"
---
# <a name="replay-a-single-event-at-a-time-sql-server-profiler"></a>一度に単一のイベントの再生 (SQL Server Profiler)
  このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、再生トレース ファイルまたはテーブルで一度に単一のイベントを再生する方法を説明します。  
  
### <a name="to-replay-a-single-event-at-a-time"></a>一度に単一のイベントを再生するには  
  
1.  再生するトレース ファイルまたはトレース テーブルを開きます。 詳細については、「[トレース ファイルを開く &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md)」または「[トレース テーブルを開く &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)」を参照してください。  
  
     開いたトレース ファイルまたはトレース テーブルに、再生に必要なイベント クラスが含まれていることを確認します。 詳細については、「 [再生を実行するための必要条件](replay-requirements.md)」を参照してください。  
  
2.  **[再生]** メニューの **[ステップ実行]** をクリックし、トレースを再生するサーバー インスタンスに接続します。  
  
3.  **[構成の再生]** ダイアログ ボックスで設定を確認し、**[OK]** をクリックします。 **[構成の再生]** ダイアログ ボックスで設定内容を指定する方法の詳細については、「[トレース ファイルの再生 &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md)」または「[トレース テーブルの再生 &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md)」を参照してください。  
  
4.  最初のイベントを再生するには、**[構成の再生]** ダイアログ ボックスで **[OK]** をクリックします。  
  
5.  後続のイベントを再生するには、 **[再生]** メニューの **[ステップ実行]** をクリックするか、F10 キーを押します。 各イベントに対して **[ステップ実行]** をクリックするか、または F10 キーを押す操作を繰り返します。  
  
## <a name="see-also"></a>参照  
 [トレースを再生します。](replay-traces.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  