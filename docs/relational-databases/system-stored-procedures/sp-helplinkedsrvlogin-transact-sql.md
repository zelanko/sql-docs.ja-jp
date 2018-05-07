---
title: sp_helplinkedsrvlogin (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_helplinkedsrvlogin_TSQL
- sp_helplinkedsrvlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplinkedsrvlogin
ms.assetid: a2b1eba0-bf71-47e7-a4c7-9f55feec82a3
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b9615c833939c18b3653fa4035258b91bb5bdfc8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sphelplinkedsrvlogin-transact-sql"></a>sp_helplinkedsrvlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  分散クエリとリモート ストアド プロシージャで使用する特定のリンク サーバーに対して定義された、ログインのマッピングに関する情報を提供します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helplinkedsrvlogin [ [ @rmtsrvname = ] 'rmtsrvname' ]   
     [ , [ @locallogin = ] 'locallogin' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@rmtsrvname=**] **'***rmtsrvname***'**  
 ログインのマッピングが適用されているリンク サーバーの名前を指定します。 *rmtsrvname*は**sysname**、既定値は NULL です。 NULL の場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行中のローカル コンピューターで定義されているすべてのリンク サーバーに対して定義された、すべてのログインのマッピングが返されます。  
  
 [  **@locallogin=**] **'***locallogin***'**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、リンク サーバーにマップされているローカル サーバー上のログイン*rmtsrvname*です。 *locallogin*は**sysname**、既定値は NULL です。 NULL を指定ですべてのログイン マッピングが定義されている*rmtsrvname*が返されます。 ない場合 NULL の場合、マッピングを*locallogin*に*rmtsrvname*既に存在する必要があります。 *locallogin*できます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインまたは Windows ユーザーです。 Windows ユーザー必要がありますがへのアクセス権[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]直接またはアクセスが許可されている Windows グループのメンバーシップのいずれか。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**リンク サーバー**|**sysname**|リンク サーバー名。|  
|**ローカル ログイン**|**sysname**|マッピングが適用されているローカル ログイン。|  
|**自己マッピング**|**smallint**|0 =**ローカル ログイン**にマップされて**リモート ログイン**への接続時**リンク サーバー**です。<br /><br /> 1 =**ローカル ログイン**に接続する場合は、同じログインとパスワードにマップ**リンク サーバー**です。|  
|**リモート ログイン**|**sysname**|上のログイン名**LinkedServer**にマップされている**LocalLogin**とき**IsSelfMapping**は 0 です。 場合**IsSelfMapping** 1 に設定されて**RemoteLogin**は NULL です。|  
  
## <a name="remarks"></a>解説  
 ログインのマッピングを削除する前に使用して**sp_helplinkedsrvlogin**含まれているリンク サーバーを決定します。  
  
## <a name="permissions"></a>権限  
 権限は確認されません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-displaying-all-login-mappings-for-all-linked-servers"></a>A. すべてのリンク サーバーのすべてのログインのマッピングを表示する  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行中のローカル コンピューターで定義されているすべてのリンク サーバーの、すべてのログインのマッピングを表示します。  
  
```  
EXEC sp_helplinkedsrvlogin;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Accounts         NULL          1               NULL  
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
Marketing        NULL          1               NULL  
  
(4 row(s) affected)  
```  
  
### <a name="b-displaying-all-login-mappings-for-a-linked-server"></a>B. 特定リンク サーバーのすべてのログインのマッピングを表示する  
 次の例のすべてのローカルに定義されたログインのマッピングを表示する、`Sales`リンク サーバー。  
  
```  
EXEC sp_helplinkedsrvlogin 'Sales';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
  
(2 row(s) affected)  
```  
  
### <a name="c-displaying-all-login-mappings-for-a-local-login"></a>C. 特定ローカル ログインに対するすべてのログインのマッピングを表示する  
 次の例は、ログインに対するすべてのローカルに定義されたログイン マッピングを表示`Mary`です。  
  
```  
EXEC sp_helplinkedsrvlogin NULL, 'Mary';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
  
(2 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
