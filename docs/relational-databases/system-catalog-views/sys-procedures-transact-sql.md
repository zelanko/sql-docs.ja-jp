---
title: sys. プロシージャ (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- procedures
- sys.procedures_TSQL
- sys.procedures
- procedures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.procedures catalog view
ms.assetid: d17af274-b2dd-464e-9523-ee1f43e1455b
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 894bcc1a5dc6400fe6e13ae66b63af6cec4cb128
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831448"
---
# <a name="sysprocedures-transact-sql"></a>sys. プロシージャ (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  特定の種類のプロシージャであるオブジェクトごとに1行の値を格納します。 **type** = P、X、RF、および PC。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**\<Sys. オブジェクトから継承された列>**||このビューが継承する列の一覧については、「 [sys. objects &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) 」を参照してください。|  
|**is_auto_executed**|**bit**|1 = プロシージャは、サーバーの起動時に自動的に実行されます。それ以外の場合は0です。 master データベースのプロシージャに対してのみ設定できます。|  
|**is_execution_replicated**|**bit**|プロシージャの実行をレプリケートします。|  
|**is_repl_serializable_only**|**bit**|プロシージャ実行のレプリケーションは、トランザクションをシリアル化できる場合にのみ実行されます。|  
|**skips_repl_constraints**|**bit**|実行時に、NOT FOR REPLICATION とマークされた制約がスキップされます。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
