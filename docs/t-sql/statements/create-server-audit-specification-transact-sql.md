---
title: "サーバー監査の仕様 (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SERVER_AUDIT_SPECIFICATION_TSQL
- CREATE SERVER AUDIT SPECIFICATION
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE SERVER AUDIT SPECIFICATION statement
ms.assetid: db77fa77-fedb-40ac-83e6-06343063e518
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06457f549575de83fc93c53d204a79061f4f4254
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="create-server-audit-specification-transact-sql"></a>CREATE SERVER AUDIT SPECIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー監査仕様オブジェクトを使用して、作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]監査機能します。 詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE SERVER AUDIT SPECIFICATION audit_specification_name  
FOR SERVER AUDIT audit_name  
{  
    { ADD ( { audit_action_group_name } )   
    } [, ...n]  
    [ WITH ( STATE = { ON | OFF } ) ]  
}  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *audit_specification_name*  
 サーバー監査仕様の名前。  
  
 *audit_name*  
 この仕様が適用される監査の名前。  
  
 *audit_action_group_name*  
 サーバーレベルの監査可能なアクションのグループの名前。 監査アクション グループの一覧は、次を参照してください。 [SQL サーバー監査アクション グループとアクション](../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md)です。  
  
 **(**状態 **=**  {ON |オフ} **)**  
 監査による、この監査仕様についてのレコードの収集を有効または無効にします。  
  
## <a name="remarks"></a>解説  
 サーバー監査仕様を作成するには、対象の監査が事前に存在している必要があります。 サーバー監査仕様は作成されたとき無効な状態です。  
  
## <a name="permissions"></a>Permissions  
 ALTER ANY SERVER AUDIT 権限を持つユーザーは、サーバー監査の仕様を作成し、任意の監査にバインドできます。  
  
 サーバー監査仕様の作成後は、CONTROL SERVER 権限または ALTER ANY SERVER AUDIT 権限を持つプリンシパル、sysadmin アカウント、またはその監査への明示的なアクセス権を持つプリンシパルがその仕様を表示できます。  
  
## <a name="examples"></a>使用例  
 次の例では、失敗したログインを監査する `HIPPA_Audit_Specification` というサーバー監査仕様を、`HIPPA_Audit` という [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監査に対して作成します。  
  
```  
CREATE SERVER AUDIT SPECIFICATION HIPPA_Audit_Specification  
FOR SERVER AUDIT HIPPA_Audit  
    ADD (FAILED_LOGIN_GROUP);  
GO  
```  
  
 監査を作成する方法に関する完全な例を参照してください。 [SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)です。  
  
## <a name="see-also"></a>参照  
 [SERVER AUDIT &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [データベース監査の仕様 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [サーバー監査およびサーバー監査の仕様を作成する](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
