---
title: "CURRENT_USER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
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
- CURRENT_USER
- CURRENT_USER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- usernames [SQL Server]
- current user names
- niladic functions
- CURRENT_USER
- users [SQL Server], names
ms.assetid: 29248949-325b-4063-9f55-5a445fb35c6e
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 7fbb100c34c2a8b1b33a585cb5ead6aaca56f0d8
ms.contentlocale: ja-jp
ms.lasthandoff: 10/17/2017

---
# <a name="currentuser-transact-sql"></a>CURRENT_USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

現在のユーザーの名前を返します。 この関数を実行すると、USER_NAME() と同じ結果が得られます。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
CURRENT_USER  
```  

## <a name="return-types"></a>戻り値の型
**sysname**
  
## <a name="remarks"></a>解説  
CURRENT_USER では、現在のセキュリティ コンテキストの名前が返されます。 EXECUTE AS への呼び出しでコンテキストが切り替えられた後に CURRENT_USER を実行した場合、CURRENT_USER では権限を借用したコンテキストの名前が返されます。 Windows プリンシパルには、グループのメンバーシップを使用して、データベースがアクセスした場合は、グループの名前ではなく Windows プリンシパルの名前が返されます。
  
現在のユーザーのログインを返すを参照してください[SUSER_NAME (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/suser-name-transact-sql.md)と[SYSTEM_USER (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/system-user-transact-sql.md).
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-currentuser-to-return-the-current-user-name"></a>A. CURRENT_USER を使用して現在のユーザー名を返す  
次の例では、現在のユーザー名を返します。
  
```sql
SELECT CURRENT_USER;  
GO  
```  
  
### <a name="b-using-currentuser-as-a-default-constraint"></a>B. DEFAULT 制約として CURRENT_USER を使用する  
次の例を使用するテーブルを作成する`CURRENT_USER`として、`DEFAULT`の制約、 `order_person` sales 行の列です。
  
```sql
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
      WHERE TABLE_NAME = 'orders22')  
   DROP TABLE orders22;  
GO  
SET NOCOUNT ON;  
CREATE TABLE orders22  
(  
order_id int IDENTITY(1000, 1) NOT NULL,
cust_id  int NOT NULL,
order_date smalldatetime NOT NULL DEFAULT GETDATE(),
order_amt money NOT NULL,
order_person char(30) NOT NULL DEFAULT CURRENT_USER
);  
GO  
```  
  
次のコードでは、テーブルにレコードを挿入します。 これらのステートメントを実行するユーザーは `Wanida` です。
  
```sql
INSERT orders22 (cust_id, order_amt)  
VALUES (5105, 577.95);  
GO  
SET NOCOUNT OFF;  
GO  
```  
  
次のクエリでは、`orders22` テーブルからすべての情報を選択します。
  
```sql
SELECT * FROM orders22;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
order_id    cust_id     order_date           order_amt    order_person
----------- ----------- -------------------- ------------ ------------
1000        5105        2005-04-03 23:34:00  577.95       Wanida
  
(1 row(s) affected)
```
  
### <a name="c-using-currentuser-from-an-impersonated-context"></a>C. 権限を借用したコンテキストから CURRENT_USER を使用する  
次の例では、ユーザー `Wanida` として次の [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行します。
  
```sql
SELECT CURRENT_USER;  
GO  
EXECUTE AS USER = 'Arnalfo';  
GO  
SELECT CURRENT_USER;  
GO  
REVERT;  
GO  
SELECT CURRENT_USER;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Wanida
Arnalfo
Wanida
```
  
## <a name="see-also"></a>参照
[USER_NAME & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/user-name-transact-sql.md)  
[SYSTEM_USER & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/system-user-transact-sql.md)  
[sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[システム関数 & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/system-functions-for-transact-sql.md)
  
  


