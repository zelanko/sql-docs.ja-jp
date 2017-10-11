---
title: "SUSER_SNAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUSER_SNAME_TSQL
- SUSER_SNAME
dev_langs:
- TSQL
helpviewer_keywords:
- security identification names [SQL Server]
- logins [SQL Server], users
- SIDs [SQL Server]
- SUSER_SNAME function
- users [SQL Server], logins
- logins [SQL Server], names
- IDs [SQL Server], logins
- identification numbers [SQL Server], logins
- names [SQL Server], logins
ms.assetid: 11ec7d86-d429-4004-a436-da25df9f8761
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 35e3429d49940cd863cd04fc336226268ddf61c9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="susersname-transact-sql"></a>SUSER_SNAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  セキュリティ ID 番号 (SID) に関連付けられているログイン名を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SUSER_SNAME ( [ server_user_sid ] )   
```  
  
## <a name="arguments"></a>引数  
 *server_user_sid*  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 ログイン名のセキュリティ ID 番号を指定します (省略可能)。 *server_user_sid*は**varbinary (85)**です。 *server_user_sid*任意のセキュリティ識別番号を指定できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインまたは[!INCLUDE[msCoName](../../includes/msconame-md.md)]Windows ユーザーまたはグループ。 場合*server_user_sid*が指定されていない、現在のユーザーに関する情報が返されます。 パラメーターに "NULL" という語が含まれていると、NULL が返されます。  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar (128)**  
  
## <a name="remarks"></a>解説  
 SUSER_SNAME は、ALTER TABLE または CREATE TABLE の中で、DEFAULT 制約として使用できます。 SUSER_SNAME は、選択リストの中、WHERE 句の中、また、式を使える所ならどこにでも使用できます。 SUSER_SNAME の後には、パラメーターを指定しない場合も含め、常にかっこが必要です。  
  
 SUSER_SNAME を引数なしで呼び出すと、現在のセキュリティ コンテキストの名前が返されます。 EXECUTE AS を使用してコンテキストを切り替えたバッチ内で SUSER_SNAME を引数なしで呼び出すと、権限を借用したコンテキストの名前が返されます。 権限を借用したコンテキストから ORIGINAL_LOGIN を呼び出すと、元のコンテキストの名前が返されます。  
  
## <a name="includesssdsfullincludessssdsfull-mdmd-remarks"></a>[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]「解説」  
 SUSER_NAME では、常に現在のセキュリティ コンテキストのログイン名が返されます。  
  
 SUSER_SNAME ステートメントでは、EXECUTE AS で借用したセキュリティ コンテキストを使用した実行がサポートされません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-susersname"></a>A. SUSER_SNAME を使用する  
 次の例では、現在のセキュリティ コンテキストのログイン名が返されます。  
  
```  
SELECT SUSER_SNAME();  
GO  
```  
  
### <a name="b-using-susersname-with-a-windows-user-security-id"></a>B. SUSER_SNAME を Windows ユーザーのセキュリティ ID と共に使用する  
 次の例では、Windows セキュリティ ID 番号に関連付けられているログイン名が返されます。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SNAME(0x010500000000000515000000a065cf7e784b9b5fe77c87705a2e0000);  
GO  
```  
  
### <a name="c-using-susersname-as-a-default-constraint"></a>C. SUSER_SNAME を DEFAULT 制約として使用する  
 次の例では、`SUSER_SNAME` ステートメントで `DEFAULT` を `CREATE TABLE` 制約として使用しています。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE sname_example  
(  
login_sname sysname DEFAULT SUSER_SNAME(),  
employee_id uniqueidentifier DEFAULT NEWID(),  
login_date  datetime DEFAULT GETDATE()  
);   
GO  
INSERT sname_example DEFAULT VALUES;  
GO  
```  
  
### <a name="d-calling-susersname-in-combination-with-execute-as"></a>D. SUSER_SNAME を EXECUTE AS と組み合わせて呼び出す  
 次の例は、権限を借用したコンテキストから呼び出した場合の SUSER_SNAME の動作を示しています。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SNAME();  
GO  
EXECUTE AS LOGIN = 'WanidaBenShoof';  
SELECT SUSER_SNAME();  
REVERT;  
GO  
SELECT SUSER_SNAME();  
GO  
  
```  
  
 結果を次に示します。  
  
 ```
sa  
WanidaBenShoof  
sa
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-susersname"></a>E. SUSER_SNAME を使用する  
 次の例では、セキュリティ ID 番号が `0x01` のログイン名を返します。  
  
```  
SELECT SUSER_SNAME(0x01);  
GO  
```  
  
### <a name="f-returning-the-current-login"></a>F. 現在のログインを返す  
 次の例では、現在のログインのログイン名を返します。  
  
```  
SELECT SUSER_SNAME() AS CurrentLogin;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SUSER_SID & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/suser-sid-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [実行 AS (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/execute-as-transact-sql.md)  
  
  


