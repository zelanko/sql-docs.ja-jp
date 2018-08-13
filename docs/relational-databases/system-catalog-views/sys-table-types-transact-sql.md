---
title: sys.table_types (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: eef7f540231ff230bf32e4f2e0d4613c5dab8477
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39559252"
---
# <a name="systabletypes-transact-sql"></a>sys.table_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ユーザー定義テーブル型のプロパティを表示します。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 テーブル型は、テーブル変数またはテーブル値パラメーターを宣言できる型です。 各テーブルの種類には、 **type_table_object_id**への外部キーは、 [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)カタログ ビューです。 この ID 列を使用するには次のような方法で、さまざまなカタログ ビューに対してクエリを**object_id**列や制約などのテーブル型の構造を検出する通常のテーブルの列。    
 
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|*\<列を継承 >*||このビューが継承する列の一覧は、次を参照してください。 [sys.types &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)します。|  
|**type_table_object_id**|**int**|オブジェクト ID 番号。 この番号はデータベース内で一意です。|  
|**is_memory_optimized**|**bit**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 使用できる値を次に示します。<br /><br /> 0 = メモリ最適化ではありません<br /><br /> 1 = メモリ最適化です<br /><br /> 値 0 が既定の値です。<br /><br /> テーブル型は、常に DURABILITY = SCHEMA_ONLY で作成されます。 スキーマだけがディスクに保存されます。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [テーブル値パラメーターの使用 &#40;データベース エンジン&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)   
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
