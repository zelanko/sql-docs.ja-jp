---
title: "TABLE_CONSTRAINTS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-information-schema-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TABLE_CONSTRAINTS
- TABLE_CONSTRAINTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.TABLE_CONSTRAINTS view
- TABLE_CONSTRAINTS view
ms.assetid: 687f3284-2849-4853-8a5c-fc936deceae0
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4b5b62068ab1afb9d697686d259b7fa6d1222a56
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="tableconstraints-transact-sql"></a>TABLE_CONSTRAINTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベース内のテーブル制約ごとに 1 行のデータを返します。 この情報スキーマ ビューは、現在のユーザーが権限を所有しているオブジェクトについての情報を返します。  
  
 これらのビューから情報を取得するには、完全修飾の名前を指定**INFORMATION_SCHEMA** 。*view_name*です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**nvarchar (**128**)**|制約修飾子|  
|**CONSTRAINT_SCHEMA**|**nvarchar (**128**)**|制約を含むスキーマの名前です。<br /><br /> **\*\*重要な\* \*** オブジェクトのスキーマを決定 INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**CONSTRAINT_NAME**|**sysname**|制約名。|  
|**TABLE_CATALOG**|**nvarchar (**128**)**|テーブル修飾子|  
|**TABLE_SCHEMA、**|**nvarchar (**128**)**|テーブルを含むスキーマの名前<br /><br /> **\*\*重要な\* \*** オブジェクトのスキーマを決定 INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**TABLE_NAME**|**sysname**|テーブル名です。|  
|**CONSTRAINT_TYPE**|**varchar (**11**)**|制約の種類。<br /><br /> CHECK<br /><br /> UNIQUE<br /><br /> PRIMARY KEY<br /><br /> FOREIGN KEY|  
|**IS_DEFERRABLE**|**varchar (**2**)**|制約チェックを延期できるかどうかを示します。 常に NO を返します。|  
|**INITIALLY_DEFERRED**|**varchar (**2**)**|制約チェックが最初に延期されているかどうかを示します。 常に NO を返します。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40;です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマ ビュー &#40;です。TRANSACT-SQL と #41 です。](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.key_constraints &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)   
 [sys.check_constraints &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)  
  
  
