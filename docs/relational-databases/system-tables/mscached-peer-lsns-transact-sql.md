---
title: "MScached_peer_lsns (TRANSACT-SQL) |Microsoft ドキュメント"
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
f1_keywords:
- MScached_peer_lsns_TSQL
- MScached_peer_lsns
dev_langs:
- TSQL
helpviewer_keywords:
- MScached_peer_lsns system table
ms.assetid: f8b6089a-0230-45f9-8c34-9fe0d2a3a74e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 93c1c8600541f1f5710cc9dc2fe4675d1433fa92
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mscachedpeerlsns-transact-sql"></a>MScached_peer_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MScached_peer_lsns**テーブルはピア ツー ピア レプリケーションで任意のサブスクライバーに戻るにはコマンドを判断するために使用されるトランザクション ログに LSN 値を追跡するために使用します。 このテーブルは、ディストリビューション データベースに保存されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|ディストリビューション エージェントの ID。|  
|**発信元**|**sysname**|発信元のパブリッシャーの名前。|  
|**originator_db**|**sysname**|発信元のパブリケーション データベースの名前。|  
|**originator_publication_id**|**int**|発信元のパブリケーションの識別子。|  
|**originator_db_version**|**int**|発信元のデータベースのバージョン番号識別子。|  
|**originator_lsn**|**varbinary (16)**|発信元のトランザクションの LSN。|  
  
## <a name="remarks"></a>解説  
 LSN 値は、挿入直後にのみ使用され、システムで永続的に有効にはなりません。  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
