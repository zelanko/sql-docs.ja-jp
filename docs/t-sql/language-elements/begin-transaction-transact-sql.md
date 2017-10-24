---
title: "BEGIN TRANSACTION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BEGIN_TRANSACTION_TSQL
- TRANSACTION_TSQL
- TRANSACTION
- BEGIN TRANSACTION
- BEGIN TRAN
- BEGIN_TRAN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transaction logs [SQL Server], BEGIN TRANSACTION statement
- marked transactions [SQL Server], BEGIN TRANSACTION statement
- BEGIN TRANSACTION statement
- local transactions [SQL Server]
- marking transactions [SQL Server]
- transactions [SQL Server], starting
- transaction names [SQL Server]
- starting point marked for transactions
- starting transactions
ms.assetid: c6258df4-11f1-416a-816b-54f98c11145e
caps.latest.revision: 56
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f52f237795de00f4ad78403bed986ac571005c31
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="begin-transaction-transact-sql"></a>BEGIN TRANSACTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  明示的なローカル トランザクションの開始位置をマークします。 明示的なトランザクションでは、BEGIN TRANSACTION ステートメントで起動し、COMMIT または ROLLBACK ステートメントで終了します。  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
--Applies to SQL Server and Azure SQL Database
 
BEGIN { TRAN | TRANSACTION }   
    [ { transaction_name | @tran_name_variable }  
      [ WITH MARK [ 'description' ] ]  
    ]  
[ ; ]  
```  
 
```  
--Applies to Azure SQL Data Warehouse and Parallel Data Warehouse
 
