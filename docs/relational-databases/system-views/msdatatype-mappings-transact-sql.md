---
title: MSdatatype_mappings (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdatatype_mappings
- MSdatatype_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdatatype_mappings view
ms.assetid: 13cdabb3-6e07-4e8d-ae80-4235022ccc7f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5af1233e81c996e98287a637e01ad1d249671303
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52785094"
---
# <a name="msdatatypemappings-transact-sql"></a>MSdatatype_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdatatype_mappings**ビューでは、SQL Server データ型を SQL Server 以外のデータベース管理システム (DBMS) によって使用されるデータ型にマップします。 このテーブルに格納されます、 **msdb**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**dbms_name**|**nvarchar(128)**|DBMS の名前です。 使用可能な値とその説明を次に示します。<br /><br /> **MSSQLSERVER**:変換先は、SQL Server データベースです。<br />**ORACLE**:マップ先は Oracle データベース。<br />**DB2**:マップ先は IBM DB2 データベース。<br />**SYBASE**:マップ先は Sybase データベース。|  
|**sql_type**|**nvarchar(128)**|SQL Server のデータ型です。|  
|**dest_type**|**nvarchar(128)**|SQL Server 以外のデータ型の名前です。|  
|**dest_prec**|**bigint**|SQL Server 以外のデータ型の有効桁数です。|  
|**dest_create_params**|**int**|内部使用のみです。|  
|**dest_nullable**|**bit**|SQL Server 以外のデータ型が NULL 値をサポートするかどうかです。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Oracle パブリッシャーのデータ型マッピングを指定します。](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
