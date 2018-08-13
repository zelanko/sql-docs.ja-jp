---
title: sys.default_constraints (Transact SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 362006b22a60ab8c7e36ca7f3b8bbe513eb6c31c
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39561518"
---
# <a name="sysdefaultconstraints-transact-sql"></a>sys.default_constraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  (既定の作成ステートメントの代わりに、CREATE TABLE または ALTER TABLE ステートメントの一部として作成されます)、既定の定義は、オブジェクトごとに行が含まれています**sys.objects.type** = D.  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**\<Sys.objects から継承された列 >**||このビューが継承する列の一覧は、次を参照してください。 [sys.objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)します。|  
|**parent_column_id**|**int**|内の列の ID **parent_object_id**この既定値が所属します。|  
|**definition**|**nvarchar(max)**|この既定値を定義する SQL 式。|  
|**is_system_named**|**bit**|1 = 名前はシステムによって生成されました。<br /><br /> 0 = ユーザー指定の名前。|  
  
## <a name="permissions"></a>アクセス許可  
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
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
