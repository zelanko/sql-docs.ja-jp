---
title: sp_dropmessage (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropmessage_TSQL
- sp_dropmessage
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropmessage
ms.assetid: 17287a15-cdde-43d1-bb18-9f920bc15db8
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8e6a8187936e7a2f824315123937cf9c7eca9c5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933865"
---
# <a name="sp_dropmessage-transact-sql"></a>sp_dropmessage (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  のインスタンスから、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]指定されたユーザー定義エラーメッセージを削除します。 ユーザー定義のメッセージは、**システム**カタログビューを使用して表示できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropmessage [ @msgnum = ] message_number  
    [ , [ @lang = ] 'language' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @msgnum = ] message_number`削除するメッセージ番号を指定します。 *message_number*は、5万より大きいメッセージ番号を持つユーザー定義メッセージである必要があります。 *message_number*は**int**,、既定値は NULL です。  
  
`[ @lang = ] 'language'`削除するメッセージの言語を示します。 **All**を指定した場合、 *message_number*のすべての言語バージョンが削除されます。 *language*は**sysname**,、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 [なし] :  
  
## <a name="permissions"></a>アクセス許可  
 **Sysadmin**および**serveradmin**固定サーバーロールのメンバーシップが必要です。  
  
## <a name="remarks"></a>解説  
 *Language*に**all**を指定しない限り、英語版のメッセージを削除する前に、メッセージのすべてのローカライズ版を削除する必要があります。  
  
## <a name="examples"></a>例  
  
### <a name="a-dropping-a-user-defined-message"></a>A. ユーザー定義メッセージを削除する  
 次の例では、ユーザー定義メッセージ (number `50001`) を削除し**ます。**  
  
```  
USE master;  
GO  
EXEC sp_dropmessage 50001;  
```  
  
### <a name="b-dropping-a-user-defined-message-that-includes-a-localized-version"></a>B. ローカライズされたバージョンを含むユーザー定義メッセージを削除する  
 次の例では、メッセージのローカライズされ`60000`たバージョンを含む、ユーザー定義のメッセージ番号を削除します。  
  
```  
USE master;  
GO  
  
-- Create a user-defined message in U.S. English  
EXEC sp_addmessage   
    @msgnum = 60000,  
    @severity = 16,  
    @msgtext = N'The item named %s already exists in %s.',   
    @lang = 'us_english';  
  
-- Create a localized version of the same message.  
EXEC sp_addmessage   
    @msgnum = 60000,  
    @severity = 16,  
    @msgtext = N'L''élément nommé %1! existe déjà dans %2!',  
    @lang = 'French';  
GO  
  
-- This statement will fail as long as the localized version  
-- of the message exists.  
EXEC sp_dropmessage 60000;  
GO  
  
-- This statement will drop the message.  
EXEC sp_dropmessage  
    @msgnum = 60000,  
    @lang = 'all';  
GO  
```  
  
### <a name="c-dropping-a-localized-version-of-a-user-defined-message"></a>C. ユーザー定義メッセージのローカライズ版の削除  
 次の例では、メッセージ全体を削除せずに、ユーザー `60000`定義のメッセージ数のローカライズ版を削除します。  
  
```  
USE master;  
GO  
  
-- Create a user-defined message in U.S. English  
EXEC sp_addmessage   
    @msgnum = 60000,  
    @severity = 16,  
    @msgtext = N'The item named %s already exists in %s.',   
    @lang = 'us_english';  
  
-- Create a localized version of the same message.  
EXEC sp_addmessage   
    @msgnum = 60000,  
    @severity = 16,  
    @msgtext = N'L''élément nommé %1! existe déjà dans %2!',  
    @lang = 'French';  
GO  
-- This statement will remove only the localized version of the   
-- message.  
EXEC sp_dropmessage  
    @msgnum = 60000,  
    @lang = 'French';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [RAISERROR &#40;Transact-sql&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_addmessage &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sp_altermessage &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [FORMATMESSAGE &#40;Transact-sql&#41;](../../t-sql/functions/formatmessage-transact-sql.md)   
 [Transact-sql&#41;&#40;のメッセージ](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
