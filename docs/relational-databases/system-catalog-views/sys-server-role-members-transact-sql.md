---
title: "sys.server_role_members (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- server_role_members
- sys.server_role_members_TSQL
- server_role_members_TSQL
- sys.server_role_members
dev_langs: TSQL
helpviewer_keywords: sys.server_role_members catalog view
ms.assetid: efa20414-2c6b-45a2-a7a9-60110a24da18
caps.latest.revision: "31"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: dd26b9ea6419e17df0e318fbffeaeee958c0c501
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysserverrolemembers-transact-sql"></a>sys.server_role_members (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  固定サーバー ロールおよびユーザー定義サーバー ロールのメンバーごとに 1 行のデータを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**role_principal_id**|**int**|ロールのサーバー プリンシパル ID。|  
|**member_principal_id**|**int**|メンバーのサーバー プリンシパル ID。|  
  
 を追加またはサーバー ロールのメンバーシップを削除するには、 [ALTER SERVER ROLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-role-transact-sql.md)ステートメントです。  
  
## <a name="permissions"></a>Permissions  
 ログインは、自身のサーバー ロール メンバーシップを表示できます。また、固定サーバー ロールのメンバーの principal_id を表示できます。 すべてのサーバー ロールのメンバーシップを表示する必要があります、 **VIEW DEFINITION ON SERVER ROLE**権限またはメンバーシップ、 **securityadmin**固定サーバー ロール。  
  
 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例では、ロールおよびそのメンバーの名前と ID を返します。  
  
```  
SELECT sys.server_role_members.role_principal_id, role.name AS RoleName,   
    sys.server_role_members.member_principal_id, member.name AS MemberName  
FROM sys.server_role_members  
JOIN sys.server_principals AS role  
    ON sys.server_role_members.role_principal_id = role.principal_id  
JOIN sys.server_principals AS member  
    ON sys.server_role_members.member_principal_id = member.principal_id;  
```  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [サーバー レベルのロール](../../relational-databases/security/authentication-access/server-level-roles.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
