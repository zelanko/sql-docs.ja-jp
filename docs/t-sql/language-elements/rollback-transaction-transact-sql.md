---
title: "ROLLBACK TRANSACTION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ROLLBACK TRANSACTION
- ROLLBACK
- ROLLBACK_TSQL
- ROLLBACK_TRANSACTION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- transaction rollbacks [SQL Server]
- ROLLBACK TRANSACTION statement
- erasing data modifications [SQL Server]
- rolling back transactions, ROLLBACK TRANSACTION
- roll back transactions [SQL Server]
- savepoints [SQL Server]
ms.assetid: 6882c5bc-ff74-476a-984b-164aeb036c66
caps.latest.revision: "52"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: c0480f1c295c45f32f4ca3bdaec761a6bd2fa924
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="rollback-transaction-transact-sql"></a>ROLLBACK TRANSACTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  明示的または暗黙的なトランザクションを、トランザクションの開始位置またはトランザクション内のセーブポイントまでロールバックします。 ROLLBACK TRANSACTION を使用して、トランザクションの開始またはセーブポイント発行時点以降に行われたすべてのデータ変更を消去できます。 トランザクションが保持していたリソースも解放されます。  
  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ROLLBACK { TRAN | TRANSACTION }   
     [ transaction_name | @tran_name_variable  
     | savepoint_name | @savepoint_variable ]   
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *transaction_name*  
 BEGIN TRANSACTION においてトランザクションに割り当てられた名前です。 *では無視*識別子の規則に従う必要がありますが、トランザクション名の最初の 32 文字だけが使用されます。 トランザクションを入れ子にする場合*では無視*最も外側の BEGIN TRANSACTION ステートメントから名前にする必要があります。 *では無視*、大文字小文字を区別は常に場合でも、インスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]小文字は区別されません。  
  
 **@** *tran_name_variable*  
 有効なトランザクション名を格納しているユーザー定義変数の名前を指定します。 変数を宣言する必要があります、 **char**、 **varchar**、 **nchar**、または**nvarchar**データ型。  
  
 *savepoint_name*  
 *Savepoint_name* SAVE TRANSACTION ステートメントからです。 *savepoint_name*識別子の規則に従う必要があります。 使用して*savepoint_name*と条件付きのロールバックには影響は、トランザクションの一部のみです。  
  
 **@** *savepoint_variable*  
 有効なセーブポイント名を格納しているユーザー定義変数の名前です。 変数を宣言する必要があります、 **char**、 **varchar**、 **nchar**、または**nvarchar**データ型。  
  
## <a name="error-handling"></a>エラー処理  
 ROLLBACK TRANSACTION ステートメントでは、ユーザーに対するメッセージは生成されません。 ストアド プロシージャまたはトリガーで警告が必要な場合は、RAISERROR ステートメントまたは PRINT ステートメントを使用します。 エラーを指示するには、RAISERROR ステートメントの方が適しています。  
  
## <a name="general-remarks"></a>全般的な解説  
 せずに ROLLBACK TRANSACTION、 *savepoint_name*または*では無視*トランザクションの先頭にロールバックします。 トランザクションを入れ子にしている場合は、同じステートメントが、内部のすべてのトランザクションを、最も外側の BEGIN TRANSACTION ステートメントにロールバックします。 どちらの場合も、ROLLBACK TRANSACTION デクリメント、@@TRANCOUNTシステム関数を 0 にします。 ROLLBACK TRANSACTION *savepoint_name* @ をデクリメントされません@TRANCOUNTです。  
  
 ROLLBACK TRANSACTION が参照することはできません、 *savepoint_name* BEGIN DISTRIBUTED TRANSACTION で明示的に開始された分散トランザクションにまたはローカル トランザクションのエスカレートします。  
  
 COMMIT TRANSACTION ステートメントの実行後は、トランザクションをロールバックできません。ただし、COMMIT TRANSACTION が、ロールバックするトランザクション内に含まれている入れ子にされたトランザクションに関連付けられている場合を除きます。 このインスタンスで、入れ子になったトランザクションはロールバックの COMMIT TRANSACTION を発行した場合でもされます。  
  
 トランザクションの中で、同じセーブポイント名を重複して指定することができます。しかし、重複するセーブポイント名を使用する ROLLBACK TRANSACTION は、そのセーブポイント名を使用する最新の SAVE TRANSACTION にしかロールバックできません。  
  
