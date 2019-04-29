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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910299"
---
# <a name="msmergemetadataactionrequest-transact-sql"></a>MSmerge_metadataaction_request (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_metadataaction_request**テーブルには、必要な各補正アクションに対して 1 行が格納されます。 エントリを作成し、Web 同期を使用して、エラーが発生し、同期を再試行する必要がある場合、 **MSmerge_metadataaction_request**します。 以降のマージのアップロード フェーズでは、同期されているパブリケーションに属するすべてのアーティクルに対して要求がこのテーブルから取得され、アップロードされます。 同期が正常に完了すると、対応する行で、 **MSmerge_metadataaction_request**テーブルを削除します。 このテーブルは、パブリケーション データベースでパブリッシャーとサブスクライバー側でサブスクリプション データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|パブリッシュされたテーブルのニックネームです。|  
|**rowguid**|**uniqueidentifier**|特定の行の行識別子。|  
|**action**|**tinyint**|必要な補正アクションの識別子。|  
|**生成**|**bigint**|補正アクションを必要とする生成の値。|  
|**changed**|**int**|内部使用のみ。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [マージ レプリケーションの Web 同期](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
