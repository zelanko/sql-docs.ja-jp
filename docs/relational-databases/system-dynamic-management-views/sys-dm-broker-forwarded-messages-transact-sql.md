---
title: sys.dm_broker_forwarded_messages (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_broker_forwarded_messages
- dm_broker_forwarded_messages
- sys.dm_broker_forwarded_messages_TSQL
- dm_broker_forwarded_messages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_broker_forwarded_messages dynamic management view
ms.assetid: 5576376d-6364-417a-8475-aa770e060845
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2e1476051a45a7a4bc01cd6445a944f372e816e9
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmbrokerforwardedmessages-transact-sql"></a>sys.dm_broker_forwarded_messages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各 Service Broker のメッセージを 1 行を返しますのインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]転送中です。  
  

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**conversation_id**|**uniqueidentifier**|メッセージが属するメッセージ交換の ID。 NULL 値は許可されます。|  
|**is_initiator**|**bit**|メッセージがメッセージ交換の発信側から送信されたものかどうかを示します。  NULL 値は許可されます。<br /><br /> 0 = 発信側からでないメッセージ<br /><br /> 1 = 発信側からのメッセージ|  
|**to_service_name**|**nvarchar(512)**|メッセージの送信先であるサービスの名前。 NULL 値は許可されます。|  
|**to_broker_instance**|**nvarchar(512)**|メッセージの送信先となるサービスをホストしているブローカーの識別子。 NULL 値は許可されます。|  
|**from_service_name**|**nvarchar(512)**|メッセージの送信元サービスの名前。 NULL 値は許可されます。|  
|**from_broker_instance**|**nvarchar(512)**|メッセージの送信元となるサービスをホストしているブローカーの識別子。 NULL 値は許可されます。|  
|**adjacent_broker_address**|**nvarchar(512)**|メッセージの送信先のネットワーク アドレス。 NULL 値は許可されます。|  
|**message_sequence_number**|**bigint**|ダイアログでの、メッセージのシーケンス番号。 NULL 値は許可されます。|  
|**message_fragment_number**|**int**|ダイアログ メッセージが断片化している場合、このトランスポート メッセージに含まれるフラグメント番号。 NULL 値は許可されます。|  
|**hops_remaining**|**tinyint**|メッセージが最終送信先に届くまでに再転送される回数。 メッセージが転送されるたび、この数は 1 ずつ減少します。 NULL 値は許可されます。|  
|**time_to_live**|**int**|メッセージがアクティブなまま保持される最大時間。 この値が 0 に達すると、メッセージは破棄されます。 NULL 値は許可されます。|  
|**time_consumed**|**int**|メッセージがアクティブなまま保持されている時間。 メッセージが転送されるたび、メッセージの転送にかかった時間がこの数に加えられます。 Null を許容しません。|  
|**message_id**|**uniqueidentifier**|メッセージの ID です。 NULL 値は許可されます。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Service Broker 関連の動的管理ビュー & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

