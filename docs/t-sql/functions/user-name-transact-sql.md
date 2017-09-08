---
title: "USER_NAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- USER_NAME
- USER_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- usernames [SQL Server]
- IDs [SQL Server], databases
- USER_NAME function
- users [SQL Server], database username
- names [SQL Server], database users
- identification numbers [SQL Server], databases
- database usernames [SQL Server]
ms.assetid: ab32d644-4228-449a-9ef0-5a975c305775
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5179a5d031dbc654f1624f4d64c3e94bf28efe40
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="username-transact-sql"></a>USER_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定した識別番号から、データベース ユーザー名を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
USER_NAME ( [ id ] )  
```  
  
## <a name="arguments"></a>引数  
 *id*  
 データベース ユーザーに関連付けられている識別番号を指定します。 *id*は**int**です。かっこで囲む必要があります。  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar (256)**  
  
## <a name="remarks"></a>解説  
 ときに*id*は省略すると、現在のコンテキストで現在のユーザーが想定されます。 場合は、パラメーターには、NULL は NULL を返しますという単語が含まれています。指定せずに USER_NAME を呼び出したときに、 *id*実行後にステートメントとして USER_NAME が権限を借用したユーザーの名前を返します。 場合は、Windows プリンシパルをアクセスすると、グループのメンバーシップを使用して、データベース、ユーザー名の名前を返します、Windows グループではなくプリンシパル。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-username"></a>A. USER_NAME を使用する  
 次の例では、ユーザー ID `13` のユーザー名を返します。  
  
```  
SELECT USER_NAME(13);  
GO  
```  
  
### <a name="b-using-username-without-an-id"></a>B. ID を指定せずに USER_NAME を使用する  
 次の例では、ID を指定せずに、現在のユーザーの名前を検索します。  
  
```  
SELECT USER_NAME();  
GO  
```  
  
 次に、ユーザーが sysadmin 固定サーバー ロールのメンバーである場合の結果セットを示します。  
  
 `------------------------------`  
  
 `dbo`  
  
 `(1 row(s) affected)`  
  
### <a name="c-using-username-in-the-where-clause"></a>C. WHERE 句で USER_NAME を使用する  
 次の例では、`sysusers` の行を検索します。検索される名前は、ユーザー識別番号 `USER_NAME` に対してシステム関数 `1` を適用した結果と同じになります。  
  
```  
SELECT name FROM sysusers WHERE name = USER_NAME(1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `name`  
  
 `------------------------------`  
  
 `dbo`  
  
 `(1 row(s) affected)`  
  
### <a name="d-calling-username-during-impersonation-with-execute-as"></a>D. EXECUTE AS での権限借用中に USER_NAME を呼び出す  
 例を次にどのように`USER_NAME`権限借用中に動作します。  
  
```  
SELECT USER_NAME();  
GO  
EXECUTE AS USER = 'Zelig';  
GO  
SELECT USER_NAME();  
GO  
REVERT;  
GO  
SELECT USER_NAME();  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DBO`  
  
 `Zelig`  
  
 `DBO`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-username"></a>E. USER_NAME を使用する  
 次の例では、ユーザー ID `13` のユーザー名を返します。  
  
```  
SELECT USER_NAME(13);  
```  
  
### <a name="f-using-username-without-an-id"></a>F. ID を指定せずに USER_NAME を使用する  
 次の例では、ID を指定せずに、現在のユーザーの名前を検索します。  
  
```  
SELECT USER_NAME();  
```  
  
 現在のログイン ユーザーの結果セットを次に示します。  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------------------------------   
User7                              
```  
  
### <a name="g-using-username-in-the-where-clause"></a>G. WHERE 句で USER_NAME を使用する  
 次の例では、`sysusers` の行を検索します。検索される名前は、ユーザー識別番号 `USER_NAME` に対してシステム関数 `1` を適用した結果と同じになります。  
  
```  
SELECT name FROM sysusers WHERE name = USER_NAME(1);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
name                             
------------------------------   
User7                              
```  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CURRENT_TIMESTAMP & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/current-timestamp-transact-sql.md)   
 [CURRENT_USER と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/current-user-transact-sql.md)   
 [SESSION_USER と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/session-user-transact-sql.md)   
 [システム関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [SYSTEM_USER & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/system-user-transact-sql.md)  
  
  


