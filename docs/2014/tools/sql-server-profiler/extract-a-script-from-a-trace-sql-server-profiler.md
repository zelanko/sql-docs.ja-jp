---
title: トレースからのスクリプトの抽出 (SQL Server Profiler) | Microsoft Docs
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
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 035df37fccf2507195e6576e062b7ce254dd1dba
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074708"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>トレースからのスクリプトの抽出 (SQL Server Profiler)
  このトピックでは、トレース ファイルまたはテーブルから [!INCLUDE[tsql](../../includes/tsql-md.md)] イベントを抽出し、 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]スクリプト ファイルとして保存する方法について説明します。  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>トレース ファイルまたはテーブルから Transact-SQL スクリプトを抽出するには  
  
1.  [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルに保存する [!INCLUDE[tsql](../../includes/tsql-md.md)] イベントが含まれているトレース ファイルまたはテーブルを開きます。 詳細については、「[トレース ファイルを開く &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md)」または「[トレース テーブルを開く &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)」を参照してください。  
  
2.  **[ファイル]** メニューで **[エクスポート]**、**[SQL Server イベントの抽出]** の順にポイントし、**[Transact-SQL イベントの抽出]** をクリックします。  
  
3.  **[名前を付けて保存]** ダイアログ ボックスで、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ファイルの名前を入力し、 **[保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](sql-server-profiler.md)  
  
  