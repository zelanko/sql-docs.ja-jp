---
title: "マージ メタデータのクリーンアップ (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
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
  - "メタデータ [SQL Server レプリケーション]"
  - "sp_mergemetadataretentioncleanup"
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# マージ メタデータのクリーンアップ (レプリケーション Transact-SQL プログラミング)
  マージ レプリケーションのメタデータは、パブリケーションの保有期間設定に基づき、マージ エージェントによって定期的にクリーンアップされます。 パブリッシャーとサブスクライバー側でこの時間帯、 [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), 、[MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), 、[MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), 、[MSmerge_past_partition_mappings](../../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md), 、および [MSmerge_current_partition_mappings](../../../relational-databases/system-tables/msmerge-current-partition-mappings.md) システム テーブルです。 これらのテーブルに格納されたデータは、レプリケーションのストアド プロシージャを使って、プログラムからクリーンアップすることもできます。  
  
### マージ メタデータを手動でクリーンアップするには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_mergemetadataretentioncleanup](../../../relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql.md)します。  
  
2.  (省略可能)削除された行の数から 1 の手順に注意してください、 [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), 、[MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), 、および [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) それぞれで返されるシステム テーブル、 **@num_genhistory_rows**, 、**@num_contents_rows**, 、および **@num_tombstone_rows** 出力パラメーターです。  
  
3.  サブスクライバーで手順 1. と手順 2. を繰り返し、サブスクリプション データベースのメタデータをクリーンアップします。  
  
## 参照  
 [サブスクリプションの有効期限と非アクティブ化](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  