---
title: "サブスクリプション、[未配布のコマンド] (トランザクション サブスクリプション、SQL Server 2005 以降) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.subscription.performance.f1"
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# サブスクリプション、[未配布のコマンド] (トランザクション サブスクリプション、SQL Server 2005 以降)
   **[未配布のコマンド** ] タブは、これらのコマンドを提供するには、選択したサブスクライバーと予測の時間に配信されていないディストリビューション データベースにコマンドの数についての情報を表示します。 ディストリビューション データベースにコマンドを表示する方法の詳細については、次を参照してください。 [sp_replshowcmds & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md)します。  
  
## オプション  
 **[このサブスクライバーへの適用を待機しているディストリビューション データベース内のコマンド数]**  
 ディストリビューション データベース内のコマンドで、選択したサブスクライバーにまだ配布されていないコマンドの数を示します。 コマンドは、1 つの Transact-SQL データ操作言語 (DML) ステートメントまたは 1 つのデータ定義言語 (DDL) ステートメントから構成されます。  
  
 **[以前のパフォーマンスに基づく、これらのコマンドの適用にかかる推定時間]**  
 コマンドをサブスクライバーに配布するのに要すると推定される時間を示します。 スナップショットを生成してサブスクライバーに適用するのに必要な時間よりもこの値が大きい場合は、サブスクライバーの再初期化を検討してください。 詳細については、次を参照してください。 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-subscriptions.md)します。  
  
## 参照  
 [レプリケーション モニターの開始](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [レプリケーション モニターを使用したパフォーマンスの監視](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  