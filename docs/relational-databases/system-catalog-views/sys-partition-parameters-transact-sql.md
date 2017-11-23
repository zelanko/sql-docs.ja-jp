---
title: "sys.partition_parameters (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- partition_parameters_TSQL
- partition_parameters
- sys.partition_parameters_TSQL
- sys.partition_parameters
dev_langs: TSQL
helpviewer_keywords: sys.partition_parameters catalog view
ms.assetid: 2012ed9d-3ea3-4c29-9b78-dfa54a392dce
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ea75798552d0521204e063663566b08b36a5797b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syspartitionparameters-transact-sql"></a>sys.partition_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  パーティション関数の各パラメーターの行を保持します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**function_id**|**int**|このパラメーターが属するパーティション関数の ID です。|  
|**parameter_id**|**int**|パラメーターの ID です。 パーティション関数内で一意であり、1 から始まります。|  
|**system_type_id**|**tinyint**|パラメーターのシステム型の ID です。 対応する、 **system_type_id**の列、 **sys.types**カタログ ビューです。|  
|**max_length**|**smallint**|バイト単位でパラメーターの最大長。|  
|**有効桁数**|**tinyint**|数値ベースの場合は、パラメーターの有効桁数です。それ以外の場合は、0 です。|  
|**小数点以下桁数**|**tinyint**|数値ベースの場合は、パラメーターの小数点以下桁数です。それ以外の場合は、0 です。|  
|**collation_name**|**sysname**|文字ベースの場合は、パラメーターの照合順序の名前です。それ以外の場合は、NULL です。|  
|**user_type_id**|**int**|型の ID。 データベース内で一意です。 システム データ型の場合、 **user_type_id** = **system_type_id**です。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [パーティション関数のカタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.partition_functions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [sys.partition_range_values &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)  
  
  
