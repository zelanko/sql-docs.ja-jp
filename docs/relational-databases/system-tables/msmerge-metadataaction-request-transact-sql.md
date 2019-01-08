---
title: MSmerge_metadataaction_request (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_metadataaction_request
- MSmerge_metadataaction_request_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_metadataaction_request system table
ms.assetid: cd31a114-900a-4218-ab58-d959e547c647
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a46570a30254341fede1fb96fd368e94a09e58ea
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52791664"
---
# <a name="msmergemetadataactionrequest-transact-sql"></a>MSmerge_metadataaction_request (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_metadataaction_request**テーブルには、必要な各補正アクションに対して 1 行が格納されます。 エントリを作成し、Web 同期を使用して、エラーが発生し、同期を再試行する必要がある場合、 **MSmerge_metadataaction_request**します。 その後のマージのアップロード フェーズ中、同期するパブリケーションに属するすべてのアーティクルへの要求は、このテーブルから取得されてアップロードされます。 同期が正常に完了すると、対応する行で、 **MSmerge_metadataaction_request**テーブルを削除します。 このテーブルは、パブリッシャー側ではパブリケーション データベースに、サブスクライバー側ではサブスクリプション データベースに格納されます。  
  
|列名|データ型|説明|  
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
  
  
