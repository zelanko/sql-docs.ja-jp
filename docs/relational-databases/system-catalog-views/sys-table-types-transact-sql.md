---
title: "sys.table_types (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- table_types_TSQL
- sys.table_types
- sys.table_types_TSQL
- table_types
dev_langs:
- TSQL
helpviewer_keywords:
- table types [SQL Server]
- table-valued parameters, sys.table_types
- sys.table_types
- UDTT
ms.assetid: c05fd873-aff2-4a89-9936-a54c2ea09996
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e9c55e83d67fcd5817575b0b045bb680b0269217
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systabletypes-transact-sql"></a>sys.table_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ユーザー定義テーブル型のプロパティを表示[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 テーブル型は、テーブル変数またはテーブル値パラメーターを宣言できる型です。 テーブルの種類ごとに、 **type_table_object_id**への外部キーは、 [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)カタログ ビューです。 次のような方法で、さまざまなカタログ ビューにクエリをこの ID 列を使用することができます、 **object_id**列、標準のテーブル、列や制約などのテーブル型の構造を検出します。    
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|*\<継承された列 >*||このビューが継承する列の一覧は、次を参照してください。 [sys.types &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-types-transact-sql.md).|  
|**type_table_object_id**|**int**|オブジェクト ID 番号。 この番号はデータベース内で一意です。|  
|**is_memory_optimized**|**bit**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 使用できる値を次に示します。<br /><br /> 0 = メモリ最適化ではありません<br /><br /> 1 = メモリ最適化です<br /><br /> 値 0 が既定の値です。<br /><br /> テーブル型は、常に DURABILITY = SCHEMA_ONLY で作成されます。 スキーマだけがディスクに保存されます。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [使用してテーブル値パラメーター &#40; データベース エンジン&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)   
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
