---
title: MScached_peer_lsns (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MScached_peer_lsns_TSQL
- MScached_peer_lsns
dev_langs:
- TSQL
helpviewer_keywords:
- MScached_peer_lsns system table
ms.assetid: f8b6089a-0230-45f9-8c34-9fe0d2a3a74e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7e062d1f7ef5a1c184211a8f4040ac8c295216e7
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832383"
---
# <a name="mscached_peer_lsns-transact-sql"></a>MScached_peer_lsns (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MScached_peer_lsns**テーブルは、ピアツーピアレプリケーションで特定のサブスクライバーに返すコマンドを決定するために使用される、トランザクションログの LSN 値を追跡するために使用されます。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|ディストリビューションエージェントの ID。|  
|**送信者**|**sysname**|発信元のパブリッシャーの名前。|  
|**originator_db**|**sysname**|元のパブリケーションデータベースの名前。|  
|**originator_publication_id**|**int**|発信元のパブリケーションを識別します。|  
|**originator_db_version**|**int**|発信元のデータベースのバージョン番号識別子。|  
|**originator_lsn**|**varbinary(16)**|発信元のトランザクションの LSN。|  
  
## <a name="remarks"></a>解説  
 LSN 値は挿入直後にのみ使用され、システムでは永続的な意味を持ちません。  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
