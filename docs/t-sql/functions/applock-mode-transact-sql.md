---
title: "APPLOCK_MODE (TRANSACT-SQL) |Microsoft ドキュメント"
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
- APPLOCK_MODE_TSQL
- APPLOCK_MODE
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], applications
- applications [SQL Server], locks
- sessions [SQL Server], application locks
- APPLOCK_MODE function
ms.assetid: e43d4917-77f1-45cc-b231-68ba7fee3385
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ceec0a5465187e1b470bd9eb8b1039a5b3d60aae
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="applockmode-transact-sql"></a>APPLOCK_MODE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

特定のアプリケーション リソースで、ロック所有者によって保持されているロック モードを返します。 APPLOCK_MODE はアプリケーション ロック関数であり、現在のデータベースで動作します。 アプリケーション ロックのスコープはデータベースです。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
APPLOCK_MODE( 'database_principal' , 'resource_name' , 'lock_owner' )  
```  
  
## <a name="arguments"></a>引数  
'*database_principal*'  
データベース内のオブジェクトに対する権限を許可されるユーザー、ロール、またはアプリケーション ロールです。 関数の呼び出し元のメンバーである必要があります*database_principal*、関数を呼び出すに dbo、または db_owner 固定データベース ロール。
  
'*resource_name*'  
クライアント アプリケーションによって指定されたロック リソース名を指定します。 アプリケーション側では、リソース名が一意になるよう管理されている必要があります。 指定した名前は内部的にハッシュされ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ロック マネージャーに格納できる値に変換されます。 *resource_name*は**nvarchar (255)**既定値はありません。 *resource_name*はバイナリ比較し、現在のデータベースの照合順序の設定に関係なく大文字小文字を区別します。
  
'*lock_owner*'  
これは、ロックの所有者である、 *lock_owner*ロックが要求されたときの値します。 *lock_owner*は**nvarchar (32)**、値は、いずれかを指定できます**トランザクション**(既定) または**セッション**です。
  
## <a name="return-types"></a>戻り値の型
**nvarchar (32)**
  
## <a name="return-value"></a>戻り値
特定のアプリケーション リソースで、ロック所有者によって保持されているロック モードを返します。 ロック モードは次のいずれかの値になります。
  
||||  
|-|-|-|  
|**NoLock**|**Update**|**\*SharedIntentExclusive**|  
|**IntentShared**|**IntentExclusive**|**\*UpdateIntentExclusive**|  
|**共有**|**[Exclusive]**||  
  
* このロック モードは他のロック モードの組み合わせであり、sp_getapplock を使用して明示的に取得することはできません。
  
## <a name="function-properties"></a>関数のプロパティ
**非決定的**
  
**Nonindexable**
  
**Nonparallelizable**
  
## <a name="examples"></a>使用例  
次の例では、個別にセッションを開いている 2 人のユーザー (ユーザー A とユーザー B) が、一連の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行します。
  
ユーザー A が次のステートメントを実行します。
  
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
  
次に、ユーザー B が次のステートメントを実行します。
  
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
  
次に、ユーザー A が次のステートメントを実行します。
  
```sql
EXEC sp_releaseapplock @Resource='Form1', @DbPrincipal='public';  
GO  
```  
  
次に、ユーザー B が次のステートメントを実行します。
  
```sql
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: '1' (The lock is grantable.)  
GO  
```  
  
次に、ユーザー A とユーザー B が次のステートメントを実行します。
  
```sql
COMMIT TRAN;  
GO  
```  
  
## <a name="see-also"></a>参照
[APPLOCK_TEST & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/applock-test-transact-sql.md)  
[sp_getapplock & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
[sp_releaseapplock & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)
  
  

