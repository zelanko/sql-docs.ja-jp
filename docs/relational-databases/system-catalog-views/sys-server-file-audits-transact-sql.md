---
title: "sys.server_file_audits (TRANSACT-SQL) |Microsoft ドキュメント"
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
- server_file_audits_TSQL
- sys.server_file_audits_TSQL
- sys.server_file_audits
- server_file_audits
dev_langs: TSQL
helpviewer_keywords: sys.server_file_audits catalog view
ms.assetid: 553288a0-be57-4d79-ae53-b7cbd065e127
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 42a00870788129a007511766ea8b2a87ef73740d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysserverfileaudits-transact-sql"></a>sys.server_file_audits (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ファイル監査タイプに関する拡張情報を含む、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバー インスタンス上の監査します。 詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|audit_id|**int**|監査の ID。|  
|name|**sysname**|監査の名前です。|  
|audit_guid|**uniqueidentifier**|監査の GUID。|  
|create_date|**datetime**|ファイル監査が作成された UTC 日付。|  
|modify_date|**datatime**|ファイル監査が最後に変更された UTC 日付。|  
|principal_id|**int**|サーバーに登録されている監査の所有者の ID。|  
|型|**char(2)**|監査の種類。<br /><br /> 0 = NT セキュリティ イベント ログ<br /><br /> 1 = NT アプリケーション イベント ログ<br /><br /> 2 = ファイル システムのファイル|  
|type_desc|**nvarchar (60)**|監査タイプの説明。|  
|on_failure|**tinyint**|失敗した場合 : <br /><br /> 0 = 続行<br /><br /> 1 = サーバー インスタンスのシャットダウン<br /><br /> 2 = 失敗の操作|  
|on_failure_desc|**nvarchar (60)**|アクション エントリの書き込みに失敗した場合 : <br /><br /> CONTINUE<br /><br /> SHUTDOWN SERVER INSTANCE<br /><br /> FAIL OPERATION|  
|is_state_enabled|**tinyint**|0 = 無効<br /><br /> 1 = 有効|  
|queue_delay|**int**|ディスクに書き込むまでに待機する推奨最大時間 (ミリ秒)。 0 の場合は、イベントが続行する前に必ず書き込みが行われます。|  
|predicate|**nvarchar(8000)**|イベントに適用される述語式。|  
|max_file_size|**bigint**|監査の最大サイズ (MB):<br /><br /> 0 = 無制限/選択した監査タイプには適用されません。|  
|max_rollover_files|**int**|使用するファイルの最大数 (ロールオーバー オプションあり)。|  
|max_files|**int**|使用するファイルの最大数 (ロールオーバー オプションなし)。|  
|reserved_disk_space|**int**|ファイルごとに予約するディスク領域の容量。|  
|log_file_path|**nvarchar (260)**|監査が配置される場所のパス。 ファイル監査の場合はファイルのパス、アプリケーション ログ監査の場合はアプリケーション ログのパス。|  
|log_file_name|**nvarchar (260)**|CREATE AUDIT DDL で提供されるログ ファイルの基本名。 base_log_name ファイルにサフィックスとして連番が付加されて、ログ ファイル名が作成されます。|  
  
## <a name="permissions"></a>Permissions  
 持つプリンシパル、 **ALTER ANY SERVER AUDIT**または**VIEW ANY DEFINITION**アクセス許可があるこのカタログ ビューにアクセスします。 さらに、プリンシパル拒否されていない**VIEW ANY DEFINITION**権限です。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
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
 [sys.server_file_audits (TRANSACT-SQL)](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.database_audit_specifications &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [サーバー監査およびサーバー監査の仕様を作成する](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
