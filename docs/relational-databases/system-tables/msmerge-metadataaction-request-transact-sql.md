---
title: MSmerge_metadataaction_request (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_metadataaction_request
- MSmerge_metadataaction_request_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_metadataaction_request system table
ms.assetid: cd31a114-900a-4218-ab58-d959e547c647
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bd34379e4bdf4a9567d1bc3e9bb1e3aff2f8a401
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="msmergemetadataactionrequest-transact-sql"></a>MSmerge_metadataaction_request (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_metadataaction_request**テーブルが必要な補正アクションごとに 1 行を格納します。 エントリを作成し、エラーが発生し、同期を再試行する必要がある場合は、Web 同期を使用して、 **MSmerge_metadataaction_request**です。 その後のマージのアップロード フェーズ中、同期するパブリケーションに属するすべてのアーティクルへの要求は、このテーブルから取得されてアップロードされます。 同期を正常に完了すると、対応する行で、 **MSmerge_metadataaction_request**テーブルを削除します。 このテーブルは、パブリッシャー側ではパブリケーション データベースに、サブスクライバー側ではサブスクリプション データベースに格納されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|パブリッシュされたテーブルのニックネーム。|  
|**rowguid**|**uniqueidentifier**|指定した行の行識別子 (ROWID)。|  
|**action**|**tinyint**|必要な補正アクションの識別子。|  
|**生成**|**bigint**|補正アクションが必要とされる世代の値。|  
|**変更されました。**|**int**|内部使用のみ。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [マージ レプリケーションの Web 同期](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
