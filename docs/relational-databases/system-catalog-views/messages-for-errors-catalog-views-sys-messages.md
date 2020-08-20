---
description: メッセージ (エラー用) のカタログ ビュー - sys.messages
title: sys. messages (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 572e29d83a63b97484f6c59a139375d4a18d3384
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482186"
---
# <a name="messages-for-errors-catalog-views---sysmessages"></a>メッセージ (エラー用) のカタログ ビュー - sys.messages
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  システム定義メッセージとユーザー定義メッセージの両方について、システム内のエラーメッセージの **message_id** または **language_id** ごとに1行の値を格納します。 詳細については、「[sp_addmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)」を参照してください。  
   
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**message_id**|**int**|メッセージの ID。 これはサーバー内で一意です。 5万未満のメッセージ Id はシステムメッセージです。|  
|**language_id**|**smallint**|**Sys.syslanguages**で定義されているように、**テキスト**内のテキストが使用される言語 ID。 これは、指定された **message_id**に対して一意です。|  
|**severity**|**tinyint**|メッセージの重大度レベル (1 ~ 25)。 これは、 **message_id**内のすべてのメッセージ言語で同じです。|  
|**is_event_logged**|**bit**|1 = メッセージは、エラーが発生するとイベントがログに記録されます。 これは、 **message_id**内のすべてのメッセージ言語で同じです。|  
|**text**|**nvarchar(2048)**|対応する **language_id** がアクティブな場合に使用されるメッセージのテキスト。|  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [THROW &#40;Transact-SQL&#41;](../../t-sql/language-elements/throw-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [エラーのメッセージ &#40;&#41; カタログビュー &#40;Transact-sql&#41;](https://msdn.microsoft.com/library/8ac78c53-7b97-41b3-9cbd-5f97c179f1f2)   
 [例外メッセージボックスのプログラミング](https://msdn.microsoft.com/library/0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c)   
 [エラーメッセージ](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [データベース エンジンのイベントとエラー](../../relational-databases/errors-events/database-engine-events-and-errors.md)  
  
  
