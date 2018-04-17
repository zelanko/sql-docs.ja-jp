---
title: MSrepl_queuedtraninfo (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
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
- MSrepl_queuedtraninfo_TSQL
- MSrepl_queuedtraninfo
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_queuedtraninfo system table
ms.assetid: af7a5baf-32ea-475f-b6b9-68c557b4980c
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 819c810f99fb0a526c260a3a7e25114a6984412e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="msreplqueuedtraninfo-transact-sql"></a>MSrepl_queuedtraninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplication_queuedtraninfo** SQL ベースのキューに置かれた更新を使用している、キューに置かれたすべての更新サブスクリプションによって発行されたキューに置かれたコマンドに関する情報を格納するテーブルがレプリケーション プロセスによって使用されます。 このテーブルは、サブスクリプション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前。|  
|**publisher_db**|**sysname**|パブリケーション データベースの名前です。|  
|**パブリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**Tranid**|**sysname**|キューに登録されたコマンドが実行されたときのトランザクション ID。|  
|**maxorderkey**|**bigint**|内部使用のみ。|  
|**commandcount**|**bigint**|内部使用のみ。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
