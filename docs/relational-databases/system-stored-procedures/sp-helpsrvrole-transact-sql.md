---
title: sp_helpsrvrole (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpsrvrole_TSQL
- sp_helpsrvrole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpsrvrole
ms.assetid: 5c7f39f3-c261-4f70-8beb-08242d4ac242
author: stevestein
ms.author: sstein
ms.openlocfilehash: a632e6923ab3127a363650c63533fa548d1acc12
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68006120"
---
# <a name="sp_helpsrvrole-transact-sql"></a>sp_helpsrvrole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定サーバー ロールの一覧を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpsrvrole [ [ @srvrolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @srvrolename = ] 'role'`固定サーバーロールの名前を指定します。 *role*の部分は**sysname**で、既定値は NULL です。 *role*には、次のいずれかの値を指定できます。  
  
|固定サーバーロール|[説明]|  
|-----------------------|-----------------|  
|sysadmin|システム管理者|  
|securityadmin|セキュリティ管理者|  
|serveradmin|サーバー管理者|  
|setupadmin|セットアップ管理者|  
|processadmin|プロセス管理者|  
|diskadmin|ディスク管理者|  
|dbcreator|データベース作成者|  
|bulkadmin|BULK INSERT ステートメントを実行できます|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|ServerRole|**sysname**|サーバーロールの名前|  
|[説明]|**sysname**|ServerRole の説明。|  
  
## <a name="remarks"></a>解説  
 固定サーバー ロールは、サーバー レベルで定義され、特定のサーバーレベルの管理操作を実行する権限が与えられます。 固定サーバー ロールは、追加、削除、または変更することはできません。  
  
 サーバーロールのメンバーを追加または削除するには、「 [ALTER SERVER ROLE &#40;transact-sql&#41;](../../t-sql/statements/alter-server-role-transact-sql.md)」を参照してください。  
  
 すべてのログインは public のメンバーです。 内部で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は public がロールとして実装されていないため、sp_helpsrvrole はパブリックロールを認識しません。  
  
 sp_helpsrvrole は、ユーザー定義のサーバーロールを引数として受け取りません。 ユーザー定義サーバーロールの一覧を表示するには、「 [ALTER SERVER ROLE &#40;transact-sql&#41;](../../t-sql/statements/alter-server-role-transact-sql.md)」の例を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
  
### <a name="a-listing-the-fixed-server-roles"></a>A. 固定サーバーロールを一覧表示する  
 次のクエリでは、固定サーバー ロールの一覧が返されます。  
  
```  
EXEC sp_helpsrvrole ;  
```  
  
### <a name="b-listing-fixed-and-user-defined-server-roles"></a>B. 固定サーバーロールとユーザー定義サーバーロールの一覧表示  
 次のクエリでは、固定サーバーロールとユーザー定義サーバーロールの両方の一覧が返されます。  
  
```  
SELECT * FROM sys.server_principals WHERE type = 'R' ;  
```  
  
### <a name="c-returning-a-description-of-a-fixed-server-role"></a>C. 固定サーバー ロールの説明を返す  
 次のクエリでは、`diskadmin` 固定サーバー ロールの名前と説明を返します。  
  
```  
sp_helpsrvrole 'diskadmin' ;  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [サーバーレベルのロール](../../relational-databases/security/authentication-access/server-level-roles.md)   
 [sp_addsrvrolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpsrvrolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
