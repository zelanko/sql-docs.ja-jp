---
title: sys.server_permissions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0a1631532cb31813d8425fbf97ee4eec1936d9a8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62683835"
---
# <a name="sysserverpermissions-transact-sql"></a>sys.server_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  各サーバー レベルのアクセス許可の 1 つの行を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**class**|**tinyint**|権限が存在するリソースのクラスの識別子。<br /><br /> 100 = サーバー<br /><br /> 101 = サーバー プリンシパル<br /><br /> 105 = エンドポイント|  
|**class_desc**|**nvarchar(60)**|アクセス許可が存在するクラスの説明です。 次のいずれかの値です。<br /><br /> **サーバー**<br /><br /> **SERVER_PRINCIPAL**<br /><br /> **ENDPOINT**|  
|**major_id**|**int**|権限が存在するセキュリティ保護可能なリソースの ID。クラスに基づいて解釈されます。 ほとんどは、これは、クラスが表す内容に適用される ID の種類だけです。 標準以外のリソースに対する解釈は、次のようになります。<br /><br /> 100 = 常に 0|  
|**minor_id**|**int**|アクセス許可が存在するリソースのセカンダリ ID は、クラスに基づいて解釈されます。|  
|**grantee_principal_id**|**int**|サーバー プリンシパル ID、アクセス許可を付与します。|  
|**grantor_principal_id**|**int**|サーバー プリンシパル ID のこれらのアクセス許可の許可者。|  
|**type**|**char(4)**|サーバー権限の種類。 アクセス許可の種類の一覧は、次の表を参照してください。|  
|**permission_name**|**nvarchar(128)**|権限名。|  
|**state**|**char(1)**|アクセス許可の状態:<br /><br /> D = 拒否<br /><br /> R = 取り消し<br /><br /> G = 許可<br /><br /> W = Grant With Grant オプション|  
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
|XA|外部アクセス|SERVER|  
  
## <a name="permissions"></a>アクセス許可  
 すべてのユーザーは自分の権限を参照できます。 他のログインのアクセス許可を表示するには、VIEW DEFINITION、ALTER ANY LOGIN、またはログインに対する権限が必要です。 ユーザー定義サーバー ロールを参照する ALTER ANY SERVER ROLE をまたはロールのメンバーシップが必要です。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次のクエリは、明示的に付与または拒否サーバー プリンシパル アクセス許可を一覧表示します。  
  
> [!IMPORTANT]  
>  固定サーバー ロールの権限は、sys.server_permissions には表示されません。 そのため、サーバー プリンシパルには、この一覧にない追加のアクセス許可があります。  
  
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
  
  
