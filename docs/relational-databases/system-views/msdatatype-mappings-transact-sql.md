---
title: "MSdatatype_mappings (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSdatatype_mappings
- MSdatatype_mappings_TSQL
dev_langs: TSQL
helpviewer_keywords: MSdatatype_mappings view
ms.assetid: 13cdabb3-6e07-4e8d-ae80-4235022ccc7f
caps.latest.revision: "12"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7ad922397a8c2ed6e0b4faf0f92b84ee8d3408af
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="msdatatypemappings-transact-sql"></a>MSdatatype_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdatatype_mappings**ビューでは、SQL Server データ型を SQL Server 以外のデータベース管理システム (DBMS) によって使用されるデータ型にマップします。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**dbms_name**|**nvarchar (128)**|DBMS の名前です。 使用可能な値とその説明のとおりです。<br /><br /> **MSSQLSERVER**: 接続先は、SQL Server データベース。<br />**ORACLE**: 接続先は Oracle データベース。<br />**DB2**: 接続先は IBM DB2 データベース。<br />**SYBASE**: 接続先は Sybase データベース。|  
|**sql_type**|**nvarchar (128)**|SQL Server データ型です。|  
|**dest_type**|**nvarchar (128)**|SQL Server 以外のデータ型の名前です。|  
|**dest_prec**|**bigint**|SQL Server 以外のデータ型の有効桁数です。|  
|**dest_create_params**|**int**|内部使用のみです。|  
|**dest_nullable**|**bit**|SQL Server 以外のデータ型が NULL 値をサポートするかどうかです。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Oracle パブリッシャーのデータ型マッピングを指定します。](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
