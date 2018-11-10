---
title: sys.fn_get_audit_file (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 05/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_get_audit_file_TSQL
- sys.fn_get_audit_file_TSQL
- fn_get_audit_file
- sys.fn_get_audit_file
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_get_audit_file function
- fn_get_audit_file function
ms.assetid: d6a78d14-bb1f-4987-b7b6-579ddd4167f5
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b80ec93ef671f2f9a564c81ae2ebb10c19c43dfd
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018337"
---
# <a name="sysfngetauditfile-transact-sql"></a>sys.fn_get_audit_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサーバー監査で作成された監査ファイルからの情報を返します。 詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
fn_get_audit_file ( file_pattern,   
    { default | initial_file_name | NULL },   
    { default | audit_record_offset | NULL } )  
```  
  
## <a name="arguments"></a>引数  
 *file_pattern*  
 読み取り対象に設定する監査ファイルのディレクトリまたはパスとファイル名を指定します。 種類は**nvarchar (260)** します。 
 
 - **SQL Server**:
    
    この引数には、パス (ドライブ文字またはネットワーク共有) とファイル名の両方を含める必要があります。ファイル名にはワイルドカードを使用できます。 監査ファイル セットから複数のファイルを収集する 1 つのアスタリスク (*) を使用できます。 以下に例を示します。  
  
    -   **\<パス >\\ \*** 収集 - すべての監査ファイルが指定された場所にします。  
  
    -   **\<パス > \LoginsAudit_{GUID}** 収集 - すべての監査を指定した名前と GUID のペアを持つファイル。  
  
    -   **\<path>\LoginsAudit_{GUID}_00_29384.sqlaudit** - Collect a specific audit file.  
  
 - **Azure SQL Database**:
 
    この引数は、blob の URL を (ストレージ エンドポイントとコンテナーを含む) を指定するに使用されます。 アスタリスクのワイルドカードはサポートされません、中には、このプレフィックスで始まる複数のファイル (blob) を収集する (完全な blob 名) ではなく、部分的なファイル (blob) 名のプレフィックスを使用できます。 以下に例を示します。
 
      - **\<Storage_endpoint\>/\<コンテナー\>/\<ServerName\>/\<DatabaseName\> /**  -特定のデータベースのすべての監査ファイル (blob) を収集します。    
      
      - **\<Storage_endpoint\>/\<コンテナー\>/\<ServerName\>/\<DatabaseName\> / \<AuditName\>/\<CreationDate\>/\<FileName\>.xel** -特定の監査ファイル (blob) を収集します。
  
> [!NOTE]  
>  ファイル名のパターンがないパスを渡すとエラーが発生します。  
  
 *initial_file_name*  
 監査レコードの最初の読み取り元に設定する監査ファイル内の特定のファイルのパスと名前を指定します。 種類は**nvarchar (260)** します。  
  
> [!NOTE]  
>  *Initial_file_name*引数が有効なエントリを含める必要がありますまたはいずれかの既定値を含める必要があります |NULL 値です。  
  
 *audit_record_offset*  
 initial_file_name で指定したファイルを使用して既知の場所を指定します。 この引数を使用した場合、関数は、指定されたオフセットの直後にあるバッファーの最初のレコードから読み取りを開始します。  
  
> [!NOTE]  
>  *Audit_record_offset*引数が有効なエントリを含める必要がありますまたはいずれかの既定値を含める必要があります |NULL 値です。 種類は**bigint**します。  
  
## <a name="tables-returned"></a>返されるテーブル  
 次の表に、この関数から返される監査ファイルの内容を示します。  
  
|列名|型|説明|  
|-----------------|----------|-----------------|  
|event_time|**datetime2**|監査可能なアクションが発生した日時。 NULL 値は許可されません。|  
|sequence_number|**int**|大きすぎて監査の書き込みバッファーに収まらなかった 1 つの監査レコード内のレコードの順序を追跡します。 NULL 値は許可されません。|  
|action_id|**varchar (4)**|アクションの ID。 NULL 値は許可されません。|  
|succeeded|**bit**|イベントをトリガーしたアクションが成功したかどうかを示します。 NULL 値は許可されません。 ログイン イベント以外のすべてのイベントで、操作ではなく、権限チェックが成功したか失敗したかのみを報告します。<br /> 1 = 成功<br /> 0 = 失敗|  
|permission_bitmask|**varbinary(16)**|一部のアクションでは、権限の許可、拒否、または取り消しを示します。|  
|is_column_permission|**bit**|列レベルの権限かどうかを示すフラグ。 NULL 値は許可されません。 permission_bitmask = 0 の場合は 0 を返します。<br /> 1 = true<br /> 0 = false|  
|session_id|**smallint**|イベントが発生したセッションの ID。 NULL 値は許可されません。|  
|server_principal_id|**int**|アクションが実行されるログイン コンテキストの ID。 NULL 値は許可されません。|  
|database_principal_id|**int**|アクションが実行されるデータベース ユーザー コンテキストの ID。 NULL 値は許可されません。 この場合は 0 を返します。 には適用されません。 たとえば、サーバー操作などの場合です。|  
|target_server_principal_id|**int**|GRANT/DENY/REVOKE 操作が実行されるサーバー プリンシパル。 NULL 値は許可されません。 該当しない場合は 0 を返します。|  
|target_database_principal_id|**int**|GRANT/DENY/REVOKE 操作が実行されるデータベース プリンシパル。 NULL 値は許可されません。 該当しない場合は 0 を返します。|  
|object_id|**int**|監査が発生したエンティティの ID。 これには、次の内容が含まれます。<br /> Server オブジェクト<br /> データベース<br /> データベース オブジェクト<br /> スキーマ オブジェクト<br /> NULL 値は許可されません。 エンティティがサーバー自体である場合、または監査がオブジェクト レベルで実行されない場合は 0 を返します。 たとえば、認証などの場合です。|  
|class_type|**varchar(2)**|監査が発生する監査可能なエンティティの種類。 NULL 値は許可されません。|  
|session_server_principal_name|**sysname**|セッションのサーバー プリンシパル。 NULL 値が許可されます。|  
|server_principal_name|**sysname**|現在のログイン。 NULL 値が許可されます。|  
|server_principal_sid|**varbinary**|現在のログイン SID。 NULL 値が許可されます。|  
|database_principal_name|**sysname**|現在のユーザー。 NULL 値が許可されます。 使用できない場合は NULL を返します。|  
|target_server_principal_name|**sysname**|アクションの対象ログインします。 NULL 値が許可されます。 該当しない場合は NULL を返します。|  
|target_server_principal_sid|**varbinary**|対象ログインの SID。 NULL 値が許可されます。 該当しない場合は NULL を返します。|  
|target_database_principal_name|**sysname**|アクションの対象ユーザー。 NULL 値が許可されます。 該当しない場合は NULL を返します。|  
|server_instance_name|**sysname**|監査が発生したサーバー インスタンスの名前。 標準の server\instance の形式が使用されます。|  
|database_name|**sysname**|アクションが発生したデータベース コンテキスト。 NULL 値が許可されます。 サーバー レベルの監査には、NULL を返します。|  
|schema_name|**sysname**|アクションが発生したスキーマ コンテキスト。 NULL 値が許可されます。 監査がスキーマの外部で発生しているは、NULL を返します。|  
|object_name|**sysname**|監査が発生したエンティティの名前。 これには、次の内容が含まれます。<br /> Server オブジェクト<br /> データベース<br /> データベース オブジェクト<br /> スキーマ オブジェクト<br /> NULL 値が許可されます。 エンティティがサーバー自体である場合、または監査がオブジェクト レベルで実行されない場合は NULL を返します。 たとえば、認証などの場合です。|  
|statement|**nvarchar (4000)**|TSQL ステートメント (存在する場合)。 NULL 値が許可されます。 該当しない場合は NULL を返します。|  
|additional_information|**nvarchar (4000)**|単一のイベントに対してだけ適用される固有の情報が XML として返されます。 この種類の情報は、少数の監査可能なアクションに含まれます。<br /><br /> TSQL スタックが関連付けられているアクションに関して、XML 形式には、1 レベルの TSQL スタックが表示されます。 この XML 形式は次のとおりです。<br /><br /> `<tsql_stack><frame nest_level = '%u' database_name = '%.*s' schema_name = '%.*s' object_name = '%.*s' /></tsql_stack>`<br /><br /> frame nest_level は、フレームの現在の入れ子レベルを示します。 モジュール名は 3 つの部分 (database_name、schema_name、object_name) から成る形式で表されます。  モジュール名を解析してなどの無効な xml 文字をエスケープ`'\<'`、 `'>'`、 `'/'`、`'_x'`します。 としてエスケープする必要がある`_xHHHH\_`します。 HHHH は、その文字の 4 桁の 16 進数 UCS-2 コードを表しています。<br /><br /> NULL 値が許可されます。 イベントから追加情報が報告されない場合は NULL を返します。|  
|file_name|**varchar(260)**|レコードの読み取り元の監査ログ ファイルのパスと名前。 NULL 値は許可されません。|  
|audit_file_offset|**bigint**|監査レコードを含むファイルのバッファー オフセット。 NULL 値は許可されません。|  
|user_defined_event_id|**smallint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 引数として渡されるユーザー定義済みのイベント id **sp_audit_write**します。 **NULL**システム イベント (既定値) のユーザー定義のイベントに対しては 0 以外。 詳細については、次を参照してください。 [sp_audit_write &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-audit-write-transact-sql.md)します。|  
|user_defined_information|**nvarchar (4000)**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> ユーザーに記録する追加情報を記録するために使用 |監査ログを使用して、 **sp_audit_write**ストアド プロシージャ。|  
|audit_schema_version |**int** | |  
|sequence_group_id |**varbinary** | **適用対象**: SQL Server のみ (2016年以降) |  
|transaction_id |**bigint** | **適用対象**: SQL Server のみ (2016年以降) |  
|client_ip |**nvarchar(128)** | **適用対象**: Azure SQL DB + SQL Server (2017年以降) |  
|application_name |**nvarchar(128)** | **適用対象**: Azure SQL DB + SQL Server (2017年以降) |  
|duration_milliseconds |**bigint** | **適用対象**: Azure SQL DB のみ |  
|response_rows |**bigint** | **適用対象**: Azure SQL DB のみ |  
|affected_rows |**bigint** | **適用対象**: Azure SQL DB のみ |  
|connection_id |GUID | **適用対象**: Azure SQL DB のみ |
|data_sensitivity_information |nvarchar (4000) | **適用対象**: Azure SQL DB のみ |
  
## <a name="remarks"></a>コメント  
 場合、 *file_pattern*に渡される引数**fn_get_audit_file**参照パスまたはファイルが存在しない、または、ファイルは、監査ファイルがない場合、 **MSG_INVALID_AUDIT_FILE**エラー メッセージが返されます。  
  
## <a name="permissions"></a>アクセス許可  
 - **SQL Server**: が必要です、 **CONTROL SERVER**権限。  
 - **Azure SQL DB**: が必要です、 **CONTROL DATABASE**権限。     
    - サーバー管理者は、サーバー上のすべてのデータベースの監査ログにアクセスできます。
    - 以外のサーバー管理者は、現在のデータベースから監査ログをのみアクセスできます。
    - 上記の条件を満たしていない blob はスキップされます (スキップされた blob の一覧は、クエリの出力メッセージの表示は、)、関数は、アクセスが許可されている blob からのみログを返します。  
  
## <a name="examples"></a>使用例

- **SQL Server**

  この例では、`\\serverName\Audit\HIPPA_AUDIT.sqlaudit` という名前のファイルから読み取ります。  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file ('\\serverName\Audit\HIPPA_AUDIT.sqlaudit',default,default);  
  GO  
  ```  

- **Azure SQL Database**

  この例は、という名前のファイルから読み取ります`ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel`:  
  
  ```  
  SELECT * FROM sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel',default,default);
  GO  
  ```  

  この例で、追加の T-SQL 句を使用した前述のように、同じファイルから読み取ります (**上部**、 **ORDER BY**、および**場所**句によって返される監査レコードをフィルター処理するため、関数の場合):
  
  ```  
  SELECT TOP 10 * FROM sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/ShiraServer/MayaDB/SqlDbAuditing_Audit/2017-07-14/10_45_22_173_1.xel',default,default)
  WHERE server_principal_name = 'admin1'
  ORDER BY event_time
  GO
  ```  

  この例では、すべての監査ログで始まるサーバーからは読み取り`Sh`: 
  
  ```  
  SELECT * FROM sys.fn_get_audit_file ('https://mystorage.blob.core.windows.net/sqldbauditlogs/Sh',default,default);
  GO  
  ```

監査を作成する方法の完全な例については、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」をご覧ください。

Azure SQL Database 監査をセットアップする方法については、次を参照してください。 [SQL Database 監査の](https://docs.microsoft.com/azure/sql-database/sql-database-auditing)します。
  
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
 [sys.server_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [サーバー監査およびサーバー監査の仕様を作成する](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
