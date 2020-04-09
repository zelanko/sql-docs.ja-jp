---
title: database_principals (トランザクション-SQL) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 10/27/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: feed483cf3ee08c0652e55de51b1f73fc087ed39
ms.sourcegitcommit: 7ed12a64f7f76d47f5519bf1015d19481dd4b33a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80873118"
---
# <a name="sysdatabase_principals-transact-sql"></a>database_principals (トランザクション-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベース内の各セキュリティ プリンシパルの行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**Sysname**|プリンシパルの名前。データベース内で一意です。|  
|**principal_id**|**int**|プリンシパルの ID で、データベース内で一意です。|  
|**type**|**char(1)**|プリンシパルの種類:<br /><br /> A = アプリケーション ロール<br /><br /> C = 証明書にマップされたユーザー<br /><br /> E = Azure アクティブ ディレクトリからの外部ユーザー<br /><br /> G = Windows グループ<br /><br /> K = 非対称キーにマップされたユーザー<br /><br /> R = データベース ロール<br /><br /> S = SQL ユーザー<br /><br /> U = Windows ユーザー<br /><br /> X = Azure アクティブ ディレクトリ グループまたはアプリケーションの外部グループ|  
|**type_desc**|**nvarchar(60)**|プリンシパルの種類の説明。<br /><br /> APPLICATION_ROLE<br /><br /> CERTIFICATE_MAPPED_USER<br /><br /> EXTERNAL_USER<br /><br /> WINDOWS_GROUP<br /><br /> ASYMMETRIC_KEY_MAPPED_USER<br /><br /> DATABASE_ROLE<br /><br /> SQL_USER<br /><br /> WINDOWS_USER<br /><br /> EXTERNAL_GROUPS|  
|**default_schema_name**|**Sysname**|SQL 名でスキーマが指定されていない場合に使用する名前。 S、U、または A のタイプではないプリンシパルの場合は null。|  
|**create_date**|**datetime**|プリンシパルが作成された日時。|  
|**modify_date**|**datetime**|プリンシパルが最後に修正された時刻。|  
|**owning_principal_id**|**int**|このプリンシパルを所有するプリンシパルの ID。 すべての固定データベース ロールは、既定で**dbo**によって所有されます。|  
|**Sid**|**varbinary(85)**|プリンシパルの SID (セキュリティ識別子)  SYS および情報スキーマの場合は NULL です。|  
|**is_fixed_role**|**bit**|1 の場合、この行は、固定データベース ロールの 1 つ(db_owner、db_accessadmin、db_datareader、db_datawriter、db_ddladmin、db_securityadmin、db_backupoperator、db_denydatareader、db_denydatawriterのいずれかのエントリを表します。|  
|**authentication_type**|**int**|**に適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]および後で。<br /><br /> 認証の種類を示します。 以下に、使用できる値とその説明を示します。<br /><br /> 0 : 認証なし<br />1 : インスタンス認証<br />2 : データベース認証<br />3 : Windows 認証<br />4 : Azure アクティブ ディレクトリ認証|  
|**authentication_type_desc**|**nvarchar(60)**|**に適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]および後で。<br /><br /> 認証の種類の説明。 以下に、使用できる値とその説明を示します。<br /><br /> NONE : 認証なし<br />インスタンス : インスタンス認証<br />データベース : データベース認証<br />ウィンドウズ: Windows 認証<br />外部: Azure アクティブ ディレクトリ認証|  
|**default_language_name**|**Sysname**|**に適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]および後で。<br /><br /> このプリンシパルの既定の言語を示します。|  
|**default_language_lcid**|**int**|**に適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]および後で。<br /><br /> このプリンシパルの既定の LCID を示します。|  
|**allow_encrypted_value_modifications**|**bit**|**に適用されます**。 [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]<br /><br /> 一括コピー操作でのサーバーの暗号化メタデータ チェックを抑制します。 これにより、ユーザーは、データを復号化することなく、テーブルまたはデータベース間で Always Encrypted を使用して暗号化されたデータを一括コピーできます。 既定値は OFF です。 |      
  
## <a name="remarks"></a>Remarks  
 *プロパティ*は、サポートされているすべての SQL Server 構成で使用できますが、その他のプロパティは、SQL Server が Windows Server 2003 以降で実行されており、CHECK_POLICYとCHECK_EXPIRATIONの両方が有効になっている場合にのみ使用できます。 詳細については[、「パスワード ポリシー](../../relational-databases/security/password-policy.md) 」を参照してください。
principal_idの値は、プリンシパルが削除され、したがって増加が保証されない場合に再利用できます。
  
## <a name="permissions"></a>アクセス許可  
 すべてのユーザーは自分のユーザー名、システム ユーザー、および固定データベース ロールを参照できます。 他のユーザーを参照するには、ALTER ANY USER、またはユーザーに対する権限が必要です。 ユーザー定義ロールを参照するには、ALTER ANY ROLE、またはロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
  
### <a name="a-listing-all-the-permissions-of-database-principals"></a>A: データベース プリンシパルのすべての権限を一覧表示する  
 次のクエリは、データベース プリンシパルに明示的に許可または拒否された権限を一覧表示します。  
  
> [!IMPORTANT]  
>  固定データベース ロールの権限は sys.database_permissions には表示されません。 したがって、データベース プリンシパルには、ここに記載されていない追加の権限が付与されている場合があります。  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc, pe.permission_name  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
### <a name="b-listing-permissions-on-schema-objects-within-a-database"></a>B: データベース内のスキーマ オブジェクトに対する権限の一覧表示  
 次のクエリは、sys.database_principals と sys.database_permissions を sys.objects および sys.schema に結合して、特定のスキーマ オブジェクトに対して許可または拒否されたアクセス許可を一覧表示します。  
  
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
  
## <a name="examples-sssdwfull-and-sspdw"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-listing-all-the-permissions-of-database-principals"></a>C: データベース プリンシパルのすべての権限の一覧表示  
 次のクエリは、データベース プリンシパルに明示的に許可または拒否された権限を一覧表示します。  
  
> [!IMPORTANT]  
>  固定データベース ロールの権限は、 には`sys.database_permissions`表示されません。 したがって、データベース プリンシパルには、ここに記載されていない追加の権限が付与されている場合があります。  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pr.authentication_type_desc, pe.state_desc, pe.permission_name  
FROM sys.database_principals AS pr  
JOIN sys.database_permissions AS pe  
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
### <a name="d-listing-permissions-on-schema-objects-within-a-database"></a>D: データベース内のスキーマ オブジェクトに対する権限の一覧表示  
 次のクエリは`sys.database_principals`、`sys.database_permissions`特定`sys.objects`の`sys.schemas`スキーマ オブジェクトに対して許可または拒否されたアクセス許可の結合と一覧表示を行います。  
  
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
 [プリンシパル&#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [トランザクション SQL&#41;&#40;sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [セキュリティ カタログ ビュー&#40;トランザクション SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [包含データベース ユーザー - データベースを移植可能にする](../../relational-databases/security/contained-database-users-making-your-database-portable.md)   
 [Azure Active Directory の認証を使用して、SQL データベースに接続する](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication)  
  
  


