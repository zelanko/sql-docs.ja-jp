---
title: "パフォーマンスの監視とチューニング | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 07/18/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- instances of SQL Server, monitoring performance
- monitoring server performance [SQL Server]
- Database Engine [SQL Server], performance
- monitoring performance [SQL Server], about performance
- server performance [SQL Server]
- monitoring performance [SQL Server]
- database performance [SQL Server], about performance
- tuning databases [SQL Server], about performance
- status information [SQL Server], performance monitoring
- database monitoring [SQL Server], about performance
- monitoring [SQL Server], queries performance
- server performance [SQL Server], about performance
- tuning databases [SQL Server]
- database performance [SQL Server]
- monitoring [SQL Server], server performance
- database monitoring [SQL Server]
- monitoring server performance [SQL Server], about monitoring server performance
ms.assetid: 87f23f03-0f19-4b2e-bfae-efa378f7a0d4
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 28e89f06241fe44250b058e03717a30da62f308e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="monitor-and-tune-for-performance"></a>パフォーマンスの監視とチューニング
  データベースを監視する目的は、サーバーのパフォーマンスを評価することです。 適切な監視には、現在のパフォーマンスのスナップショットを定期的にキャプチャして問題の原因となっているプロセスを特定したり、長期にわたって継続的にデータを採取してパフォーマンスの傾向を追跡する作業が必要です。  
  
 データベース パフォーマンスの継続的な評価は、応答時間を最小限にし、スループットを最大限にして、最適なパフォーマンスを実現するために役立ちます。 パフォーマンスを最大限に高めるには、効率的なネットワーク トラフィック、ディスク I/O、および CPU 使用が重要です。 アプリケーションの要件を十分に分析し、データの論理構造と物理構造を理解し、データベースの使用状況を評価し、競合する処理 (オンライン トランザクション処理 (OLTP) と意思決定支援など) の関係を調整する必要があります。  
  
## <a name="monitoring-and-tuning-databases-for-performance"></a>パフォーマンスのためのデータベースの監視とチューニング  
 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および Microsoft Windows オペレーティング システムでは、データベースの現在の状態を参照したり、状態の変化に伴うパフォーマンスを追跡するためのユーティリティが用意されています。 さまざまなツールや技法を使用して [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を監視できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の監視は、次のことに役立ちます。  
  
-   パフォーマンスを向上できるかどうかの判断。 たとえば、頻繁に使用するクエリの応答時間を監視することで、テーブルに対するクエリまたはインデックスの変更が必要かどうかを判断できます。  
  
-   ユーザーの利用状況の評価。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続しようとするユーザーを監視することで、セキュリティが適切に設定されているかどうかを判断し、アプリケーションや開発システムをテストできます。 また、実行時に SQL クエリを監視することで、クエリが正しく作成され、期待どおりの結果が得られているかどうかを判断できます。  
  
-   問題のトラブルシューティングや、ストアド プロシージャなどのアプリケーション コンポーネントのデバッグ。  
  
## <a name="monitoring-in-a-dynamic-environment"></a>動的な環境での監視  
条件を変更すると、パフォーマンスが変化します。 評価では、ユーザー数の増加によるパフォーマンスの変化、ユーザーのアクセス方法と接続方法の変化、データベース コンテンツの増加、クライアント アプリケーションの変化、アプリケーション内のデータの変化、クエリの複雑化、およびネットワーク トラフィックの増加を確認できます。 ツールを使用してパフォーマンスを監視することにより、パフォーマンスの変化を、変化する条件と複雑なクエリに関連付けることができます。 **例:**:  
  
-   頻繁に使用されるクエリの応答時間を監視することによって、クエリを実行するテーブルに対するクエリまたはインデックスの変更が必要かどうかを判断できます。  
  
-   実行時に [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを監視することによって、クエリが正しく作成され、期待どおりの結果が得られているかどうかを判断できます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続しようとするユーザーを監視することによって、セキュリティが適切に設定されているかどうかを判断でき、アプリケーションまたは開発システムをテストできます。  
  
 応答時間は、クエリが処理されていることを視覚的に確認できる形式で、結果セットの先頭行をユーザーに返すのに必要な時間の長さです。 スループットは、指定した時間内にサーバーで処理されたクエリの合計数です。  
  
 ユーザーの数が増えるにつれて、サーバーのリソースの競合も増えます。その結果、応答時間が長くなり、全般的なスループットが減少します。  
  
## <a name="monitoring-and-performance-tuning-tasks"></a>監視とパフォーマンス チューニングのタスク  
  
|トピック| タスク|  
|-----------|----------------------|  
|[SQL Server コンポーネントの監視](../../relational-databases/performance/monitor-sql-server-components.md)|SQL Server コンポーネントの監視に必要な手順。|  
|[パフォーマンス監視およびチューニング ツール](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)|SQL Server で利用可能な監視およびチューニング ツールの一覧を表示します。|  
|[パフォーマンスのベースラインの設定](../../relational-databases/performance/establish-a-performance-baseline.md)|パフォーマンスのベースラインの設定方法。|  
|[パフォーマンスの問題の特定](../../relational-databases/performance/isolate-performance-problems.md)|データベースのパフォーマンスの問題を特定します。|  
|[ボトルネックの特定](../../relational-databases/performance/identify-bottlenecks.md)|ボトルネックを特定するために、サーバーのパフォーマンスを監視および追跡します。|  
|[サーバーのパフォーマンスと利用状況の監視](../../relational-databases/performance/server-performance-and-activity-monitoring.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と、Windows のパフォーマンスと利用状況の監視ツールを使用します。|  
|[実行プランの表示と保存](../../relational-databases/performance/display-and-save-execution-plans.md)|実行プランを表示し、XML 形式でファイルに保存します。|  
|[ライブ クエリ統計](../../relational-databases/performance/live-query-statistics.md)|クエリ実行ステップに関するリアルタイムの統計情報を表示します。|  
|[クエリのストアを使用した、パフォーマンスの監視](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)|クエリ ストアを使用して、自動的にクエリ、プラン、および実行時統計の履歴をキャプチャし、確認用に保持します。|  
|[インメモリ OLTP でのクエリ ストアの使用](../../relational-databases/performance/using-the-query-store-with-in-memory-oltp.md)|メモリ最適化テーブルに関する考慮事項。|  
|[クエリ ストアを使用する際の推奨事項](../../relational-databases/performance/best-practice-with-the-query-store.md)|クエリ ストアの使用に関してアドバイスします。|  
  
## <a name="see-also"></a>参照  
 [エンタープライズ全体の管理の自動化](http://msdn.microsoft.com/library/44d8365b-42bd-4955-b5b2-74a8a9f4a75f)   
 [データベース エンジン チューニング アドバイザー](../../relational-databases/performance/database-engine-tuning-advisor.md)   
 [リソースの利用状況の監視 &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
