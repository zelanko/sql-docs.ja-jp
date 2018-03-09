---
title: "sp_droplogin (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_droplogin
- sp_droplogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droplogin
ms.assetid: e58684d1-c394-48de-906e-da6ee91100c3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c544ffb9e3093296f38c357b17e68e18607f7634
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spdroplogin-transact-sql"></a>sp_droplogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを削除します。 削除されたログイン名では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにアクセスできなくなります。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して[DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_droplogin [ @loginame = ] 'login'  
```  
  
## <a name="arguments"></a>引数  
 [  **@loginame =** ] **'***ログイン***'**  
 削除するログインを指定します。 *ログイン*は**sysname**、既定値はありません。 *ログイン*に既に存在する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_droplogin** DROP LOGIN を呼び出します。  
  
 **sp_droplogin**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>Permissions  
 サーバーに対する ALTER ANY LOGIN 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`DROP LOGIN` を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスからログイン `Victoria` を削除します。 これは推奨される方法です。  
  
```  
DROP LOGIN Victoria;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP LOGIN &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-login-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
