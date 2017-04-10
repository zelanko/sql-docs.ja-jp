---
title: "トランザクション レプリケーションの連携バックアップの有効化 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
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
  - "トランザクション レプリケーション, バックアップと復元"
  - "sp_replicationdboption"
  - "sync with backup [SQL Server レプリケーション]"
  - "連携バックアップ [SQL Server レプリケーション]"
  - "バックアップ [SQL Server レプリケーション], トランザクション レプリケーション"
ms.assetid: 73a914ba-8b2d-4f4d-ac1b-db9bac676a30
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# トランザクション レプリケーションの連携バックアップの有効化 (レプリケーション Transact-SQL プログラミング)
  データベースでトランザクション レプリケーションを有効にする場合、ディストリビューション データベースに配布する前にすべてのトランザクションをバックアップするように指定できます。 また、ディストリビューション データベースの連携バックアップを有効にして、ディストリビューターに反映されたトランザクションがバックアップされるまで、パブリケーション データベースのトランザクション ログが切り捨てられないようにすることができます。 詳細については、次を参照してください。 [データベースのバックアップおよび復元するスナップショットおよびトランザクション レプリケーションのための戦略](../../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)します。  
  
### トランザクション レプリケーションでパブリッシュされたデータベースの連携バックアップを有効にするには  
  
1.  パブリッシャーで使用して、 [DATABASEPROPERTYEX & #40 です。Transact SQL と #41;](../../../t-sql/functions/databasepropertyex-transact-sql.md) 返す関数、 **IsSyncWithBackup** パブリケーション データベースのプロパティです。 関数が返した場合 **1**, 、連携バックアップがパブリッシュされたデータベースに対して既に有効になっています。  
  
2.  手順 1. で関数を返す場合 **0**, 、実行 [sp_replicationdboption & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 値を指定して **バックアップと同期** の **@optname**, 、および **true** の **@value**します。  
  
    > [!NOTE]  
    >  変更した場合、 **バックアップと同期** オプションを **false**, 、パブリケーション データベースの切り捨てポイントが更新されます、ログ リーダー エージェントを実行すた後、または一定の間隔、ログ リーダー エージェントが継続的に実行されている場合。 によって最長期間を制御、 **– MessageInterval** エージェント パラメーター (既定は 30 秒)。  
  
### ディストリビューション データベースの連携バックアップを有効にするには  
  
1.  ディストリビューターを使用して、 [DATABASEPROPERTYEX & #40 です。Transact SQL と #41;](../../../t-sql/functions/databasepropertyex-transact-sql.md) 返す関数、 **IsSyncWithBackup** ディストリビューション データベースのプロパティです。 関数が返した場合 **1**, 、連携バックアップがディストリビューション データベースに既に有効になっています。  
  
2.  手順 1. で関数を返す場合 **0**, 、実行 [sp_replicationdboption & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) ディストリビューター側でディストリビューション データベースです。 値を指定して **バックアップと同期** の **@optname** と **true** の **@value**します。  
  
### 連携バックアップを無効にするには  
  
1.  パブリケーション データベースのパブリッシャー側で、またはディストリビューターのディストリビューション データベースでは、実行 [sp_replicationdboption & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)します。 値を指定して **バックアップと同期** の **@optname** と **false** の **@value**します。  
  
  