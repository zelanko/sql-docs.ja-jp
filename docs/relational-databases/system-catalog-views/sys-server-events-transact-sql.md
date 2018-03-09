---
title: "sys.server_events (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- server_events_TSQL
- sys.server_events_TSQL
- server_events
- sys.server_events
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_events catalog view
ms.assetid: 996f6c9b-6426-4847-95d9-6b77541422be
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bbacdd3b1f3943906be711c64f2368c4a5e7a779
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysserverevents-transact-sql"></a>sys.server_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー レベルのイベント通知またはサーバー レベルの DDL トリガーが起動されるイベントごとに 1 行のデータを保持します。 列**object_id**と**型**サーバー イベントを一意に識別します。  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|起動するサーバー レベル イベント通知またはサーバー レベル DDL トリガーの ID です。|  
|**型**|**int**|イベント通知または DDL トリガーを起動させるイベントの種類です。|  
|**type_desc**|**nvarchar (60)**|DDL トリガーまたはイベント通知を起動させるイベントの説明です。|  
|**event_group_type**|**int**|トリガーまたはイベント通知を作成する対象のイベント グループです。イベント グループが作成対象でない場合は NULL になります。|  
|**event_group_type**|**nvarchar (60)**|トリガーまたはイベント通知が作成されるイベント グループの説明またはイベント グループに対して作成されていない場合は null|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
