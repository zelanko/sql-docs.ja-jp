---
title: "DROP SERVER AUDIT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SERVER AUDIT
- DROP_SERVER_AUDIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP SERVER AUDIT statement
ms.assetid: faace8a3-daa9-4208-a2cd-4249eb32175c
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 83d383f58c4ebf5bcc7492057b142d4db311992e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-server-audit--transact-sql"></a>DROP SERVER AUDIT (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  SQL Server Audit 機能を使用して、SQL Server 監査オブジェクトを削除します。 SQL Server Audit の詳細については、次を参照してください。 [SQL Server Audit (&) #40";"データベース エンジン"&"#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP SERVER AUDIT audit_name  
    [ ; ]  
```  
  
## <a name="remarks"></a>解説  
 監査を変更する場合は、監査の状態を OFF に設定する必要があります。 STATE=OFF 以外のオプションを使用して監査を有効にしているときに DROP AUDIT を実行すると、MSG_NEED_AUDIT_DISABLED エラー メッセージが表示されます。  
  
 DROP SERVER AUDIT は、監査のメタデータを削除します。ただし、コマンドの実行前に収集された監査データは削除されません。  
  
 DROP SERVER AUDIT では、関連付けられているサーバー監査仕様またはデータベース監査仕様が削除されません。 これらの仕様は手動で削除するか、または孤立した状態にしておき、後で新しいサーバー監査にマップする必要があります。  
  
## <a name="permissions"></a>Permissions  
 サーバー監査のプリンシパルを作成、変更、または削除するには、サーバー監査の ALTER ANY SERVER AUDIT 権限または CONTROL SERVER 権限を持っている必要があります。  
  
## <a name="examples"></a>使用例  
 次の例と呼ばれる監査を削除する`HIPAA_Audit`です。  
  
```  
ALTER SERVER AUDIT HIPAA_Audit  
STATE = OFF;  
GO  
DROP SERVER AUDIT HIPAA_Audit;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SERVER AUDIT &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [サーバー監査の仕様 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [データベース監査の仕様 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
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
 [sys.dm_audit_class_type_map & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [サーバー監査およびサーバー監査の仕様を作成する](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  

