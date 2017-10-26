---
title: "パフォーマンスの問題の特定 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- isolating performance problems [SQL Server]
- monitoring performance [SQL Server], isolating problems
- database monitoring [SQL Server], isolating problems
- tuning databases [SQL Server], isolating problems
- monitoring server performance [SQL Server], isolating problems
- database performance [SQL Server], isolating problems
- server performance [SQL Server], isolating problems
ms.assetid: 2eb425cb-9166-4027-ae08-c8fc2d236f44
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f9ae4ada18ad96ba2675b95610316186c417c986
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="isolate-performance-problems"></a>パフォーマンスの問題の特定
  一般に、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または Microsoft Windows の複数のツールを併用した方が、ツールを 1 つずつ使用するよりも、データベースのパフォーマンスに関する問題を効率よく特定できます。 たとえば、グラフィカル実行プラン機能 (プラン表示) を使用すると、1 つのクエリ内のデッドロックをすばやく特定できます。 さらに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の監視機能と Windows の監視機能を同時に使用すると、その他のパフォーマンス問題をより簡単に特定できます。  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用すると、Transact-SQL とアプリケーションに関連する問題を監視して、問題点を突き止めることができます。 システム モニターを使用すると、ハードウェアとその他のシステムに関連する問題を監視できます。  
  
 次の要素を監視することによって、問題のトラブルシューティングを行うことができます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャまたは [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのバッチ (ユーザー アプリケーションから送信されたもの)。  
  
-   ブロッキング ロックまたはデッドロックなどのユーザーの利用状況  
  
-   ディスクの使用量などのハードウェア利用状況  
  
 問題としては、次のようなものがあります。  
  
-   不適切に記述された [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに関係するアプリケーション開発エラー  
  
-   ディスクまたはネットワークに関連するエラーなどのハードウェア エラー  
  
-   不適切に設計されたデータベースによる過剰なブロッキング  
  
## <a name="tools-for-common-performance-problems"></a>パフォーマンスの一般的な問題を解決するツール  
 各ツールでパフォーマンス問題を監視または調整する場合は、問題を慎重に選択することも重要になります。 ツールとユーティリティは、解決するパフォーマンス問題の種類によって異なります。  
  
 監視および調整ツールの種類と特定可能な問題については、次のトピックで説明します。  
  
 [ボトルネックの特定](../../relational-databases/performance/identify-bottlenecks.md)  
  
 [メモリ使用率の監視](../../relational-databases/performance-monitor/monitor-memory-usage.md)  
  
  

