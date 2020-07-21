---
title: server_audit_specification_details (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 04/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_audit_specification_details
- sys.server_audit_specification_details_TSQL
- server_audit_specification_details_TSQL
- sys.server_audit_specification_details
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_audit_specification_details catalog view
ms.assetid: 792724dc-402e-4b17-9f2c-029d910bf88e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a1c8b9e11f5dc1f7445459e1b2d727c52bdb609c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85894780"
---
# <a name="sysserver_audit_specification_details-transact-sql"></a>server_audit_specification_details (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  サーバー インスタンス上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監査に含まれるサーバー監査仕様の詳細 (アクション) に関する情報を含みます。 詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。 すべての audit_action_id とその名前の一覧については、 [dm_audit_actions &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)をクエリします。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|server_specification_id|**int**|監査サーバーの仕様の ID|  
|audit_action_id|**int**|監査アクションの ID|  
|audit_action_name|**sysname**|グループ名または監査アクションの名前|  
|class|**tinyint**|予約されています。|  
|class_desc|**nvarchar(60)**|予約されています。|  
|major_id|**int**|予約されています。|  
|minor_id|**int**|予約されています。|  
|audited_principal_id|**int**|予約されています。|  
|audited_result|**nvarchar(60)**|監査結果:<br /><br /> - SUCCESS AND FAILURE (成功および失敗)<br /><br /> - SUCCESS (成功)<br /><br /> -失敗|  
|is_group|**bit**|監査対象オブジェクトがグループかどうか:<br /><br /> 0 - グループではない<br /><br /> 1 - グループ|  
  
## <a name="permissions"></a>アクセス許可  
 **ALTER ANY SERVER AUDIT**または**VIEW any DEFINITION**権限を持つプリンシパルは、このカタログビューにアクセスできます。 また、プリンシパルに**対して VIEW ANY DEFINITION**権限を拒否することはできません。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [CREATE SERVER AUDIT &#40;Transact-sql&#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40;Transact-sql&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40;Transact-sql&#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [Transact-sql&#41;&#40;のサーバー監査の仕様の作成](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-sql&#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-sql&#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [Transact-sql&#41;&#40;データベース監査の仕様の作成](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [Transact-sql&#41;&#40;データベース監査の仕様の変更](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [Transact-sql&#41;&#40;データベース監査の仕様を削除します。](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-sql&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [fn_get_audit_file &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [server_audits &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [server_file_audits &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [server_audit_specifications &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [database_audit_specifications &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [database_audit_specification_details &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [dm_server_audit_status &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [dm_audit_actions &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [dm_audit_class_type_map &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [サーバー監査およびサーバー監査の仕様を作成する](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
