---
title: MSagentparameterlist (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSagentparameterlist_TSQL
- MSagentparameterlist
dev_langs:
- TSQL
helpviewer_keywords:
- Msagentparameterlist system table
ms.assetid: 4ea571a0-078d-4e13-95ee-f3d4bbd4dfb2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f03817f9e7b13e21eb7513de4a4d96216b700460
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890067"
---
# <a name="msagentparameterlist-transact-sql"></a>MSagentparameterlist (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **Msagentparameterlist**テーブルには、レプリケーションエージェントのパラメーター情報が含まれており、特定の種類のエージェントに対して設定できるパラメーターを指定するために使用されます。 このテーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**agent_type**|**tinyint**|エージェントの種類。<br /><br /> **1** = スナップショットエージェント。<br /><br /> **2** = ログリーダーエージェント。<br /><br /> **3** = ディストリビューションエージェント。<br /><br /> **4** = マージエージェント。<br /><br /> **9** = キューリーダーエージェント。|  
|**parameter_name**|**sysname**|有効なエージェント パラメーターの名前です。|  
|**default_value**|**nvarchar (4000)**|エージェントパラメーターの既定値です。 NULL は、そのような値が存在しないことを示します。|  
|**min_value**|**int**|エージェントパラメーターの下限を設定します。 NULL は下限がないことを示します。|  
|**max_value**|**int**|エージェント パラメーターの上限を設定します。NULL は上限がないことを示します。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
