---
title: "トレース (SQL Server Profiler) を実行するための TRANSACT-SQL スクリプトを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], running
- scripts [SQL Server], traces
ms.assetid: 6b0e2519-998d-40d5-b8ba-5e6a773f91a6
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d855ef185a7110c4beb7ecf33512ebb50b3ea51f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="create-a-transact-sql-script-for-running-a-trace-sql-server-profiler"></a>トレースを実行するための Transact-SQL スクリプトの作成 (SQL Server Profiler)
  このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、既存のトレース ファイルまたはトレース テーブルから Transact-SQL スクリプトを作成する方法について説明します。  
  
### <a name="to-create-a-transact-sql-script-to-run-a-trace"></a>トレースを実行するための Transact-SQL スクリプトを作成するには  
  
1.  トレース ファイルまたはトレース テーブルを開きます。 詳細については、「[トレース ファイルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)」または「[トレース テーブルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)」を参照してください。  
  
2.  **[ファイル]** メニューで **[エクスポート]**、**[トレース定義のスクリプト]** の順にポイントし、トレースするサーバーに対応するバージョンをクリックします。  
  
3.  **[名前を付けて保存]** ダイアログ ボックスで、スクリプト ファイルの名前を入力し、 **[保存]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [SQL Server プロファイラーのテンプレートと権限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
