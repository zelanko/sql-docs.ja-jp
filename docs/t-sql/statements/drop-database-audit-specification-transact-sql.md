---
title: "データベース監査の仕様 (TRANSACT-SQL) を削除します |Microsoft ドキュメント"
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
- DROP_DATABASE_AUDIT_SPECIFICATION_TSQL
- DROP DATABASE AUDIT SPECIFICATION
dev_langs:
- TSQL
helpviewer_keywords:
- database audit specification
- DROP DATABASE AUDIT SPECIFICATION statement
ms.assetid: 3c387c6e-9a67-4daa-b64a-c87f6b3c9c4f
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 45d501c90d9f4988772d4ccbae3cd20aa860e477
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-database-audit-specification-transact-sql"></a>DROP DATABASE AUDIT SPECIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース監査仕様オブジェクトを使用して、削除、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]監査機能します。 詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP DATABASE AUDIT SPECIFICATION audit_specification_name  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *audit_specification_name*  
 既存の監査仕様オブジェクトの名前。  
  
## <a name="remarks"></a>解説  
 DROP DATABASE AUDIT SPECIFICATION は、監査仕様のメタデータを削除します。ただし、DROP コマンドが実行される前に収集された監査データは削除されません。 データベース監査の仕様の状態を OFF に設定する必要がありますを使用して`ALTER DATABASE AUDIT SPECIFICATION`を削除する前にします。  
  
## <a name="permissions"></a>Permissions  
 持つユーザー、 **ALTER ANY DATABASE AUDIT**権限は、データベース監査の仕様を削除できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-a-database-audit-specification"></a>A. データベース監査仕様を削除する  
 次の例と呼ばれる監査を削除する`HIPAA_Audit_DB_Specification`です。  
  
```  
DROP DATABASE AUDIT SPECIFICATION HIPAA_Audit_DB_Specification;  
GO  
```  
  
 監査の作成の完全な例を参照してください。 [SQL Server Audit (&) #40";"データベース エンジン"&"#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)です。  
  
## <a name="see-also"></a>参照  
 [SERVER AUDIT &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [サーバー監査の仕様 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [データベース監査の仕様 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
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
 [sys.dm_audit_class_type_map & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [サーバー監査およびサーバー監査の仕様を作成する](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
