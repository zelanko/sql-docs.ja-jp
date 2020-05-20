---
title: table_types (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e000d4e4f7f46d57bb1ae9a4e5c370169eb1227f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82821323"
---
# <a name="systable_types-transact-sql"></a>table_types (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ユーザー定義テーブル型のプロパティを表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。 テーブル型は、テーブル変数またはテーブル値パラメーターを宣言できる型です。 各テーブル型には、 [sys. objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)カタログビューの外部キーである**type_table_object_id**があります。 この ID 列を使用すると、通常のテーブルの**object_id**列に似た方法でさまざまなカタログビューに対してクエリを実行し、列や制約などのテーブル型の構造を検出することができます。    
 
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|*\<継承された列>*||このビューが継承する列の一覧については、「 [sys &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)」を参照してください。|  
|**type_table_object_id**|**int**|オブジェクト ID 番号。 この数値は、データベース内で一意です。|  
|**is_memory_optimized**|**bit**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 以降。<br /><br /> 使用できる値を次に示します。<br /><br /> 0 = メモリ最適化ではありません<br /><br /> 1 = メモリ最適化済み<br /><br /> 値 0 が既定の値です。<br /><br /> テーブル型は、常に DURABILITY = SCHEMA_ONLY で作成されます。 スキーマはディスクにのみ保存されます。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [テーブル値パラメーターを使用する &#40;データベースエンジン&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)   
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
