---
title: "ALTER データベース監査の仕様 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_DATABASE_AUDIT_SPECIFICATION_TSQL
- ALTER DATABASE AUDIT SPECIFICATION
- ALTER_DATABASE_AUDIT_TSQL
- ALTER DATABASE AUDIT
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER DATABASE AUDIT SPECIFICATION statement
ms.assetid: 85f4e7e6-a330-4de0-9048-64f386ccc314
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 06d58a9ecce3175e021e7db484aeadbe41f3b372
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-audit-specification-transact-sql"></a>ALTER DATABASE AUDIT SPECIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース監査仕様オブジェクトを使用して、変更、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]監査機能します。 詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER DATABASE AUDIT SPECIFICATION audit_specification_name  
{  
    [ FOR SERVER AUDIT audit_name ]  
    [ { { ADD | DROP } (   
           { <audit_action_specification> | audit_action_group_name }   
                )   
      } [, ...n] ]  
    [ WITH ( STATE = { ON | OFF } ) ]  
}  
[ ; ]  
<audit_action_specification>::=  
{  
      <action_specification>[ ,...n ] ON [ class :: ] securable   
     BY principal [ ,...n ]   
}  
  
```  
  
## <a name="arguments"></a>引数  
 *audit_specification_name*  
 監査の仕様の名前です。  
  
 *audit_name*  
 この仕様が適用される監査の名前。  
  
 *audit_action_specification*  
 データベース レベルの 1 つ以上の監査可能なアクションの名前。 監査アクション グループの一覧は、次を参照してください。 [SQL サーバー監査アクション グループとアクション](../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md)です。  
  
 *audit_action_group_name*  
 データベース レベルの 1 つ以上の監査可能なアクション グループの名前。 監査アクション グループの一覧は、次を参照してください。 [SQL サーバー監査アクション グループとアクション](../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md)です。  
  
 *クラス*  
 セキュリティ保護可能なリソースのクラス名 (該当する場合)。  
  
 *セキュリティ保護可能です*  
 監査アクションまたは監査アクション グループを適用するデータベース内のテーブル、ビュー、またはその他のセキュリティ保護可能なオブジェクト。 詳細については、「 [セキュリティ保護可能](../../relational-databases/security/securables.md)」を参照してください。  
  
 *列*  
 セキュリティ保護可能なリソースの列名 (該当する場合)。  
  
 *プリンシパル*  
 監査アクションまたは監査アクション グループを適用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プリンシパルの名前。 詳細については、次を参照してください。[プリンシパル & #40";"データベース エンジン"&"#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)です。  
  
 **(**状態 **=**  {ON |オフ} **)**  
 監査による、この監査仕様についてのレコードの収集を有効または無効にします。 監査仕様の状態の変更はユーザー トランザクション外部で実行する必要があります。また、状態が ON から OFF に遷移中の場合、同じステートメントで他の変更を行うことはできません。  
  
## <a name="remarks"></a>解説  
 データベース監査仕様は、セキュリティ保護できないオブジェクトであり、特定のデータベースに保存されます。 監査の仕様をデータベースに変更するためにオプションを OFF は、監査の仕様の状態を設定する必要があります。 STATE=OFF 以外のオプションを使用して監査仕様を有効にしているときに ALTER DATABASE AUDIT SPECIFICATION を実行すると、エラー メッセージが表示されます。 詳細については、「 [tempdb Database](../../relational-databases/databases/tempdb-database.md)」をご覧ください。  
  
## <a name="permissions"></a>Permissions  
 ALTER ANY DATABASE AUDIT 権限を持つユーザーは、データベース監査仕様を変更し、任意の監査にバインドできます。  
  
 データベース監査の仕様を作成すると後、は、プリンシパルは、CONTROL SERVER または ALTER ANY DATABASE AUDIT 権限、sysadmin アカウント、またはその監査への明示的なアクセス権を持つプリンシパルが表示できます。  
  
## <a name="examples"></a>使用例  
 次の例では、`HIPPA_Audit_DB_Specification` ユーザーによる `SELECT` ステートメントを監査する、`dbo` という [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監査の `HIPPA_Audit` というデータベース監査仕様を変更します。  
  
```  
ALTER DATABASE AUDIT SPECIFICATION HIPPA_Audit_DB_Specification  
FOR SERVER AUDIT HIPPA_Audit  
    ADD (SELECT  
         ON OBJECT::dbo.Table1  
         BY dbo)  
    WITH (STATE = ON);  
GO  
```  
  
 監査を作成する方法に関する完全な例を参照してください。 [SQL Server Audit (&) #40";"データベース エンジン"&"#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)です。  
  
## <a name="see-also"></a>参照  
 [SERVER AUDIT &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [サーバー監査の仕様 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [データベース監査の仕様 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [サーバー監査およびサーバー監査の仕様を作成する](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
