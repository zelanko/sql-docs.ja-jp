---
title: "APPLOCK_TEST (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- APPLOCK_TEST_TSQL
- APPLOCK_TEST
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], applications
- APPLOCK_TEST function
- applications [SQL Server], locks
- sessions [SQL Server], application locks
- testing application locks
ms.assetid: 4ea33d04-f8e9-46ff-ae61-985bd3eaca2c
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a272abaccb41653c9b1b0569738b74905e93e5c9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="applocktest-transact-sql"></a>APPLOCK_TEST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

ロックを取得せずに指定されたロック所有者の特定のアプリケーション リソースのロックを許可できるかどうかについての情報を返します。 APPLOCK_TEST はアプリケーション ロック関数であり、現在のデータベース上で動作します。 アプリケーション ロックのスコープはデータベースです。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
APPLOCK_TEST ( 'database_principal' , 'resource_name' , 'lock_mode' , 'lock_owner' )  
```  
  
## <a name="arguments"></a>引数  
**'** *database_principal* **'**  
データベース内のオブジェクトに対する権限を許可されるユーザー、ロール、またはアプリケーション ロールです。 関数の呼び出し元のメンバーである必要があります*database_principal*、 **dbo**、または**db_owner**関数を正常に呼び出すために、固定データベース ロール。
  
**'** *resource_name* **'**  
クライアント アプリケーションによって指定されたロック リソース名を指定します。 アプリケーション側で、リソースが一意になるように管理しなければなりません。 指定した名前は内部的にハッシュされ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ロック マネージャーに格納できる値に変換されます。 *resource_name*は**nvarchar (255)**既定値はありません。 *resource_name*はバイナリ比較は、現在のデータベースの照合順序の設定に関係なく大文字小文字が区別されます。
  
**'** *lock_mode* **'**  
特定のリソースに対して取得されるロック モードを指定します。 *lock_mode*は**nvarchar (32)**既定値はありません。 値は、次のいずれかを指定できます: **Shared**、**更新**、 **IntentShared**、 **IntentExclusive**、**排他**.
  
**'** *lock_owner* **'**  
これは、ロックの所有者である、 *lock_owner*ロックが要求されたときの値します。 *lock_owner*は**nvarchar (32)**です。 値を指定できます**トランザクション**(既定) または**セッション**です。 場合は既定値または**トランザクション**が明示的に指定されて、APPLOCK_TEST は、トランザクション内から実行する必要があります。
  
## <a name="return-types"></a>戻り値の型
**smallint**
  
## <a name="return-value"></a>戻り値
指定された所有者にロックを許可できない場合は 0 を、ロックを許可できる場合は 1 を返します。
  
## <a name="function-properties"></a>関数のプロパティ
**非決定的**
  
**Nonindexable**
  
**Nonparallelizable**
  
## <a name="examples"></a>使用例  
次の例では、2 人のユーザー (**ユーザー A**と**ユーザー B**) の次のシーケンスを実行する個別のセッションで[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。
  
**ユーザー A**を実行します。
  
```sql
USE AdventureWorks2012;  
GO  
BEGIN TRAN;  
DECLARE @result int;  
EXEC @result=sp_getapplock  
    @DbPrincipal='public',  
    @Resource='Form1',  
    @LockMode='Shared',  
    @LockOwner='Transaction';  
SELECT APPLOCK_MODE('public', 'Form1', 'Transaction');  
GO  
```  
  
**ユーザー B**が実行されます。
  
```sql
Use AdventureWorks2012;  
GO  
BEGIN TRAN;  
SELECT APPLOCK_MODE('public', 'Form1', 'Transaction');  
--Result set: NoLock  
  
SELECT APPLOCK_TEST('public', 'Form1', 'Shared', 'Transaction');  
--Result set: 1 (Lock is grantable.)  
  
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: 0 (Lock is not grantable.)  
GO  
```  
  
**ユーザー A**が実行されます。
  
```sql
EXEC sp_releaseapplock @Resource='Form1', @DbPrincipal='public';  
GO  
```  
  
**ユーザー B**が実行されます。
  
```sql
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: '1' (The lock is grantable.)  
GO  
```  
  
**ユーザー A**と**ユーザー B**し、両方を実行します。
  
```sql
COMMIT TRAN;  
GO  
```  
  
## <a name="see-also"></a>参照
[APPLOCK_MODE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/applock-mode-transact-sql.md)  
[sp_getapplock & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
[sp_releaseapplock & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)
  
  

