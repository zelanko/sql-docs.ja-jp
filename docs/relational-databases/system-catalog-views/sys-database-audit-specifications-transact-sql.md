---
title: "sys.database_audit_specifications (TRANSACT-SQL) |Microsoft ドキュメント"
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
- database_audit_specifications_TSQL
- sys.database_audit_specifications_TSQL
- sys.database_audit_specifications
- database_audit_specifications
dev_langs: TSQL
helpviewer_keywords: sys.database_audit_specifications catalog view
ms.assetid: bf80e5c6-0588-4eb7-86ff-aa7c73461335
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 29f59374c1baea886755e2aa6ba483df64513ba3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysdatabaseauditspecifications-transact-sql"></a>sys.database_audit_specifications (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー インスタンス上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監査に含まれるデータベース監査仕様に関する情報を含みます。 詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|名前|**sysname**|監査の仕様の名前。|  
|database_specification_id|**int**|データベース仕様の ID。|  
|create_date|**datetime**|監査仕様が作成された日付。|  
|modified_date|**datetime**|監査仕様が最後に変更された日付。|  
|is_state_enabled|**bit**|監査仕様の状態。<br /><br /> 0 – DISABLED<br /><br /> 1 – ENABLED|  
|audit_GUID|**uniqueidentifer**|この仕様を含む監査の GUID。 データベースのインポートまたは起動時に、メンバー データベース監査仕様を列挙するときに使用されます。|  
  
## <a name="remarks"></a>解説  
 データベースが読み取り専用モードの場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit 機能ではデータベース監査仕様を追加できません。  
  
## <a name="permissions"></a>Permissions  
 持つプリンシパル、 **ALTER ANY DATABASE AUDIT**または**VIEW DEFINITION**アクセス許可、dbo ロール、および db_owners 固定データベース ロールのメンバーは、このカタログ ビューにアクセス権を持ちます。 さらに、プリンシパル拒否されていない**VIEW DEFINITION**権限です。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]」をご覧ください。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
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
 [sys.server_audit_specification_details &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specification_details &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [サーバー監査およびサーバー監査の仕様を作成する](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
