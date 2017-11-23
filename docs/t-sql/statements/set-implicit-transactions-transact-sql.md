---
title: "[SET implicit_transactions] (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IMPLICIT_TRANSACTIONS
- SET IMPLICIT_TRANSACTIONS
- IMPLICIT_TRANSACTIONS_TSQL
- SET_IMPLICIT_TRANSACTIONS_TSQL
dev_langs: TSQL
helpviewer_keywords:
- implicit transactions
- transactions [SQL Server], implicit
- connections [SQL Server], implicit transaction mode
- SET IMPLICIT_TRANSACTIONS statement
- IMPLICIT_TRANSACTIONS option
ms.assetid: a300ac43-e4c0-4329-8b79-a1a05e63370a
caps.latest.revision: "45"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 2d46d60c67556fe5c779fdd4e68e7f4993074198
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="set-implicittransactions-transact-sql"></a>SET IMPLICIT_TRANSACTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  BEGIN TRANSACTION モードに設定*暗黙*、接続します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SET IMPLICIT_TRANSACTIONS { ON | OFF }  
```  
  
## <a name="remarks"></a>解説  
 ときに、システムが*暗黙的な*トランザクション モードです。 つまり、@@TRANCOUNT = 0 で、次の TRANSACT-SQL ステートメントのいずれかが新しいトランザクションを開始します。 これは、最初に実行されている見えない、BEGIN の TRANSACTION と同じです。  
  
||||  
|-|-|-|  
|ALTER TABLE|FETCH|REVOKE|  
|BEGIN TRANSACTION|GRANT|SELECT (以下の例外を参照)|  
|CREATE|INSERT|TRUNCATE TABLE|  
|DELETE|OPEN|UPDATE|  
|DROP|のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。|のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。|  
  
 ときに OFF、上記の T-SQL ステートメントの各に制限されます、含まれる未知の BEGIN TRANSACTION と含まれる未知の COMMIT TRANSACTION ステートメント。 OFF の場合、トランザクション モードは言う*autocommit*です。 T-SQL コードは、視覚的に、BEGIN TRANSACTION を発行した場合、トランザクション モードは言う*明示的な*します。  
  
 理解しておく clarifying いくつかの点があります。  
  
-   トランザクション モードは、暗黙の型が、含まれる未知の BEGIN TRANSACTION が発行されない場合に @@trancount > 0 は既にです。 ただし、明示的な BEGIN TRANSACTION ステートメントが @ 増分値をまだ@TRANCOUNTします。  
  
-   @ まで COMMIT TRANSACTION ステートメントを発行する必要があります、INSERT ステートメントと、作業単位に何が完了したら、@TRANCOUNTが 0 まで戻しますデクリメントします。 または、1 つの ROLLBACK TRANSACTION を発行することができます。  
  
-   テーブルからの選択操作を伴わない SELECT ステートメントでは、暗黙のトランザクションは開始されません。 たとえば、`SELECT GETDATE();` や `SELECT 1, 'ABC';` にトランザクションは不要です。  
  
-   暗黙のトランザクションが予期せずがあります ON ANSI の既定値です。 詳細をご覧ください[SET ANSI_DEFAULTS &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-ansi-defaults-transact-sql.md).  
  
     IMPLICIT_TRANSACTIONS ON は、人気のあるではないです。 IMPLICIT_TRANSACTIONS が ON ほとんどの場合、これは SET ANSI_DEFAULTS の選択が行われたためです。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC ドライバーは、接続時に IMPLICIT_TRANSACTIONS を OFF に自動的に設定します。 SET IMPLICIT_TRANSACTIONS を OFF に、SQLClient マネージ プロバイダーとの接続でと既定で使用する HTTP エンドポイントを介して受信した SOAP 要求します。  
  
 IMPLICIT_TRANSACTIONS の現在の設定を表示するには、次のクエリを実行します。  
  
```  
DECLARE @IMPLICIT_TRANSACTIONS VARCHAR(3) = 'OFF';  
IF ( (2 & @@OPTIONS) = 2 ) SET @IMPLICIT_TRANSACTIONS = 'ON';  
SELECT @IMPLICIT_TRANSACTIONS AS IMPLICIT_TRANSACTIONS;  
```  
  
## <a name="examples"></a>使用例  
 次の TRANSACT-SQL スクリプトは、いくつかの異なるテスト_ケースを実行します。 テキスト出力は動作の詳細を表示され、各テスト・ケースの結果も提供されます。  
  
```tsql  
-- Transact-SQL.  
go  
-- Preparations.  
SET NOCOUNT ON;  
SET IMPLICIT_TRANSACTIONS OFF;  
go  
WHILE (@@TranCount > 0) COMMIT TRANSACTION;  
go  
IF (OBJECT_ID(N'dbo.t1',N'U') IS NOT NULL) DROP TABLE dbo.t1;  
go  
CREATE table dbo.t1 (a int);  
go  
  
PRINT N'-------- [Test A] ---- OFF ----';  
PRINT N'[A.01] Now, SET IMPLICIT_TRANSACTIONS OFF.';  
PRINT N'[A.02] @@TranCount, at start, == ' + CAST(@@TRANCOUNT AS NVARCHAR(10));  
SET IMPLICIT_TRANSACTIONS OFF;  
go  
INSERT INTO dbo.t1 VALUES (11);  
INSERT INTO dbo.t1 VALUES (12);  
PRINT N'[A.03] @@TranCount, after INSERTs, == ' + CAST(@@TRANCOUNT AS NVARCHAR(10));  
go  
  
