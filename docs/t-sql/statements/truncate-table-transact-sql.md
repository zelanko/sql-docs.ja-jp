---
title: "TRUNCATE TABLE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
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
- TRUNCATE
- TRUNCATE TABLE
- TRUNCATE_TSQL
- TRUNCATE_TABLE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- row removal [SQL Server], TRUNCATE TABLE statement
- table truncating [SQL Server]
- removing rows
- TRUNCATE TABLE statement
- deleting rows
- dropping rows
ms.assetid: 3d544eed-3993-4055-983d-ea334f8c5c58
caps.latest.revision: "41"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5523e2797d3f0a69e39f0fb3cdbd70a6f389eed2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="truncate-table-transact-sql"></a>TRUNCATE TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  個々 の行の削除ログに記録せず、テーブルまたはテーブルの指定したパーティションからすべての行を削除します。 TRUNCATE TABLE は、WHERE 句を伴わない DELETE ステートメントに似ています。ただし、TRUNCATE TABLE の方が高速で、使用するシステム リソースとトランザクション ログ リソースも少なくなります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```tsql  
-- Syntax for SQL Server and Azure SQL Database  
  
TRUNCATE TABLE   
    [ { database_name .[ schema_name ] . | schema_name . } ]  
    table_name  
    [ WITH ( PARTITIONS ( { <partition_number_expression> | <range> }   
    [ , ...n ] ) ) ]  
[ ; ]  
  
<range> ::=  
<partition_number_expression> TO <partition_number_expression>  
```  
  
