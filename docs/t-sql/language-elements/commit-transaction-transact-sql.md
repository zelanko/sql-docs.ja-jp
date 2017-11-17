---
title: "COMMIT TRANSACTION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/09/2016
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COMMIT
- COMMIT TRANSACTION
- COMMIT_TSQL
- COMMIT_TRANSACTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ending transactions [SQL Server]
- user-defined transactions [SQL Server]
- committed transactions
- transactions [SQL Server], ending
- marking end of transactions [SQL Server]
- implicit transactions
- distributed transactions [SQL Server], committed
- transactions [SQL Server], committed
- COMMIT TRANSACTION statement
- rolling back transactions, COMMIT TRANSACTION
ms.assetid: f8fe26a9-7911-497e-b348-4e69c7435dc1
caps.latest.revision: 53
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 84ca8221700d3eabd443b84d97dea4f698e9f945
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="commit-transaction-transact-sql"></a>COMMIT TRANSACTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  正常終了した暗黙的または明示的なトランザクションの終点をマークします。 @ If@TRANCOUNT 1、COMMIT TRANSACTION では、データベースの一部として、トランザクションの開始、トランザクション、および @ デクリメントによって保持されているリソースを解放するためにすべてのデータ変更が実行されるは@TRANCOUNTを 0 にします。 @ If@TRANCOUNT @ 1 の場合、COMMIT TRANSACTION デクリメントより大きい@TRANCOUNT1 と、トランザクションでのみアクティブに保ちます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Applies to SQL Server (starting with 2008) and Azure SQL Database
  
COMMIT [ { TRAN | TRANSACTION }  [ transaction_name | @tran_name_variable ] ] [ WITH ( DELAYED_DURABILITY = { OFF | ON } ) ]  
[ ; ]  
```  
 
```  
-- Applies to Azure SQL Data Warehouse and Parallel Data Warehouse Database
  
