---
title: "トレース (SQL Server Profiler) からのスクリプトの抽出 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d4449e7ba2193993b738850678bfd067f9780b3c
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>トレースからのスクリプトの抽出 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]このトピックの内容を抽出する方法を説明する[!INCLUDE[tsql](../../includes/tsql-md.md)]イベントのトレースからファイルまたはテーブルが表示されとして保存、[!INCLUDE[tsql](../../includes/tsql-md.md)]スクリプト ファイルを使用して[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]です。  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>トレース ファイルまたはテーブルから Transact-SQL スクリプトを抽出するには  
  
1.  [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルに保存する [!INCLUDE[tsql](../../includes/tsql-md.md)] イベントが含まれているトレース ファイルまたはテーブルを開きます。 詳細については、「[トレース ファイルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)」または「[トレース テーブルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)」を参照してください。  
  
2.  **[ファイル]** メニューで **[エクスポート]**、**[SQL Server イベントの抽出]** の順にポイントし、**[Transact-SQL イベントの抽出]** をクリックします。  
  
3.  **[名前を付けて保存]** ダイアログ ボックスで、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ファイルの名前を入力し、 **[保存]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
