---
title: トレースを実行するための Transact-SQL スクリプトの作成 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], running
- scripts [SQL Server], traces
ms.assetid: 6b0e2519-998d-40d5-b8ba-5e6a773f91a6
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1915ac39a66ab2aee74db29ade8485755348a76d
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="create-a-transact-sql-script-for-running-a-trace-sql-server-profiler"></a>トレースを実行するための Transact-SQL スクリプトの作成 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して、既存のトレース ファイルまたはトレース テーブルから Transact-SQL スクリプトを作成する方法について説明します。  
  
### <a name="to-create-a-transact-sql-script-to-run-a-trace"></a>トレースを実行するための Transact-SQL スクリプトを作成するには  
  
1.  トレース ファイルまたはトレース テーブルを開きます。 詳細については、「 [トレース ファイルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) や [トレース テーブルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)に付属の定義済みチューニング テンプレートを使用します。  
  
2.  **[ファイル]** メニューで **[エクスポート]**、**[トレース定義のスクリプト]** の順にポイントし、トレースするサーバーに対応するバージョンをクリックします。  
  
3.  **[名前を付けて保存]** ダイアログ ボックスで、スクリプト ファイルの名前を入力し、 **[保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SQL Server プロファイラーのテンプレートと権限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
