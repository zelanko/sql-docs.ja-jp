---
description: sysmail_delete_profile_sp (Transact-SQL)
title: sysmail_delete_profile_sp (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 58139a6b9f0471d499c1419f33be28e6a8bbc5f3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419426"
---
# <a name="sysmail_delete_profile_sp-transact-sql"></a>sysmail_delete_profile_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  データベースメールによって使用されるメールプロファイルを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_delete_profile_sp  { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>引数  
`[ @profile_id = ] profile_id` 削除するプロファイルのプロファイル id を指定します。 *profile_id* は **int**,、既定値は NULL です。 *Profile_id*または*profile_name*のいずれかを指定する必要があります。  
  
`[ @profile_name = ] 'profile_name'` 削除するプロファイルの名前を指定します。 *profile_name* は **sysname**,、既定値は NULL です。 *Profile_id*または*profile_name*のいずれかを指定する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または **1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 プロファイルを削除しても、プロファイルで使用されているアカウントは削除されません。  
  
 このストアドプロシージャは、ユーザーがプロファイルにアクセスできるかどうかに関係なく、プロファイルを削除します。 ユーザーの既定のプライベートプロファイルまたは **msdb** データベースの既定のパブリックプロファイルを削除するときは注意してください。 既定のプロファイルが使用できない場合、 **sp_send_dbmail** にはプロファイルの名前を引数として指定する必要があります。 したがって、既定のプロファイルを削除すると、 **sp_send_dbmail** の呼び出しが失敗する可能性があります。 詳細については、「 [sp_send_dbmail &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md)」を参照してください。  
  
 ストアドプロシージャ **sysmail_delete_profile_sp** は **msdb** データベースにあり、 **dbo** スキーマが所有しています。 現在のデータベースが **msdb**でない場合は、3つの部分で構成される名前を使用してプロシージャを実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの実行権限は、既定では **sysadmin** 固定サーバーロールのメンバーに与えています。  
  
## <a name="examples"></a>例  
 次の例では、`AdventureWorks Administrator` というプロファイルを削除します。  
  
```  
EXECUTE msdb.dbo.sysmail_delete_profile_sp  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベースメール構成オブジェクト](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースメール ](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
