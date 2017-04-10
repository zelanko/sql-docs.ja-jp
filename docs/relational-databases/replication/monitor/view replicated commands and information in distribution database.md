---
title: "レプリケートされたコマンドなどディストリビューション データベースに格納されている情報を表示する (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sp_browsereplcmds"
  - "トランザクション レプリケーション、監視"
  - "ディストリビューション データベース [SQL Server レプリケーション], レプリケートされたコマンドの表示"
  - "レプリケートされたコマンドの表示"
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# レプリケートされたコマンドなどディストリビューション データベースに格納されている情報を表示する (レプリケーション Transact-SQL プログラミング)
  トランザクション レプリケーションでは、トランザクション コマンドが、ディストリビューション エージェントによってすべてのサブスクライバーに反映されるか、サブスクライバーのディストリビューション エージェントによって変更が抽出されるまで、ディストリビューション データベースに格納されます。 ディストリビューション データベース内で保留状態のコマンドは、レプリケーションのストアド プロシージャを使用してプログラムから表示できます。 詳細については、次を参照してください。 [レプリケーション ストアド プロシージャと #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)します。  
  
### すべてのトランザクション パブリケーションからディストリビューション データベース内のレプリケートされたコマンドを表示するには  
  
1.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md)します。  
  
### トランザクション レプリケーションを使用してパブリッシュされた特定のアーティクルまたは特定のデータベースから、ディストリビューション データベース内のレプリケートされたコマンドを表示するには  
  
1.  (省略可能)パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)します。 指定 **@publication** と **@article**します。 値に注意してください **アーティクル id** 結果に設定します。  
  
2.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md)します。 (省略可能)手順 2. のアーティクル ID を指定して **@article_id**します。 (省略可能)パブリケーション データベースの ID を指定して **@publisher_database_id**, から取得できる、 **database_id** 内の列、 [sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューです。  
  
## 参照  
 [Programmatically Monitor Replication](../../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  