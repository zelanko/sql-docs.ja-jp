---
title: masked_columns (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.masked_columns
- masked_columns_tsql
- sys.masked_columns_tsql
- masked_columns
helpviewer_keywords:
- sys.masked_columns catalog view
ms.assetid: 671577e4-d757-4b8d-9aa9-0fc8d51ea9ca
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d1872dfd9d7ffd90696743972d38d7ad4af1171c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85648748"
---
# <a name="sysmasked_columns-transact-sql"></a>masked_columns (Transact-sql)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asdw](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asdw.md)]

  動的データマスク関数が適用されているテーブル列を照会するには、 **masked_columns**ビューを使用します。 このビューが継承、 **sys.columns** ビューです。 **sys.columns** ビューのすべての列と、 **is_masked** 列および **masking_function** 列を返して、マスクされた列かどうかを示し、マスクされた列の場合は、どのようなマスキング関数が定義されているかを示します。 これは、列があるマスキング関数が適用されるは表示のみを表示します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|object_id|**int**|この列が所属するオブジェクトの ID。|  
|name|**sysname**|列の名前です。 は、オブジェクト内で一意です。|  
|column_id|**int**|列の ID。 は、オブジェクト内で一意です。<br /><br /> 列 Id が連続していない可能性があります。|  
|**masked_columns**は、 **sys**から継承された多くの列を返します。|各種|列の定義については、「 [&#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) 」を参照してください。|  
|is_masked|**bit**|列がマスクされているかどうかを示します。 1はマスクされたことを示します。|  
|masking_function|**nvarchar (4000)**|列のマスク関数。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="permissions"></a>アクセス許可  
 このビューは、ユーザーがテーブルに対してなんらかの権限を持っている場合、またはユーザーが VIEW ANY DEFINITION 権限を持っている場合に、テーブルに関する情報を返します。  
  
## <a name="example"></a>例  
 次のクエリでは、 **sys. masked_columns**を**テーブル**に結合して、マスクされたすべての列に関する情報を返します。  
  
```  
SELECT tbl.name as table_name, c.name AS column_name, c.is_masked, c.masking_function  
FROM sys.masked_columns AS c  
JOIN sys.tables AS tbl   
    ON c.object_id = tbl.object_id  
WHERE is_masked = 1;  
```  
  
## <a name="see-also"></a>関連項目  
 [動的データ マスク](../../relational-databases/security/dynamic-data-masking.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
