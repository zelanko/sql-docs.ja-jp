---
title: sp_changedbowner (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_changedbowner
- sp_changedbowner_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changedbowner
ms.assetid: 516ef311-e83b-45c9-b9cd-0e0641774c04
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4bca86b00ca5b2d84cc1c737ecf9d253a0451ea9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68126459"
---
# <a name="sp_changedbowner-transact-sql"></a>sp_changedbowner (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースの所有者を変更します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに[ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md)を使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changedbowner [ @loginame = ] 'login'  
     [ , [ @map = ] remap_alias_flag ]  
```  
  
## <a name="arguments"></a>引数  
 [ @loginame= ]'*login*'  
 現在のデータベースの新しい所有者のログイン ID を指定します。 *login*は**sysname**,、既定値はありません。 *ログイン*は既に存在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するログインまたは Windows ユーザーである必要があります。 データベース内の既存のユーザーセキュリティアカウントを使用して既にデータベースにアクセスできる場合、*ログイン*を現在のデータベースの所有者にすることはできません。 この問題を回避するには、先に現在のデータベース内のユーザーを削除してください。  
  
 [ @map= ]*remap_alias_flag*  
 ログイン** の別名はから[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]削除されているため、remap_alias_flag パラメーターは非推奨とされます。 *Remap_alias_flag*パラメーターを使用してもエラーは発生しませんが、効果はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 sp_changedbowner を実行した後、新しい所有者はデータベース内で dbo ユーザーとして認識されるようになります。 dbo には、データベース内ですべての操作を実行できる権限が暗黙的に与えられます。  
  
 master、model、または tempdb システム データベースの所有者を変更することはできません。  
  
 有効な*ログイン*値の一覧を表示するには、sp_helplogins ストアドプロシージャを実行します。  
  
 *Login*パラメーターだけを指定して sp_changedbowner を実行すると、*ログイン*するデータベースの所有権が変更されます。  
  
 任意のセキュリティ保護可能なリソースの所有者を変更するには、ALTER AUTHORIZATION ステートメントを使用します。 詳細については、「[ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する TAKE OWNERSHIP 権限が必要です。 新しい所有者に対応するユーザーがデータベース内に存在する場合は、ログインに対する IMPERSONATE 権限が必要です。存在しない場合は、サーバーに対する CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>例  
 次の例では、ログイン `Albert` を、現在のデータベースの所有者にします。  
  
```  
EXEC sp_changedbowner 'Albert';  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-sql&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sp_dropalias &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropalias-transact-sql.md)   
 [sp_dropuser &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helpdb &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helplogins &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
