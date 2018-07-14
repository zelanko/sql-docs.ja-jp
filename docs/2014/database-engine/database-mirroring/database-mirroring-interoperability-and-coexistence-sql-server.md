---
title: 'データベース ミラーリング: 相互運用性と共存 (SQL Server) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], interoperability and coexistence
- Database Engine [SQL Server], high availability
ms.assetid: 89fef397-e0cf-4e08-b598-25b8d4170523
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8ffc13093ff3ee486643ac94202e9575e6dea574
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37225852"
---
# <a name="database-mirroring-interoperability-and-coexistence-sql-server"></a>データベース ミラーリング: 相互運用性と共存 (SQL Server)
  データベース ミラーリングは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の次の機能またはコンポーネントと共に使用できます。  
  
-   [AlwaysOn フェールオーバー クラスター インスタンス (SQL Server フェールオーバー クラスタ リング)](database-mirroring-and-sql-server-failover-cluster-instances.md)  
  
-   [変更データ キャプチャと変更の追跡](../../relational-databases/track-changes/change-data-capture-and-other-sql-server-features.md)  
  
-   [データベース スナップショット](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
-   [フルテキスト カタログ](database-mirroring-and-full-text-catalogs-sql-server.md)  
  
-   [ログ配布](database-mirroring-and-log-shipping-sql-server.md)  
  
-   [レプリケーション](database-mirroring-and-replication-sql-server.md)  
  
 データベース ミラーリングは、次の機能との相互運用はできません。  
  
-   複数データベースにまたがるトランザクション/分散トランザクション  
  
     このようなトランザクションがサポートされない理由の詳細については、「[データベース ミラーリングまたは AlwaysOn 可用性グループではサポートされない複数データベースにまたがるトランザクション &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)」を参照してください。  
  
-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
  
## <a name="see-also"></a>参照  
 [データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
  
