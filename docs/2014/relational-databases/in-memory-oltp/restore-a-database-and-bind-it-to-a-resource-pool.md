---
title: データベースの復元とリソース プールへのバインド | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0d20a569-8a27-409c-bcab-0effefb48013
caps.latest.revision: 13
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f34bd77c9c1cb9aee941219d289560c9411516ff
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325862"
---
# <a name="restore-a-database-and-bind-it-to-a-resource-pool"></a>データベースの復元とリソース プールへのバインド
  メモリ最適化テーブルが含まれるデータベースを復元するためのメモリが十分にある場合も、ベスト プラクティスに従って名前付きリソース プールにデータベースをバインドする必要があります。 データベースをプールにバインドする前に、そのデータベースが存在する必要があるため、データベースを復元するプロセスには複数のステップが含まれます。 このトピックでは、そのプロセスについて説明します。  
  
## <a name="restoring-a-database-with-memory-optimized-tables"></a>メモリ最適化テーブルが含まれるデータベースの復元  
 データベース IMOLTP_DB を完全復元し、Pool_IMOLTP にバインドする手順は次のとおりです。  
  
1.  [NORECOVERY を指定して復元を行う](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_norecovery)  
  
2.  [リソース プールを作成する](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_createpool)  
  
3.  [データベースとリソース プールをバインドする](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_bind)  
  
4.  [RECOVERY を指定して復元を行う](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_recovery)  
  
5.  [リソース プール パフォーマンスの監視](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_monitor)  
  
###  <a name="bkmk_NORECOVERY"></a> NORECOVERY を指定して復元を行う  
 データベースを復元するときに、NORECOVERY ではメモリを使用せずにデータベースが作成され、ディスク イメージが復元されます。  
  
```tsql  
RESTORE DATABASE IMOLTP_DB   
   FROM DISK = 'C:\IMOLTP_test\IMOLTP_DB.bak'  
   WITH NORECOVERY  
```  
  
###  <a name="bkmk_createPool"></a> リソース プールを作成する  
 次の [!INCLUDE[tsql](../../includes/tsql-md.md)] では、使用可能なメモリを 50% に指定して、Pool_IMOLTP という名前のリソース プールが作成されます。  プールが作成された後、Pool_IMOLTP が含まれるようにリソース ガバナーが再構成されます。  
  
```tsql  
CREATE RESOURCE POOL Pool_IMOLTP WITH (MAX_MEMORY_PERCENT = 50);  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
###  <a name="bkmk_bind"></a> データベースとリソース プールをバインドする  
 システム関数 `sp_xtp_bind_db_resource_pool` を使用して、データベースをリソース プールにバインドします。 この関数は、パラメーターとしてデータベース名とリソース プール名をこの順序で受け取ります。  
  
 次の [!INCLUDE[tsql](../../includes/tsql-md.md)] では、リソース プール Pool_IMOLTP へのデータベース IMOLTP_DB のバインドを定義しています。 このバインドは、次の手順を完了するまで有効になりません。  
  
```tsql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
###  <a name="bkmk_RECOVERY"></a> RECOVERY を指定して復元を行う  
 RECOVERY を指定してデータベースを復元すると、データベースがオンラインになり、すべてのデータが復元されます。  
  
```tsql  
RESTORE DATABASE IMOLTP_DB   
   WITH RECOVERY  
```  
  
###  <a name="bkmk_Monitor"></a> リソース プール パフォーマンスの監視  
 データベースが名前付きリソース プールにバインドされ、RECOVERY を指定して復元されたら、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、Resource Pool Stats オブジェクトを監視します。 詳細については、「 [SQL Server、Resource Pool Stats オブジェクト](../performance-monitor/sql-server-resource-pool-stats-object.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [メモリ最適化テーブルを持つデータベースのリソース プールへのバインド](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql)   
 [SQL Server、Resource Pool Stats オブジェクト](../performance-monitor/sql-server-resource-pool-stats-object.md)   
 [sys.dm_resource_governor_resource_pools](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql)  
  
  
