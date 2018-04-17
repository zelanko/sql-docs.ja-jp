---
title: MSagentparameterlist (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSagentparameterlist_TSQL
- MSagentparameterlist
dev_langs:
- TSQL
helpviewer_keywords:
- Msagentparameterlist system table
ms.assetid: 4ea571a0-078d-4e13-95ee-f3d4bbd4dfb2
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1bdbba583ece9a4a9020b27803ac07cf12137f1c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="msagentparameterlist-transact-sql"></a>MSagentparameterlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSagentparameterlist**テーブルがレプリケーション エージェント パラメーターの情報を保持し、指定されたエージェントの種類に設定できるパラメーターを指定するために使用します。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**agent_type**|**tinyint**|エージェントの種類。<br /><br /> **1**スナップショット エージェントを = です。<br /><br /> **2**ログ リーダー エージェントを = です。<br /><br /> **3**ディストリビューション エージェントを = です。<br /><br /> **4**マージ エージェントを = です。<br /><br /> **9**キュー リーダー エージェントを = です。|  
|**parameter_name**|**sysname**|有効なエージェント パラメーターの名前です。|  
|**default_value**|**nvarchar (4000)**|エージェント パラメーターの既定値です。NULL は既定値がないことを示します。|  
|**min_value**|**int**|エージェント パラメーターの下限を設定します。NULL は下限がないことを示します。|  
|**max_value**|**int**|エージェント パラメーターの上限を設定します。NULL は上限がないことを示します。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
