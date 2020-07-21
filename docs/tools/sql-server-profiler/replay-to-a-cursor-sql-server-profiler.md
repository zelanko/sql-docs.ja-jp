---
title: カーソルまで再生する
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 9df4fe8bf442fae11aefeb2b3d4e3c95aa13037e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "74957786"
---
# <a name="replay-to-a-cursor-sql-server-profiler"></a>カーソルまでの再生 (SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、カーソルに到達したときに一時停止するトレース ファイルまたはトレース テーブルの再生方法について説明します。 カーソル到達時点でトレースを一時停止することでデバッグがサポートされることになります。これは、長いトレース スクリプトの再生を、順番に分析できる短いセグメントに分割できるためです。  
  
### <a name="to-replay-to-the-cursor"></a>カーソルまで再生するには  
  
1.  再生するトレース ファイルまたはトレース テーブルを開きます。 詳細については、「 [トレース ファイルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) や [トレース テーブルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)に付属の定義済みチューニング テンプレートを使用します。  
  
     開いたトレース ファイルまたはトレース テーブルに、再生に必要なイベント クラスが含まれていることを確認します。 詳細については、「 [再生を実行するための必要条件](../../tools/sql-server-profiler/replay-requirements.md)」を参照してください。  
  
2.  トレース ウィンドウで、イベントを 1 つクリックします。  
  
3.  **[再生]** メニューの **[カーソルまで実行]** をクリックし、トレースを再生するサーバーに接続します。  
  
4.  **[構成の再生]** ダイアログ ボックスで設定を確認し、 **[OK]** をクリックします。  
  
     再生が開始され、最初のカーソルに到達した時点で一時停止されます。  
  
5.  F5 キーを押してトレースを再開します。  
  
6.  手順 5. をトレースの最後まで繰り返します。  
  
## <a name="see-also"></a>参照  
 [ブレークポイントまでの再生 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)   
 [トレースの再生](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
