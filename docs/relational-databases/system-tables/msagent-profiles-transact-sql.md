---
title: MSagent_profiles (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSagent_profiles
- MSagent_profiles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSagent_profiles system table
ms.assetid: 4ab1b2ae-b6d9-42b7-9b31-98547dbb7f99
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c7e5033c5fd66141a7d6bc656f33dd5720bae016
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47700400"
---
# <a name="msagentprofiles-transact-sql"></a>MSagent_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSagent_profiles**テーブルに定義されているレプリケーション エージェントのプロファイルごとに 1 つの行が含まれています。 このテーブルに格納されます、 **msdb**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|プロファイル ID です。|  
|**profile_name**|**sysname**|エージェントの種類に固有のプロファイル名です。|  
|**agent_type**|**int**|エージェントの種類。<br /><br /> **1** = スナップショット エージェント<br /><br /> **2** = ログ リーダー エージェント<br /><br /> **3** = ディストリビューション エージェント<br /><br /> **4** = マージ エージェント<br /><br /> **9** = キュー リーダー エージェント|  
|**type**|**int**|プロファイルの種類です。<br /><br /> **0** = システム**1** = カスタム|  
|**description**|**nvarchar(3000)**|プロファイルの説明。|  
|**def_profile**|**bit**|このプロファイルがこのエージェント タイプの既定値かどうかを示します。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
