---
title: "MSagent_parameters (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSagent_parameters_TSQL
- MSagent_parameters
dev_langs: TSQL
helpviewer_keywords: MSagent_parameters system table
ms.assetid: be30abc9-c00d-446f-b1b4-1269772f37e6
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 43af050b9a0512e84a9c9ed3b3a745c4eb630888
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msagentparameters-transact-sql"></a>MSagent_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSagent_parameters**テーブルには、エージェント プロファイルに関連付けられているパラメーターが含まれています。 パラメーター名は、エージェントがサポートするパラメーター名と同じです。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|プロファイルの ID、 **MSagent_profiles**テーブル。|  
|**parameter_name**|**sysname**|パラメーターの名前。|  
|**値**|**nvarchar (255)**|パラメーターの値。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
