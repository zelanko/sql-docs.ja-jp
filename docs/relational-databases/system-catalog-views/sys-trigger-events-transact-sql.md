---
title: "sys.trigger_events (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- trigger_events_TSQL
- trigger_events
- sys.trigger_events
- sys.trigger_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trigger_events catalog view
ms.assetid: 92540447-131c-491c-b033-c064c7d950e1
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: afdbaaabef2123204f73fe9710e2c625ddeacb1f
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="systriggerevents-transact-sql"></a>sys.trigger_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  トリガーが起動されるイベントごとに 1 行のデータを保持します。  
  
> [!NOTE]  
>  **sys.trigger_events**イベント通知には適用されません。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<Sys.events から継承された列 >**|適用なし|継承、 **object_id**、**型**、 **type_desc**から列[sys.events](../../relational-databases/system-catalog-views/sys-events-transact-sql.md)です。|  
|**is_first**|**bit**|トリガーはこのイベントに対して最初に起動されます。|  
|**is_last**|**bit**|トリガーはこのイベントに対して最後に起動されます。|  
|**event_group_type**|**int**|トリガーを作成する対象のイベント グループです。イベント グループが作成対象でない場合は NULL になります。|  
|**event_group_type**|**nvarchar (60)**|トリガーを作成する対象のイベント グループの説明です。イベント グループが作成対象でない場合は NULL になります。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
