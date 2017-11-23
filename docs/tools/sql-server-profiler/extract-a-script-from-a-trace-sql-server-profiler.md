---
title: "トレース (SQL Server Profiler) からのスクリプトの抽出 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 47f551c20ae4f9e521e782bb29c8498287a3106e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>トレースからのスクリプトの抽出 (SQL Server Profiler)
  このトピックでは、トレース ファイルまたはテーブルから [!INCLUDE[tsql](../../includes/tsql-md.md)] イベントを抽出し、 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]スクリプト ファイルとして保存する方法について説明します。  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>トレース ファイルまたはテーブルから Transact-SQL スクリプトを抽出するには  
  
1.  [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルに保存する [!INCLUDE[tsql](../../includes/tsql-md.md)] イベントが含まれているトレース ファイルまたはテーブルを開きます。 詳細については、「[トレース ファイルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)」または「[トレース テーブルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)」を参照してください。  
  
2.  **[ファイル]** メニューで **[エクスポート]**、**[SQL Server イベントの抽出]** の順にポイントし、**[Transact-SQL イベントの抽出]** をクリックします。  
  
3.  **[名前を付けて保存]** ダイアログ ボックスで、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ファイルの名前を入力し、 **[保存]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
