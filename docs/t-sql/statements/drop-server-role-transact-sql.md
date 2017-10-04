---
title: "サーバー ロール (TRANSACT-SQL) を削除します |Microsoft ドキュメント"
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
- DROP SERVER ROLE
- DROP_SERVER_ROLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SERVER ROLE, DROP
- DROP SERVER ROLE statement
ms.assetid: a2a1e6e6-e40c-4d6a-81be-d197b80bf226
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5c493ed6556bde690f6b4a9ec6b46aeb3ceb59ae
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-server-role-transact-sql"></a>DROP SERVER ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-pdw-md.md)]

  ユーザー定義サーバー ロールを削除します。  
  
 ユーザー定義サーバー ロールは、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] で新しく追加されました。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DROP SERVER ROLE role_name  
```  
  
## <a name="arguments"></a>引数  
 *role_name*  
 サーバーから削除するユーザー定義サーバー ロールを指定します。  
  
## <a name="remarks"></a>解説  
 セキュリティ保護可能なリソースを所有するユーザー定義サーバー ロールは、サーバーから削除できません。 セキュリティ保護可能なリソースを所有するユーザー定義サーバー ロールを削除するには、最初に、セキュリティ保護可能なリソースの所有権を転送するか、リソースを削除する必要があります。  
  
 メンバーを含むユーザー定義サーバー ロールは削除できません。 メンバーを持つユーザー定義サーバー ロールを削除する必要がありますまず削除するロールのメンバーを使用して[ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md)です。  
  
 固定サーバー ロールは削除できません。  
  
 ロールのメンバーシップに関する情報を表示するにはクエリを実行して、 [sys.server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)カタログ ビューです。  
  
## <a name="permissions"></a>Permissions  
 サーバー ロールに対する CONTROL 権限か、ALTER ANY SERVER ROLE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-to-drop-a-server-role"></a>A. サーバー ロールを削除するには  
 次の例は、サーバーの役割を削除`purchasing`です。  
  
```  
DROP SERVER ROLE purchasing;  
GO  
```  
  
### <a name="b-to-view-role-membership"></a>B. ロールのメンバーシップを表示するには  
 表示するにはロールのメンバーシップを使用して、**サーバーの役割 (メンバー**) ページに[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]または次のクエリを実行します。  
  
```  
SELECT SRM.role_principal_id, SP.name AS Role_Name,   
SRM.member_principal_id, SP2.name  AS Member_Name  
FROM sys.server_role_members AS SRM  
JOIN sys.server_principals AS SP  
    ON SRM.Role_principal_id = SP.principal_id  
JOIN sys.server_principals AS SP2   
    ON SRM.member_principal_id = SP2.principal_id  
ORDER BY  SP.name,  SP2.name  
```  
  
### <a name="c-to-view-role-membership"></a>C. ロールのメンバーシップを表示するには  
 サーバー ロールが別のサーバー ロールを所有しているかどうかを確認するには、次のクエリを実行します。  
  
```  
SELECT SP1.name AS RoleOwner, SP2.name AS Server_Role  
FROM sys.server_principals AS SP1  
JOIN sys.server_principals AS SP2  
    ON SP1.principal_id = SP2.owning_principal_id   
ORDER BY SP1.name ;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER ROLE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-role-transact-sql.md)   
 [ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-role-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [DROP ROLE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-role-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  
