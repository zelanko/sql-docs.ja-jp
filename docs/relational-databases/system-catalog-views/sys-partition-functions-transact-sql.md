---
title: "sys.partition_functions (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.partition_functions_TSQL
- partition_functions
- sys.partition_functions
- partition_functions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partition_functions catalog view
ms.assetid: 96515727-728b-4bea-804a-36ce915b8b75
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a440995a63e75705c0a7b5d3c56e1e649c6defbe
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syspartitionfunctions-transact-sql"></a>sys.partition_functions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のパーティション関数ごとに 1 行のデータを保持します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|パーティション関数の名前です。 データベース内で一意です。|  
|**function_id**|**int**|パーティション関数 ID です。 データベース内で一意です。|  
|**型**|**char(2)**|関数の種類。<br /><br /> R = 範囲|  
|**type_desc**|**nvarchar (60)**|関数の種類。<br /><br /> RANGE|  
|**ファンアウト**|**int**|関数により作成されたパーティションの数です。|  
|**boundary_value_on_right**|**bit**|範囲パーティション分割用です。<br /><br /> 1 = 境界値は境界の右側の範囲に含まれます。<br /><br /> 0 = 境界値は境界の左側の範囲に含まれます。|  
|**is_system**||**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 1 = オブジェクトは、フルテキスト インデックス フラグメントに使用されます。<br /><br /> 0 = オブジェクトは、フルテキスト インデックス フラグメントに使用されません。|  
|**create_date**|**datetime**|関数が作成された日付です。|  
|**modify_date**|**datetime**|関数が ALTER ステートメントを使用して最後に変更された日付です。|  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [パーティション関数のカタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.partition_range_values &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)   
 [sys.partition_parameters &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)  
  
  
