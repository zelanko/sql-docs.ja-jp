---
title: sys.database_permissions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- database_permissions
- sys.database_permissions_TSQL
- database_permissions_TSQL
- sys.database_permissions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_permissions catalog view
ms.assetid: c1e261f8-6cb0-4759-b5f1-5ec233602655
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a1bf31190d1dbdcac8506d2306b6cd6ecbd259ac
ms.sourcegitcommit: c86335a432e109322d718a13c37ff4b948c39d2d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2018
ms.locfileid: "43193048"
---
# <a name="sysdatabasepermissions-transact-sql"></a>sys.database_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベースに含まれている、権限ごとまたは列例外の権限ごとに 1 行のデータを返します。 列権限が、対応するオブジェクトレベルの権限とは異なる場合、列権限ごとに行が存在します。 列権限がオブジェクトに対応する権限と同じである場合、その行がないと、適用されるアクセス許可は、オブジェクトの。  
  
> [!IMPORTANT]  
>  列レベルの権限は、同じエンティティ上のオブジェクトレベルの権限をオーバーライドします。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**class**|**tinyint**|権限が存在するクラスの識別子。<br /><br /> 0 = データベース<br />1 = オブジェクトまたは列<br />3 = スキーマ<br />4 = データベース プリンシパル<br />5 = アセンブリが**に適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。<br />6 = 型<br />10 = XML スキーマ コレクションの場合 - <br />                      **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />15 = メッセージの種類 -**に適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。<br />16 = サービス コントラクトの**に適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。<br />17 = サービス -**に適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。<br />18 = リモート サービス バインドの**に適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。<br />19 = ルート -**に適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。<br />23 = フルテキスト カタログ -**に適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。<br />24 = 対称キー -**に適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。<br />25 = 証明書 -**に適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。<br />26 = 非対称キー -**に適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。|  
|**class_desc**|**nvarchar(60)**|権限が存在するクラスの説明。<br /><br /> DATABASE<br /><br /> OBJECT_OR_COLUMN<br /><br /> SCHEMA<br /><br /> DATABASE_PRINCIPAL<br /><br /> ASSEMBLY<br /><br /> TYPE<br /><br /> XML_SCHEMA_COLLECTION<br /><br /> MESSAGE_TYPE<br /><br /> SERVICE_CONTRACT<br /><br /> SERVICE<br /><br /> REMOTE_SERVICE_BINDING<br /><br /> ROUTE<br /><br /> FULLTEXT_CATALOG<br /><br /> SYMMETRIC_KEYS<br /><br /> CERTIFICATE<br /><br /> ASYMMETRIC_KEY|  
|**major_id**|**int**|権限が存在するリソースの ID。クラスに基づいて解釈されます。 通常、 **major_id**はクラス自体に適用される ID の種類だけです。 <br /><br /> 0 = データベース自体 <br /><br /> > 0 = ユーザー オブジェクトのためのオブジェクト Id <br /><br /> \<0 = システム オブジェクトのためのオブジェクト Id |  
|**minor_id**|**int**|アクセス許可が存在するリソースのセカンダリ ID は、クラスに基づいて解釈されます。 多くの場合、 **minor_id** 0 の場合は、オブジェクトのクラスのサブカテゴリがないためです。 それ以外の場合、テーブルの列 ID を勧めします。|  
|**grantee_principal_id**|**int**|権限が許可されているデータベース プリンシパル ID。|  
|**grantor_principal_id**|**int**|権限の許可者のデータベース プリンシパル ID。|  
|**type**|**char(4)**|データベース権限の種類。 権限の種類の一覧については、次の表を参照してください。|  
|**permission_name**|**nvarchar(128)**|権限名。|  
|**state**|**char(1)**|権限の状態。<br /><br /> D = 拒否<br /><br /> R = 取り消し<br /><br /> G = 許可<br /><br /> W = 許可の許可オプション|  
|**state_desc**|**nvarchar(60)**|権限の状態の説明。<br /><br /> DENY<br /><br /> REVOKE<br /><br /> GRANT<br /><br /> GRANT_WITH_GRANT_OPTION|  

