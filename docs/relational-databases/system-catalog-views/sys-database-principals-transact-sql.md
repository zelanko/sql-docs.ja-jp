---
title: sys.database_principals (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 10/27/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- database_principals
- database_principals_TSQL
- sys.database_principals
- sys.database_principals_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_principals catalog view
ms.assetid: 8cb239e9-eb8c-4109-9cec-0d35de95fa0e
caps.latest.revision: 46
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d6d3cd64336d3374e74e5df05310e2e337ded062
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdatabaseprincipals-transact-sql"></a>sys.database_principals (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  プリンシパルのそれぞれのセキュリティの行を返します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|プリンシパルの名前。データベース内で一意です。|  
|**principal_id**|**int**|プリンシパルの ID。データベース内で一意です。|  
|**type**|**char(1)**|プリンシパルの種類。<br /><br /> A = アプリケーション ロール<br /><br /> C = 証明書にマップされているユーザー<br /><br /> E = Azure Active Directory からの外部のユーザー<br /><br /> G = Windows グループ<br /><br /> K = 非対称キーにマップされているユーザー<br /><br /> R = データベース ロール<br /><br /> S = SQL ユーザー<br /><br /> U = Windows ユーザー<br /><br /> X = Azure Active Directory グループまたはアプリケーションからの外部グループ|  
|**type_desc**|**nvarchar(60)**|プリンシパルの種類の説明。<br /><br /> APPLICATION_ROLE<br /><br /> CERTIFICATE_MAPPED_USER<br /><br /> EXTERNAL_USER<br /><br /> WINDOWS_GROUP<br /><br /> ASYMMETRIC_KEY_MAPPED_USER<br /><br /> DATABASE_ROLE<br /><br /> SQL_USER<br /><br /> WINDOWS_USER<br /><br /> EXTERNAL_GROUPS|  
|**default_schema_name**|**sysname**|SQL 名でスキーマが指定されなかったときに使用される名前。 種類が S、U、A 以外のプリンシパルの場合は Null になります。|  
|**create_date**|**datetime**|プリンシパルが作成された日時。|  
|**modify_date**|**datetime**|プリンシパルが変更された時刻。|  
|**owning_principal_id**|**int**|このプリンシパルを所有するプリンシパルの ID。 データベース ロール以外のすべてのプリンシパルが所有する必要があります**dbo**です。|  
|**sid**|**varbinary(85)**|プリンシパルの SID (セキュリティ識別子)。  SYS および INFORMATION SCHEMAS の場合は NULL になります。|  
|**is_fixed_role**|**bit**|1 の場合は、固定データベース ロール db_owner、db_accessadmin、db_datareader、db_datawriter、db_ddladmin、db_securityadmin、db_backupoperator、db_denydatareader、db_denydatawriter のいずれかのエントリを表します。|  
|**authentication_type**|**int**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 認証の種類を示します。 使用可能な値とその説明を次に示します。<br /><br /> 0: 認証なし<br />1: インスタンスの認証<br />2: データベースの認証<br />3: Windows 認証|  
|**authentication_type_desc**|**nvarchar(60)**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 認証の種類の説明。 使用可能な値とその説明を次に示します。<br /><br /> NONE: 認証なし<br />インスタンス: インスタンスの認証<br />データベース: データベースの認証<br />WINDOWS: Windows 認証|  
|**default_language_name**|**sysname**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このプリンシパルの既定の言語を示します。|  
|**default_language_lcid**|**int**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このプリンシパルの既定の LCID を示します。|  
|**allow_encrypted_value_modifications**|**bit**|**適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]。<br /><br /> 一括コピー操作でのサーバーの暗号化メタデータ チェックを抑制します。 これにより、ユーザーを使用して Always encrypted により、テーブルまたはデータベース間でデータの暗号化を解除せずに暗号化データの一括コピーにします。 既定値は OFF です。 |      
  
## <a name="remarks"></a>解説  
 *PasswordLastSetTime*プロパティは、SQL Server のサポートされているすべての構成で使用できますが、その他のプロパティは SQL Server が Windows Server 2003 以降、CHECK_POLICY と CHECK_ の両方で実行されている場合にのみ使用できます有効期限が有効にします。 参照してください[パスワード ポリシー](../../relational-databases/security/password-policy.md)詳細についてはします。  
  
## <a name="permissions"></a>権限  
 すべてのユーザーは自分のユーザー名、システム ユーザー、および固定データベース ロールを参照できます。 他のユーザーを参照するには、ALTER ANY USER、またはユーザーに対する権限が必要です。 ユーザー定義ロールを参照するには、ALTER ANY ROLE、またはロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-all-the-permissions-of-database-principals"></a>A: データベース プリンシパルのすべての権限を一覧表示する  
 次のクエリは、データベース プリンシパルに対して明示的に付与または拒否されている権限を一覧表示します。  
  
> [!IMPORTANT]  
>  固定データベース ロールの権限は、sys.database_permissions には表示されません。 したがって、データベース プリンシパルには、ここに一覧表示されていない追加の権限がある可能性があります。  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc, pe.permission_name  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
### <a name="b-listing-permissions-on-schema-objects-within-a-database"></a>B: データベース内のスキーマ オブジェクト上の権限を一覧表示する  
 次のクエリは、sys.database_principals と sys.database_permissions を sys.objects と sys.schemas に結合して、特定のスキーマ オブジェクトに対して付与または拒否されている権限を一覧表示します。  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc,   
    pe.permission_name, s.name + '.' + o.name AS ObjectName  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id  
JOIN sys.objects AS o  
    ON pe.major_id = o.object_id  
JOIN sys.schemas AS s  
    ON o.schema_id = s.schema_id;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-listing-all-the-permissions-of-database-principals"></a>C: は、データベース プリンシパルのすべての権限を一覧表示します。  
 次のクエリは、データベース プリンシパルに対して明示的に付与または拒否されている権限を一覧表示します。  
  
> [!IMPORTANT]  
>  固定データベース ロールのアクセス許可は表示されません`sys.database_permissions`です。 したがって、データベース プリンシパルには、ここに一覧表示されていない追加の権限がある可能性があります。  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc, pe.permission_name  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
### <a name="d-listing-permissions-on-schema-objects-within-a-database"></a>D:、データベース内のスキーマ オブジェクトのアクセス許可が一覧表示します。  
 次のクエリの結合`sys.database_principals`と`sys.database_permissions`に`sys.objects`と`sys.schemas`特定のスキーマ オブジェクトに付与または拒否アクセス許可を一覧します。  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc,   
    pe.permission_name, s.name + '.' + o.name AS ObjectName  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id  
JOIN sys.objects AS o  
    ON pe.major_id = o.object_id  
JOIN sys.schemas AS s  
    ON o.schema_id = s.schema_id;  
```  
  
## <a name="see-also"></a>参照  
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [包含データベース ユーザー - データベースの可搬](../../relational-databases/security/contained-database-users-making-your-database-portable.md)   
 [Azure Active Directory の認証を使用して、SQL データベースに接続します。](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication)  
  
  


