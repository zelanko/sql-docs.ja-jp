---
title: SQL Server 監査レコード | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audit records [SQL Server]
ms.assetid: 7a291015-df15-44fe-8d53-c6d90a157118
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 3cc249ebfce796d7932e68d993ac98ede867845f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63238387"
---
# <a name="sql-server-audit-records"></a>SQL Server 監査レコード
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 監査機能を使用すると、サーバー レベルおよびデータベース レベルのイベントのグループおよびイベントを監査することができます。 詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](sql-server-audit-database-engine.md)」を参照してください。 [https://login.microsoftonline.com/consumers/]([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)])  
  
 監査は、監査 *対象*に記録される 0 個以上の監査アクション項目で構成されます。 監査ターゲットには、バイナリ ファイル、Windows アプリケーション イベント ログ、または Windows セキュリティ イベント ログを使用できます。 ターゲットに送信されるレコードに含まれる可能性がある要素を次の表に示します。  
  
|列名|[説明]|種類|常に使用可能かどうか|  
|-----------------|-----------------|----------|----------------------|  
|**event_time**|監査可能なアクションが発生した日付/時刻。|`datetime2`|はい|  
|**sequence_no**|大きすぎて監査の書き込みバッファーに収まらなかった 1 つの監査レコード内のレコードの順序を追跡します。|`int`|はい|  
|**action_id**|アクションの ID<br /><br /> ヒント: **action_id** を述語として使用するには、文字列から数値に変換する必要があります。 詳細については、「 [Filter SQL Server Audit on action_id / class_type predicate (action_id/class_type 述語での SQL Server 監査のフィルター選択)](https://blogs.msdn.com/b/sqlsecurity/archive/2012/10/03/filter-sql-server-audit-on-action-id-class-type-predicate.aspx)」を参照してください。|`varchar(4)`|はい|  
|**succeeded**|イベントを発生させたアクションが成功したかどうかを示します。|`bit`-1 = 成功、0 = 失敗|はい|  
|**permission_bitmask**|該当する場合、許可、拒否、または取り消されたアクセス許可を表示します。|`bigint`|いいえ|  
|**is_column_permission**|列レベル権限を示すフラグ。|`bit`-1 = True、0 = False|いいえ|  
|**session_id**|イベントが発生したセッションの ID。|`int`|はい|  
|**server_principal_id**|アクションが実行されるログイン コンテキストの ID。|`int`|はい|  
|**database_principal_id**|アクションが実行されるデータベース ユーザー コンテキストの ID。|`int`|いいえ|  
|**object_ id**|監査が発生したエンティティのプライマリ ID。 これには次のものが含まれます<br /><br /> サーバー オブジェクト<br /><br /> databases<br /><br /> データベース オブジェクト<br /><br /> スキーマ オブジェクト|`int`|いいえ|  
|**target_server_principal_id**|監査可能なアクションが適用されるサーバー プリンシパル。|`int`|はい|  
|**target_database_principal_id**|監査可能なアクションが適用されるデータベース プリンシパル。|`int`|いいえ|  
|**class_type**|監査が発生する監査可能なエンティティの種類。|`varchar(2)`|はい|  
|**session_server_principal_name**|セッションのサーバー プリンシパル。|`sysname`|はい|  
|**server_principal_name**|現在のログイン。|`sysname`|はい|  
|**server_principal_sid**|現在のログイン SID。|`varbinary`|はい|  
|**database_principal_name**|現在のユーザー。|`sysname`|いいえ|  
|**target_server_principal_name**|アクションの対象ログイン。|`sysname`|いいえ|  
|**target_server_principal_sid**|対象ログインの SID。|`varbinary`|いいえ|  
|**target_database_principal_name**|アクションの対象ユーザー。|`sysname`|いいえ|  
|**server_instance_name**|監査が発生したサーバー インスタンスの名前。 標準の machine\instance の形式を使用します。|`nvarchar(120)`|はい|  
|**database_name**|アクションが発生したデータベース コンテキスト。|`sysname`|いいえ|  
|**schema_name**|アクションが発生したスキーマ コンテキスト。|`sysname`|いいえ|  
|**object_name**|監査が発生したエンティティの名前。 これには次のものが含まれます<br /><br /> サーバー オブジェクト<br /><br /> databases<br /><br /> データベース オブジェクト<br /><br /> スキーマ オブジェクト<br /><br /> TSQL ステートメント (あれば)|`sysname`|いいえ|  
|**諸表**|TSQL ステートメント (あれば)|`nvarchar(4000)`|いいえ|  
|**additional_information**|XML として格納されるイベントに関する追加情報。|`nvarchar(4000)`|いいえ|  
  
## <a name="remarks"></a>解説  
 アクションに該当しないために列の値が設定されない場合もあります。  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 監査は、監査レコードの文字フィールドに 4,000 文字のデータを格納します。 監査可能なアクションから返される **additional_information** と **statement** の値が 4,000 文字を超えていた場合は、そのデータを記録するために、 **sequence_no** 列を使用して 1 つの監査アクションの監査レポートに複数のレコードが書き込まれます。 このプロセスは次のとおりです。  
  
-   
  **statement** 列が 4,000 文字に分割されます。  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分割されたデータが監査レコードの最初の行として書き込まれます。 他のすべてのフィールドは各行で複製されます。  
  
-   
  **sequence_no** の値が増加されます。  
  
-   すべてのデータが記録されるまでこのプロセスが繰り返されます。  
  
 このデータに接続するには、 **sequence_no** の値を使用して行を順番に読み取ります。アクションを識別するには、 **event_Time**、 **action_id** 、および **session_id** の各列を使用します。  
  
## <a name="related-content"></a>関連コンテンツ  
 [CREATE SERVER AUDIT &#40;Transact-sql&#41;](/sql/t-sql/statements/create-server-audit-transact-sql)  
  
 [ALTER SERVER AUDIT &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-server-audit-specification-transact-sql)  
  
 [DROP SERVER AUDIT &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-server-audit-transact-sql)  
  
 [Transact-sql&#41;&#40;のサーバー監査の仕様の作成](/sql/t-sql/statements/create-server-audit-specification-transact-sql)  
  
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-server-audit-transact-sql)  
  
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-server-audit-specification-transact-sql)  
  
 [Transact-sql&#41;&#40;データベース監査の仕様の作成](/sql/t-sql/statements/create-database-audit-specification-transact-sql)  
  
 [Transact-sql&#41;&#40;データベース監査の仕様の変更](/sql/t-sql/statements/alter-database-audit-specification-transact-sql)  
  
 [Transact-sql&#41;&#40;データベース監査の仕様を削除します。](/sql/t-sql/statements/drop-database-encryption-key-transact-sql)  
  
 [ALTER AUTHORIZATION &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
 [fn_get_audit_file &#40;Transact-sql&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql)  
  
 [server_audits &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-server-audits-transact-sql)  
  
 [server_file_audits &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-server-file-audits-transact-sql)  
  
 [server_audit_specifications &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql)  
  
 [server_audit_specification_details &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql)  
  
 [database_audit_specifications &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql)  
  
 [database_audit_specification_details &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql)  
  
 [dm_server_audit_status &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql)  
  
 [dm_audit_actions &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql)  
  
 [dm_audit_class_type_map &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql)  
  
  
