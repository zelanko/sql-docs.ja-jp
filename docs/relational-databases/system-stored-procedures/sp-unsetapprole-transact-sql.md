---
title: sp_unsetapprole (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_unsetapprole_TSQL
- sp_unsetapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unsetapprole
ms.assetid: 4c4033d3-1a34-4dfb-835d-e3293d1a442d
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 817a2c5e10069654725efeab656b7788c8ce2a1c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
 アプリケーション ロールがアクティブ化されたときに作成されたクッキーを指定します。 Cookie がによって作成された[sp_setapprole &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)です。 **varbinary (8000)** です。  
  
> [!NOTE]  
>  **sp_setapprole** のクッキーの **OUTPUT** パラメーターは現在、適切な最大長である **varbinary(8000)** としてドキュメントに記載されています。 ただし、現在の実装では **varbinary(50)** を返します。 アプリケーションが継続して予約する必要があります**varbinary (8000)** アプリケーションのサイズの増加、将来のリリースでクッキーの戻り値が正しく動作を継続できるようにします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 使用して、アプリケーション後ロールがアクティブ化された**sp_setapprole**、ユーザーがサーバーからの接続が切断またはが実行されるまで、ロールがアクティブなまま**sp_unsetapprole**です。  
  
 アプリケーション ロールの概要については、次を参照してください。[アプリケーション ロール](../../relational-databases/security/authentication-access/application-roles.md)です。  
  
## <a name="permissions"></a>権限  
 メンバーシップが必要**パブリック**とアプリケーション ロールがアクティブ化されたときに保存されたクッキーの情報です。  
  
## <a name="examples"></a>使用例  
  
### <a name="activating-an-application-role-with-a-cookie-then-reverting-to-the-previous-context"></a>クッキーの作成を指定してアプリケーション ロールをアクティブ化し、その後以前のコンテキストに戻す  
 次の例では、パスワード `Sales11` が設定されているアプリケーション ロール `fdsd896#gfdbfdkjgh700mM` をアクティブ化し、クッキーを作成します。 例では、現在のユーザーの名前を返し、し、実行して元のコンテキストに戻します**sp_unsetapprole**です。  
  
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
  
  