PRINT N' ';  
PRINT N'-------- [Test B] ---- ON ----';  
PRINT N'[B.01] Now, SET IMPLICIT_TRANSACTIONS ON.';  
PRINT N'[B.02] @@TranCount, at start, == ' + CAST(@@TRANCOUNT AS NVARCHAR(10));  
SET IMPLICIT_TRANSACTIONS ON;  
go  
INSERT INTO dbo.t1 VALUES (21);  
INSERT INTO dbo.t1 VALUES (22);  
PRINT N'[B.03] @@TranCount, after INSERTs, == ' + CAST(@@TRANCOUNT AS NVARCHAR(10));  
go  
COMMIT TRANSACTION;  
PRINT N'[B.04] @@TranCount, after COMMIT, == ' + CAST(@@TRANCOUNT AS NVARCHAR(10));  
go  
  
PRINT N' ';  
PRINT N'-------- [Test C] ---- ON, then BEGIN TRAN ----';  
PRINT N'[C.01] Now, SET IMPLICIT_TRANSACTIONS ON.';  
PRINT N'[C.02] @@TranCount, at start, == ' + CAST(@@TRANCOUNT AS NVARCHAR(10));  
SET IMPLICIT_TRANSACTIONS ON;  
go  
BEGIN TRANSACTION;  
INSERT INTO dbo.t1 VALUES (31);  
INSERT INTO dbo.t1 VALUES (32);  
PRINT N'[C.03] @@TranCount, after INSERTs, == ' + CAST(@@TRANCOUNT AS NVARCHAR(10));  
go  
COMMIT TRANSACTION;  
PRINT N'[C.04] @@TranCount, after a COMMIT, == ' + CAST(@@TRANCOUNT AS NVARCHAR(10));  
COMMIT TRANSACTION;  
PRINT N'[C.05] @@TranCount, after another COMMIT, == ' + CAST(@@TRANCOUNT AS NVARCHAR(10));  
go  
  
PRINT N' ';  
PRINT N'-------- [Test D] ---- ON, INSERT, BEGIN TRAN, INSERT ----';  
PRINT N'[D.01] Now, SET IMPLICIT_TRANSACTIONS ON.';  
PRINT N'[D.02] @@TranCount, at start, == ' + CAST(@@TRANCOUNT AS NVARCHAR(10));  
SET IMPLICIT_TRANSACTIONS ON;  
go  
INSERT INTO dbo.t1 VALUES (41);  
BEGIN TRANSACTION;  
INSERT INTO dbo.t1 VALUES (42);  
PRINT N'[D.03] @@TranCount, after INSERTs, == ' + CAST(@@TRANCOUNT AS NVARCHAR(10));  
go  
COMMIT TRANSACTION;  
PRINT N'[D.04] @@TranCount, after INSERTs, == ' + CAST(@@TRANCOUNT AS NVARCHAR(10));  
COMMIT TRANSACTION;  
PRINT N'[D.05] @@TranCount, after INSERTs, == ' + CAST(@@TRANCOUNT AS NVARCHAR(10));  
go  
  
-- Clean up.  
SET IMPLICIT_TRANSACTIONS OFF;  
go  
WHILE (@@TranCount > 0) COMMIT TRANSACTION;  
go  
DROP TABLE dbo.t1;  
go  
```  
  
 次は、前述の TRANSACT-SQL スクリプトからのテキストの出力です。  
  
```tsql  
-- Text output from Transact-SQL:  
  
-------- [Test A] ---- OFF ----  
[A.01] Now, SET IMPLICIT_TRANSACTIONS OFF.  
[A.02] @@TranCount, at start, == 0  
[A.03] @@TranCount, after INSERTs, == 0  
  
-------- [Test B] ---- ON ----  
[B.01] Now, SET IMPLICIT_TRANSACTIONS ON.  
[B.02] @@TranCount, at start, == 0  
[B.03] @@TranCount, after INSERTs, == 1  
[B.04] @@TranCount, after COMMIT, == 0  
  
-------- [Test C] ---- ON, then BEGIN TRAN ----  
[C.01] Now, SET IMPLICIT_TRANSACTIONS ON.  
[C.02] @@TranCount, at start, == 0  
[C.03] @@TranCount, after INSERTs, == 2  
[C.04] @@TranCount, after a COMMIT, == 1  
[C.05] @@TranCount, after another COMMIT, == 0  
  
-------- [Test D] ---- ON, INSERT, BEGIN TRAN, INSERT ----  
[D.01] Now, SET IMPLICIT_TRANSACTIONS ON.  
[D.02] @@TranCount, at start, == 0  
[D.03] @@TranCount, after INSERTs, == 2  
[D.04] @@TranCount, after INSERTs, == 1  
[D.05] @@TranCount, after INSERTs, == 0  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [BEGIN TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [DROP TABLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-table-transact-sql.md)   
 [フェッチ &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/fetch-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [開く &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/open-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [[SET ansi_defaults] &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)   
 [TRUNCATE TABLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/truncate-table-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  
  
  
