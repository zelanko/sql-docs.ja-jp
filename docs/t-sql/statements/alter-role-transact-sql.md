---
title: "ALTER ロール (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_ROLE_TSQL
- ALTER ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- modifying database roles
- ALTER ROLE statement
- renaming database roles
- database roles [SQL Server], modifying
- names [SQL Server], database roles
ms.assetid: e1e83caa-17cc-4871-b2db-2711339fb64f
caps.latest.revision: 64
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3eaee2d346eda964545caa60cd7168b531f47ad9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-role-transact-sql"></a>ALTER ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  追加またはデータベース ロールのメンバーを削除するか、ユーザー定義データベース ロールの名前を変更します。  
  
> [!NOTE]  
>  内のロールを変更する[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]を使用して[sp_addrolemember & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)と[sp_droprolemember & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server (starting with 2012) and Azure SQL Database  
  
ALTER ROLE  role_name  
{  
       ADD MEMBER database_principal  
    |  DROP MEMBER database_principal  
    |  WITH NAME = new_name  
}  
[;]  
```  
  
 
```  
-- Syntax for SQL Server 2008 only  
  
-- Change the name of a user-defined database role  
ALTER ROLE role_name   
    WITH NAME = new_name  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *role_name*  
 **適用対象:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (2008 以降)  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 変更するデータベース ロールを指定します。  
  
 メンバーの追加*database_principal*l  
 **適用対象:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (2012 以降)  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 データベース ロールのメンバーシップをデータベース プリンシパルを追加するように指定します。  
  
-   *database_principal*がデータベース ユーザーまたはユーザー定義データベース ロール。  
  
-   *database_principal*固定データベース ロールまたはサーバー プリンシパルにすることはできません。  
  
DROP MEMBER *database_principal*  
 **適用対象:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (2012 以降)  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 データベース ロールのメンバーシップから、データベース プリンシパルを削除するように指定します。  
  
-   *database_principal*がデータベース ユーザーまたはユーザー定義データベース ロール。  
  
-   *database_principal*固定データベース ロールまたはサーバー プリンシパルにすることはできません。  
  
NAME = *new_name*  
 **適用対象:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (2008 以降)  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
 ユーザー定義データベース ロールの名前を変更することを指定します。 新しい名前は、データベースに既に存在する必要があります。  
  
 データベース ロールの名前を変更しても、ロールの ID 番号、所有者、権限は変わりません。  
  
## <a name="permissions"></a>Permissions  
 このコマンドを実行するには、1 つ以上のこれらの権限またはメンバーシップが必要。  
  
-   **ALTER**ロールに対する権限  
-   **ALTER ANY ROLE**データベースに対する権限  
-   メンバーシップ、 **db_securityadmin**固定データベース ロール  
  
さらに、固定データベース ロールのメンバーシップを変更する必要があります。  
  
-   メンバーシップ、 **db_owner**固定データベース ロール  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 固定データベース ロールの名前を変更することはできません。  
  
## <a name="metadata"></a>メタデータ  
 これらのシステム ビューは、データベース ロールとデータベース プリンシパルに関する情報を格納します。  
  
-   [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)  
  
-   [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
## <a name="examples"></a>使用例  
  
### <a name="a-change-the-name-of-a-database-role"></a>A. データベース ロールの名前を変更します。  
 **適用対象:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (2008 以降)  [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
 次の例は、ロールの名前を変更`buyers`に`purchasing`です。 [!INCLUDE[AdWorks-example](../../includes/adworks-example-md.md)]  
  
```tsql  
ALTER ROLE buyers WITH NAME = purchasing;  
```  
  
### <a name="b-add-or-remove-role-members"></a>B. 追加またはロールのメンバーを削除します。  
 **適用対象:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (2012 以降)  [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
 この例は、という名前のデータベース ロールを作成`Sales`です。 メンバーシップ、Barry をという名前のデータベース ユーザーを追加し、Barry のメンバーを削除する方法を示します。 [!INCLUDE[AdWorks-example](../../includes/adworks-example-md.md)]  
  
```tsql  
CREATE ROLE Sales;  
ALTER ROLE Sales ADD MEMBER Barry;  
ALTER ROLE Sales DROP MEMBER Barry;  
```  
  
## <a name="see-also"></a>参照  
 [ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-role-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [DROP ROLE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-role-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  

