---
title: CREATE SERVER AUDIT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 01/22/2018
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SERVER_AUDIT_TSQL
- SERVER AUDIT
- SERVER_AUDIT_TSQL
- CREATE SERVER AUDIT
dev_langs:
- TSQL
helpviewer_keywords:
- server audit [SQL Server]
- CREATE SERVER AUDIT statement
- audits [SQL Server], creating
ms.assetid: 1c321680-562e-41f1-8eb1-e7fa5ae45cc5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b6e637bec3ddcfd7b24bb4f4adb87011bbbe2471
ms.sourcegitcommit: e851f3cab09f8f09a9a4cc0673b513a1c4303d2d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2018
---
# <a name="create-server-audit-transact-sql"></a>CREATE SERVER AUDIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit を使用してサーバーの監査オブジェクトを作成します。 詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE SERVER AUDIT audit_name  
{  
    TO { [ FILE (<file_options> [ , ...n ] ) ] | APPLICATION_LOG | SECURITY_LOG }  
    [ WITH ( <audit_options> [ , ...n ] ) ]   
    [ WHERE <predicate_expression> ]  
}  
[ ; ]  
  
<file_options>::=  
{  
        FILEPATH = 'os_file_path'  
    [ , MAXSIZE = { max_size { MB | GB | TB } | UNLIMITED } ]  
    [ , { MAX_ROLLOVER_FILES = { integer | UNLIMITED } } | { MAX_FILES = integer } ]  
    [ , RESERVE_DISK_SPACE = { ON | OFF } ]   
}  
  
<audit_options>::=  
{  
    [   QUEUE_DELAY = integer ]  
    [ , ON_FAILURE = { CONTINUE | SHUTDOWN | FAIL_OPERATION } ]  
    [ , AUDIT_GUID = uniqueidentifier ]  
}  
  
<predicate_expression>::=  
{  
    [NOT ] <predicate_factor>   
    [ { AND | OR } [NOT ] { <predicate_factor> } ]   
    [,...n ]  
}  
  
<predicate_factor>::=   
    event_field_name { = | < > | ! = | > | > = | < | < = } { number | ' string ' }  
