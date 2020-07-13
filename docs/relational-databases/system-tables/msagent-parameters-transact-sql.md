---
title: MSagent_parameters (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSagent_parameters_TSQL
- MSagent_parameters
dev_langs:
- TSQL
helpviewer_keywords:
- MSagent_parameters system table
ms.assetid: be30abc9-c00d-446f-b1b4-1269772f37e6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9070fd9ee8b3e1bb9a32f5a28ccf189496e6b38b
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890084"
---
# <a name="msagent_parameters-transact-sql"></a>MSagent_parameters (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSagent_parameters**テーブルには、エージェントプロファイルに関連付けられているパラメーターが含まれています。 パラメーター名は、エージェントでサポートされている名前と同じです。 このテーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|**MSagent_profiles**テーブルのプロファイル ID。|  
|**parameter_name**|**sysname**|パラメーターの名前。|  
|**value**|**nvarchar(255)**|パラメーターの値。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
