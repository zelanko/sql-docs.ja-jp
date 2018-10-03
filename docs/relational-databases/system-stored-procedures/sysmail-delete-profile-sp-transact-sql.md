---
title: sysmail_delete_profile_sp (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_profile_sp
- sysmail_delete_profile_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_profile_sp
ms.assetid: 71998653-4a02-446d-b6f7-50646a29e8a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c1f358385205c15954fe033a2f6631964a86fabc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47793280"
---
# <a name="sysmaildeleteprofilesp-transact-sql"></a>sysmail_delete_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メールによって使用されるメール プロファイルを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_delete_profile_sp  { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>引数  
 [ **@profile_id** = ] *profile_id*  
 削除するプロファイルのプロファイル ID を指定します。 *profile_id*は**int**、既定値は NULL です。 いずれか*profile_id*または*profile_name*指定する必要があります。  
  
 [ **@profile_name** =] **'***profile_name***'**  
 削除するプロファイルの名前を指定します。 *profile_name*は**sysname**、既定値は NULL です。 いずれか*profile_id*または*profile_name*指定する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 プロファイルを削除しても、そのプロファイルで使用されているアカウントは削除されません。  
  
 このストアド プロシージャでは、プロファイルにアクセスできるかどうかに関係なく、プロファイルを削除できます。 ユーザーの既定のプライベート プロファイル、または既定のパブリック プロファイルを削除するときに注意を使用して、 **msdb**データベース。 既定のプロファイルが使用できないときに**sp_send_dbmail**を引数としてプロファイルの名前が必要です。 そのため、既定のプロファイルを削除する可能性への呼び出し**sp_send_dbmail**が失敗します。 詳細については、次を参照してください。 [sp_send_dbmail &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md)します。  
  
 ストアド プロシージャ**sysmail_delete_profile_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマ。 現在のデータベースがない場合、3 つの部分の名前を持つプロシージャを実行する必要があります**msdb**します。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの既定のメンバーへのアクセス許可を実行、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、`AdventureWorks Administrator` というプロファイルを削除します。  
  
```  
EXECUTE msdb.dbo.sysmail_delete_profile_sp  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール構成オブジェクト](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [データベース メール ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