COMMIT [ TRAN | TRANSACTION ] 
[ ; ]  
``` 
 
  
## <a name="arguments"></a>引数  
 *では無視*  
 **適用対象:** SQL Server と Azure SQL Database
 
 は無視されます、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]です。 *では無視*前の BEGIN TRANSACTION により割り当てられるトランザクション名を指定します。 *では無視*識別子の規則に従う必要がありますが、32 文字を超えることはできません。 *では無視*プログラマは、BEGIN TRANSACTION と COMMIT TRANSACTION の関連を入れ子になったに指定することにより、読みやすさを目的として使用できます。  
  
 *@tran_name_variable*  
 **適用対象:** SQL Server と Azure SQL Database  
 
有効なトランザクション名を格納しているユーザー定義変数の名前を指定します。 Char、varchar、nchar、または nvarchar データ型では、変数を宣言する必要があります。 変数に 32 文字を超える文字が渡された場合は、32 文字だけが使用され、残りの文字は切り捨てられます。  
  
 DELAYED_DURABILITY  
 **適用対象:** SQL Server と Azure SQL Database   

 このトランザクションを持続性が遅延した状態でコミットすることを要求するオプション。 データベースがによって変更されている場合、要求は無視されます`DELAYED_DURABILITY = DISABLED`または`DELAYED_DURABILITY = FORCED`です。 トピックを参照して[トランザクションの持続性の制御](../../relational-databases/logs/control-transaction-durability.md)詳細についてはします。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] のプログラマは、トランザクションで参照されるすべてのデータが論理的に正しいことを確認したうえで COMMIT TRANSACTION を実行する必要があります。  
  
 トランザクションがコミットされた場合、[!INCLUDE[tsql](../../includes/tsql-md.md)]分散トランザクションをコミット トランザクションが 2 フェーズ コミット プロトコルを使用して、すべてのトランザクションに関係するサーバーのコミットに MS DTC をトリガーします。 ローカル トランザクションで、[!INCLUDE[ssDE](../../includes/ssde-md.md)]の同じインスタンス上にある 2 つ以上のデータベースが対象となっている場合、インスタンスでは内部の 2 フェーズ コミットにより、トランザクションに参加しているすべてのデータベースがコミットされます。  
  
 入れ子にされたトランザクションで使用する場合は、入れ子内のトランザクションをコミットしてもリソースは解放されず、修正も永久保存されません。 データ修正が永久保存され、リソースが解放されるのは、入れ子の外側のトランザクションをコミットした場合だけです。 各 COMMIT TRANSACTION を発行時に @@TRANCOUNT 1 だけデクリメント @ より大きい@TRANCOUNTを 1 つです。 場合 @@TRANCOUNTは外側のトランザクション全体がコミットされた最後にデクリメントを 0 にします。 *では無視*では無視されます、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、@ だけデクリメント未処理の内側のトランザクションがある場合は、外側のトランザクションの名前を参照する COMMIT TRANSACTION を発行@TRANCOUNTを 1 つです。  
  
 COMMIT TRANSACTION を発行時に @@TRANCOUNTエラー結果が 0 です。 対応する BEGIN TRANSACTION がありません。  
  
 COMMIT TRANSACTION ステートメントの実行後は、データ修正がデータベースに永久保存されるので、トランザクションをロールバックすることはできません。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]ステートメントの開始時点のトランザクション数が 0 の場合にのみ、ステートメント内でトランザクション数が増加します。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-committing-a-transaction"></a>A. トランザクションをコミットする  
**適用対象:** SQL Server、Azure SQL Database、Azure SQL Data Warehouse、および並列データ ウェアハウス   

次の例では、ジョブ候補を削除します。 AdventureWorks を使用します。 
  
```   
BEGIN TRANSACTION;   
DELETE FROM HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;   
COMMIT TRANSACTION;   
```  
  
### <a name="b-committing-a-nested-transaction"></a>B. 入れ子になったトランザクションをコミットする  
**適用対象:** SQL Server と Azure SQL Database    

次の例では、テーブルを作成し、3 レベルの入れ子にされたトランザクションを生成してから、入れ子になったトランザクションをコミットします。 各`COMMIT TRANSACTION`ステートメントでは、*では無視*パラメーター間の関係はありません、`COMMIT TRANSACTION`と`BEGIN TRANSACTION`ステートメントです。 *では無視*パラメーターは、単に参考情報として適切なコミット数がデクリメントするためにコード化されたことを確認してください。 プログラマが役立つ`@@TRANCOUNT`を 0 になり、その結果、外側のトランザクションをコミットします。 
  
```   
IF OBJECT_ID(N'TestTran',N'U') IS NOT NULL  
    DROP TABLE TestTran;  
GO  
CREATE TABLE TestTran (Cola int PRIMARY KEY, Colb char(3));  
GO  
-- This statement sets @@TRANCOUNT to 1.  
BEGIN TRANSACTION OuterTran;  
  
PRINT N'Transaction count after BEGIN OuterTran = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
 
INSERT INTO TestTran VALUES (1, 'aaa');  
 
-- This statement sets @@TRANCOUNT to 2.  
BEGIN TRANSACTION Inner1;  
 
PRINT N'Transaction count after BEGIN Inner1 = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
  
INSERT INTO TestTran VALUES (2, 'bbb');  
  
-- This statement sets @@TRANCOUNT to 3.  
BEGIN TRANSACTION Inner2;  
  
PRINT N'Transaction count after BEGIN Inner2 = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
  
INSERT INTO TestTran VALUES (3, 'ccc');  
  
-- This statement decrements @@TRANCOUNT to 2.  
-- Nothing is committed.  
COMMIT TRANSACTION Inner2;  
 
PRINT N'Transaction count after COMMIT Inner2 = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
 
-- This statement decrements @@TRANCOUNT to 1.  
-- Nothing is committed.  
COMMIT TRANSACTION Inner1;  
 
PRINT N'Transaction count after COMMIT Inner1 = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
  
-- This statement decrements @@TRANCOUNT to 0 and  
-- commits outer transaction OuterTran.  
COMMIT TRANSACTION OuterTran;  
  
PRINT N'Transaction count after COMMIT OuterTran = '  
    + CAST(@@TRANCOUNT AS nvarchar(10));  
```  
  
## <a name="see-also"></a>参照  
 [BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [BEGIN TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [コミット動作 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [ROLLBACK WORK & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/rollback-work-transact-sql.md)   
 [SAVE TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/save-transaction-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  

