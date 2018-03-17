---
title: APPLOCK_TEST (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f4009a151873bf989a39bc4fb91ec3a9963af9f2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="applocktest-transact-sql"></a>APPLOCK_TEST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

ロックを取得せずに指定されたロック所有者の特定のアプリケーション リソースのロックを許可できるかどうかについての情報を返します。 APPLOCK_TEST はアプリケーション ロック関数であり、現在のデータベース上で動作します。 アプリケーション ロックのスコープはデータベースです。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
APPLOCK_TEST ( 'database_principal' , 'resource_name' , 'lock_mode' , 'lock_owner' )  
```  
  
## <a name="arguments"></a>引数  
**'** *database_principal* **'**  
データベース内のオブジェクトに対する権限を許可されるユーザー、ロール、またはアプリケーション ロールです。 関数を呼び出すには、*database_principal*、**dbo**、または固定データベース ロール **db_owner** のメンバーであることが必要です。
  
**'** *resource_name* **'**  
クライアント アプリケーションによって指定されたロック リソース名を指定します。 アプリケーション側で、リソースが一意になるように管理しなければなりません。 指定した名前は内部的にハッシュされ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ロック マネージャーに格納できる値に変換されます。 *resource_name*は **nvarchar (255**) 既定値はありません。 *resource_name* はバイナリ比較し、現在のデータベースの照合順序の設定に関係なく大文字小文字を区別します。
  
**'** *lock_mode* **'**  
特定のリソースに対して取得されるロック モードを指定します。 *lock_mode* は **nvarchar (32)** 、既定値はありません。 **Shared**、**Update**、**IntentShared**、**IntentExclusive**、**Exclusive** のいずれかの値をとります。
  
**'** *lock_owner* **'**  
ロックの所有者を指定します。これはロックが要求されたときの *lock_owner* 値です。 *lock_owner* は **nvarchar (32)**です。 この値は **Transaction** (既定値) または **Session** のいずれかです。 既定値または **Transaction** を明示的に指定した場合、APPLOCK_TEST はトランザクション内から実行する必要があります。
  
## <a name="return-types"></a>戻り値の型
**smallint**
  
## <a name="return-value"></a>戻り値
指定された所有者にロックを許可できない場合は 0 を、ロックを許可できる場合は 1 を返します。
  
## <a name="function-properties"></a>関数のプロパティ
**非決定的**
  
**インデックス不可**
  
**並列不可**
  
## <a name="examples"></a>使用例  
次の例では、2 人のユーザー (**ユーザー A** と**ユーザー B**) の次のシーケンスを実行する個別のセッションで [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントです。
  
**ユーザー A** が次のステートメントを実行します。
  
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
  
次に、**ユーザー B** が次のステートメントを実行します。
  
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
  
次に、**ユーザー A** が次のステートメントを実行します。
  
```sql
EXEC sp_releaseapplock @Resource='Form1', @DbPrincipal='public';  
GO  
```  
  
次に、**ユーザー B** が次のステートメントを実行します。
  
```sql
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: '1' (The lock is grantable.)  
GO  
```  
  
次に、**ユーザー A** と**ユーザー B** の両方が次のステートメントを実行します。
  
```sql
COMMIT TRAN;  
GO  
```  
  
## <a name="see-also"></a>参照
[APPLOCK_MODE &#40;Transact-SQL&#41;](../../t-sql/functions/applock-mode-transact-sql.md)  
[sp_getapplock (&) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
[sp_releaseapplock (&) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)
  
  
