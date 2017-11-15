---
title: "データベース ミラーリング セッションを手動でフェールオーバーする方法 (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
caps.latest.revision: "32"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b0cd1d03e2c3a6378e0573167e0d5be9c19fcc95
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="manually-fail-over-a-database-mirroring-session-transact-sql"></a>データベース ミラーリング セッションを手動でフェールオーバーする方法 (Transact-SQL)
  ミラー化されたデータベースが同期されている場合 (つまり、データベースが SYNCHRONIZED 状態である場合)、データベース所有者はミラー サーバーに対して手動フェールオーバーを開始できます。 手動フェールオーバーは、プリンシパル サーバーのみから開始できます。  
  
### <a name="to-manually-fail-over-a-database-mirroring-session"></a>データベース ミラーリング セッションを手動でフェールオーバーするには  
  
1.  プリンシパル サーバーに接続します。  
  
2.  次のように、データベース コンテキストを **master** データベースに設定します。  
  
     **USE master;**  
  
3.  プリンシパル サーバーで次のステートメントを実行します。  
  
     [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md) *database_name* SET PARTNER FAILOVER ( *database_name* はミラー データベースの名前です)。  
  
     これにより、プリンシパル ロールへのミラー サーバーの移行がすぐに開始されます。  
  
 前のプリンシパルでは、クライアントはデータベースとの接続が切断され、インフライト トランザクションがロールバックされます。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーターを使用して準備したトランザクションのうち、フェールオーバーの発生時点でコミットされなかったトランザクションは、データベースのフェールオーバー後に中断したと見なされます。  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
 [データベース ミラーリング セッションを手動でフェールオーバーする方法 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)   
 [データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  
