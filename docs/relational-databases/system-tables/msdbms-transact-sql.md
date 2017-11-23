---
title: "MSdbms (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSdbms_TSQL
- MSdbms
dev_langs: TSQL
helpviewer_keywords: MSdbms system table
ms.assetid: 2be631bf-de09-4e7a-9ccb-d6c37b81c237
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: faadf4ccae5cd37a0f9b374d2dfb3af144439129
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msdbms-transact-sql"></a>MSdbms (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdbms**テーブルには、異種データベース レプリケーションのサポートされているデータベース管理システム (DBMS) のすべてのバージョンのマスター リストが含まれています。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**dbms_id**|**int**|一意の各 DBMS およびバージョンを識別します。|  
|**dbms**|**sysname**|DBMS 名です。<br /><br /> MSSQLSERVER<br /><br /> DB2<br /><br /> ORACLE<br /><br /> SYBASE|  
|**version**|**varchar (10)**|DBMS バージョンです。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
