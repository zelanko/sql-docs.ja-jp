---
title: MSmerge_articlehistory (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_articlehistory
- MSmerge_articlehistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_articlehistory system table
ms.assetid: 2870e7ea-dbec-4636-9171-c2cee96018ac
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 256a2c3ca6801e09bed0a96a63cc6d6540d466ff
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52791514"
---
# <a name="msmergearticlehistory-transact-sql"></a>MSmerge_articlehistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_articlehistory**テーブル アーティクルに変更が行われる各アーティクルに対して 1 つの行と、マージ エージェントの同期セッション中に加えられた変更を追跡します。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|マージ エージェント ジョブ セッションの ID、 [MSmerge_sessions](../../relational-databases/system-tables/msmerge-sessions-transact-sql.md)システム テーブル。|  
|**phase_id**|**int**|次のいずれかの同期セッションのフェーズ:<br /><br /> **1** = アップロードします。<br /><br /> **2** = ダウンロードします。<br /><br /> **4**クリーンアップを = です。<br /><br /> **5** = シャット ダウンします。<br /><br /> **6**スキーマの変更を = です。<br /><br /> **7** BCP を = です。|  
|**article_name**|**sysname**|変更が行われたアーティクル名です。|  
|**start_time**|**datetime**|エージェントがアーティクルの処理を開始した時刻です。|  
|**duration**|**int**|エージェントがアーティクルを処理した時間の長さ (秒単位) です。|  
|**挿入します**|**int**|同期中に特定のアーティクルに適用された挿入数です。 この値は同期処理中に増加し、最終値は総数を表します。|  
|**更新プログラム**|**int**|同期中に特定のアーティクルに適用された更新数です。 この値は同期処理中に増加し、最終値は総数を表します。|  
|**削除します**|**int**|同期中に特定のアーティクルに適用された削除数です。 この値は同期処理中に増加し、最終値は総数を表します。|  
|**競合**|**int**|同期中に発生した競合の数です。 この値は同期処理中に増加し、最終値は総数を表します。|  
|**conflicts_resolved**|**int**|同期中に発生し、解決された競合の数です。 この値は同期処理中に増加し、最終値は総数を表します。|  
|**rows_retried**|**int**|同期中に再試行され、失敗した行数です。 この値は同期処理中に増加し、最終値は総数を表します。|  
|**percent_complete**|**decimal**|セッション中にマージ エージェントが費やした総同期時間の割合です。 セッションが完了するまでこの値は NULL です。|  
|**estimated_changes**|**int**|アーティクルに適用する必要のある行の変更の予想される数です。|  
|**relative_cost**|**decimal**|セッション全体の合計時間に対する、このアーティクルの変更を適用するのに要した時間です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
