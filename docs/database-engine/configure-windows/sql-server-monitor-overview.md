---
title: "SQL Server モニターの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.sqlservermonitor.main.f1"
helpviewer_keywords: 
  - "SQL Server モニター [SQL Server]"
ms.assetid: 048ae16d-31c3-489a-9f1e-1400a3bacd39
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# SQL Server モニターの概要
  SQL Server モニターでは、監視機能を実行するのではなく、監視を行うモジュールをホストします。 SQL Server モニターのモジュールには、レプリケーション モニターやデータベース ミラーリング モニターが含まれます。  
  
 これらのモジュールのいずれかを使用するには、**[実行]** メニューから該当するモジュールを選択します。 現在選択されているモジュールには、ナビゲーション ペインと詳細ペインの内容、詳細ペインでのユーザーとのやり取り、および内容と状態に関するクエリがあります。  
  
> [!NOTE]  
>  これらのモニターの詳細については、「[レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)」および「[データベース ミラーリングの監視&#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)」をご覧ください。  
  
## 権限  
  
-   レプリケーション モニター  
  
     レプリケーションを監視するためには、ディストリビューターで **sysadmin** 固定サーバー ロールのメンバーか、ディストリビューション データベースの **replmonitor** 固定データベース ロールのメンバーであることが必要です。 システム管理者は、**replmonitor** ロールに任意のユーザーを追加することが可能で、これによりユーザーがレプリケーション モニターでレプリケーションの動作状況を表示できるようになります。ただし、レプリケーションを管理することはできません。  
  
-   データベース ミラーリング モニター (Database Mirroring Monitor)  
  
     データベース ミラーリングを監視するには、**sysadmin** 固定サーバー ロールのメンバーか、サーバー インスタンスの **dbm_monitor** 固定データベース ロールのメンバーであることが必要です。 1 つのパートナー サーバー インスタンスだけが **sysadmin** または **dbm_monitor** のメンバーの場合、モニターは、該当するパートナーにのみ接続でき、他のパートナーからは情報を取得できません。 詳細については、「[データベース ミラーリング モニターの概要](../../database-engine/database-mirroring/database-mirroring-monitor-overview.md)」を参照してください。  
  
## メニュー オプション  
 SQL Server モニターには、SQL Server モニターに関連するコマンドを含むメニューがあります。 このメニューには、選択されたモジュールのコマンドが設定されている場合もあります。  
  
 次のメニュー オプションは、SQL Server モニターに関するものです。  
  
 **ファイル**  
 このメニューには、**[終了]** が含まれます。  
  
 **操作**  
 ナビゲーション ツリーで選択されたノードのコンテキスト メニューが含まれます。  
  
 **[実行]**  
 監視するコンポーネントの一覧が含まれます。  
  
-   データベース ミラーリング  
  
-   レプリケーション  
  
 **SQL Server Management Studio を使用してデータベース ミラーリングを監視するには**  
  
-   [データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## 参照  
 [データベース ミラーリングの監視 &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
  