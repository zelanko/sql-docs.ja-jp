---
title: "ロール (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE ROLE
- DATABASE ROLE
- ROLE_TSQL
- DATABASE_ROLE_TSQL
- CREATE_ROLE_TSQL
- CREATE DATABASE ROLE
- ROLE
- CREATE_DATABASE_ROLE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- database roles [SQL Server], creating
- CREATE DATABASE ROLE statement
- roles [SQL Server], creating
- CREATE ROLE statement
ms.assetid: b0cd54ad-e81d-4d71-acec-8a6d7261ca08
caps.latest.revision: "54"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: cccfc9f6f9810d8f674ea32858e08683160b2ef1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="create-role-transact-sql"></a>CREATE ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースに新しいデータベース ロールを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE ROLE role_name [ AUTHORIZATION owner_name ]  
```  
  
## <a name="arguments"></a>引数  
 *role_name*  
 作成するロールの名前を指定します。  
  
 承認*owner_name*  
 新しいロールを所有するデータベース ユーザーまたはロールを指定します。 ユーザーを指定しない場合、ロールは CREATE ROLE を実行するユーザーが所有します。  
  
## <a name="remarks"></a>解説  
 ロールはデータベース レベルのセキュリティ保護可能なリソースです。 ロールを作成した後は、GRANT、DENY、および REVOKE を使って、ロールのデータベース レベルの権限を構成します。 データベース ロールにメンバーを追加するには、使用[ALTER ROLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-role-transact-sql.md). 詳細については、次を参照してください。[データベース レベルのロール](../../relational-databases/security/authentication-access/database-level-roles.md)です。  
  
 データベース ロールは、sys.database_role_members および sys.database_principals カタログ ビューで確認できます。  
  
 権限システムの設計の詳細については、「 [データベース エンジンの権限の概要](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)」を参照してください。  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 必要があります**CREATE ROLE**メンバーシップまたはデータベースに対する権限、 **db_securityadmin**固定データベース ロール。 使用すると、**承認**オプションでは、次のアクセス許可も必要です。  
  
-   ロールの所有権を別のユーザーに割り当てるには、そのユーザーに対する IMPERSONATE 権限が必要です。  
  
-   ロールの所有権を別のロールに割り当てるには、割り当て先のロールのメンバーシップまたはそのロールに対する ALTER 権限が必要です。  
  
-   ロールの所有権をアプリケーション ロールに割り当てるには、アプリケーション ロールに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
すべての次の例では、AdventureWorks データベースを使用します。   

### <a name="a-creating-a-database-role-that-is-owned-by-a-database-user"></a>A. データベース ユーザーが所有するデータベース ロールを作成する  
 次の例は、データベース ロールを作成`buyers`ユーザーによって所有されている`BenMiller`です。  
  
```  
CREATE ROLE buyers AUTHORIZATION BenMiller;  
GO  
```  
  
### <a name="b-creating-a-database-role-that-is-owned-by-a-fixed-database-role"></a>B. 固定データベース ロールが所有するデータベース ロールを作成する  
 次の例は、データベース ロールを作成`auditors`が所有する、`db_securityadmin`固定データベース ロール。  
  
```  
CREATE ROLE auditors AUTHORIZATION db_securityadmin;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [ALTER ROLE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-role-transact-sql.md)   
 [DROP ROLE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-role-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [データベース エンジンの権限の概要](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)  
  
  


