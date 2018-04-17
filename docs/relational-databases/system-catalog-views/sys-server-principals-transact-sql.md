---
title: sys.server_principals (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- server_principals
- sys.server_principals_TSQL
- sys.server_principals
- server_principals_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_principals catalog view
ms.assetid: c5dbe0d8-a1c8-4dc4-b9b1-22af20effd37
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3705caa0221d2e0f4a6b93b6d2ffffb9b2fcb9e4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysserverprincipals-transact-sql"></a>sys.server_principals (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  サーバー レベルのプリンシパルごとに 1 行のデータを格納します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|プリンシパルの名前。 サーバー内で一意です。|  
|**principal_id**|**int**|プリンシパルの ID 番号。 サーバー内で一意です。|  
|**sid**|**varbinary(85)**|プリンシパルの SID (セキュリティ識別子)。 Windows プリンシパルの場合、これは Windows SID に一致します。|  
|**type**|**char(1)**|プリンシパルの種類。<br /><br /> S = SQL ログイン<br /><br /> U = Windows ログイン<br /><br /> G = Windows グループ<br /><br /> R = サーバー ロール<br /><br /> C = 証明書にマップされるログイン<br /><br /> K = 非対称キーにマップされるログイン|  
|**type_desc**|**nvarchar(60)**|プリンシパルの種類の説明:<br /><br /> SQL_LOGIN<br /><br /> WINDOWS_LOGIN<br /><br /> WINDOWS_GROUP<br /><br /> SERVER_ROLE<br /><br /> CERTIFICATE_MAPPED_LOGIN<br /><br /> ASYMMETRIC_KEY_MAPPED_LOGIN|  
|**is_disabled**|**int**|1 = ログインは無効です。|  
|**create_date**|**datetime**|プリンシパルが作成された日時。|  
|**modify_date**|**datetime**|プリンシパルの定義が最後に変更された日時。|  
|**default_database_name**|**sysname**|プリンシパルの既定のデータベース。|  
|**default_language_name**|**sysname**|プリンシパルの既定の言語。|  
|**credential_id**|**int**|プリンシパルに関連付けられている証明書の ID。 プリンシパルに関連付けられている証明書がない場合、credential_id は NULL になります。|  
|**owning_principal_id**|**int**|**Principal_id**サーバー ロールの所有者のです。 プリンシパルがサーバー ロールでない場合は NULL です。|  
|**is_fixed_role**|**bit**|プリンシパルが固定サーバー ロールの場合、1 を返します。 詳細については、「 [サーバー レベルのロール](../../relational-databases/security/authentication-access/server-level-roles.md)」を参照してください。|  
  
## <a name="permissions"></a>権限  
 すべてのログインは自分のログイン名、システム ログイン、および固定サーバー ロールを参照できます。 他のログインを参照するには、ALTER ANY LOGIN、またはログインに対する権限が必要です。 ユーザー定義のサーバー ロールを参照するには、ALTER ANY SERVER ROLE、またはロールのメンバーシップが必要です。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="examples"></a>使用例  
 次のクエリは、サーバー プリンシパルに対して明示的に付与または拒否されている権限を一覧表示します。  
  
> [!IMPORTANT]  
>  固定サーバー ロールの権限は、sys.server_permissions には表示されません。 したがって、サーバー プリンシパルには、ここに一覧表示されていない追加の権限がある可能性があります。  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pe.state_desc, pe.permission_name   
FROM sys.server_principals AS pr   
JOIN sys.server_permissions AS pe   
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [権限の階層 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
  
  
