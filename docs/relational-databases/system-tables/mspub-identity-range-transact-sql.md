---
title: "MSpub_identity_range (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSpub_identity_range_TSQL
- MSpub_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSpub_identity_range system table
ms.assetid: 68746eef-32e1-42bc-aff0-9798cd0e88b8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dcf00bab09fb47969439740d4b93b40fd89bf42e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mspubidentityrange-transact-sql"></a>MSpub_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpub_identity_range**テーブルは、id 範囲管理サポートを提供します。 次の表は、パブリケーションおよびサブスクリプション データベースに格納されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**オブジェクト id**|**int**|レプリケーションで管理される ID 列を持つテーブルの ID です。|  
|**範囲**|**bigint**|サブスクリプションで調整の際に割り当てられる連続する ID 値の範囲の大きさを制御します。|  
|**pub_range**|**bigint**|パブリケーションで調整の際に割り当てられる連続する ID 値の範囲の大きさを制御します。|  
|**current_pub_range**|**bigint**|パブリケーションが使用している現在の範囲です。 異なる*pub_range*を変更した後に表示する場合**sp_changearticle**し、[次へ] の範囲調整する前にします。|  
|**しきい値**|**int**|ディストリビューション エージェントがどの時点で新しい ID 範囲を割り当てるかを制御するパーセンテージの値です。 値の比率が指定されている場合*しきい値*はディストリビューション エージェントは、新しい id 範囲を作成を使用します。|  
|**last_seed**|**bigint**|現在の範囲の下限です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