## <a name="database-permissions"></a>データベース権限   
次の種類のアクセス許可もあります。
  
|権限の種類|アクセス許可の名前|適用されるセキュリティ保護可能なリソース|  
|---------------------|---------------------|--------------------------|  
|AADS |ALTER ANY DATABASE EVENT SESSION |DATABASE |  
|AAMK |任意のマスクを変更します。 |DATABASE |  
|AEDS |すべての外部データ ソースを変更します。 |DATABASE |  
|AEFF |任意の外部のファイル形式を変更します。 |DATABASE |  
|AL|ALTER|APPLICATION ROLE、ASSEMBLY、ASYMMETRIC KEY、CERTIFICATE、CONTRACT、DATABASE、FULLTEXT CATALOG、MESSAGE TYPE、OBJECT、REMOTE SERVICE BINDING、ROLE、ROUTE、SCHEMA、SERVICE、SYMMETRIC KEY、USER、XML SCHEMA COLLECTION|  
|ALAK|ALTER ANY ASYMMETRIC KEY|DATABASE|  
|ALAR|ALTER ANY APPLICATION ROLE|DATABASE|  
|ALAS|ALTER ANY ASSEMBLY|DATABASE|  
|ALCF|ALTER ANY CERTIFICATE|DATABASE|  
|ALDS|ALTER ANY DATASPACE|DATABASE|  
|ALED|ALTER ANY DATABASE EVENT NOTIFICATION|DATABASE|  
|ALFT|ALTER ANY FULLTEXT CATALOG|DATABASE|  
|ALMT|ALTER ANY MESSAGE TYPE|DATABASE|  
|ALRL|ALTER ANY ROLE|DATABASE|  
|ALRT|ALTER ANY ROUTE|DATABASE|  
|ALSB|ALTER ANY REMOTE SERVICE BINDING|DATABASE|  
|ALSC|ALTER ANY CONTRACT|DATABASE|  
|ALSK|ALTER ANY SYMMETRIC KEY|DATABASE|  
|ALSM|ALTER ANY SCHEMA|DATABASE|  
|ALSV|ALTER ANY SERVICE|DATABASE|  
|ALTG|ALTER ANY DATABASE DDL TRIGGER|DATABASE|  
|ALUS|ALTER ANY USER|DATABASE|  
|AUTH|AUTHENTICATE|DATABASE|  
|BADB|BACKUP DATABASE|DATABASE|  
|BALO|BACKUP LOG|DATABASE|  
|CL|CONTROL|APPLICATION ROLE、ASSEMBLY、ASYMMETRIC KEY、CERTIFICATE、CONTRACT、DATABASE、FULLTEXT CATALOG、MESSAGE TYPE、OBJECT、REMOTE SERVICE BINDING、ROLE、ROUTE、SCHEMA、SERVICE、SYMMETRIC KEY、TYPE、USER、XML SCHEMA COLLECTION|  
|CO|CONNECT|DATABASE|  
|CORP|CONNECT REPLICATION|DATABASE|  
|CP|CHECKPOINT|DATABASE|  
|CRAG|CREATE AGGREGATE|DATABASE|  
|CRAK|CREATE ASYMMETRIC KEY|DATABASE|  
|CRAS|CREATE ASSEMBLY|DATABASE|  
|CRCF|CREATE CERTIFICATE|DATABASE|  
|CRDB|CREATE DATABASE|DATABASE|  
|CRDF|CREATE DEFAULT|DATABASE|  
|CRED|CREATE DATABASE DDL EVENT NOTIFICATION|DATABASE|  
|CRFN|CREATE FUNCTION|DATABASE|  
|CRFT|CREATE FULLTEXT CATALOG|DATABASE|  
|CRMT|CREATE MESSAGE TYPE|DATABASE|  
|CRPR|CREATE PROCEDURE|DATABASE|  
|CRQU|CREATE QUEUE|DATABASE|  
|CRRL|CREATE ROLE|DATABASE|  
|CRRT|CREATE ROUTE|DATABASE|  
|CRRU|CREATE RULE|DATABASE|  
|CRSB|CREATE REMOTE SERVICE BINDING|DATABASE|  
|CRSC|CREATE CONTRACT|DATABASE|  
|CRSK|CREATE SYMMETRIC KEY|DATABASE|  
|CRSM|CREATE SCHEMA|DATABASE|  
|CRSN|CREATE SYNONYM|DATABASE|  
|CRSO|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> CREATE SEQUENCE|DATABASE|  
|CRSV|CREATE SERVICE|DATABASE|  
|CRTB|CREATE TABLE|DATABASE|  
|CRTY|CREATE TYPE|DATABASE|  
|CRVW|CREATE VIEW|DATABASE|  
|CRXS|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> CREATE XML SCHEMA COLLECTION|DATABASE|  
|DABO |ADMINISTER DATABASE BULK OPERATIONS | DATABASE |
|DL|Del|DATABASE、OBJECT、SCHEMA|  
|EAES |EXECUTE ANY EXTERNAL SCRIPT |DATABASE |
|EX|EXECUTE|ASSEMBLY、DATABASE、OBJECT、SCHEMA、TYPE、XML SCHEMA COLLECTION|  
|IM|IMPERSONATE|User|  
|IN|INSERT|DATABASE、OBJECT、SCHEMA|  
|RC|RECEIVE|OBJECT|  
|RF|REFERENCES|ASSEMBLY、ASYMMETRIC KEY、CERTIFICATE、CONTRACT、DATABASE、FULLTEXT CATALOG、MESSAGE TYPE、OBJECT、SCHEMA、SYMMETRIC KEY、TYPE、XML SCHEMA COLLECTION|  
|SL|SELECT|DATABASE、OBJECT、SCHEMA|  
|SN|SEND|SERVICE|  
|SPLN|SHOWPLAN|DATABASE|  
|SUQN|SUBSCRIBE QUERY NOTIFICATIONS|DATABASE|  
|TO|TAKE OWNERSHIP|ASSEMBLY、ASYMMETRIC KEY、CERTIFICATE、CONTRACT、DATABASE、FULLTEXT CATALOG、MESSAGE TYPE、OBJECT、REMOTE SERVICE BINDING、ROLE、ROUTE、SCHEMA、SERVICE、SYMMETRIC KEY、TYPE、XML SCHEMA COLLECTION|  
|UP|UPDATE|DATABASE、OBJECT、SCHEMA|  
|VW|VIEW DEFINITION|APPLICATION ROLE、ASSEMBLY、ASYMMETRIC KEY、CERTIFICATE、CONTRACT、DATABASE、FULLTEXT CATALOG、MESSAGE TYPE、OBJECT、REMOTE SERVICE BINDING、ROLE、ROUTE、SCHEMA、SERVICE、SYMMETRIC KEY、TYPE、USER、XML SCHEMA COLLECTION|  
|VWCK |列の暗号化キーの定義を表示します。|DATABASE |  
|VWCM |任意の列のマスター_キーの定義の表示|DATABASE |  
|VWCT|VIEW CHANGE TRACKING|TABLE、SCHEMA|  
|VWDS|VIEW DATABASE STATE|DATABASE|  
  
## <a name="permissions"></a>アクセス許可  
 すべてのユーザーは自分の権限を参照できます。 他のユーザーの権限を参照するには、VIEW DEFINITION、ALTER ANY USER、またはユーザーに対するすべての権限が必要です。 ユーザー定義ロールを参照するには、ALTER ANY ROLE、またはロール (public など) のメンバーシップが必要です。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
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
    
  
## <a name="see-also"></a>参照  
 [Securables](../../relational-databases/security/securables.md)   
 [権限の階層 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  


