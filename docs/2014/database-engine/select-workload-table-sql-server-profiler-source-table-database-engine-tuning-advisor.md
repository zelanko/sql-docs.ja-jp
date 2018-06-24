---
title: SQL Server プロファイラー - ソース テーブル データベース エンジン チューニング アドバイザーでワークロード テーブルの選択 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.pro.replay.tools.sourcetable.f1
helpviewer_keywords:
- Select Workload Table dialog box
- Source Table dialog box
ms.assetid: 51185be7-7092-480a-a52c-cf7786c4a0a0
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8b5ccfddb032fb3833e517632290cfdf7d82e643
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072825"
---
# <a name="sql-server-profiler---source-table-database-engine-tuning-advisor---select-workload-table"></a>SQL Server プロファイラー - ソース テーブル データベース エンジン チューニング アドバイザー - ワークロード テーブル
  Microsoft [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] および[!INCLUDE[ssDE](../includes/ssde-md.md)] チューニング アドバイザーでは、このダイアログ ボックスを使用してテーブルを選択します。  
  
 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] では、**[基になるテーブル]** ダイアログ ボックスを使用して、トレース テーブルの基になるテーブルを指定します。 This is a table from which a trace is loaded, and the contents of which are viewed or used for replaying the trace.  
  
 [!INCLUDE[ssDE](../includes/ssde-md.md)] チューニング アドバイザーでは、**[ワークロード テーブルの選択]** ダイアログ ボックスを使用して、チューニング ワークロードとして使用する [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] のトレース情報が格納されているデータベース テーブルを選択したり、チューニング分析を開始する前にテーブルの内容をプレビューしたりします。  
  
## <a name="options"></a>および  
 **SQL Server**  
 現在接続されている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを指定します。 このフィールドには自動的に値が入力され、更新することはできません。  
  
 **[データベース]**  
 トレース テーブルがあるデータベースを指定します。  
  
 **[所有者]**  
 Specifies the owner of the trace table. このフィールドは、 **dbo**として自動的に入力されます。  
  
 **Table**  
 トレースの読み込み元のトレース テーブルの名前を指定します。  
  
## <a name="see-also"></a>参照  
 [トレース結果をテーブルに保存&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)   
 [SQL Server プロファイラーのテンプレートと権限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [データベース エンジン チューニング アドバイザー](../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  