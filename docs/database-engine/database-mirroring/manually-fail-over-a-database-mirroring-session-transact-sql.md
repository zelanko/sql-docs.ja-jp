---
title: "データベース ミラーリング セッションを手動でフェールオーバーする方法 (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フェールオーバー [SQL Server], データベース ミラーリング"
  - "手動フェールオーバー [SQL Server]"
  - "データベース ミラーリング [SQL Server], フェールオーバー"
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
caps.latest.revision: 32
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 32
---
# データベース ミラーリング セッションを手動でフェールオーバーする方法 (Transact-SQL)
  ミラー化されたデータベースが同期されている場合 (つまり、データベースが SYNCHRONIZED 状態である場合)、データベース所有者はミラー サーバーに対して手動フェールオーバーを開始できます。 手動フェールオーバーは、プリンシパル サーバーのみから開始できます。  
  
### データベース ミラーリング セッションを手動でフェールオーバーするには  
  
1.  プリンシパル サーバーに接続します。  
  
2.  次のように、データベース コンテキストを **master** データベースに設定します。  
  
     **USE master;**  
  
3.  プリンシパル サーバーで次のステートメントを実行します。  
  
     [ALTER DATABASE](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md) *database_name* SET PARTNER FAILOVER (*database_name* はミラー データベースの名前です)。  
  
     これにより、プリンシパル ロールへのミラー サーバーの移行がすぐに開始されます。  
  
 前のプリンシパルでは、クライアントはデータベースとの接続が切断され、インフライト トランザクションがロールバックされます。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーターを使用して準備したトランザクションのうち、フェールオーバーの発生時点でコミットされなかったトランザクションは、データベースのフェールオーバー後に中断したと見なされます。  
  
## 参照  
 [ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md)   
 [データベース ミラーリング セッションを手動でフェールオーバーする方法 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)   
 [データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  