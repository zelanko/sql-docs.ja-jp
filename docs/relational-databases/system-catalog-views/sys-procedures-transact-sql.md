---
title: "sys.procedures (TRANSACT-SQL) |Microsoft ドキュメント"
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
- procedures
- sys.procedures_TSQL
- sys.procedures
- procedures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.procedures catalog view
ms.assetid: d17af274-b2dd-464e-9523-ee1f43e1455b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 62640bc781b5c6be11fed4129a2b467e7b74c93c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysprocedures-transact-sql"></a>sys.procedures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ある種のプロシージャは、各オブジェクトの行を格納**sys.objects.type** = P、X、RF、および PC です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<Sys.objects から継承された列 >**||このビューが継承する列の一覧は、次を参照してください。 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)|  
|**is_auto_executed**|**bit**|プロシージャをサーバー起動時に自動実行する場合は 1、それ以外の場合は 0。 master データベースのプロシージャに対してのみ設定できます。|  
|**is_execution_replicated**|**bit**|プロシージャの実行をレプリケートします。|  
|**is_repl_serializable_only**|**bit**|プロシージャ実行のレプリケーションを、トランザクションがシリアル化される場合にのみ実行します。|  
|**skips_repl_constraints**|**bit**|プロシージャの実行中、NOT FOR REPLICATION としてマークされた制約をスキップします。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
