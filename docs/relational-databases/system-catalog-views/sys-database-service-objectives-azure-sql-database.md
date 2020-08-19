---
description: sys.database_service_objectives (Azure SQL Database)
title: sys.database_service_objectives
titleSuffix: Azure SQL Database
ms.date: 03/21/2018
ms.service: sql-database
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.topic: conceptual
keywords:
- エラスティックプール
- エラスティックプール, 管理
f1_keywords:
- DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
author: CarlRabeler
ms.author: carlrab
ms.custom: seo-dt-2019
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 4b6714721748fb0e41cdaa8986341385bf9d84a5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88475460"
---
# <a name="sysdatabase_service_objectives-azure-sql-database"></a>sys.database_service_objectives (Azure SQL Database)
[!INCLUDE [asdb-asdbmi-asa](../../includes/applies-to-version/asdb-asdbmi-asa.md)]

Azure SQL database または Azure SQL Data Warehouse について、エディション (サービスレベル)、サービス目標 (価格レベル)、およびエラスティックプール名 (存在する場合) を返します。 Azure SQL Database サーバーの master データベースにログオンしている場合は、すべてのデータベースの情報が返されます。 Azure SQL Data Warehouse の場合は、master データベースに接続する必要があります。  
  
  
 価格の詳細については、「 [SQL Database のオプションとパフォーマンス: SQL Database の価格](https://azure.microsoft.com/pricing/details/sql-database/) と [SQL Data Warehouse 価格](https://azure.microsoft.com/pricing/details/sql-data-warehouse/)」を参照してください。  
  
 サービスの設定を変更するには、「 [ALTER database (Azure SQL Database)](../../t-sql/statements/alter-database-azure-sql-database.md) 」および「 [alter database (Azure SQL Data Warehouse)](https://docs.microsoft.com/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest)」を参照してください。  
  
 Database_service_objectives ビューには、次の列が含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|database_id|INT|データベースの ID。 Azure SQL Database server のインスタンス内で一意です。 [Transact-sql&#41;&#40;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)に付属しています。|  
|edition|sysname|データベースまたはデータウェアハウスのサービスレベル: **Basic**、 **Standard**、 **Premium** 、または **data warehouse**。|  
|service_objective|sysname|データベースの価格レベル。 データベースがエラスティックプール内にある場合、は **ElasticPool**を返します。<br /><br /> **Basic**レベルでは、は**basic**を返します。<br /><br /> **Standard サービスレベルの単一データベースで** は、次のいずれかが返されます。 S0、S1、S2、S3、S4、S6、S7、S9、または S12。<br /><br /> **Premium レベルの単一のデータベース** は、次の値を返します: P1、P2、P4、P6、P11、または P15。<br /><br /> **SQL Data Warehouse** は DW30000C から DW100 を返します。<br /><br /> 詳細については、「[単一データベース](/azure/sql-database/sql-database-dtu-resource-limits-single-databases/)、[エラスティックプール](/azure/sql-database/sql-database-dtu-resource-limits-elastic-pools/)、[データウェアハウス](/azure/sql-data-warehouse/what-is-a-data-warehouse-unit-dwu-cdwu/)」を参照してください。|  
|elastic_pool_name|sysname|データベースが属する [エラスティックプール](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/) の名前。 データベースが単一データベースまたはデータウェアハウスの場合は **NULL** を返します。|  
  
## <a name="permissions"></a>アクセス許可  
 Master データベースに対する **dbManager** 権限が必要です。  データベースレベルでは、ユーザーは作成者または所有者である必要があります。  
  
## <a name="examples"></a>例  
 この例は、master データベースまたは Azure SQL Database ユーザーデータベースで実行できます。 このクエリでは、データベースの名前、サービス、およびパフォーマンスレベルの情報が返されます。  
  
```sql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
