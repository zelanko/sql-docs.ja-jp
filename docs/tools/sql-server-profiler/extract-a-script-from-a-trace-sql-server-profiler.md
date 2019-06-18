---
title: トレースからのスクリプトの抽出 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5cab84931db11e91e474ffd38aecfa4fb2aafae4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62712459"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>トレースからのスクリプトの抽出 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、トレース ファイルまたはテーブルから [!INCLUDE[tsql](../../includes/tsql-md.md)] イベントを抽出し、 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]スクリプト ファイルとして保存する方法について説明します。  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>トレース ファイルまたはテーブルから Transact-SQL スクリプトを抽出するには  
  
1.  [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルに保存する [!INCLUDE[tsql](../../includes/tsql-md.md)] イベントが含まれているトレース ファイルまたはテーブルを開きます。 詳細については、「 [トレース ファイルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) や [トレース テーブルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)に付属の定義済みチューニング テンプレートを使用します。  
  
2.  **[ファイル]** メニューで **[エクスポート]** 、 **[SQL Server イベントの抽出]** の順にポイントし、 **[Transact-SQL イベントの抽出]** をクリックします。  
  
3.  **[名前を付けて保存]** ダイアログ ボックスで、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ファイルの名前を入力し、 **[保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
