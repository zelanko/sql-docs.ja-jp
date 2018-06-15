---
title: sys.database_scoped_configurations (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 05/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords:
- sys.database_scoped_configurations catalog view
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
caps.latest.revision: 13
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 373d2933d362f565799518bfe1af516ad1943276
ms.sourcegitcommit: 0cc2cb281e467a13a76174e0d9afbdcf4ccddc29
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172991"
---
# <a name="sysdatabasescopedconfigurations-transact-sql"></a>sys.database_scoped_configurations (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  構成ごとに 1 行が含まれています。 
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|構成オプションの ID です。|  
|**name**|**nvarchar(60)**|構成オプションの名前です。 可能な構成については、次を参照してください。 [ALTER DATABASE SCOPED CONFIGURATION &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)です。|  
|**value**|**sqlvariant**|プライマリ レプリカの場合は、この構成オプションの設定値です。|  
|**value_for_secondary**|**sqlvariant**|セカンダリ レプリカには、この構成オプションの設定値です。|  
|**elevate_online**|**nvarchar(60)** |データベース スコープのインデックス操作、online オプションに既定の設定 |
|**elevate_resumable**|nvarchar(60)|データベース スコープでのインデックス操作の再開可能なオプションの既定のセット| 
  
##  <a name="Permissions"></a> アクセス許可  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="remarks"></a>解説  
 値として NULL が返される場合**value_for_secondary**、これには、セカンダリがプライマリに設定されていることを意味します。  
 
 データベース スコープ構成設定はデータベースで継承されます。 つまり、特定のデータベースが復元されたり、アタッチされたりしたとき、既存の構成設定が残ります。
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
