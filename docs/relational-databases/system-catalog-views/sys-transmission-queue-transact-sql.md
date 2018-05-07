---
title: sys.transmission_queue (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- transmission_queue
- sys.transmission_queue_TSQL
- sys.transmission_queue
- transmission_queue_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.transmission_queue catalog view
ms.assetid: f3515d1a-be8f-4a27-8058-8865f0919838
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 04a1eb9729cf819d8c01fe1cc20fd963379d9fc4
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="systransmissionqueue-transact-sql"></a>sys.transmission_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このカタログ ビューは、転送キュー内のメッセージごとに 1 行のデータを格納します。ビューの内容を次の表に示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**conversation_handle**|**uniqueidentifier**|メッセージが属するメッセージ交換の識別子。 Null を許容しません。|  
|**to_service_name**|**nvarchar (256)**|メッセージの送信先サービスの名前。 NULL 値は許可されます。|  
|**to_broker_instance**|**nvarchar(128)**|メッセージの送信先サービスをホストしているブローカーの識別子。 NULL 値は許可されます。|  
|**from_service_name**|**nvarchar (256)**|メッセージの送信元サービスの名前。 NULL 値は許可されます。|  
|**service_contract_name**|**nvarchar (256)**|メッセージで使用されるメッセージ交換が従うコントラクトの名前。 NULL 値は許可されます。|  
|**enqueue_time**|**datetime**|メッセージがキューに入った時刻。 この値には、インスタンスのローカルのタイム ゾーンに関係なく UTC が使用されます。 Null を許容しません。|  
|**message_sequence_number**|**bigint**|メッセージのシーケンス番号。 Null を許容しません。|  
|**message_type_name**|**nvarchar (256)**|メッセージのメッセージ型名。 NULL 値は許可されます。|  
|**is_conversation_error**|**bit**|メッセージがエラー メッセージかどうかを示します。<br /><br /> 0 = エラー メッセージではありません。<br /><br /> 1 = エラー メッセージです。<br /><br /> Null を許容しません。|  
|**is_end_of_dialog**|**bit**|メッセージがメッセージ交換の最後のメッセージかどうかを示します。 Null を許容しません。<br /><br /> 0 = メッセージ交換の最後のメッセージではありません。<br /><br /> 1 = メッセージ交換の最後のメッセージです。<br /><br /> Null を許容しません。|  
|**message_body**|**varbinary(max)**|メッセージの本文。 NULL 値は許可されます。|  
|**transmission_status**|**nvarchar (4000)**|メッセージがキューにある理由。 これは通常、メッセージ送信が失敗した理由を示すエラー メッセージです。 空白の場合、メッセージはまだ送信されていません。 NULL 値は許可されます。|  
|**priority**|**tinyint**|このメッセージに割り当てられている優先度レベル。 Null を許容しません。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
  
