---
title: sys.database_scoped_configurations (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/16/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 94affb513c3e7d0b9cdc6111599b9861025b86e8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
  
##  <a name="Permissions"></a> アクセス許可  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="remarks"></a>解説  
 値として NULL が返される場合**value_for_secondary**、これには、セカンダリがプライマリに設定されていることを意味します。  
 
 データベース スコープ構成設定はデータベースで継承されます。 つまり、特定のデータベースが復元されたり、アタッチされたりしたとき、既存の構成設定が残ります。
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
