---
title: sys.masked_columns (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.masked_columns
- masked_columns_tsql
- sys.masked_columns_tsql
- masked_columns
helpviewer_keywords:
- sys.masked_columns catalog view
ms.assetid: 671577e4-d757-4b8d-9aa9-0fc8d51ea9ca
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 64461261b624ace154376250419ec2e9a2f6ac89
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39558932"
---
# <a name="sysmaskedcolumns-transact-sql"></a>sys.masked_columns (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  使用して、 **sys.masked_columns**クエリを持つ動的データ マスク関数がそれらに適用されたテーブルの列を表示します。 このビューが継承、 **sys.columns** ビューです。 **sys.columns** ビューのすべての列と、 **is_masked** 列および **masking_function** 列を返して、マスクされた列かどうかを示し、マスクされた列の場合は、どのようなマスキング関数が定義されているかを示します。 これは、列があるマスキング関数が適用されるは表示のみを表示します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|object_id|**int**|この列が属するオブジェクトの ID です。|  
|NAME|**sysname**|列の名前です。 オブジェクト内で一意です。|  
|column_id|**int**|列の ID です。 オブジェクト内で一意です。<br /><br /> 列 ID は連続した値にならないことがあります。|  
|**sys.masked_columns**から継承された数の多い列を返します**sys.columns**します。|さまざまな|参照してください[sys.columns &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)列定義の詳細についてはします。|  
|is_masked|**bit**|列はマスクされているかどうかを示します。 1 には、マスクのことを示します。|  
|masking_function|**nvarchar (4000)**|列のマスキング関数。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="permissions"></a>アクセス許可  
 このビューは、ユーザーが、テーブルにある種のアクセス許可を持っているか、ユーザーが VIEW ANY DEFINITION 権限を持つかどうかに、テーブルに関する情報を返します。  
  
## <a name="example"></a>例  
 次のクエリの結合**sys.masked_columns**に**sys.tables**すべてに関する情報を返すには、列をマスクします。  
  
```  
SELECT tbl.name as table_name, c.name AS column_name, c.is_masked, c.masking_function  
FROM sys.masked_columns AS c  
JOIN sys.tables AS tbl   
    ON c.object_id = tbl.object_id  
WHERE is_masked = 1;  
```  
  
## <a name="see-also"></a>参照  
 [動的データ マスク](../../relational-databases/security/dynamic-data-masking.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
