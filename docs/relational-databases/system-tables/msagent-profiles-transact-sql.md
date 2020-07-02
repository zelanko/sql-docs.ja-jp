---
title: MSagent_profiles (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSagent_profiles
- MSagent_profiles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSagent_profiles system table
ms.assetid: 4ab1b2ae-b6d9-42b7-9b31-98547dbb7f99
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bd255e174a02463d1cdc05c047f97c1befba1ceb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762580"
---
# <a name="msagent_profiles-transact-sql"></a>MSagent_profiles (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  **MSagent_profiles**テーブルには、定義されているレプリケーションエージェントプロファイルごとに1つの行が含まれています。 このテーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|プロファイル ID。|  
|**profile_name**|**sysname**|エージェントの種類に固有のプロファイル名です。|  
|**agent_type**|**int**|エージェントの種類。<br /><br /> **1** = スナップショットエージェント<br /><br /> **2** = ログリーダーエージェント<br /><br /> **3** = ディストリビューションエージェント<br /><br /> **4** = マージエージェント<br /><br /> **9** = キューリーダーエージェント|  
|**type**|**int**|プロファイルの種類です。<br /><br /> **0** = システム**1** = カスタム|  
|**description**|**nvarchar (3000)**|プロファイルの説明。|  
|**def_profile**|**bit**|このプロファイルがこの種類のエージェントの既定のプロファイルかどうかを指定します。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
