---
title: "MSdbms_datatype (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdbms_datatype
- MSdbms_datatype_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_datatype system table
ms.assetid: 606168cc-79a8-442f-ab43-936f8f884d72
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dd690436908a61b43b4e7af829e8bc3528fd5305
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msdbmsdatatype-transact-sql"></a>MSdbms_datatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdbms_datatype**テーブルには、異種データベース レプリケーションでパブリッシャーまたはサブスクライバーとして使用される各サポートされているデータベース管理システム (DBMS) でのネイティブ データ型の完全な一覧が含まれています。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**datatype_id**|**int**|個々の一意なデータ型を識別します。|  
|**dbms_id**|**int**|型が属する DBMS を識別します。|  
|**型**|**sysname**|データ型の名前 (ネイティブ) です。|  
|**createparams**|**int**|各データ型に適用できる長さ、有効桁数、および小数点以下桁数の組み合わせを表すビットマップです。以下の要素が含まれます。<br /><br /> **0x1**有効桁数を = です。<br /><br /> **0x2**スケールを = です。<br /><br /> **0x4**長さを = です。|  
  
## <a name="remarks"></a>解説  
 このテーブルには、SQL Server のインスタンスに SQL Server 以外のデータベースをサブスクライブありを SQL Server 以外のサブスクライバーを発行できるための SQL Server データ型のエントリが含まれています。  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Oracle パブリッシャーのデータ型マッピングを指定します。](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
