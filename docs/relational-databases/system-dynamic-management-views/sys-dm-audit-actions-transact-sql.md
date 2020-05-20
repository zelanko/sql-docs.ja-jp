---
title: dm_audit_actions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_audit_actions_TSQL
- sys.dm_audit_actions
- dm_audit_actions_TSQL
- dm_audit_actions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_audit_actions dynamic management view
ms.assetid: b987c2b9-998a-4a5f-a82d-280dc6963cbe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 10558ea4d489ad39fe762f360affdaae372ddee6
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830906"
---
# <a name="sysdm_audit_actions-transact-sql"></a>sys.dm_audit_actions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  監査ログで報告される可能性のあるすべての監査アクション、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit の一部として構成できるすべての監査アクション グループに対して 1 つの行を返します。 監査の詳細につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server audit &#40;データベースエンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**action_id**|**varchar (4)**|監査アクションの ID。 各監査レコードに書き込まれた**action_id**値に関連します。 NULL 値が許可されます。 監査グループの場合は NULL。|  
|**action_in_log**|**bit**|アクションを監査ログに書き込むことができるかどうかを示します。 値は次のとおりです。<br /><br /> 1 = はい<br /><br /> 0 = いいえ|  
|**name**|**sysname**|監査アクションまたはアクショングループの名前。 NULL 値は許可されません。|  
|**class_desc**|**nvarchar(120)**|監査アクションが適用されるオブジェクトのクラス名。 には、サーバー、データベース、またはスキーマスコープオブジェクトのいずれかを指定できますが、スキーマオブジェクトは含まれません。 NULL 値は許可されません。|  
|**parent_class_desc**|**nvarchar(120)**|class_desc で記述されるオブジェクトの親クラスの名前。 Class_desc がサーバーの場合は NULL です。|  
|**covering_parent_action_name**|**nvarchar(120)**|この行で記述される監査アクションを含む、監査アクションまたは監査グループの名前。 これは、アクションとカバーアクションの階層を作成するために使用されます。 NULL 値が許可されます。|  
|**configuration_level**|**nvarchar (10)**|この行に指定されているアクションまたはアクショングループがグループまたはアクションレベルで構成可能であることを示します。 アクションが構成可能でない場合、は NULL になります。|  
|**containing_group_name**|**nvarchar(120)**|指定されたアクションを含む監査グループの名前。 Name の値がグループの場合は NULL になります。|  
  
## <a name="permissions"></a>アクセス許可  
 プリンシパルには**SELECT**権限が必要です。 既定では、これは Public に与えられます。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)].  詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
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
 [server_audit_specification_details &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [database_audit_specifications &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [database_audit_specification_details &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [dm_server_audit_status &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [dm_audit_class_type_map &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [サーバー監査およびサーバー監査の仕様を作成する](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
