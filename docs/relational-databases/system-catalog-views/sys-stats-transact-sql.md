---
title: sys.stats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 12/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.stats
- stats_TSQL
- sys.stats_TSQL
- stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.stats catalog view
ms.assetid: 42605c80-126f-460a-befb-a0b7482fae6a
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1a50bf492641da227f355f1e844a3e9d7156d93e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68108962"
---
# <a name="sysstats-transact-sql"></a>sys.stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  テーブル、インデックス、およびインデックス付きビューに、データベース内に存在する統計オブジェクトごとの行を格納[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 すべてのインデックスが同じ名前と ID を持つ対応する統計の行になります (**index_id** = **stats_id**)、統計のないすべての行が対応するインデックス。  
  
 カタログ ビュー [sys.stats_columns](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md)データベース内の各列の統計情報を提供します。 統計の詳細については、「[統計](../../relational-databases/statistics/statistics.md)」を参照してください。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|これらの統計情報が所属するオブジェクトの ID。|  
|**name**|**sysname**|統計の名前。 オブジェクト内で一意です。|  
|**stats_id**|**int**|統計の ID。 オブジェクト内で一意です。<br /><br />統計、インデックスに対応する場合、 *stats_id*値は同じで、 *index_id*値、 [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)カタログ ビューです。|  
|**auto_created**|**bit**|統計が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって自動的に作成されたかどうかを示します。<br /><br /> 0 = 統計は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって自動的に作成されませんでした。<br /><br /> 1 = 統計は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって自動的に作成されました。|  
|**user_created**|**bit**|統計がユーザーによって作成されたかどうかを示します。<br /><br /> 0 = 統計はユーザーによって作成されませんでした。<br /><br /> 1 = 統計はユーザーによって作成されました。|  
|**no_recompute**|**bit**|統計が作成されたかどうかを示す、 **NORECOMPUTE**オプション。<br /><br /> 0 = 統計は使っては作成されませんでした、 **NORECOMPUTE**オプション。<br /><br /> 1 = 統計はで作成された、 **NORECOMPUTE**オプション。|  
|**has_filter**|**bit**|0 = 統計情報は、フィルターがないと、すべての行で計算されます。<br /><br /> 1 = 統計にフィルターがあり、フィルター定義を満たす行についてのみ計算されます。|  
|**filter_definition**|**nvarchar(max)**|フィルター選択された統計に含まれる行のサブセットの式。<br /><br /> NULL = 非フィルター選択された統計。|  
|**is_temporary**|**bit**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 統計情報は一時的なものかどうかを示します。 一時的な統計サポート[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]読み取り専用アクセスを有効になっているセカンダリ データベース。<br /><br /> 0 = 統計は一時的なものではありません。<br /><br /> 1 = 統計は一時的なものです。|  
|**is_incremental**|**bit**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 増分統計として統計を作成するかどうかを示します。<br /><br /> 0 = 統計は増分統計ではありません。<br /><br /> 1 = 統計が増分します。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例では、`HumanResources.Employee` テーブルのすべての統計情報および統計情報列を返します。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT s.name AS statistics_name  
      ,c.name AS column_name  
      ,sc.stats_column_id  
FROM sys.stats AS s  
INNER JOIN sys.stats_columns AS sc   
    ON s.object_id = sc.object_id AND s.stats_id = sc.stats_id  
INNER JOIN sys.columns AS c   
    ON sc.object_id = c.object_id AND c.column_id = sc.column_id  
WHERE s.object_id = OBJECT_ID('HumanResources.Employee');  
```  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [統計](../../relational-databases/statistics/statistics.md)    
 [sys.dm_db_stats_properties &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)   
 [sys.dm_db_stats_histogram &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md)   
 [sys.stats_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md)
 

 
