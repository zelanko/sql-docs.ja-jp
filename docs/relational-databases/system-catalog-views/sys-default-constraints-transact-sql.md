---
title: "sys.default_constraints (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
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
- sys.default_constraints
- sys.default_constraints_TSQL
- default_constraints
- default_constraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.default_constraints catalog view
ms.assetid: 096e3659-edeb-4440-a016-f847acd6166b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b6fa6021993aa0c9f24bf2e18f4b6702cdfc2079
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysdefaultconstraints-transact-sql"></a>sys.default_constraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  (CREATE DEFAULT ステートメントの代わりに CREATE TABLE または ALTER TABLE ステートメントの一部として作成される)、既定の定義であるオブジェクトごとに行を持つ**sys.objects.type** D. を =  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<Sys.objects から継承された列 >**||このビューが継承する列の一覧は、次を参照してください。 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**parent_column_id**|**int**|内の列の ID **parent_object_id**この既定値が属しています。|  
|**定義**|**nvarchar(max)**|この既定値を定義する SQL 式。|  
|**is_system_named**|**bit**|1 = 名前はシステムによって生成されました。<br /><br /> 0 = ユーザー指定の名前。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例では、`VacationHours` テーブルの `HumanResources.Employee` 列に適用される DEFAULT 制約の定義を返します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT d.definition   
FROM sys.default_constraints AS d  
INNER JOIN sys.columns AS c  
ON d.parent_column_id = c.column_id  
WHERE d.parent_object_id = OBJECT_ID(N'HumanResources.Employee', N'U')  
AND c.name = 'VacationHours';  
```  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