BEGIN { TRAN | TRANSACTION }   
[ ; ]  
```  

  
## <a name="arguments"></a>引数  
 *では無視*  
 **適用対象:** SQL Server (2008年以降)、Azure SQL Database
 
 トランザクションに割り当てられた名前を指定します。 *では無視*識別子は 32 文字は使用できないよりも長い識別子の規則に従う必要があります。 トランザクション名は、入れ子にされた BEGIN...COMMIT ステートメントまたは BEGIN...ROLLBACK ステートメントの最も外側の組だけに使用します。 *では無視*は常に大文字と小文字、場合でも、インスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]大文字小文字は区別されません。  
  
 @*tran_name_variable*  
 **適用対象:** SQL Server (2008年以降)、Azure SQL Database
 
 有効なトランザクション名を格納しているユーザー定義変数の名前を指定します。 変数を宣言する必要があります、 **char**、 **varchar**、 **nchar**、または**nvarchar**データ型。 変数に 32 文字を超える文字が渡された場合は、最初の 32 文字だけが使用され、残りの文字は切り捨てられます。  
  
 WITH MARK ['*説明*']  
**適用対象:** SQL Server (2008年以降)、Azure SQL Database

ログの中でトランザクションにマークを付けます。 *説明*マークを説明する文字列です。 A*説明*られてから msdb.dbo.logmarkhistory テーブルに格納されている 128 文字に切り捨てが 128 文字よりも長い時間です。  
  
 WITH MARK を使用する場合は、トランザクション名を指定する必要があります。 WITH MARK によって、トランザクション ログを指定のマークに復元できます。  
  
## <a name="general-remarks"></a>全般的な解説
BEGIN TRANSACTION はインクリメント@TRANCOUNTを 1 つです。
  
BEGIN TRANSACTION は、接続で参照されるデータが論理的にも物理的にも一貫している位置を表します。 エラーが発生した場合は、BEGIN TRANSACTION 以降に加えられたすべてのデータ修正をロールバックし、一貫性が確認されている状態にデータを戻すことができます。 それぞれのトランザクションの終了時点は、エラーなく完了した場合は COMMIT TRANSACTION を実行して修正内容をデータベースに永久保存した時点になり、エラーが発生した場合は ROLLBACK TRANSACTION ステートメントですべての修正内容を消去した時点になります。  
  
BEGIN TRANSACTION では、ステートメントを実行する接続のローカル トランザクションが開始されます。 この接続で実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントをサポートするため、トランザクションでは多くのリソースが取得されますが、これらのリソースは現在のトランザクション分離レベルの設定に応じてロックされ、COMMIT TRANSACTION または ROLLBACK TRANSACTION ステートメントのいずれかでトランザクションが完了するまでロックされたままになります。 トランザクションが完了するまでの間、他のユーザーはロックされたリソースにアクセスできなくなります。また、ログの切り捨ても行われません。  
  
 BEGIN TRANSACTION ではローカル トランザクションが開始されますが、これはその後アプリケーションで INSERT、UPDATE、DELETE ステートメントなど、ログへの記録が必要な操作が行われるまで、トランザクション ログに記録されません。 アプリケーションでは、ロックの取得などの操作を行って、SELECT ステートメントのトランザクション分離レベルを保護することができます。ただし、アプリケーションで変更操作が行われるまで、ログには何も記録されません。  
  
 1 つのトランザクション名で、何重にも入れ子になったトランザクション内の複数のトランザクションを指定しても、トランザクションに影響はほとんどありません。 システムに登録されるのは、最初の (最も外側の) トランザクション名だけです。 他の名前にロールバックするとエラーが発生します。ただし、有効なセーブポイント名へのロールバックではエラーは発生しません。 このエラーが発生した場合、ロールバック前に実行されたステートメントは一切ロールバックされません。 ステートメントは、外側のトランザクションがロールバックされた場合にのみロールバックされます。  
  
 BEGIN TRANSACTION ステートメントがコミットまたはロールバックされる前に次の操作を実行すると、このステートメントで開始されたローカル トランザクションは、分散トランザクションにエスカレートされます。  
  
-   リンク サーバー上のリモート テーブルを参照する INSERT、DELETE、または UPDATE ステートメントを実行する。 リンク サーバーにアクセスするために使用する OLE DB プロバイダーが ITransactionJoin インターフェイスをサポートしていない場合、INSERT、UPDATE、または DELETE ステートメントが失敗します。  
  
-   REMOTE_PROC_TRANSACTIONS オプションがオンのときに、リモート ストアド プロシージャを呼び出す。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル コピーはトランザクションのコントローラーになり、[!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) を使用して分散トランザクションを管理します。  
  
 BEGIN DISTRIBUTED TRANSACTION を使用して、トランザクションを分散トランザクションとして明示的に実行できます。 詳細については、次を参照してください。 [BEGIN DISTRIBUTED TRANSACTION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md).  
  
 SET IMPLICIT_TRANSACTIONS が ON に設定されている場合、BEGIN TRANSACTION ステートメントは 2 つの入れ子構造のトランザクションを作成します。 詳細については、「 [SET IMPLICIT_TRANSACTIONS & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-implicit-transactions-transact-sql.md)  
  
## <a name="marked-transactions"></a>マーク付きのトランザクション  
 WITH MARK オプションを使用すると、トランザクション名がトランザクション ログに挿入されます。 データベースを以前の状態に復元する場合は、日付や時刻の代わりにマークが付いたトランザクションを使用できます。 詳細については、次を参照してください[関連のデータベースを一貫して復旧 &#40; を使用してマークされたトランザクション。完全復旧モデル &#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)と[復元 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-statements-transact-sql.md).  
  
 さらに、関連するデータベースのセットを論理的に一貫した状態に復元する必要がある場合は、トランザクション ログ マークが必要です。 分散トランザクションによって、関連するデータベースのトランザクション ログにマークを設定できます。 関連するデータベースのセットをこれらのマークに復元すると、トランザクションとして一貫性のあるデータベースのセットが作成されます。 関連するデータベースにマークを設定するには、特別な手順が必要です。  
  
 トランザクション ログにマークが設定されるのは、マーク付きのトランザクションによってデータベースが更新される場合のみです。 データを変更しないトランザクションには、マークは付きません。  
  
 BEGIN TRAN *new_name* WITH MARK は、マークされていない既存のトランザクション内でネストできます。 これを時に*new_name*トランザクションが既に与えられている名前に関係なく、トランザクションのマーク名になります。 次の例では、`M2`マークの名前を指定します。  
  
```  
BEGIN TRAN T1;  
UPDATE table1 ...;  
BEGIN TRAN M2 WITH MARK;  
UPDATE table2 ...;  
SELECT * from table1;  
COMMIT TRAN M2;  
UPDATE table3 ...;  
COMMIT TRAN T1;  
```  
  
 トランザクションを入れ子にしている場合、既にマークが付いているトランザクションにマークを付けようとすると、エラーではなく警告のメッセージが表示されます。  
  
 "BEGIN TRAN T1 WITH MARK ...;"  
  
 "UPDATE table1 ...;"  
  
 "BEGIN TRAN M2 WITH MARK ...;"  
  
 "サーバー: メッセージ 3920、レベル 16、状態 1、行 3"  
  
 "WITH MARK オプションだけが最初の BEGIN TRAN WITH MARK ステートメントに適用されます。"  
  
 "オプションは無視されます。"  
  
## <a name="permissions"></a>Permissions  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-an-explicit-transaction"></a>A. 明示的なトランザクションを使用します。
**適用対象:** SQL Server (2008年以降)、Azure SQL Database、Azure SQL Data Warehouse、Parallel Data Warehouse

この例では、AdventureWorks で使用します。 

```
BEGIN TRANSACTION;  
DELETE FROM HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
COMMIT;  
```

### <a name="b-rolling-back-a-transaction"></a>B. トランザクションのロールバック
**適用対象:** SQL Server (2008年以降)、Azure SQL Database、Azure SQL Data Warehouse、Parallel Data Warehouse

次の例では、トランザクションのロールバックの効果を示します。 この例で ROLLBACK ステートメントがロールバックされます、INSERT ステートメントでは、作成されたテーブルはそのまま残ります。

```
 
CREATE TABLE ValueTable (id int);  
BEGIN TRANSACTION;  
       INSERT INTO ValueTable VALUES(1);  
       INSERT INTO ValueTable VALUES(2);  
ROLLBACK;  

```

### <a name="c-naming-a-transaction"></a>C. トランザクションの名前を指定する 
**適用対象:** SQL Server (2008年以降)、Azure SQL Database

次の例では、トランザクションの名前を指定する方法を示します。  
  
```  
DECLARE @TranName VARCHAR(20);  
SELECT @TranName = 'MyTransaction';  
  
BEGIN TRANSACTION @TranName;  
USE AdventureWorks2012;  
DELETE FROM AdventureWorks2012.HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
  
COMMIT TRANSACTION @TranName;  
GO  
```  
  
### <a name="d-marking-a-transaction"></a>D. トランザクションにマークを付ける  
**適用対象:** SQL Server (2008年以降)、Azure SQL Database

次の例では、トランザクションにマークを付ける方法を示します。 トランザクション`CandidateDelete`がマークされています。  
  
```  
BEGIN TRANSACTION CandidateDelete  
    WITH MARK N'Deleting a Job Candidate';  
GO  
USE AdventureWorks2012;  
GO  
DELETE FROM AdventureWorks2012.HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
GO  
COMMIT TRANSACTION CandidateDelete;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [COMMIT TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [コミット動作 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [ROLLBACK WORK & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/rollback-work-transact-sql.md)   
 [SAVE TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/save-transaction-transact-sql.md)  
  
  

