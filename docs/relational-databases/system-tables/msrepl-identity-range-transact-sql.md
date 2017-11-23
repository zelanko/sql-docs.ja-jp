---
title: "MSrepl_identity_range (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSrepl_identity_range_TSQL
- MSrepl_identity_range
dev_langs: TSQL
helpviewer_keywords: MSrepl_identity_range system table
ms.assetid: 6e92a8e8-7667-4c98-b1c4-46735bac50d8
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a7a70f77f93037ac958211a0dbb7abb685ac4d1a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msreplidentityrange-transact-sql"></a>MSrepl_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSrepl_identity_range**テーブルは、id 範囲管理サポートを提供します。 このテーブルは、パブリケーション データベース、ディストリビューション データベース、およびサブスクリプション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前。|  
|**publisher_db**|**sysname**|パブリケーション データベースの名前です。|  
|**テーブル名**|**sysname**|テーブルの名前です。|  
|**identity_support**|**int**|ID 範囲の自動処理が有効かどうかを指定します。 0 は、ID 範囲の自動処理が有効でないことを指定します。|  
|**next_seed**|**bigint**|ID 範囲の自動処理が有効な場合、次の範囲の開始位置を指定します。|  
|**pub_range**|**bigint**|パブリッシャーの ID 範囲の大きさ。|  
|**範囲**|**bigint**|調整の際にサブスクライバーに割り当てられる、連続する ID 値の大きさ。|  
|**max_identity**|**bigint**|ID 範囲の上限です。|  
|**しきい値**|**int**|ID 範囲のしきい値のパーセンテージ。|  
|**current_max**|**bigint**|必ずしも割り当てられていないが、割り当てることができる現在の最大値です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
