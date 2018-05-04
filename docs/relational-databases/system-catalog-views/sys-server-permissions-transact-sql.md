---
title: sys.server_permissions (TRANSACT-SQL) |Microsoft ドキュメント
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
- sys.server_permissions_TSQL
- sys.server_permissions
- server_permissions
- server_permissions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_permissions catalog view
ms.assetid: 7d78bf17-6c64-4166-bd0b-9e9e20992136
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 378b7e617151a10db17f044ad7d16530cd01c96f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysserverpermissions-transact-sql"></a>sys.server_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  サーバーレベルの権限ごとに 1 行のデータを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**class**|**tinyint**|権限が存在するリソースのクラスの識別子。<br /><br /> 100 = サーバー<br /><br /> 101 = サーバー プリンシパル<br /><br /> 105 = エンドポイント|  
|**class_desc**|**nvarchar(60)**|権限が存在するクラスの説明。 次の値のいずれかになります。<br /><br /> **サーバー**<br /><br /> **SERVER_PRINCIPAL**<br /><br /> **ENDPOINT**|  
|**major_id**|**int**|権限が存在するセキュリティ保護可能なリソースの ID。クラスに基づいて解釈されます。 ほとんどの場合、これは、クラスが表すに適用される ID の種類だけです。 標準以外のリソースに対する解釈は、次のようになります。<br /><br /> 100 = 常に 0|  
|**minor_id**|**int**|権限が存在するリソースのセカンダリ ID。クラスに基づいて解釈されます。|  
|**grantee_principal_id**|**int**|権限が許可されているサーバー プリンシパル ID。|  
|**grantor_principal_id**|**int**|権限の許可者のサーバー プリンシパル ID。|  
|**type**|**char(4)**|サーバー権限の種類。 権限の種類の一覧については、次の表を参照してください。|  
|**permission_name**|**nvarchar(128)**|権限名。|  
|**状態**|**char(1)**|権限の状態。<br /><br /> D = 拒否<br /><br /> R = 取り消し<br /><br /> G = 許可<br /><br /> W = Grant With Grant オプション|  
|**state_desc**|**nvarchar(60)**|権限の状態の説明。<br /><br /> DENY<br /><br /> REVOKE<br /><br /> GRANT<br /><br /> GRANT_WITH_GRANT_OPTION|  
  
|権限の種類|アクセス許可の名前|適用されるセキュリティ保護可能なリソース|  
|---------------------|---------------------|--------------------------|  
|ADBO|ADMINISTER BULK OPERATIONS|SERVER|  
|AL|ALTER|ENDPOINT、LOGIN|  
|ALCD|ALTER ANY CREDENTIAL|SERVER|  
|ALCO|ALTER ANY CONNECTION|SERVER|  
|ALDB|ALTER ANY DATABASE|SERVER|  
|ALES|ALTER ANY EVENT NOTIFICATION|SERVER|  
|ALHE|ALTER ANY ENDPOINT|SERVER|  
|ALLG|ALTER ANY LOGIN|SERVER|  
|ALLS|ALTER ANY LINKED SERVER|SERVER|  
|ALRS|ALTER RESOURCES|SERVER|  
|ALSS|ALTER SERVER STATE|SERVER|  
|ALST|ALTER SETTINGS|SERVER|  
|ALTR|ALTER TRACE|SERVER|  
|AUTH|AUTHENTICATE SERVER|SERVER|  
|CL|CONTROL|ENDPOINT、LOGIN|  
|CL|CONTROL SERVER|SERVER|  
|CO|CONNECT|ENDPOINT|  
|COSQ|CONNECT SQL|SERVER|  
|CRDB|CREATE ANY DATABASE|SERVER|  
|CRDE|CREATE DDL EVENT NOTIFICATION|SERVER|  
|CRHE|CREATE ENDPOINT|SERVER|  
|CRTE|CREATE TRACE EVENT NOTIFICATION|SERVER|  
|IM|IMPERSONATE|Login|  
|SHDN|SHUTDOWN|SERVER|  
|TO|TAKE OWNERSHIP|ENDPOINT|  
|VW|VIEW DEFINITION|ENDPOINT、LOGIN|  
|VWAD|VIEW ANY DEFINITION|SERVER|  
|VWDB|VIEW ANY DATABASE|SERVER|  
|VWSS|VIEW SERVER STATE|SERVER|  
|XA|EXTERNAL ACCESS|SERVER|  
  
## <a name="permissions"></a>権限  
 すべてのユーザーは自分の権限を参照できます。 他のログインの権限を参照するには、VIEW DEFINITION、ALTER ANY LOGIN、またはログインに対するすべての権限が必要です。 ユーザー定義のサーバー ロールを参照するには、ALTER ANY SERVER ROLE、またはロールのメンバーシップが必要です。  
  
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
 [Securables](../../relational-databases/security/securables.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [権限の階層 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
  
  