```tsql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
TRUNCATE TABLE [ { database_name . [ schema_name ] . | schema_name . ] table_name  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 データベースの名前です。  
  
 *schema_name*  
 テーブルが所属するスキーマの名前を指定します。  
  
 *table_name*  
 切り捨てるまたはすべての行を削除するテーブルの名前を指定します。 *table_name*リテラルを指定する必要があります。 *table_name*することはできません、 **OBJECT_ID()**関数または変数です。  
  
 使用 (パーティション ({ \< *partition_number_expression*> |\<*範囲*>} [、.. .n]))  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 切り捨てるパーティション、またはすべての行を削除するパーティションを指定します。 テーブルがパーティション分割されていない場合、**でパーティション**引数でエラーが発生します。 場合、**でパーティション**句が指定されていない、テーブル全体が切り捨てられます。  
  
 *\<partition_number_expression >*次のように指定することができます。 
  
-   たとえば、パーティションの数を提供します。`WITH (PARTITIONS (2))`  
  
-   たとえば、コンマで区切られた複数の個別のパーティションのパーティション番号を提供します。`WITH (PARTITIONS (1, 5))`  
  
-   たとえば範囲と個別のパーティションの両方を提供します。`WITH (PARTITIONS (2, 4, 6 TO 8))`  
  
-   *\<範囲 >*パーティション番号、word で区切って指定できます**TO**、例を示します。`WITH (PARTITIONS (6 TO 8))`  
  
 パーティション テーブルの切り捨てを行うためのテーブルとインデックス必要がありますは整列する (同じパーティション関数でパーティション分割された)。  
  
## <a name="remarks"></a>解説  
 DELETE ステートメントと比較して、TRUNCATE TABLE には次の利点があります。  
  
-   トランザクション ログが使用する領域が削減されます。  
  
     DELETE ステートメントは、一度に 1 行ずつ削除し、削除した各行のエントリをトランザクション ログに記録します。 TRUNCATE TABLE は、テーブル データを格納するのに使用するデータ ページの割り当てを解除することによってデータを削除し、ページの割り当ての解除だけをトランザクション ログに記録します。  
  
-   通常、使用されるロックの数が削減されます。  
  
     DELETE ステートメントが行ロックを使用して実行される場合、テーブル内の各行は削除対象としてロックされます。 TRUNCATE TABLE は、(スキーマ (SCH-M) ロックを含め) 常にテーブルとページをロックしますが、行はロックしません。  
  
-   テーブル内にページは一切残されません。  
  
     DELETE ステートメントが実行された後には、テーブルに空のページが残る場合があります。 たとえば、少なくとも 1 つの排他 (LCK_M_X) テーブル ロックを使用しない限り、ヒープ内の空のページの割り当てを解除できません。 削除操作がテーブル ロックを使用しない場合は、テーブル (ヒープ) には多数の空のページが含まれます。 インデックスの場合、削除操作によって空のページが残る場合がありますが、これらのページの割り当てはバックグラウンドのクリーンアップ プロセスによってすばやく解除されます。  
  
 TRUNCATE TABLE はテーブルからすべての行を削除しますが、テーブル構造と、テーブルの列、制約、インデックスなどは残ります。 テーブルのデータとテーブル定義を削除する場合は、DROP TABLE ステートメントを使用します。  
  
 テーブルに ID 列が含まれている場合は、その列に対するカウンターは、その列に対して定義されたシード値にリセットされます。 シードが定義されていなかった場合は、既定値である 1 が使用されます。 ID カウンターを保持するには、代わりに DELETE を使用します。  
  
## <a name="restrictions"></a>制限  
 次のテーブルには TRUNCATE TABLE を使用できません。  
  
-   FOREIGN KEY 制約で参照されるテーブル (それ自体を参照する外部キーを持つテーブルを切り捨てることができます)  
  
-   インデックス付きビューで使用されているテーブル  
  
-   トランザクション レプリケーションとマージ レプリケーションを使用してパブリッシュされているテーブル  
  
 これらの特性を 1 つ以上持つテーブルには、代わりに DELETE ステートメントを使用します。  
  
 TRUNCATE TABLE では、個別の行の削除がログに記録されないため、この操作によってトリガーをアクティブ化することはできません。 詳細については、「[CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)」を参照してください。 
 
 [!INCLUDE[sssdwfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[sspdw](../../includes/sspdw-md.md)]:

- 説明文の中では、TRUNCATE TABLE は許可されていません。

- TRUNCATE TABLE は、トランザクション内で実行できません。
  
## <a name="truncating-large-tables"></a>大きなテーブルの切り捨て  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を削除するか、削除に必要なすべてのエクステントに対する同時ロックを保持することがなく、128 を超えるエクステントを持つテーブルを切り捨てる権限を持ちます。  
  
## <a name="permissions"></a>Permissions  
 必要な最小権限が ALTER *table_name*です。 TRUNCATE TABLE 権限は、特に指定のない限り、テーブル所有者、固定サーバー ロール sysadmin、および固定データベース ロール db_owner および db_ddladmin のメンバーに与えられ、譲渡できません。 ただし、TRUNCATE TABLE ステートメントをストアド プロシージャなどのモジュール内に組み込み、EXECUTE AS 句を使用してそのモジュールに適切な権限を与えることはできます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-truncate-a-table"></a>A. テーブルを切り捨てる  
 次の例では、すべてのデータを`JobCandidate`テーブル。 `SELECT` ステートメントを `TRUNCATE TABLE` ステートメントの前後に挿入して結果を比較しています。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT COUNT(*) AS BeforeTruncateCount   
FROM HumanResources.JobCandidate;  
GO  
TRUNCATE TABLE HumanResources.JobCandidate;  
GO  
SELECT COUNT(*) AS AfterTruncateCount   
FROM HumanResources.JobCandidate;  
GO  
```  
  
### <a name="b-truncate-table-partitions"></a>B. テーブル パーティションを切り捨てる  
  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 次の例では、パーティション分割されたテーブルの指定パーティションを切り捨てます。 `WITH (PARTITIONS (2, 4, 6 TO 8))`構文によりパーティション番号 2、4、6、7、および 8 が切り捨てられます。  
  
```  
TRUNCATE TABLE PartitionTable1   
WITH (PARTITIONS (2, 4, 6 TO 8));  
GO  
```  
  
## <a name="see-also"></a>参照  
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [DROP TABLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-table-transact-sql.md)   
 [IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql-identity-property.md)  
  
  