```  
  
## <a name="arguments"></a>引数  
 TO { FILE | APPLICATION_LOG | SECURITY_LOG }  
 監査ターゲットの場所を指定します。 オプションは、バイナリ ファイル、Windows アプリケーション ログまたは Windows セキュリティ ログです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、Windows で追加の設定を行わないと Windows セキュリティ ログに書き込むことができません。 詳細については、「 [セキュリティ ログへの SQL サーバー監査イベントの書き込み](../../relational-databases/security/auditing/write-sql-server-audit-events-to-the-security-log.md)」を参照してください。  
  
 FILEPATH ='*os_file_path*'  
 監査ログのパス。 ファイル名は、監査名と監査 GUID に基づいて生成されます。  
  
 MAXSIZE = { *max_size }*  
 監査ファイルのサイズの上限を指定します。 *Max_size*値は MB、GB、TB で、または無制限後に整数である必要があります。 に対して指定できる最小サイズ*max_size* 2 mb、最大値は 2,147, 483,647 TB です。 UNLIMITED を指定した場合、ファイルはディスクがいっぱいになるまで拡張されます。 0 も UNLIMITED を示します。2 MB より小さい値を指定すると、MSG_MAXSIZE_TOO_SMALL エラーを発生させます。 既定値は UNLIMITED です。  
  
 MAX_ROLLOVER_FILES =*{ integer* | UNLIMITED }  
 現在のファイルに加えてファイル システム内に保持するファイルの最大数を指定します。 *MAX_ROLLOVER_FILES*整数または UNLIMITED を値として使用することがあります。 既定値は UNLIMITED です。 監査が再開されるたびに、このパラメーターが評価されます (が発生する可能性がときのインスタンス、[!INCLUDE[ssDE](../../includes/ssde-md.md)]の再起動や、監査が有効にするとオフにし、もう一度) または MAXSIZE に達しているため、新しいファイルが必要とします。 ときに*MAX_ROLLOVER_FILES*が評価され、ファイルの数を超えています、 *MAX_ROLLOVER_FILES*設定すると、最も古いファイルが削除されます。 その結果の設定*MAX_ROLLOVER_FILES*は新しいファイルが作成するたびに 0、 *MAX_ROLLOVER_FILES*設定は評価されます。 1 つのファイルが自動的には時に削除*MAX_ROLLOVER_FILES*設定を評価すると、ための値*MAX_ROLLOVER_FILES*が低下しているファイルの数は圧縮されません古いファイルがない限り、手動で削除します。 指定できるファイルの最大数は 2,147,483,647 です。  
  
 MAX_FILES =*integer*  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 作成できる監査ファイルの最大数を指定します。 制限に達しても、最初のファイルへのロールオーバーは行われません。 MAX_FILES の制限に達すると、生成される追加の監査イベントの原因となる任意のアクションはエラーで失敗します。  
  
 RESERVE_DISK_SPACE = { ON | OFF }  
 このオプションは、ディスク上のファイルを MAXSIZE 値に事前に割り当てます。 MAXSIZE が UNLIMITED と等しくない場合にのみ適用されます。 既定値は OFF です。  
  
 QUEUE_DELAY =*integer*  
 監査アクションが処理を強制する前に経過時間をミリ秒単位の時間を決定します。 値 0 は同期配信を表します。 クエリ遅延に設定可能な最小値は 1000 (1 秒) で、これが既定値です。 最大値は 2,147,483,647 (2,147,483.647 秒、つまり 24 日、20 時間、31 分、23.647 秒) です。 無効な数値を指定すると、MSG_INVALID_QUEUE_DELAY エラーが発生します。  
  
 ON_FAILURE = { CONTINUE | SHUTDOWN | FAIL_OPERATION }  
 かどうか、インスタンスが、ターゲットへの書き込みが失敗する、続行する、か停止を示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合は、ターゲットが監査ログに書き込むことはできません。 既定値は CONTINUE です。  
  
 CONTINUE  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 操作を続行します。 監査レコードは保持されません。 監査は、エラー状態が解決される場合に、イベントと再開をログに記録し続けます。 続行のオプションを選択すると、セキュリティ ポリシーに違反する可能性がありますを許すおそれのアクティビティを許可できます。 完全な監査を維持することより、[!INCLUDE[ssDE](../../includes/ssde-md.md)]の操作を続行することの方が重要である場合に、このオプションを使用します。  
  
SHUTDOWN  
インスタンスを強制的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をシャット ダウン、if[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]監査ターゲットに何らかの理由のデータの書き込みに失敗します。 実行しているログイン、`CREATE SERVER AUDIT`ステートメントが必要、`SHUTDOWN`内で権限[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 シャット ダウンの問題が解決しない場合でも、`SHUTDOWN`実行されているログインから権限を取り消す以降。 ユーザーは、このアクセス許可を持っていない場合、ステートメントが失敗して、監査が作成できません。 監査エラーによってシステムのセキュリティまたは整合性が阻害される可能性がある場合に、このオプションを使用します。 詳細については、次を参照してください。[シャット ダウン](../../t-sql/language-elements/shutdown-transact-sql.md)です。  
  
 FAIL_OPERATION  
 監査イベントを発生させるデータベース アクションを失敗させます。 監査イベントを発生させないアクションは続行できますが、監査イベントは発生しません。 監査は、エラー状態が解決される場合に、イベントと再開をログに記録し続けます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]へのフル アクセスより、完全な監査の維持の方が重要である場合に、このオプションを使用します。  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]

 AUDIT_GUID =*uniqueidentifier*  
 監査には、データベース ミラーリングなどのシナリオをサポートするために、ミラーリングされたデータベースで見つかった GUID と照合する特定の GUID が必要です。 この GUID は、監査が作成されると変更できなくなります。  
  
 predicate_expression  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 イベントを処理する必要があるかどうかを判定するために使用する述語式を指定します。 述語式は 3,000 文字に制限され、これにより文字列引数が制限されます。  
  
 event_field_name  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 述語ソースを識別するイベント フィールドの名前を指定します。 監査フィールドについては、「 [sys.fn_get_audit_file &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). 除くすべてのフィールドをフィルター処理できます`file_name`、 `audit_file_offset`、および`event_time`です。  

> [!NOTE]  
>  中に、`action_id`と`class_type`型のフィールドは、 **varchar** sys.fn_get_audit_file で、のみ使用できますの数字でフィルター処理の述語ソースがあるときにします。 使用する値の一覧を取得する`class_type`、次のクエリを実行します。  
> ```sql
> SELECT spt.[name], spt.[number]
> FROM   [master].[dbo].[spt_values] spt
> WHERE  spt.[type] = N'EOD'
> ORDER BY spt.[name];
> ```


 number  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 任意の数値型を含む**decimal**です。 制限として、使用可能な物理メモリの不足、または 64 ビット整数として表すのに大きすぎる数字が挙げられます。  
  
 ' string '  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 述語の比較に必要な ANSI 文字列または Unicode 文字列です。 述語比較関数に対しては、暗黙の文字列型変換は行われません。 無効な型を渡すとエラーになります。  
  
## <a name="remarks"></a>解説  
 作成されたサーバー監査は無効な状態です。  
  
 CREATE SERVER AUDIT ステートメントはトランザクションのスコープ内にあります。 トランザクションがロールバックされると、ステートメントもロールバックされます。  
  
## <a name="permissions"></a>権限  
 サーバー監査を作成、変更、または削除する場合、プリンシパルには、ALTER ANY SERVER AUDIT または CONTROL SERVER の権限が必要です。  
  
 改ざんを防止するために監査情報をファイルに保存する場合は、そのファイルの場所へのアクセスを制限します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-server-audit-with-a-file-target"></a>A. ファイル ターゲットを使用するサーバー監査を作成する  
 次の例では、バイナリ ファイルをターゲットとする `HIPPA_Audit` というサーバー監査を、オプションなしで作成します。  
  
```sql  
CREATE SERVER AUDIT HIPAA_Audit  
    TO FILE ( FILEPATH ='\\SQLPROD_1\Audit\' );  
```  
  
### <a name="b-creating-a-server-audit-with-a-windows-application-log-target-with-options"></a>B. Windows アプリケーション ログ ターゲットを使用するサーバー監査をオプション付きで作成する  
 次の例と呼ばれるサーバー監査を作成する`HIPPA_Audit`Windows アプリケーション ログの設定、ターゲットとします。 キューが毎秒が書き込まれ、シャット ダウン、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー発生時にエンジンです。  
  
```sql  
CREATE SERVER AUDIT HIPAA_Audit  
    TO APPLICATION_LOG  
    WITH ( QUEUE_DELAY = 1000,  ON_FAILURE = SHUTDOWN);  
```  
  
###  <a name="ExampleWhere"></a> C. WHERE 句を含むサーバー監査を作成する  
 次の例では、データベース、スキーマ、およびサンプルの 2 つのテーブルを作成します。 という名前のテーブル`DataSchema.SensitiveData`機密データを含むテーブルへのアクセスの監査記録が必要とします。 という名前のテーブル`DataSchema.GeneralData`機密データは含まれません。 データベース監査の仕様のすべてのオブジェクトへのアクセスを監査する、`DataSchema`スキーマです。 サーバー監査の対象を `SensitiveData` テーブルのみに制限する WHERE 句付きで、サーバー監査が作成されます。 サーバー監査の前提に、監査フォルダーが存在する`C:\SQLAudit`です。  
  
```sql  
CREATE DATABASE TestDB;  
GO  
USE TestDB;  
GO  
CREATE SCHEMA DataSchema;  
GO  
CREATE TABLE DataSchema.GeneralData (ID int PRIMARY KEY, DataField varchar(50) NOT NULL);  
GO  
CREATE TABLE DataSchema.SensitiveData (ID int PRIMARY KEY, DataField varchar(50) NOT NULL);  
GO  
-- Create the server audit in the master database  
USE master;  
GO  
CREATE SERVER AUDIT AuditDataAccess  
    TO FILE ( FILEPATH ='C:\SQLAudit\' )  
    WHERE object_name = 'SensitiveData' ;  
GO  
ALTER SERVER AUDIT AuditDataAccess WITH (STATE = ON);  
GO  
-- Create the database audit specification in the TestDB database  
USE TestDB;  
GO  
CREATE DATABASE AUDIT SPECIFICATION [FilterForSensitiveData]  
FOR SERVER AUDIT [AuditDataAccess]   
ADD (SELECT ON SCHEMA::[DataSchema] BY [public])  
WITH (STATE = ON);  
GO  
-- Trigger the audit event by selecting from tables  
SELECT ID, DataField FROM DataSchema.GeneralData;  
SELECT ID, DataField FROM DataSchema.SensitiveData;  
GO  
-- Check the audit for the filtered content  
SELECT * FROM fn_get_audit_file('C:\SQLAudit\AuditDataAccess_*.sqlaudit',default,default);  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER SERVER AUDIT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [サーバー監査の仕様 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [データベース監査の仕様 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [サーバー監査およびサーバー監査の仕様を作成する](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
