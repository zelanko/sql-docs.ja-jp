---
title: "トランザクション (SQL データ ウェアハウス) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 87e5e593-a121-4428-9d3c-3af876224e35
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4ea7244857dcd25b1e36f3420811ef035d4ee3b2
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="transactions-sql-data-warehouse"></a>トランザクション (SQL データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  トランザクションが完全にコミットまたは完全にロールバックを 1 つまたは複数のデータベースのステートメントのグループとは。 各トランザクションは、分割不可能な一貫性のある、分離性、および持続性 (ACID)。 トランザクションが成功すると、その中のすべてのステートメントがコミットされます。 トランザクションが失敗するがある場合、グループ内のステートメントの少なくとも 1 つが失敗した場合は、グループ全体がロールバックします。  
  
 先頭と末尾のトランザクションは、自動コミット設定と BEGIN TRANSACTION、COMMIT、および ROLLBACK ステートメントによって異なります。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] では、次の種類のトランザクションがサポートされています。  
  
-   BEGIN TRANSACTION ステートメントで始まり、COMMIT または ROLLBACK ステートメントで終了する、*明示的なトランザクション*。  
  
-   セッション内で自動的に開始して、BEGIN TRANSACTION ステートメントでは開始されない、*自動コミット トランザクション*。 自動コミット設定が ON の場合は、各ステートメントは、トランザクションで実行され、明示的にコミットまたはロールバックする必要はありません。 自動コミット設定が OFF の場合、COMMIT または ROLLBACK ステートメントが、トランザクションの結果を決定するために必要です。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] では、自動コミット トランザクションは、COMMIT または ROLLBACK ステートメントのすぐ後、または SET OFF ステートメントの後に開始します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
BEGIN TRANSACTION [;]  
COMMIT [ TRAN | TRANSACTION | WORK ] [;]  
ROLLBACK [ TRAN | TRANSACTION | WORK ] [;]  
SET AUTOCOMMIT { ON | OFF } [;]  
SET IMPLICIT_TRANSACTIONS { ON | OFF } [;]  
```  
  
## <a name="arguments"></a>引数  
 BEGIN TRANSACTION  
 明示的なトランザクションの開始位置をマークします。  
  
 コミット [作業]  
 明示的または自動コミット トランザクションの最後をマークします。 このステートメントでは、データベースに完全にコミットされるトランザクションで変更が発生します。 ステートメントのコミットは、COMMIT WORK、COMMIT TRAN、COMMIT TRANSACTION と同じです。  
  
 [作業] のロールバック  
 トランザクションの先頭に、トランザクションをロールバックします。 トランザクションの変更は、データベースにコミットではありません。 ステートメントのロールバックは、ROLLBACK WORK、ROLLBACK TRAN、および ROLLBACK TRANSACTION と同じです。  
  
 SET AUTOCOMMIT { **ON** | OFF }  
 トランザクションの開始し、終了の方法を決定します。  
  
 ON  
 各ステートメントが、独自のトランザクションで実行して、COMMIT または ROLLBACK の明示的なステートメントは必要ありません。 明示的なトランザクションは、自動コミットが ON の場合は許可します。  
  
 OFF  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] は、トランザクションがまだ開始されていない場合、自動的にトランザクションを開始します。 すべての後続のステートメントは、トランザクションの一部として実行して、コミットまたはロールバックには、トランザクションの結果を特定する必要があります。 この操作モードでトランザクションがコミットまたはロールバックするとすぐに、モードは OFF のまま、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] によって新しいトランザクションを開始されます。 明示的なトランザクションでは、自動コミットが OFF の場合は使用できません。  
  
 アクティブなトランザクション内での自動コミット設定を変更する場合、設定は、現在のトランザクションには影響しに影響を受け取らない場合、トランザクションが完了するまでします。  
  
 自動コミットが ON の場合は、別のセットの自動コミット ON ステートメントを実行しても効果はありません。 同様に、自動コミットが OFF の場合は、もう 1 つ設定自動コミットを実行している効果はありません。  
  
 SET IMPLICIT_TRANSACTIONS { ON | **OFF** }  
 これは、設定の自動コミットとして同じモードを切り替えます。 SET IMPLICIT_TRANSACTIONS が ON の場合は、接続は暗黙のトランザクション モードに設定されます。 オフ、それを返す場合、接続自動コミット モードにします。  詳細については、「[SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 トランザクション関連のステートメントを実行するのには、特定のアクセス許可は必要ありません。 トランザクション内でステートメントを実行するには、権限が必要です。  
  
## <a name="error-handling"></a>エラー処理  
 コミットまたはロールバックが実行され、アクティブなトランザクションが存在しない場合、エラーが発生します。  
  
 トランザクションの中に進行状況は、BEGIN TRANSACTION が実行される場合は、エラーが発生します。 これは、ような状況は、成功の BEGIN TRANSACTION ステートメントの後、またはセッションが自動コミット オフの設定の下にある場合、BEGIN TRANSACTION が発生した場合に発生します。  
  
 ステートメントの実行時エラー以外のエラーによりトランザクションを正常に完了できない場合、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] によってトランザクションが自動的にロールバックされ、そのトランザクションで保持されていたすべてのリソースが解放されます。 たとえば、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] のインスタンスへのクライアントのネットワーク接続が切断された場合、またはクライアントがアプリケーションからログオフした場合、ネットワークからインスタンスにこの切断が通知されると、その接続に対する未処理のトランザクションがすべてロールバックされます。  
  
 バッチでステートメントの実行時エラーが発生した場合、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] は **ON** に設定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**XACT_ABORT** と一致する動作をし、トランザクション全体がロールバックされます。 **XACT_ABORT** 設定の詳細については、「[SET XACT_ABORT (Transact-SQL)](http://msdn.microsoft.com/library/ms188792.aspx)」を参照してください。  
  
## <a name="general-remarks"></a>全般的な解説  
 セッションでは 1 つのトランザクションを特定の時点でのみ実行できます。保存のポイントと入れ子になったトランザクションはサポートされていません。  
  
 [!INCLUDE[DWsql](../../includes/dwsql-md.md)] のプログラマは、トランザクションで参照されるすべてのデータが論理的に正しいことを確認したうえで COMMIT を実行する必要があります。  
  
 セッションが終了すると、トランザクションが完了する前に、トランザクションがロールバックされます。  
  
 トランザクション モードは、セッション レベルで管理されます。 たとえば、1 つのセッションは明示的なトランザクションを開始する自動コミットを OFF に設定します。 または、IMPLICIT_TRANSACTIONS が ON に設定、影響を与えません他の任意のセッションのトランザクション モードにします。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 COMMIT ステートメントが発行されると、データが変更されて、データベースの永続的な一部であるために、トランザクションはロールバックできません。  
  
 [CREATE DATABASE &#40;Azure SQL Data Warehouse&#41;](../../t-sql/statements/create-database-azure-sql-data-warehouse.md) コマンドと [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md) コマンドは、明示的なトランザクション内で使用することはできません。  
  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] にはトランザクションの共有メカニズムはありません。 これは、ことで、特定の時点におけるセッションの 1 つだけことができますに行う任意のトランザクションに対する作業システムのことを意味します。  
  
## <a name="locking-behavior"></a>ロック動作  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] では、複数のユーザーが同時にアクセスしたときにトランザクションの整合性を保証し、データベースの一貫性を保つため、ロックを使用します。 ロックは、暗黙的および明示的なトランザクションで使用されます。 各トランザクションでは、テーブルや、トランザクションが依存しているデータベースなどのリソース上で異なる種類のロックを要求します。 すべての [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ロックはテーブル レベル以上です。 ロックをかけると、ロックを要求したトランザクションにとって問題になるようなリソースの変更が行われないように、他のトランザクションがブロックされます。 各トランザクションは、ロックされたリソースの依存関係が不要になったがあるロックを解放します。明示的なトランザクションは、それがコミットまたはロールバック時に、トランザクションが完了するまで、ロックを保持します。  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-using-an-explicit-transaction"></a>A. 明示的なトランザクションを使用します。  
  
```  
BEGIN TRANSACTION;  
DELETE FROM HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
COMMIT;  
```  
  
### <a name="b-rolling-back-a-transaction"></a>B. トランザクションのロールバック  
 次の例では、トランザクションのロールバックの効果を示します。  この例で ROLLBACK ステートメントがロールバックされます、INSERT ステートメントでは、作成されたテーブルはそのまま残ります。  
  
```  
CREATE TABLE ValueTable (id int);  
BEGIN TRANSACTION;  
       INSERT INTO ValueTable VALUES(1);  
       INSERT INTO ValueTable VALUES(2);  
ROLLBACK;  
```  
  
### <a name="c-setting-autocommit"></a>C. 自動コミットの設定  
 次の例では、自動コミット設定を `ON` に設定します。  
  
```  
SET AUTOCOMMIT ON;  
```  
  
 次の例では、自動コミット設定を `OFF` に設定します。  
  
```  
SET AUTOCOMMIT OFF;  
```  
  
### <a name="d-using-an-implicit-multi-statement-transaction"></a>D. 複数ステートメントの暗黙のトランザクションを使用します。  
  
```  
SET AUTOCOMMIT OFF;  
CREATE TABLE ValueTable (id int);  
INSERT INTO ValueTable VALUES(1);  
INSERT INTO ValueTable VALUES(2);  
COMMIT;  
```  
  
## <a name="see-also"></a>参照  
 [SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  
