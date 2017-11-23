---
title: "sys.server_audit_specification_details (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/05/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- server_audit_specification_details
- sys.server_audit_specification_details_TSQL
- server_audit_specification_details_TSQL
- sys.server_audit_specification_details
dev_langs: TSQL
helpviewer_keywords: sys.server_audit_specification_details catalog view
ms.assetid: 792724dc-402e-4b17-9f2c-029d910bf88e
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 37f744da0443de8190cce19acefb6ef8a5d77f37
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysserverauditspecificationdetails-transact-sql"></a>sys.server_audit_specification_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー インスタンス上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監査に含まれるサーバー監査仕様の詳細 (アクション) に関する情報を含みます。 詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。 すべての一覧の audit_action_id とその名前を照会[sys.dm_audit_actions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md).  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|server_specification_id|**int**|監査サーバー仕様の ID|  
|audit_action_id|**int**|監査アクションの ID|  
|audit_action_name|**sysname**|グループ名または監査アクション名|  
|class|**tinyint**|予約済み。|  
|class_desc|**nvarchar (60)**|予約済み。|  
|major_id|**int**|予約済み。|  
|minor_id|**int**|予約済み。|  
|audited_principal_id|**int**|予約済み。|  
|audited_result|**nvarchar (60)**|監査結果:<br /><br /> - SUCCESS AND FAILURE (成功および失敗)<br /><br /> - SUCCESS (成功)<br /><br /> - FAILURE (失敗)|  
|is_group|**bit**|監査対象オブジェクトがグループかどうか:<br /><br /> 0 - グループではない<br /><br /> 1 - グループ|  
  
## <a name="permissions"></a>Permissions  
 持つプリンシパル、 **ALTER ANY SERVER AUDIT**または**VIEW ANY DEFINITION**アクセス許可があるこのカタログ ビューにアクセスします。 さらに、プリンシパル拒否されていない**VIEW ANY DEFINITION**権限です。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [SERVER AUDIT &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [サーバー監査の仕様 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
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
 [sys.database_audit_specifications &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [サーバー監査およびサーバー監査の仕様を作成する](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
