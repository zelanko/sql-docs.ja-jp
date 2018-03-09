---
title: "IS_ROLEMEMBER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS_ROLEMEMBER
- IS_ROLEMEMBER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- roles [SQL Server], members
- IS_ROLEMEMBER function
- members [SQL Server], verifying
ms.assetid: 73efa688-ae91-4014-98bc-1cabe47321f7
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: fd8574c27bea00127096dc1f0040c8c3f93e96cb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isrolemember-transact-sql"></a>IS_ROLEMEMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  指定されたデータベース プリンシパルが、指定されたデータベース ロールのメンバーであるかどうかを示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
IS_ROLEMEMBER ( 'role' [ , 'database_principal' ] )  
```  
  
## <a name="arguments"></a>引数  
 **'** *ロール* **'**  
 確認するデータベース ロールの名前を指定します。 *ロール*は**sysname**です。  
  
 **'** *database_principal* **'**  
 確認するデータベース ユーザー、データベース ロール、またはアプリケーション ロールの名前を指定します。 *database_principal*は**sysname**、既定値は NULL です。 値を指定しない場合、結果は現在の実行コンテキストに基づきます。 パラメーターに "NULL" という語が含まれていると、NULL が返されます。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
|戻り値|Description|  
|------------------|-----------------|  
|0|*database_principal*のメンバーではない*ロール*です。|  
|1|*database_principal*のメンバーである*ロール*です。|  
|NULL|*database_principal*または*ロール*が有効でないか、ロールのメンバーシップを表示するアクセス許可がありません。|  
  
## <a name="remarks"></a>解説  
 IS_ROLEMEMBER は、現在のユーザーがデータベース ロールの権限を必要とするアクションを実行できるかどうかを判断するために使用します。  
  
 場合*database_principal* contoso \mary5、IS_ROLEMEMBER は NULL を返します、しない限りなど、Windows ログインに基づくが、 *database_principal*許可またはへの直接アクセスが拒否されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 場合、省略可能な*database_principal*パラメーターを指定しない場合、 *database_principal*ベースは、Windows ドメイン ログインに Windows グループのメンバーシップを通じて、データベース ロールのメンバーである可能性があります. そのような間接的なメンバーシップを解決するために、IS_ROLEMEMBER は、Windows グループのメンバーシップ情報をドメイン コントローラーに要求します。 ドメイン コントローラーにアクセスできないか、またはドメイン コントローラーが応答しない場合、IS_ROLEMEMBER はユーザーとそのローカル グループのみを考慮したロール メンバーシップ情報を返します。 指定されたユーザーが現在のユーザーでない場合、IS_ROLEMEMBER が返す値は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に対する認証システム (Active Directory など) の最後のデータ更新と異なることがあります。  
  
 場合、省略可能な*database_principal*パラメーターを指定し、クエリが実行されるデータベース プリンシパルは、sys.database_principals 内に存在する必要がありますまたは IS_ROLEMEMBER は NULL を返します。 これが示す、 *database_principal*はこのデータベースでは無効です。  
  
 ときに、 *database_principal*パラメーターがに基づいてドメイン ログインまたは Windows グループに基づくと、ドメイン コント ローラーにアクセスできなくなって、IS_ROLEMEMBER の呼び出しは失敗し、不正確または不完全なデータを返す場合があります。  
  
 ローカル Windows アカウントなど、Windows プリンシパルをローカルで認証できる場合、IS_ROLEMEMBER の呼び出しが正確な情報を返す、ドメイン コント ローラーが使用できない場合、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
 **IS_ROLEMEMBER** Windows グループは、データベース プリンシパル引数として使用され、この Windows グループ、さらに、指定されたデータベース ロールのメンバーでは別の Windows グループのメンバーである場合に常に 0 を返します。  
  
 ユーザー アカウント制御 (UAC) が見つかった[!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)]し、Windows Server 2008 は、異なる結果を返すも可能性があります。 これは、ユーザーがサーバーに Windows グループのメンバーとしてアクセスしたか、特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーとしてアクセスしたかによります。  
  
 この関数で評価されるのはロールのメンバーシップであって、基になる権限ではありません。 たとえば、 **db_owner**固定データベース ロールには、 **CONTROL DATABASE**権限です。 ユーザーがある場合、 **CONTROL DATABASE**権限はない、ロールのメンバーと、この関数は、ユーザーがのメンバーではないことを報告して正しく、 **db_owner**ロールで、ユーザーがある同じ場合でもアクセス許可です。  
  
## <a name="related-functions"></a>関連する関数  
 現在のユーザーが指定された Windows グループのメンバーであるかどうかを確認するのにまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース ロールを使用して[IS_MEMBER (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/is-member-transact-sql.md). 確認するかどうか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン サーバー ロールのメンバーを使用して[IS_SRVROLEMEMBER (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/is-srvrolemember-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 データベース ロールに対する VIEW DEFINITION 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のユーザーがのメンバーであるかどうかを示す、`db_datareader`固定データベース ロール。  
  
```  
IF IS_ROLEMEMBER ('db_datareader') = 1  
   print 'Current user is a member of the db_datareader role'  
ELSE IF IS_ROLEMEMBER ('db_datareader') = 0  
   print 'Current user is NOT a member of the db_datareader role'  
ELSE IF IS_ROLEMEMBER ('db_datareader') IS NULL  
   print 'ERROR: The database role specified is not valid.';  
```  
  
## <a name="see-also"></a>参照  
 [ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-role-transact-sql.md)   
 [ALTER ROLE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-role-transact-sql.md)   
 [DROP ROLE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-role-transact-sql.md)   
 [SERVER ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-role-transact-sql.md)   
 [ALTER SERVER ROLE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-role-transact-sql.md)   
 [DROP SERVER ROLE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-server-role-transact-sql.md)   
 [IS_MEMBER &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/is-member-transact-sql.md)   
 [IS_SRVROLEMEMBER &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/is-srvrolemember-transact-sql.md)   
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
