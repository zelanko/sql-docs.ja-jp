---
title: sp_changedbowner (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_changedbowner
- sp_changedbowner_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changedbowner
ms.assetid: 516ef311-e83b-45c9-b9cd-0e0641774c04
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: cb7d6df77a581b82ca79e1962c80df827ffd1718
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38038830"
---
# <a name="spchangedbowner-transact-sql"></a>sp_changedbowner (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースの所有者を変更します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changedbowner [ @loginame = ] 'login'  
     [ , [ @map = ] remap_alias_flag ]  
```  
  
## <a name="arguments"></a>引数  
 [ @loginame=] '*ログイン*'  
 現在のデータベースの新しい所有者のログイン ID を指定します。 *ログイン*は**sysname**、既定値はありません。 *ログイン*既に存在する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインまたは Windows ユーザーです。 *ログイン*データベース内の既存のユーザー セキュリティ アカウントを使用して、データベースへのアクセスが既にある場合、現在のデータベースの所有者になることはできません。 この問題を回避するには、先に現在のデータベース内のユーザーを削除してください。  
  
 [ @map=] *remap_alias_flag*  
 *Remap_alias_flag*からログインの別名が削除されているために、パラメーターは非推奨[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 使用して、 *remap_alias_flag*パラメーターは、エラーは発生しませんが、効果はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 sp_changedbowner を実行した後、新しい所有者はデータベース内で dbo ユーザーとして認識されるようになります。 dbo には、データベース内ですべての操作を実行できる権限が暗黙的に与えられます。  
  
 master、model、または tempdb システム データベースの所有者を変更することはできません。  
  
 有効な一覧を表示する*ログイン*値は、sp_helplogins ストアド プロシージャを実行します。  
  
 だけを持つ sp_changedbowner を実行して、*ログイン*パラメーターの変更はデータベースの所有権*ログイン*します。  
  
 セキュリティ保護可能なリソースの所有者は、ALTER AUTHORIZATION ステートメントを使用して変更できます。 詳細については、次を参照してください。 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する TAKE OWNERSHIP 権限が必要です。 新しい所有者に対応するユーザーがデータベース内に存在する場合は、ログインに対する IMPERSONATE 権限が必要です。存在しない場合は、サーバーに対する CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、ログイン `Albert` を、現在のデータベースの所有者にします。  
  
```  
EXEC sp_changedbowner 'Albert';  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sp_dropalias &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropalias-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helpdb &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helplogins &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
