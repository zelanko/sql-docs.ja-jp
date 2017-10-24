---
title: "ALTER SERVER AUDIT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SERVER_AUDIT_TSQL
- ALTER SERVER AUDIT
dev_langs:
- TSQL
helpviewer_keywords:
- server audit [SQL Server]
- audits [SQL Server], specification
- ALTER SERVER AUDIT statement
ms.assetid: 63426d31-7a5c-4378-aa9e-afcf4f64ceb3
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d2522a2876165f8e18222f2268dad091a6ba342
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-server-audit--transact-sql"></a>ALTER SERVER AUDIT (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  サーバー監査オブジェクトを使用して、変更、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]監査機能します。 詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ALTER SERVER AUDIT audit_name  
{  
    [ TO { { FILE ( <file_options> [, ...n] ) } | APPLICATION_LOG | SECURITY_LOG } ]  
    [ WITH ( <audit_options> [ , ...n] ) ]   
    [ WHERE <predicate_expression> ]  
}  
| REMOVE WHERE  
| MODIFY NAME = new_audit_name  
[ ; ]  
  
<file_options>::=  
{  
      FILEPATH = 'os_file_path'   
    | MAXSIZE = { max_size { MB | GB | TB } | UNLIMITED }   
    | MAX_ROLLOVER_FILES = { integer | UNLIMITED }   
    | MAX_FILES = integer   
    | RESERVE_DISK_SPACE = { ON | OFF }   
}  
  
<audit_options>::=  
{  
      QUEUE_DELAY = integer   
    | ON_FAILURE = { CONTINUE | SHUTDOWN | FAIL_OPERATION }   
    | STATE = = { ON | OFF }   
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
 TO {FILE | APPLICATION_LOG | SECURITY}  
 監査ターゲットの場所を指定します。 オプションは、バイナリ ファイル、Windows アプリケーション ログまたは Windows セキュリティ ログです。  
  
 FILEPATH **= '***os_file_path***'**  
 監査記録のパス。 ファイル名は、監査名と監査 GUID に基づいて生成されます。  
  
 MAXSIZE  **=**  *max_size*  
 監査ファイルのサイズの上限を指定します。 *Max_size*値が続く整数を指定する必要があります**MB**、 **GB**、 **TB**、または**無制限**です。 に対して指定できる最小サイズ*max_size* 2 は、 **MB** 、最大数は 2,147, 483,647 **TB**です。 ときに**無制限**が指定されているディスクがいっぱいになるまでに、ファイルが拡張されます。 2 MB より小さい値を指定すると、MSG_MAXSIZE_TOO_SMALL エラーを発生させます。 既定値は**無制限**です。  
  
 MAX_ROLLOVER_FILES  **=** *整数* | **無制限**  
 ファイル システム内に保持するファイルの最大数を指定します。 ときに max_rollover_files 設定 = 0、作成されるロール オーバー ファイルの数に課せられる制限はありません。 既定値は 0 です。 指定できるファイルの最大数は 2,147,483,647 です。  
  
 MAX_FILES =*整数*  
 作成できる監査ファイルの最大数を指定します。 持ち越されません最初のファイルに制限に達したときにします。 MAX_FILES の制限に達すると、追加の監査イベントを生成させる原因となる任意のアクションはエラーで失敗します。  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 RESERVE_DISK_SPACE  **=**  {ON |オフ}  
 このオプションは、ディスク上のファイルを MAXSIZE 値に事前に割り当てます。 MAXSIZE が UNLIMITED でない場合にのみ適用されます。 既定値は OFF です。  
  
 QUEUE_DELAY  **=** *整数*  
 監査アクションの処理が強制されるまでの経過時間 (ミリ秒) を指定します。 値 0 は同期配信を表します。 クエリ遅延に設定可能な最小値は 1000 (1 秒) で、これが既定値です。 最大値は 2,147,483,647 (2,147,483.647 秒、つまり 24 日、20 時間、31 分、23.647 秒) です。 無効な数値を指定すると、MSG_INVALID_QUEUE_DELAY エラーを発生させます。  
  
 ON_FAILURE  **=**  {続行 |シャット ダウン |FAIL_OPERATION}  
 かを示しますインスタンスのターゲットへの書き込み必要がありますが失敗する、続行するには場合、停止[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]監査ログに書き込むことはできません。  
  
 CONTINUE  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 操作を続行します。 監査レコードは保持されません。 監査は、エラー状態が解決される場合に、イベントと再開をログに記録し続けます。 続行のオプションを選択すると、セキュリティ ポリシーに違反する可能性がありますを許すおそれのアクティビティを許可できます。 完全な監査を維持することより、[!INCLUDE[ssDE](../../includes/ssde-md.md)]の操作を続行することの方が重要である場合に、このオプションを使用します。  
  
SHUTDOWN  
インスタンスを強制的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をシャット ダウン、if[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]監査ターゲットに何らかの理由のデータの書き込みに失敗します。 実行しているログイン、`ALTER`ステートメントが必要、`SHUTDOWN`内で権限[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 シャット ダウンの問題が解決しない場合でも、`SHUTDOWN`実行されているログインから権限を取り消す以降。 ユーザーは、このアクセス許可を持っていない場合は、ステートメントが失敗し、監査は変更されません。 監査エラーによってシステムのセキュリティまたは整合性が阻害される可能性がある場合に、このオプションを使用します。 詳細については、次を参照してください。[シャット ダウン](../../t-sql/language-elements/shutdown-transact-sql.md)です。 
  
 FAIL_OPERATION  
 監査イベントを発生させるデータベース アクションを失敗させます。 監査イベントを発生させないアクションは続行できますが、監査イベントは発生しません。 監査は、エラー状態が解決される場合に、イベントと再開をログに記録し続けます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]へのフル アクセスより、完全な監査の維持の方が重要である場合に、このオプションを使用します。  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]   
  
 状態 **=**  {ON |オフ}  
 監査によるレコードの収集を有効または無効にします。 実行中の監査の状態を (ON から OFF に) 変更すると、監査が停止されたこと、監査を停止したプリンシパル、および監査が停止された時間を表す監査エントリが作成されます。  
  
 MODIFY NAME = *new_audit_name*  
 監査の名前を変更します。 他のオプションと組み合わせて使用することはできません。  
  
 predicate_expression  
 イベントを処理する必要があるかどうかを判定するために使用する述語式を指定します。 述語式は 3,000 文字に制限され、これにより文字列引数が制限されます。  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 event_field_name  
 述語ソースを識別するイベント フィールドの名前を指定します。 監査フィールドについては、「 [sys.fn_get_audit_file & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). `file_name` と `audit_file_offset` 以外のすべてのフィールドは、監査できます。  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 number  
 任意の数値型を含む**decimal**です。 制限として、使用可能な物理メモリの不足、または 64 ビット整数として表すのに大きすぎる数字が挙げられます。  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ' string '  
 述語の比較に必要な ANSI 文字列または Unicode 文字列です。 述語比較関数に対しては、暗黙の文字列型変換は行われません。 無効な型を渡すとエラーになります。  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
