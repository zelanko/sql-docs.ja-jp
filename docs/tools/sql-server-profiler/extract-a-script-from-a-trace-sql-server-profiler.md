---
title: スクリプトをトレースから抽出する
titleSuffix: SQL Server Profiler
description: SQL Server Profiler のトレース ファイルまたはテーブルから Transact-SQL イベントを抽出し、Transact-SQL スクリプト ファイルとして保存する方法について説明します。
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: 2495eb7c020e6fb64fb894d4d6bb7614707f84bc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774864"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>トレースからのスクリプトの抽出 (SQL Server Profiler)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

このトピックでは、トレース ファイルまたはテーブルから [!INCLUDE[tsql](../../includes/tsql-md.md)] イベントを抽出し、 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]スクリプト ファイルとして保存する方法について説明します。  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>トレース ファイルまたはテーブルから Transact-SQL スクリプトを抽出するには  
  
1.  [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルに保存する [!INCLUDE[tsql](../../includes/tsql-md.md)] イベントが含まれているトレース ファイルまたはテーブルを開きます。 詳細については、「 [トレース ファイルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) や [トレース テーブルを開く &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)に付属の定義済みチューニング テンプレートを使用します。  
  
2.  **[ファイル]** メニューで **[エクスポート]** 、 **[SQL Server イベントの抽出]** の順にポイントし、 **[Transact-SQL イベントの抽出]** をクリックします。  
  
3.  **[名前を付けて保存]** ダイアログ ボックスで、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ファイルの名前を入力し、 **[保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
