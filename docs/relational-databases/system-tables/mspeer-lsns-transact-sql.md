---
title: MSpeer_lsns (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
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
- MSpeer_lsns
- MSpeer_lsns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_lsns system table
ms.assetid: 0ba33907-601b-4c3d-8099-2663f680a161
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: de37f4de25bef419c67af1ff858251bec4b5e543
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102000"
---
# <a name="mspeerlsns-transact-sql"></a>MSpeer_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Mspeer_lsns**各トランザクションをピア ツー ピア レプリケーション トポロジ内のサブスクリプションにマップするテーブルを使用します。 このテーブルは、ピアツーピア レプリケーション トポロジ内にあるすべてのパブリケーション データベースと、ピアツーピア パブリケーションに対するすべてのサブスクライバーのサブスクリプション データベースに格納されます。 この種類のトランザクション レプリケーション トポロジの詳細については、次を参照してください。[ピア ツー ピア トランザクション レプリケーション](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)します。 このテーブルは、パブリケーション データベース内に保存されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ピアツーピア LSN を識別します。|  
|**last_updated**|**datetime**|**Datetime**で最後の行の更新が行われました。|  
|**originator**|**sysname**|トランザクションが発生したパブリッシャーの名前。|  
|**originator_db**|**sysname**|トランザクションが発生したデータベースの名前。|  
|**originator_publication**|**sysname**|トランザクションが発生したパブリケーションの名前。|  
|**originator_publication_id**|**int**|トランザクションが発生したパブリケーションの識別子。|  
|**originator_db_version**|**int**|発信元のデータベースのバージョン番号識別子。|  
|**originator_lsn**|**int**|発生元パブリケーションでの LSN を識別します。|  
|**originator_version**|**int**|パブリッシャーのバージョン番号を識別します。|  
|**originator_id**|**smallint**|競合検出のためにトポロジの各ノードを識別します。 詳細については、「 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
