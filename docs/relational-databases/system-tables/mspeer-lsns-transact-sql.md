---
description: MSpeer_lsns (Transact-SQL)
title: MSpeer_lsns (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_lsns
- MSpeer_lsns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_lsns system table
ms.assetid: 0ba33907-601b-4c3d-8099-2663f680a161
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 144f824c92dfb94c0b86ad1265d659ef42c648d8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469040"
---
# <a name="mspeer_lsns-transact-sql"></a>MSpeer_lsns (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **Mspeer_lsns**テーブルは、ピアツーピアレプリケーショントポロジ内の各トランザクションをサブスクリプションにマップするために使用されます。 このテーブルは、ピアツーピアレプリケーショントポロジ内のすべてのパブリケーションデータベースと、ピアツーピアパブリケーションのすべてのサブスクライバーのサブスクリプションデータベースに格納されます。 この種類のトランザクションレプリケーショントポロジの詳細については、「 [ピアツーピアトランザクションレプリケーション](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。 このテーブルは、パブリケーションデータベースに格納されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ピアツーピア LSN を識別します。|  
|**last_updated**|**datetime**|最後の行の更新が行われた **日時** 。|  
|**送信者**|**sysname**|トランザクションを開始したパブリッシャーの名前。|  
|**originator_db**|**sysname**|トランザクションが発生したデータベースの名前。|  
|**originator_publication**|**sysname**|トランザクションが発生したパブリケーションの名前。|  
|**originator_publication_id**|**int**|トランザクションが発生したパブリケーションの識別子。|  
|**originator_db_version**|**int**|発信元のデータベースのバージョン番号識別子。|  
|**originator_lsn**|**int**|元のパブリケーションの LSN を識別します。|  
|**originator_version**|**int**|パブリッシャーのバージョン番号を識別します。|  
|**originator_id**|**smallint**|競合検出のためにトポロジの各ノードを識別します。 詳細については、「 [ピア ツー ピア レプリケーションにおける競合検出](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
