---
title: "ドロップ ロール (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP ROLE
- DROP_ROLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting roles
- database roles [SQL Server], removing
- removing roles
- DROP ROLE statement
- roles [SQL Server], removing
- dropping roles
ms.assetid: 1f6f13ae-56a2-4ef1-93f5-8e6151b83e1d
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 41c2caf816ca412e4a6048713dc66f97da5155ae
ms.openlocfilehash: 86266835ec5d54ce08bdf7fe18d93dd9d4de1737
ms.contentlocale: ja-jp
ms.lasthandoff: 10/07/2017

---
# <a name="drop-role-transact-sql"></a>DROP ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  データベースからロールを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
  
DROP ROLE [ IF EXISTS ] role_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP ROLE role_name  
```  
  
## <a name="arguments"></a>引数  
 *場合に存在します。*  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
 条件付きでは既に存在する場合にのみ、ロールを削除します。  
  
 *role_name*  
 データベースから削除するロールを指定します。  
  
## <a name="remarks"></a>解説  
 セキュリティ保護可能なリソースを所有するロールは、データベースから削除できません。 セキュリティ保護可能なリソースを所有するデータベース ロールを削除するには、最初に、セキュリティ保護可能なリソースの所有権を転送するか、リソースをデータベースから削除する必要があります。 メンバーを含むロールは、データベースから削除できません。 メンバーを含むロールを削除するには、最初にロールのメンバーを削除する必要があります。  
  
 データベース ロールからメンバーを削除するには使用[ALTER ROLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-role-transact-sql.md).  
  
 DROP ROLE を使用して、固定データベース ロールを削除することはできません。  
  
 ロールのメンバーシップに関する情報は、sys.database_role_members カタログ ビューで表示できます。  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
 サーバーの役割を削除する使用[DROP SERVER ROLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-server-role-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 必要があります**ALTER ANY ROLE** 、データベースに対する権限または**コントロール**メンバーシップまたはロールに対する権限、 **db_securityadmin**です。  
  
## <a name="examples"></a>使用例  
 次の例は、データベース ロールを削除`purchasing`から、`AdventureWorks2012`データベース。  
  
```  
DROP ROLE purchasing;  
GO  
```  
  
  
## <a name="see-also"></a>参照  
 [ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-role-transact-sql.md)   
 [ALTER ROLE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-role-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  



