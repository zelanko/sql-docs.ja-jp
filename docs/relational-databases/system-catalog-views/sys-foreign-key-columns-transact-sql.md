---
title: foreign_key_columns (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.foreign_key_columns
- foreign_key_columns
- sys.foreign_key_columns_TSQL
- foreign_key_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.foreign_key_columns catalog view
ms.assetid: 7247f065-5441-4bcf-9f25-c84a03290dc6
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ad5bd8f5391e5903a6f9fd10e0cfb340cf4952b6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68133978"
---
# <a name="sysforeign_key_columns-transact-sql"></a>foreign_key_columns (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  外部キーを構成する列または列のセットごとに1行の値を格納します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**constraint_object_id**|**int**|外部キー制約の ID。|  
|**constraint_column_id**|**int**|外部キーを構成する*1*つまたは複数の列の ID (n = 列の数) です。|  
|**parent_object_id**|**int**|参照元のオブジェクトである、制約の親の ID。|  
|**parent_column_id**|**int**|参照元の列である、親列の ID です。|  
|**referenced_object_id**|**int**|候補キーを持つ、参照先のオブジェクトの ID。|  
|**referenced_column_id**|**int**|参照される列の ID (候補キー列)。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよく寄せられる質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
