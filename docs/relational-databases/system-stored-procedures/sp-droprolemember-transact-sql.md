---
title: sp_droprolemember (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droprolemember_TSQL
- sp_droprolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droprolemember
ms.assetid: c2f19ab1-e742-4d56-ba8e-8ffd40cf4925
ms.author: vanto
author: VanMSFT
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8be7e84ccd80d80c1345adec3450e5bc8e0f4da6
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012701"
---
# <a name="sp_droprolemember-transact-sql"></a>sp_droprolemember (Transact-SQL)

[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  現在のデータベースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ロールからセキュリティ アカウントを削除します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに[ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md)を使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  

### <a name="syntax-for-both-sql-server-and-azure-sql-database"></a>SQL Server と Azure SQL Database の両方の構文

```  
sp_droprolemember [ @rolename = ] 'role' ,   
     [ @membername = ] 'security_account'  
```  

### <a name="syntax-for-both-azure-sql-data-warehouse-and-parallel-data-warehouse"></a>Azure SQL Data Warehouse と並列データウェアハウスの両方の構文

```  
sp_droprolemember 'role' ,  
     'security_account'  
```  
  
## <a name="arguments"></a>引数  
`[ @rolename = ] 'role'`メンバーを削除するロールの名前を指定します。 *role*の型は**sysname**で、既定値はありません。 *ロール*は現在のデータベースに存在している必要があります。  
  
`[ @membername = ] 'security_account'`ロールから削除するセキュリティアカウントの名前を指定します。 *security_account*は**sysname**であり、既定値はありません。 *security_account*には、データベースユーザー、別のデータベースロール、windows ログイン、または windows グループを指定できます。 *security_account*は、現在のデータベースに存在している必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 sp_droprolemember は、sysmembers テーブルから行を削除することにより、データベース ロールからメンバーを削除します。 メンバーがロールから削除されると、メンバーはそのロールのメンバーシップによって与えられた権限を失います。  
  
 ユーザーを固定サーバー ロールから削除するには、sp_dropsrvrolemember を使用します。 public ロールからユーザーを削除することはできません。また、どのロールからも dbo は削除できません。  
  
 ロールのメンバーを表示するには sp_helpuser を使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] し、ロールにメンバーを追加するには ALTER role を使用します。  
  
## <a name="permissions"></a>アクセス許可  
 ロールに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>例  
 次の例では、ロール `JonB` からユーザー `Sales` を削除します。  
  
```sql
EXEC sp_droprolemember 'Sales', 'Jonb';  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、ロール `JonB` からユーザー `Sales` を削除します。  
  
```sql
EXEC sp_droprolemember 'Sales', 'JonB'  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpuser &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

