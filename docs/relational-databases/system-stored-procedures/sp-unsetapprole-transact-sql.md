---
title: sp_unsetapprole (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_unsetapprole_TSQL
- sp_unsetapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unsetapprole
ms.assetid: 4c4033d3-1a34-4dfb-835d-e3293d1a442d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 65fe8e1496fba4e622d63f1ce560aba4c1acfb83
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022243"
---
# <a name="spunsetapprole-transact-sql"></a>sp_unsetapprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  アプリケーション ロールを非アクティブ化し、以前のセキュリティ コンテキストに戻します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_unsetapprole @cookie   
```  
  
## <a name="arguments"></a>引数  
 **@cookie**  
 アプリケーション ロールがアクティブ化されたときに作成されたクッキーを指定します。 Cookie がによって作成された[sp_setapprole &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)します。 **varbinary (8000)** します。  
  
> [!NOTE]  
>  **sp_setapprole** のクッキーの **OUTPUT** パラメーターは現在、適切な最大長である **varbinary(8000)** としてドキュメントに記載されています。 ただし、現在の実装では **varbinary(50)** を返します。 アプリケーションが引き続き予約**varbinary (8000)** サイズの増加、将来のリリースでクッキーの戻り値が正しく動作するアプリケーションが引き続き行われるようにします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) と 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 使用して、アプリケーション後ロールをアクティブ化**sp_setapprole**、ユーザーがサーバーから切断またはを実行するまで、ロールがアクティブなまま**sp_unsetapprole**します。  
  
 アプリケーション ロールの概要については、次を参照してください。[アプリケーション ロール](../../relational-databases/security/authentication-access/application-roles.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要**パブリック**とアプリケーション ロールがアクティブ化時に保存する cookie の知識。  
  
## <a name="examples"></a>使用例  
  
### <a name="activating-an-application-role-with-a-cookie-then-reverting-to-the-previous-context"></a>クッキーの作成を指定してアプリケーション ロールをアクティブ化し、その後以前のコンテキストに戻す  
 次の例では、パスワード `Sales11` が設定されているアプリケーション ロール `fdsd896#gfdbfdkjgh700mM` をアクティブ化し、クッキーを作成します。 例では、現在のユーザーの名前を返し、し、実行して、元のコンテキストに戻します**sp_unsetapprole**します。  
  
```  
DECLARE @cookie varbinary(8000);  
EXEC sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.   
GO   
```  
  
## <a name="see-also"></a>参照  
 [sp_setapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-application-role-transact-sql.md)  
  
  
