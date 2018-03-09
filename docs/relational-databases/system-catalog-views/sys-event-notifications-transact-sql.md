---
title: "sys.event_notifications (TRANSACT-SQL) |Microsoft ドキュメント"
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
- event_notifications_TSQL
- event_notifications
- sys.event_notifications_TSQL
- sys.event_notifications
dev_langs:
- TSQL
helpviewer_keywords:
- sys.event_notifications catalog view
ms.assetid: 136a76ee-2b35-4418-ab46-fda2d51f7d99
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ef927e091f15027d8e2fd965cc50955adf7092d1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syseventnotifications-transact-sql"></a>sys.event_notifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  イベント通知では、あるオブジェクトごとに行を返します**sys.objects.type** EN を = です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|イベント通知の名前。|  
|**object_id**|**int**|オブジェクト ID 番号。 データベース内で一意です。|  
|**parent_class**|**tinyint**|親のクラスです。<br /><br /> 0 = データベース<br /><br /> 1 = オブジェクトまたは列|  
|**parent_class_desc**|**nvarchar (60)**|DATABASE<br /><br /> OBJECT_OR_COLUMN|  
|**parent_id**|**int**|親オブジェクトの 0 以外の ID。<br /><br /> 0 = 親クラスはデータベースです。|  
|**create_date**|**datetime**|作成された日付。|  
|**modify_date**|**datetime**|常に等しい**create_date**です。|  
|**service_name**|**nvarchar (256)**|通知の送信先のサービスの名前です。|  
|**broker_instance**|**nvarchar (128)**|通知の送信先であるブローカー インスタンス。|  
|**principal_id**|**int**|イベント通知を所有するデータベース プリンシパルの ID。|  
|**creator_sid**|**varbinary (85)**|イベント通知を作成したログインの SID。<br /><br /> FAN_IN オプションが指定されていない場合は NULL です。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
