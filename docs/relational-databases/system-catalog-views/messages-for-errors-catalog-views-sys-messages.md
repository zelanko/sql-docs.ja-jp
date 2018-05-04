---
title: sys.messages (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- messages_TSQL
- sys.messages_TSQL
- sys.messages
- messages
dev_langs:
- TSQL
helpviewer_keywords:
- error messages [SQL Server]
- sys.messages catalog view
- error numbers [SQL Server]
ms.assetid: 8c16ecdf-68f4-4a2a-b594-086e3344e58a
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: aa37a19743801bea70b1c78d8c9606be74dfe2f8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="messages-for-errors-catalog-views---sysmessages"></a>メッセージ (エラー) 用のカタログ ビューの sys.messages
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  それぞれの行を含みます**message_id**または**language_id**システムでは、システム定義し、ユーザー定義の両方のメッセージのエラー メッセージのです。 詳細については、「[sp_addmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)」を参照してください。  
   
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**message_id**|**int**|メッセージの ID です。 これはサーバー内で一意です。 50000 未満のメッセージ ID はシステム メッセージです。|  
|**language_id**|**smallint**|対象の言語 ID 内のテキスト**テキスト**で定義されているように、使用は**syslanguages**です。 これは、指定された一意**message_id**です。|  
|**severity**|**tinyint**|メッセージの重大度レベルです。有効値は 1 ～ 25 です。 これは、同じすべてのメッセージ内での言語、 **message_id**です。|  
|**is_event_logged**|**bit**|1 = メッセージは、エラーが発生するとイベントがログに記録されます。 これは、同じすべてのメッセージ内での言語、 **message_id**です。|  
|**text**|**nvarchar(2048)**|メッセージのテキストで使用されるときに、対応する**language_id**がアクティブです。|  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [THROW &#40;Transact-SQL&#41;](../../t-sql/language-elements/throw-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [メッセージ&#40;エラー&#41;カタログ ビュー &#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/8ac78c53-7b97-41b3-9cbd-5f97c179f1f2)   
 [例外メッセージ ボックスのプログラミング](http://msdn.microsoft.com/library/0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c)   
 [エラー メッセージ](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [データベース エンジンのイベントとエラー](../../relational-databases/errors-events/database-engine-events-and-errors.md)  
  
  
