---
title: "sys.database_scoped_configurations (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/16/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords: sys.database_scoped_configurations catalog view
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
caps.latest.revision: "13"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3e9df8c18b3ca7556b10e3e2d453c41735a07e52
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="sysdatabasescopedconfigurations-transact-sql"></a>sys.database_scoped_configurations (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  構成ごとに 1 行が含まれています。 
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|構成オプションの ID です。|  
|**name**|**nvarchar(60)**|構成オプションの名前です。 可能な構成については、次を参照してください。 [ALTER DATABASE SCOPED CONFIGURATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|  
|**value**|**sqlvariant**|プライマリ レプリカの場合は、この構成オプションの設定値です。|  
|**value_for_secondary**|**sqlvariant**|セカンダリ レプリカには、この構成オプションの設定値です。|  
  
##  <a name="Permissions"></a> アクセス許可  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="remarks"></a>解説  
 値として NULL が返される場合**value_for_secondary**、これには、セカンダリがプライマリに設定されていることを意味します。  
 
 データベース スコープの設定が引き継がれます、データベースを構成します。 これは、特定のデータベースが復元またはアタッチされたときに、既存の構成設定が残ることを意味します。
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
