---
title: "ORIGINAL_LOGIN (TRANSACT-SQL) |Microsoft ドキュメント"
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
- ORIGINAL_LOGIN_TSQL
- ORIGINAL_LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], context switches
- context switching [SQL Server], login names
- original login names [SQL Server]
- ORIGINAL_LOGIN function
- names [SQL Server], logins
ms.assetid: ddfb0991-cde3-4b97-a5b7-ee450133f160
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b1f97da47505e5c812e43f4481d9f36027bf14c9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="originallogin-transact-sql"></a>ORIGINAL_LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンスに接続したログインの名前を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 この関数を使用すると、明示的または暗黙的にコンテキストが何度も切り替えられるセッションにおける、元のログインの ID を取得できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ORIGINAL_LOGIN( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 **sysname**  
  
## <a name="remarks"></a>解説  
 この関数は、元の接続コンテキストの ID を監査するときに便利です。 一方などの関数[SESSION_USER](../../t-sql/functions/session-user-transact-sql.md)と[CURRENT_USER](../../t-sql/functions/current-user-transact-sql.md)戻り、現在実行中のコンテキスト、ORIGINAL_LOGIN を最初のインスタンスに接続したログインのidを返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、そのセッションでします。  
  
 NULL を返します[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
## <a name="examples"></a>使用例  
 次の例は、現在のセッション内のステートメントの呼び出し元からの実行コンテキストを切り替える`login1`です。 関数は、`SUSER_SNAME`と`ORIGINAL_LOGIN`現在のセッションのユーザーを返すために使用されます (コンテキストの切り替え先ユーザー) と、元のログイン アカウントです。  
  
```  
USE AdventureWorks2012;  
GO  
--Create a temporary login and user.  
CREATE LOGIN login1 WITH PASSWORD = 'J345#$)thb';  
CREATE USER user1 FOR LOGIN login1;  
GO  
--Execute a context switch to the temporary login account.  
DECLARE @original_login sysname;  
DECLARE @current_context sysname;  
EXECUTE AS LOGIN = 'login1';  
SET @original_login = ORIGINAL_LOGIN();  
SET @current_context = SUSER_SNAME();  
SELECT 'The current executing context is: '+ @current_context;  
SELECT 'The original login in this session was: '+ @original_login  
GO  
-- Return to the original execution context  
-- and remove the temporary principal.  
REVERT;  
GO  
DROP LOGIN login1;  
DROP USER user1;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [実行 AS (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/execute-as-transact-sql.md)   
 [元に戻す (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revert-transact-sql.md)  
  
  