## <a name="interoperability"></a>相互運用性  
 ストアド プロシージャ、せずに ROLLBACK TRANSACTION ステートメントで、 *savepoint_name*または*では無視*のすべてのステートメントを最も外側の BEGIN TRANSACTION にロールバックします。 @ 原因となったストアド プロシージャで ROLLBACK TRANSACTION ステートメント@TRANCOUNT別の値よりも、ストアド プロシージャが完了したときに、@@TRANCOUNT値ストアド プロシージャが呼び出されたときに、情報メッセージが生成されます。 このメッセージが出力されても、その後の処理に影響はありません。  
  
 ROLLBACK TRANSACTION がトリガー内で実行された場合  
  
-   現在のトランザクションのその時点までに加えられたすべてのデータ変更 (トリガーによって行われた変更も含む) がロールバックされます。  
  
-   ROLLBACK ステートメントの実行後、トリガーは残りのすべてのステートメントを継続して実行します。 これらのステートメントのいずれかがデータを変更する場合、その変更はロールバックされません。 残りのステートメントを実行しても入れ子にしたトリガーは起動されません。  
  
-   トリガーを起動したステートメントの後で、バッチ内のステートメントは実行されません。  
  
@@TRANCOUNT自動コミット モードにある場合でも、トリガーに入るときに、1 が加算されます。 つまり、トリガーは暗黙の入れ子にされたトランザクションとして扱われます。  
  
ストアド プロシージャで ROLLBACK TRANSACTION ステートメントを実行しても、そのプロシージャを呼び出したバッチ内にある次のステートメントには影響しません。 トリガーの中の ROLLBACK TRANSACTION ステートメントは、トリガーを起動したステートメントを含むバッチを終了します。バッチ内の以降のステートメントは実行されません。  
  
カーソル上での ROLLBACK の効果は、次の 3 つのルールによって定義されます。  
  
1.  CURSOR_CLOSE_ON_COMMIT が ON の場合、ROLLBACK はオープンしているすべてのカーソルをクローズしますが、その割り当ては解除しません。  
  
2.  CURSOR_CLOSE_ON_COMMIT を OFF に設定した場合、ROLLBACK は、オープンしていて同期している静的カーソルおよび非反映型カーソル、あるいは完全に生成されている非同期な静的カーソルのいずれにも影響しません。 他のタイプのオープン カーソルは、クローズしますが、割り当ては解除されません。  
  
3.  バッチを終了し、内部のロールバックを生成するエラーは、エラー ステートメントを含むバッチの中で宣言された、すべてのカーソルの割り当てを解除します。 すべてのカーソルは、そのタイプや CURSOR_CLOSE_ON_COMMIT の設定にかかわらず、割り当てを解除されます。 これには、エラー バッチによって呼び出されるストアド プロシージャで宣言されたカーソルも含まれます。 エラー バッチの前にバッチ内で宣言されたカーソルは、ルール 1 および 2 に従います。 このタイプのエラーの例としてはデッドロック エラーがあります。 トリガーの中で実行される ROLLBACK ステートメントも、このタイプのエラーを自動的に生成します。  
  
## <a name="locking-behavior"></a>ロック動作  
 ROLLBACK TRANSACTION ステートメントの指定、 *savepoint_name*エスカレーションおよび変換を除き、セーブポイントを超える取得されるロックは解放されます。 これらのロックは解放されず、前のロック モードに戻ることはありません。  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、名前付きトランザクションをロールバックした場合の影響を示しています。 テーブルを作成すると、次のステートメント名前付きのトランザクションを開始、2 つの行を挿入し、変数に名前付きトランザクションをロールバックして@TransactionNameです。 名前付きのトランザクションの外部で別のステートメントでは、2 つの行を挿入します。 クエリでは、前のステートメントの結果を返します。   
  
```sql    
USE tempdb;  
GO  
CREATE TABLE ValueTable ([value] int);  
GO  
  
DECLARE @TransactionName varchar(20) = 'Transaction1';  
  
BEGIN TRAN @TransactionName  
       INSERT INTO ValueTable VALUES(1), (2);  
ROLLBACK TRAN @TransactionName;  
  
INSERT INTO ValueTable VALUES(3),(4);  
  
SELECT [value] FROM ValueTable;  
  
DROP TABLE ValueTable;  
```  
[!INCLUDE[ssresult-md](../../includes/ssresult-md.md)]  
```  
value  
-----   
3    
4  
```  
  
  
## <a name="see-also"></a>参照  
 [BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [BEGIN TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [COMMIT TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [コミット動作 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK WORK &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/rollback-work-transact-sql.md)   
 [SAVE TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/save-transaction-transact-sql.md)  
  
  
