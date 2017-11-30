---
title: "sys.trigger_event_types (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- trigger_event_types_TSQL
- sys.trigger_event_types_TSQL
- sys.trigger_event_types
- trigger_event_types
dev_langs: TSQL
helpviewer_keywords: sys.trigger_event_types catalog view
ms.assetid: 054aed54-7151-4760-934a-149fa434f1ae
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 182e53fd5438363bc74c988995d407695d7d4302
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="systriggereventtypes-transact-sql"></a>sys.trigger_event_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  トリガーを起動できるイベントまたはイベント グループごとに 1 行のデータを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**型**|**int**|トリガーを起動するイベントまたはイベント グループの種類。|  
|**type_name**|**nvarchar(64)**|イベントまたはイベント グループの名前。 これは、FOR 句で指定することができます、 [CREATE TRIGGER](../../t-sql/statements/create-trigger-transact-sql.md)ステートメントです。|  
|**parent_type**|**int**|イベントまたはイベント グループの親イベント グループの種類。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
