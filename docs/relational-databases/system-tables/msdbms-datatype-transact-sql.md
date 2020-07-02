---
title: MSdbms_datatype (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdbms_datatype
- MSdbms_datatype_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_datatype system table
ms.assetid: 606168cc-79a8-442f-ab43-936f8f884d72
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2ac552c5fe8efe897ea9066819215c82a115d1d5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725467"
---
# <a name="msdbms_datatype-transact-sql"></a>MSdbms_datatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  **MSdbms_datatype**の表には、異種データベースレプリケーションでパブリッシャーまたはサブスクライバーとして使用される、サポートされている各データベース管理システム (DBMS) のネイティブデータ型の完全な一覧が含まれています。 このテーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**datatype_id**|**int**|一意の各データ型を識別します。|  
|**dbms_id**|**int**|型が属する DBMS を識別します。|  
|**type**|**sysname**|データ型名 (ネイティブ)。|  
|**createparams**|**int**|各データ型に適用できる長さ、有効桁数、および小数点以下桁数の組み合わせを表すビットマップです。以下の要素が含まれます。<br /><br /> **0x1** = 有効桁数。<br /><br /> **0x2** = スケール。<br /><br /> **0x4** = 長さ。|  
  
## <a name="remarks"></a>Remarks  
 このテーブルには SQL Server のデータ型のエントリが含まれています。 SQL Server のインスタンスは、非 SQL Server データベースにサブスクライブし、SQL Server 以外のサブスクライバーにパブリッシュすることができます。  
  
## <a name="see-also"></a>関連項目  
 [異種データベースレプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Oracle パブリッシャーのデータ型マッピングの指定](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