## <a name="remarks"></a>解説  
 ALTER AUDIT を呼び出すときは、TO 句、WITH 句、MODIFY NAME 句のうち少なくとも 1 つを指定する必要があります。  
  
 監査を変更する場合は、監査の状態を OFF オプションに設定する必要があります。 状態以外のオプションで、監査が有効な場合は、ALTER AUDIT を実行している場合 = OFF、MSG_NEED_AUDIT_DISABLED エラー メッセージが表示されます。  
  
 監査仕様の追加、変更、および削除は、監査を停止せずに実行できます。  
  
 監査を作成した後で、監査の GUID を変更することはできません。  
  
## <a name="permissions"></a>Permissions  
 サーバー監査のプリンシパルを作成、変更、または削除するには、ALTER ANY SERVER AUDIT 権限または CONTROL SERVER 権限を持っている必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-a-server-audit-name"></a>A. サーバー監査の名前を変更する  
 次の例は、サーバー監査の名前を変更`HIPPA_Audit`に`HIPAA_Audit_Old`です。  
  
```  
USE master  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
WITH (STATE = OFF);  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
MODIFY NAME = HIPAA_Audit_Old;  
GO  
ALTER SERVER AUDIT HIPAA_Audit_Old  
WITH (STATE = ON);  
GO  
```  
  
### <a name="b-changing-a-server-audit-target"></a>B. サーバー監査のターゲットを変更する  
 次の例では、`HIPPA_Audit` というサーバー監査を、ファイル ターゲットに変更します。  
  
```  
USE master  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
WITH (STATE = OFF);  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
TO FILE (FILEPATH ='\\SQLPROD_1\Audit\',  
          MAXSIZE = 1000 MB,  
          RESERVE_DISK_SPACE=OFF)  
WITH (QUEUE_DELAY = 1000,  
       ON_FAILURE = CONTINUE);  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
WITH (STATE = ON);  
GO  
```  
  
### <a name="c-changing-a-server-audit-where-clause"></a>C. サーバー監査 WHERE 句を変更する  
 次の例は、where 句の例 C で作成した[CREATE SERVER AUDIT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-audit-transact-sql.md). 新しい WHERE 句は、27 の場合は、ユーザー定義のイベントのフィルター処理します。  
  
```tsql  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = OFF)  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData]  
WHERE user_defined_event_id = 27;  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = ON);  
GO  
```  
  
### <a name="d-removing-a-where-clause"></a>D. WHERE 句を削除する  
 次の例では、WHERE 句の述語式を削除します。  
  
```tsql  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = OFF)  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData]  
REMOVE WHERE;  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = ON);  
GO  
```  
  
### <a name="e-renaming-a-server-audit"></a>E. サーバー監査の名前を変更します。  
 次の例では、サーバー監査の名前を `FilterForSensitiveData` から `AuditDataAccess` に変更します。  
  
```tsql  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = OFF)  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData]  
MODIFY NAME = AuditDataAccess;  
GO  
ALTER SERVER AUDIT [AuditDataAccess] WITH (STATE = ON);  
GO  
```  
  
## <a name="see-also"></a>参照  
 [DROP SERVER AUDIT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-server-audit-transact-sql.md)   
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
 [サーバー監査およびサーバー監査の仕様を作成する](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  

