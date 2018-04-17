---
title: sys.database_audit_specification_details (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- database_audit_specification_details
- sys.database_audit_specification_details_TSQL
- sys.database_audit_specification_details
- database_audit_specification_details_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_audit_specification_details catalog view
ms.assetid: 03fc60a9-1696-4109-b15e-a50046310859
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4a15d19cf9a70e4545984209a75042a028d852ab
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdatabaseauditspecificationdetails-transact-sql"></a>sys.database_audit_specification_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  すべてのデータベースについてサーバー インスタンス上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監査に含まれる、データベース監査仕様に関する情報を含みます。 詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。 すべての一覧の audit_action_id とその名前を照会[sys.dm_audit_actions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_specification_id**|**int**|監査仕様の ID。|  
|**audit_action_id**|**int**|監査アクションの ID。|  
|**audit_action_name**|**sysname**|監査アクションまたは監査アクション グループの名前。|  
|**クラス**|**int**|監査対象のオブジェクトのクラスを識別します。|  
|**class_ desc**|**nvarchar (60)**|監査対象のオブジェクトのクラスの説明。<br /><br /> - SCHEMA<br /><br /> - TABLE|  
|**major_id**|**int**|監査対象のオブジェクトのメジャー ID (テーブル監査アクションのテーブル ID など)。|  
|**minor_id**|**Int**|クラスに応じて解釈される監査対象のオブジェクトのセカンダリ ID (テーブル監査アクションの列 ID など)。|  
|**audited_principal_id**|**int**|監査対象のプリンシパル。|  
|**audited_result**|**nvarchar (60)**|監査アクションの結果。<br /><br /> - SUCCESS AND FAILURE (成功および失敗) – SUCCESS (成功)<br /><br /> - FAILURE (失敗)|  
|**is_group**|**Bit**|オブジェクトがグループかどうかを示します。<br /><br /> 0 - グループではない<br /><br /> 1 - グループ|  
  
## <a name="permissions"></a>権限  
 持つプリンシパル、 **ALTER ANY DATABASE AUDIT**または**VIEW DEFINITION** 、アクセス許可、 **dbo**ロール、およびのメンバー、 **db_owners**固定データベース ロールでは、このカタログ ビューにアクセスします。 さらに、プリンシパル拒否されていない**VIEW DEFINITION**権限です。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [サーバー監査およびサーバー監査の仕様を作成する](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
