---
title: sp_grantlogin (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_grantlogin_TSQL
- sp_grantlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grantlogin
ms.assetid: 0c873d99-c3bf-4eb1-948b-a46cb235ccd4
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: a32826266a9e844b01b455116e18ae821f71e9c5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68055309"
---
# <a name="sp_grantlogin-transact-sql"></a>sp_grantlogin (Transact-sql)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ログインを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]作成します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに[CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md)を使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_grantlogin [@loginame=] 'login'  
```  
  
## <a name="arguments"></a>引数  
`[ @loginame = ] 'login'`Windows ユーザーまたはグループの名前を指定します。 Windows ユーザーまたはグループは、*ドメイン*\\*ユーザー*という形式の windows ドメイン名で修飾されている必要があります。たとえば、 **London\Joeb**のようになります。 *login*は**sysname**,、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_grantlogin**は、追加オプションをサポートする CREATE LOGIN を呼び出します。 SQL Server ログインの作成の詳細については、「 [CREATE LOGIN &#40;transact-sql&#41;](../../t-sql/statements/create-login-transact-sql.md) 」を参照してください。  
  
 **sp_grantlogin**は、ユーザー定義のトランザクション内では実行できません。  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する ALTER ANY LOGIN 権限が必要です。  
  
## <a name="examples"></a>例  
 次の例で`CREATE LOGIN`は、を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用して Windows ユーザー `Corporate\BobJ.`のログインを作成します。この方法をお勧めします。  
  
```sql
CREATE LOGIN [Corporate\BobJ] FROM WINDOWS;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Transact-sql&#41;&#40;ログインの作成](../../t-sql/statements/create-login-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
