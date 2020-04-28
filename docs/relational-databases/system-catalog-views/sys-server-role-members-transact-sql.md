---
title: server_role_members (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_role_members
- sys.server_role_members_TSQL
- server_role_members_TSQL
- sys.server_role_members
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_role_members catalog view
ms.assetid: efa20414-2c6b-45a2-a7a9-60110a24da18
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 11f39b29817716799ec693d6161135010c35a233
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68133034"
---
# <a name="sysserver_role_members-transact-sql"></a>sys.server_role_members (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  固定サーバー ロールおよびユーザー定義サーバー ロールのメンバーごとに 1 行のデータを返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**role_principal_id**|**int**|ロールのサーバー プリンシパル ID。|  
|**member_principal_id**|**int**|メンバーのサーバー プリンシパル ID。|  
  
 サーバーロールのメンバーシップを追加または削除するには、 [ALTER SERVER role &#40;transact-sql&#41;](../../t-sql/statements/alter-server-role-transact-sql.md)ステートメントを使用します。  
  
## <a name="permissions"></a>アクセス許可  
 ログインでは、独自のサーバーロールのメンバーシップを表示でき、固定サーバーロールのメンバーの principal_id を表示できます。 すべてのサーバーロールのメンバーシップを表示するには、 **VIEW DEFINITION ON SERVER role**権限、または**securityadmin**固定サーバーロールのメンバーシップが必要です。  
  
  詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例では、ロールとそのメンバーの名前と id を返します。  
  
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
 [Transact-sql&#41;&#40;カタログビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [セキュリティカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [サーバーレベルのロール](../../relational-databases/security/authentication-access/server-level-roles.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
