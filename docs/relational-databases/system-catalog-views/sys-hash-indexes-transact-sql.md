---
title: "sys.hash_indexes (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.hash_indexes_TSQL
- hash_indexes
- sys.hash_indexes
- hash_indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.hash_indexes catalog view
ms.assetid: d9e230fb-d3ff-486f-86ef-44898f0a703e
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9f4f07802cf3c716021fe28a900d1a0996f86d3a
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="syshashindexes-transact-sql"></a>sys.hash_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のハッシュ インデックスとハッシュ インデックス プロパティを表示します。 ハッシュ インデックスでのみサポートされます[、インメモリ OLTP &#40;、インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)です。  
  
 Sys.hash_indexes ビューには、sys.indexes ビューと同じ列およびという列を追加が含まれています。 **bucket_count**です。 Sys.hash_indexes ビュー内の他の列に関する詳細については、次を参照してください。 [sys.indexes &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<継承された列 >**||列を継承[sys.indexes &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)。|  
|**bucket_count**|**int**|ハッシュ インデックスのハッシュ バケットの数。<br /><br /> 値を設定するためのガイドラインなど、bucket_count の値の詳細については、次を参照してください。 [CREATE TABLE &#40;です。TRANSACT-SQL と #41 です](../../t-sql/statements/create-table-transact-sql.md)。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]」をご覧ください。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
```  
SELECT object_name([object_id]) AS 'table_name', [object_id],  
     [name] AS 'index_name', [type_desc], [bucket_count]   
FROM sys.hash_indexes   
WHERE OBJECT_NAME([object_id]) = 'T1';  
```  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
