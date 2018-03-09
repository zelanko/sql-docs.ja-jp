---
title: "マージ メタデータのクリーンアップ (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords:
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
caps.latest.revision: "33"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 650703999889c9cb54d46e1c16132d1c6614537c
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a>マージ メタデータのクリーンアップ (レプリケーション Transact-SQL プログラミング)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] マージ レプリケーションのメタデータは、パブリケーションの保有期間設定に基づき、マージ エージェントによって定期的にクリーンアップされます。 クリーンアップは、パブリッシャーおよびサブスクライバーの [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md)、 [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md)、 [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md)、 [MSmerge_past_partition_mappings](../../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md)、 [MSmerge_current_partition_mappings](../../../relational-databases/system-tables/msmerge-current-partition-mappings.md) の各システム テーブルで実行されます。 これらのテーブルに格納されたデータは、レプリケーションのストアド プロシージャを使って、プログラムからクリーンアップすることもできます。  
  
### <a name="to-manually-clean-up-merge-metadata"></a>マージ メタデータを手動でクリーンアップするには  
  
1.  パブリッシャーのパブリケーション データベースで [sp_mergemetadataretentioncleanup](../../../relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql.md)を実行します。  
  
2.  (省略可) 手順 1. で [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md)、 [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md)、 [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) の各システム テーブルから削除された行数は、それぞれ、 **@num_genhistory_rows**、 **@num_contents_rows**、 **@num_tombstone_rows** の各出力パラメーターとして返されます。  
  
3.  サブスクライバーで手順 1. と手順 2. を繰り返し、サブスクリプション データベースのメタデータをクリーンアップします。  
  
## <a name="see-also"></a>参照  
 [サブスクリプションの有効期限と非アクティブ化](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
