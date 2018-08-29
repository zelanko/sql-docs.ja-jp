---
title: sys.database_scoped_configurations (TRANSACT-SQL) |Microsoft Docs
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
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e127f8935b10003a1ecfbd70d7237c5911d7f34f
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43107243"
---
# <a name="sysdatabasescopedconfigurations-transact-sql"></a>sys.database_scoped_configurations (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  構成ごとに 1 行が含まれています。 
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|構成オプションの ID。|  
|**name**|**nvarchar(60)**|構成オプションの名前。 可能な構成については、次を参照してください。 [ALTER DATABASE SCOPED CONFIGURATION &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)します。|  
|**value**|**sqlvariant**|プライマリ レプリカの場合は、この構成オプションの設定値です。|  
|**value_for_secondary**|**sqlvariant**|セカンダリ レプリカの場合は、この構成オプションの設定値です。|  
|**elevate_online**|**nvarchar(60)** |Db オンライン インデックス操作のオプションの既定のセットのスコープ |
|**elevate_resumable**|nvarchar(60)|Db スコープのインデックス操作の再開可能なオプションの既定のセット| 
  
##  <a name="Permissions"></a> Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="remarks"></a>コメント  
 値として NULL が返される**value_for_secondary**、これは、セカンダリがプライマリに設定されていることを意味します。  
 
 データベース スコープ構成設定はデータベースで継承されます。 つまり、特定のデータベースが復元されたり、アタッチされたりしたとき、既存の構成設定が残ります。
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
