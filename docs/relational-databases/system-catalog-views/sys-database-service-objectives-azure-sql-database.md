---
title: sys.database_service_objectives (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/21/2018
ms.service: sql-database
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.topic: conceptual
keywords:
- エラスティック プール
- エラスティック プールの管理
f1_keywords:
- DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 889d8d618cf017d27e3b92ce845c8ebfee179048
ms.sourcegitcommit: 1a182443e4f70f4632617cfef4efa56d898e64e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2019
ms.locfileid: "58342915"
---
# <a name="sysdatabaseserviceobjectives-azure-sql-database"></a>sys.database_service_objectives (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Azure SQL database または Azure SQL Data Warehouse に存在する場合は、edition (サービス層)、サービスの目標 (価格レベル) およびエラスティック プールの名前を返します。 Azure SQL Database サーバーの master データベースにログオンした場合は、すべてのデータベースに関する情報を返します。 Azure SQL Data Warehouse では、には、master データベースに接続する必要があります。  
  
  
 価格については、次を参照してください。 [SQL Database のオプションとパフォーマンス。SQL Database の価格](https://azure.microsoft.com/pricing/details/sql-database/)と[SQL Data Warehouse の価格](https://azure.microsoft.com/pricing/details/sql-data-warehouse/)します。  
  
 サービスの設定を変更するを参照してください。 [ALTER DATABASE (Azure SQL データベース)](../../t-sql/statements/alter-database-azure-sql-database.md)と[ALTER DATABASE (Azure SQL Data Warehouse)](https://docs.microsoft.com/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest)します。  
  
 Sys.database_service_objectives ビューには、次の列が含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|database_id|ssNoversion|Azure SQL Database サーバーのインスタンス内で一意で、データベースの ID。 結合可能な[sys.databases &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)します。|  
|のエディション|sysname|データベースまたはデータ ウェアハウスのサービス レベル:**基本的な**、**標準**、 **Premium**または**Data Warehouse**します。|  
|service_objective|sysname|データベースの価格レベルです。 データベースがエラスティック プール内にある場合は、返す**ElasticPool**します。<br /><br /> **基本的な**階層を返します**基本的な**します。<br /><br /> **Standard サービス レベル内の単一データベース**次のいずれかを返します。S0、S1、S2、S3、S4、S6、S7、S9 または S12 します。<br /><br /> **Premium レベルで 1 つのデータベース**次を返します。P1、P2、P4、P6、P11 または P15 します。<br /><br /> **SQL Data Warehouse** DW30000c を通じて DW100 を返します。|  
|elastic_pool_name|sysname|名前、[エラスティック プール](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)データベースが属しています。 返します**NULL**データベースが 1 つのデータベースまたはデータ warehoue 場合。|  
  
## <a name="permissions"></a>アクセス許可  
 必要があります**dbManager** master データベースに対する権限。  データベース レベルでは、ユーザーは、作成者または所有者である必要があります。  
  
## <a name="examples"></a>使用例  
 この例は、master データベースで、または Azure SQL Database のユーザー データベースで実行できます。 クエリでは、名前、サービス、およびデータベースのパフォーマンス レベルの情報を返します。  
  
```sql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
