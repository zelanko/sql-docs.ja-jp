---
title: "マージ メタデータのクリーンアップ (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords:
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
caps.latest.revision: "33"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5572b29922b76781429b71612e061d9014c32a7d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a>マージ メタデータのクリーンアップ (レプリケーション Transact-SQL プログラミング)
  マージ レプリケーションのメタデータは、パブリケーションの保有期間設定に基づき、マージ エージェントによって定期的にクリーンアップされます。 クリーンアップは、パブリッシャーおよびサブスクライバーの [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md)、 [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md)、 [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md)、 [MSmerge_past_partition_mappings](../../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md)、 [MSmerge_current_partition_mappings](../../../relational-databases/system-tables/msmerge-current-partition-mappings.md) の各システム テーブルで実行されます。 これらのテーブルに格納されたデータは、レプリケーションのストアド プロシージャを使って、プログラムからクリーンアップすることもできます。  
  
### <a name="to-manually-clean-up-merge-metadata"></a>マージ メタデータを手動でクリーンアップするには  
  
1.  パブリッシャーのパブリケーション データベースで [sp_mergemetadataretentioncleanup](../../../relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql.md)を実行します。  
  
2.  (省略可) 手順 1. で [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md)、 [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md)、 [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) の各システム テーブルから削除された行数は、それぞれ、 **@num_genhistory_rows**、 **@num_contents_rows**、 **@num_tombstone_rows** の各出力パラメーターとして返されます。  
  
3.  サブスクライバーで手順 1. と手順 2. を繰り返し、サブスクリプション データベースのメタデータをクリーンアップします。  
  
## <a name="see-also"></a>参照  
 [サブスクリプションの有効期限と非アクティブ化](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
