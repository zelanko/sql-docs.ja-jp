---
title: sysdatatypemappings (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysdatatypemappings
- sysdatatypemappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdatatypemappings view
ms.assetid: 5dfafb70-3e3d-4465-b293-1acff1f855b6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 31f90836b26d9551cc3e5a1200208cc51e3ef30a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52756944"
---
# <a name="sysdatatypemappings-transact-sql"></a>sysdatatypemappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysdatatypemappings**ビューを使用して、SQL Server データ型と SQL Server 以外のデータベース管理システム (DBMS) のデータ型間のマッピングを表示します。 このビューは、 **msdb**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**mapping_id**|**int**|データ型マッピングの ID です。|  
|**source_dbms**|**sysname**|データ型のマップ元となる DBMS の名前を示します。次の値のいずれかになります。<br /><br /> **MSSQLSERVER** =、ソースが SQL Server データベース。<br /><br /> **ORACLE** = ソースには、Oracle データベース。|  
|**source_version**|**sysname**|マップ元 DBMS の製品バージョンを示します。|  
|**source_type**|**sysname**|マップ元 DBMS で一覧されているデータ型を示します。|  
|**source_length_min**|**bigint**|マップ元 DBMS におけるデータ型の最小の長さ。値 NULL は長さが使用されないことを示します。|  
|**source_length_max**|**bigint**|マップ元 DBMS におけるデータ型の最大の長さ。値 NULL は長さが使用されないことを示します。|  
|**source_precision_min**|**bigint**|マップ元 DBMS におけるデータ型の最小有効桁数。値 NULL は有効桁数が使用されないことを示します。|  
|**source_precision_max**|**bigint**|マップ元 DBMS におけるデータ型の最大有効桁数。値 NULL は有効桁数が使用されないことを示します。|  
|**source_scale_min**|**int**|マップ元 DBMS におけるデータ型の最小小数点以下桁数。値 NULL は小数点以下桁数が使用されないことを示します。|  
|**source_scale_max**|**int**|マップ元 DBMS におけるデータ型の最大小数点以下桁数。値 NULL は小数点以下桁数が使用されないことを示します。|  
|**source_nullable**|**bit**|マップ先のデータ型が NULL 値をサポートするかどうかを示します。|  
|**source_createparams**|**int**|内部使用のみです。|  
|**destination_dbms**|**sysname**|マップ先 DBMS の名前を示します。次の値のいずれかになります。<br /><br /> **MSSQLSERVER** =、変換先は、SQL Server データベース。<br /><br /> **ORACLE** =、変換先は Oracle データベース。<br /><br /> **DB2** =、変換先は、IBM DB2 データベース。<br /><br /> **SYBASE** =、変換先は Sybase データベース。|  
|**destination_version**|**sysname**|マップ先 DBMS の製品バージョンです。|  
|**destination_type**|**sysname**|マップ先 DBMS でのデータ型。|  
|**destination_length**|**bigint**|マップ先 DBMS のデータ型の長さです。|  
|**destination_precision**|**bigint**|マップ先 DBMS のデータ型の有効桁数です。|  
|**destination_scale**|**int**|マップ先 DBMS のデータ型の小数点以下桁数です。|  
|**destination_nullable**|**bit**|マップ先 DBMS のデータ型が NULL 値をサポートするかどうかを示します。|  
|**destination_createparams**|**int**|内部使用のみです。|  
|**dataloss**|**bit**|マップ元 DBMS とマップ先 DBMS のデータ型をマップしたときにデータの損失が発生するかどうかを示します。|  
|**is_default**|**bit**|データ型マッピングが既定で使用されるかどうかを示します。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpdatatypemap &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)  
  
  
