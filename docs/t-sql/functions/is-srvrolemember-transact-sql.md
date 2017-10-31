---
title: "IS_SRVROLEMEMBER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS_SRVROLEMEMBER_TSQL
- IS_SRVROLEMEMBER
dev_langs:
- TSQL
helpviewer_keywords:
- roles [SQL Server], members
- IS_SRVROLEMEMBER function
- members [SQL Server], verifying
ms.assetid: 3241a44a-6958-415b-b8b7-2a1207c36ab3
caps.latest.revision: 65
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c26c0c1f4cb6a22f50cdc6a87d7a31f25b65e138
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="issrvrolemember-transact-sql"></a>IS_SRVROLEMEMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  示すかどうか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインが指定されたサーバー ロールのメンバーです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
IS_SRVROLEMEMBER ( 'role' [ , 'login' ] )  
```  
  
## <a name="arguments"></a>引数  
 **'** *ロール* **'**  
 確認するサーバー ロールの名前です。 *ロール*は**sysname**です。  
  
 有効な値*ロール*ユーザー定義サーバー ロールは、次の固定サーバー ロール。  
  
|||  
|-|-|  
|sysadmin|serveradmin|  
|dbcreator|setupadmin|  
|bulkadmin|securityadmin|  
|diskadmin|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> public|  
|processadmin||  
  
 **'** *ログイン* **'**  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインを確認します。 *ログイン*は**sysname**、既定値は NULL です。 値が指定されていない場合、結果は現在の実行コンテキストに基づきます。 パラメーターに "NULL" という語が含まれていると、NULL が返されます。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
|戻り値|Description|  
|------------------|-----------------|  
|0|*ログイン*のメンバーではない*ロール*です。<br /><br /> [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、このステートメントは常に 0 を返します。|  
|1|*ログイン*のメンバーである*ロール*です。|  
|NULL|*ロール*または*ログイン*が有効でないか、ロールのメンバーシップを表示するアクセス許可がありません。|  
  
## <a name="remarks"></a>解説  
 現在のユーザーがサーバー ロールの権限を必要とするアクションを実行できるかどうかを判断する UseIS_SRVROLEMEMBER です。  
  
 Contoso \mary5 などの Windows ログインが指定されてかどうか*ログイン*、 **IS_SRVROLEMEMBER**返します**NULL**ログインが許可またはへの直接アクセスが拒否されている場合を除き、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 場合、省略可能な*ログイン*パラメーターを指定しない場合は*ログイン*は Windows ドメイン ログイン、Windows グループのメンバーシップを通じて、固定サーバー ロールのメンバーである可能性があります。 そのような間接的なメンバーシップを解決するために、IS_SRVROLEMEMBER は、Windows グループのメンバーシップ情報をドメイン コントローラーに要求します。 ドメイン コント ローラーはアクセスできないか、応答しない場合**IS_SRVROLEMEMBER**はユーザーとそのローカル グループのみを考慮したロール メンバーシップ情報を返します。 指定されたユーザーが現在のユーザーでない場合、IS_SRVROLEMEMBER が返す値は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に対する認証システム (Active Directory など) の最後のデータ更新と異なることがあります。  
  
 省略可能な login パラメーターを指定する場合は、クエリの対象となる Windows ログインが sys.server_principals に存在する必要があります。存在しない場合、IS_SRVROLEMEMBER は NULL を返します。 これは、そのログインが無効であることを示します。  
  
 login パラメーターがドメイン ログインか、Windows グループに基づくログインである場合、ドメイン コントローラーにアクセスできないと、IS_SRVROLEMEMBER の呼び出しが失敗し、不正確なデータや不完全なデータが返される可能性があります。  
  
 ローカル Windows アカウントなど、Windows プリンシパルをローカルで認証できる場合、IS_SRVROLEMEMBER の呼び出しが正確な情報を返す、ドメイン コント ローラーが使用できない場合、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
 **IS_SRVROLEMEMBER** Windows グループがログイン引数として使用され、この Windows グループ、さらに、指定されたサーバー ロールのメンバーでは別の Windows グループのメンバーである場合に常に 0 を返します。  
  
 ユーザー アカウント制御 (UAC) の設定では、異なる結果が返されることもあります。 これは、ユーザーがサーバーに Windows グループのメンバーとしてアクセスしたか、特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーとしてアクセスしたかによります。  
  
 この関数で評価されるのはロールのメンバーシップであって、基になる権限ではありません。 たとえば、 **sysadmin**固定サーバー ロールには、 **CONTROL SERVER**権限です。 ユーザーがある場合、 **CONTROL SERVER**権限はない、ロールのメンバーと、この関数は、ユーザーがのメンバーではないことを報告して正しく、 **sysadmin**ロールで、ユーザーがある同じ場合でもアクセス許可です。  
  
## <a name="related-functions"></a>関連する関数  
 現在のユーザーが指定された Windows グループのメンバーであるかどうかを確認するのにまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース ロールを使用して[IS_MEMBER (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/is-member-transact-sql.md). 確認するかどうか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインがデータベース ロールのメンバーを使用して[IS_ROLEMEMBER (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/is-rolemember-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 サーバー ロールに対する VIEW DEFINITION 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のユーザーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインが固定サーバー ロール `sysadmin` のメンバーであるかどうかを示しています。  
  
```  
IF IS_SRVROLEMEMBER ('sysadmin') = 1  
   print 'Current user''s login is a member of the sysadmin role'  
ELSE IF IS_SRVROLEMEMBER ('sysadmin') = 0  
   print 'Current user''s login is NOT a member of the sysadmin role'  
ELSE IF IS_SRVROLEMEMBER ('sysadmin') IS NULL  
   print 'ERROR: The server role specified is not valid.';  
```  
  
 次の例では、ドメイン ログイン Pat のメンバーであるかどうかを示す、 **diskadmin**固定サーバー ロール。  
  
```  
SELECT IS_SRVROLEMEMBER('diskadmin', 'Contoso\Pat');  
```  
  
## <a name="see-also"></a>参照  
 [IS_MEMBER & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/is-member-transact-sql.md)   
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  

