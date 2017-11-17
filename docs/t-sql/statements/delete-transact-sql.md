---
title: "削除 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DELETE
- DELETE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- row removal [SQL Server]
- DELETE statement [SQL Server], about DELETE statement
- views [SQL Server], deleting rows
- removing rows
- tables [SQL Server], deleting rows
- DELETE statement [SQL Server]
- deleting rows
- row removal [SQL Server], DELETE statement
- deleting data
ms.assetid: ed6b2105-0f35-408f-ba51-e36ade7ad5b2
caps.latest.revision: 78
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 339b84a5362bd2011a557bb2f45e2bee8c3eb101
ms.contentlocale: ja-jp
ms.lasthandoff: 10/24/2017

---
# <a name="delete-transact-sql"></a>DELETE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  テーブルまたはビューから 1 つまたは複数の行を削除[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
[ WITH <common_table_expression> [ ,...n ] ]  
DELETE   
    [ TOP ( expression ) [ PERCENT ] ]   
    [ FROM ]   
    { { table_alias  
      | <object>   
      | rowset_function_limited   
      [ WITH ( table_hint_limited [ ...n ] ) ] }   
      | @table_variable  
    }  
    [ <OUTPUT Clause> ]  
    [ FROM table_source [ ,...n ] ]   
    [ WHERE { <search_condition>   
            | { [ CURRENT OF   
                   { { [ GLOBAL ] cursor_name }   
                       | cursor_variable_name   
                   }   
                ]  
              }  
            }   
    ]   
    [ OPTION ( <Query Hint> [ ,...n ] ) ]   
[; ]  
  
<object> ::=  
{   
    [ server_name.database_name.schema_name.   
      | database_name. [ schema_name ] .   
      | schema_name.  
    ]  
    table_or_view_name   
}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DELETE FROM [database_name . [ schema ] . | schema. ] table_name    
    [ WHERE <search_condition> ]   
    [ OPTION ( <query_options> [ ,...n ]  ) ]  
[; ]  
```  
  
## <a name="arguments"></a>引数  
 \<Common_table_expression >  
 DELETE ステートメントのスコープ内で定義された、一時的な名前付き結果セット (共通テーブル式とも呼ばれる) を指定します。 結果セットは SELECT ステートメントから派生します。  
  
 共通テーブル式は、SELECT、INSERT、UPDATE、CREATE VIEW の各ステートメントでも使用できます。 詳細については、次を参照してください。[で common_table_expression と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 上部**(***式***)** [PERCENT]  
 削除するランダムな行数または比率 (%) を指定します。 *expression* は行数または行の比率 (%) にすることができます。 INSERT、UPDATE、または DELETE を使用する TOP 式で参照される行は、順序付けされません。 詳細については、次を参照してください。 [TOP & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/top-transact-sql.md).  
  
 FROM  
 DELETE キーワードとターゲットの間で使用できるオプションのキーワード*table_or_view_name*、または*rowset_function_limited*です。  
  
 *table_alias*  
 FROM で指定される別名*table_source*句を削除するのには、行をテーブルまたはビューを表します。  
  
 *サーバー名*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 サーバーの名前 (リンク サーバー名を使用して、または[OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md)サーバー名として機能)、テーブルまたはビューが配置されています。 場合*server_name*が指定されている*database_name*と*schema_name*が必要です。  
  
 *database_name*  
 データベースの名前。  
  
 *schema_name*  
 テーブルまたはビューが属するスキーマの名前です。  
  
 *table_or view_name*  
 行を削除するテーブルまたはビューの名前です。  
  
 テーブル変数は、そのスコープ内では、DELETE ステートメントでテーブル ソースとしても使用できます。  
  
 によって参照されるビュー *table_or_view_name*可能にし、ビュー定義の FROM 句内のただ 1 つのベース テーブルを参照する必要があります。 更新可能なビューの詳細については、次を参照してください。 [CREATE VIEW & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-view-transact-sql.md).  
  
 *rowset_function_limited*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 いずれか、 [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md)または[OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)関数、プロバイダーの機能です。  
  
 **(** \<Table_hint_limited > [.*n*] **)**  
 対象のテーブルに設定可能なテーブル ヒントを 1 つ以上指定します。 キーワード WITH とかっこが必要です。 NOLOCK および READUNCOMMITTED は指定できません。 テーブル ヒントの詳細については、次を参照してください。[テーブル ヒント & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/hints-transact-sql-table.md).  
  
 \<OUTPUT_Clause >  
 DELETE 操作の一部として、削除された行または行に基づく式を返します。 OUTPUT 句は、ビューまたはリモート テーブルを対象とする DML ステートメントではサポートされません。 詳細については、次を参照してください。 [OUTPUT 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/output-clause-transact-sql.md).  
  
 *Table_source*  
 追加の FROM 句を指定します。 これは、[!INCLUDE[tsql](../../includes/tsql-md.md)]に削除する拡張機能により、データを指定して\<table_source > し、対応する行では、最初の FROM テーブルから句。  
  
 WHERE 句内のサブクエリを使用する代わりに、この拡張機能で結合を指定して、削除する行を特定できます。  
  
 詳細については、「[FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)」を参照してください。  
  
 WHERE  
 削除する行数を制限するときに使用する条件を指定します。 WHERE 句を指定しない場合は、DELETE によってテーブルからすべての行が削除されます。  
  
 WHERE 句に指定する内容によって、削除操作は次の 2 種類に分けられます。  
  
-   検索結果削除。削除する行を限定する検索条件を指定します。 たとえば、ここで*column_name* = *値*です。  
  
-   位置指定削除。CURRENT OF 句を使用してカーソルを指定します。 削除操作は、カーソルの現在の位置で発生します。 これは、WHERE を使用する検索結果の DELETE ステートメントよりも正確*search_condition*句を削除する行を修飾します。 検索結果削除の DELETE ステートメントでは、検索条件で 1 つの行が一意に識別されない場合、複数の行が削除されます。  
  
\<search_condition >  
 削除する行を制限する条件を指定します。 検索条件に含まれる述語の数に制限はありません。 詳細については、次を参照してください。[検索条件 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/search-condition-transact-sql.md).  
  
 CURRENT OF  
 指定したカーソルの現在位置で DELETE を実行します。  
  
 GLOBAL  
 指定する*cursor_name*はグローバル カーソルを参照します。  
  
 *cursor_name*  
 フェッチが行われるオープン カーソルの名前を指定します。 グローバルとローカル カーソルの名前を持つ場合*cursor_name*存在、GLOBAL が指定されたそれ以外の場合、この引数はグローバル カーソルを参照、ローカル カーソルを参照します。 カーソルは、更新可能である必要があります。  
  
 *cursor_variable_name*  
 カーソル変数の名前。 カーソル変数は、更新可能なカーソルを参照する必要があります。  
  
 オプション**(** \<query_hint > [ **、**.*n*] **)**  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のステートメント処理をカスタマイズするためのオプティマイザー ヒントを示すキーワードです。 詳細については、「[クエリ ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md)」を参照してください。  
  
## <a name="best-practices"></a>ベスト プラクティス  
 テーブル内のすべての行を削除するには、TRUNCATE TABLE を使用します。 DELETE と比べると TRUNCATE TABLE の方が高速で、システムとトランザクション ログのリソース使用量も少なくて済みます。 TRUNCATE TABLE には制限があり、たとえば、テーブルがレプリケーションに参加することはできません。 詳細については、次を参照してください。 [TRUNCATE TABLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/truncate-table-transact-sql.md)  
  
 使用して、@@ROWCOUNT関数の数を返しますが、クライアント アプリケーションに行を削除します。 詳細については、次を参照してください。 [@@ROWCOUNT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/rowcount-transact-sql.md).  
  
## <a name="error-handling"></a>エラー処理  
 TRY...CATCH 構造でステートメントを指定することで、DELETE ステートメントのエラー処理を実装できます。  
  
 DELETE ステートメントは、トリガーに違反したり、FOREIGN KEY 制約で別のテーブル内のデータによって参照されている行を削除しようとすると、失敗する可能性があります。 DELETE で複数の行を削除するときに、削除される行のいずれかがトリガーや制約に違反すると、ステートメントは取り消され、エラーが返されます。行は削除されません。  
  
 DELETE ステートメントで式の評価中に算術エラー (オーバーフロー、0 による除算、またはドメイン エラー) が発生すると、[!INCLUDE[ssDE](../../includes/ssde-md.md)]では SET ARITHABORT が ON に設定されている場合と同様にこれらのエラーが処理されます。 残りのバッチは取り消され、エラー メッセージが返されます。  
  
## <a name="interoperability"></a>相互運用性  
 変更するオブジェクトがテーブル変数の場合は、ユーザー定義関数内で DELETE を使用できます。  
  
 FILESTREAM 列を含む行を削除すると、その基となるファイル システム ファイルも削除されます。 基になるファイルは、FILESTREAM ガベージ コレクターによって削除されます。 詳細については、次を参照してください。 [TRANSACT-SQL による FILESTREAM データをアクセス](../../relational-databases/blob/access-filestream-data-with-transact-sql.md)です。  
  
 INSTEAD OF トリガーが定義されているビューを直接または間接的に参照している DELETE ステートメントでは、FROM 句は指定できません。 INSTEAD of トリガーの詳細については、次を参照してください。 [CREATE TRIGGER & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-trigger-transact-sql.md).  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 TOP を DELETE と共に使用する場合、参照される行は任意の順序に並べられません。また、このステートメントで、ORDER BY 句を直接指定することはできません。 TOP を使用して、意味のある順序で行を削除する必要がある場合は、サブセレクト ステートメントで ORDER BY 句を指定して TOP を使用する必要があります。 例については、後の「例」のセクションを参照してください。  
  
 パーティション ビューに対して DELETE ステートメントで TOP を使用することはできません。  
  
## <a name="locking-behavior"></a>ロック動作  
 既定では、DELETE ステートメントは、常に、そのステートメントで変更するテーブルについて排他 (X) ロックを獲得し、トランザクションが完了するまでそのロックを保持します。 排他 (X) ロックをかけたトランザクション以外はデータを変更できませんが、NOLOCK ヒントまたは READ UNCOMMITTED 分離レベルが指定されている場合に限り、読み取り操作は行うことができます。 別のロック手法を指定することで DELETE ステートメントの期間のこの既定の動作を上書きするテーブル ヒントを指定できます。ただし、このヒントは、経験豊富な開発者およびデータベース管理者が最後の手段としてのみ使用することを推奨します。 詳細については、「[テーブル ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md)」を参照してください。  
  
 ヒープから行を削除するときには、[!INCLUDE[ssDE](../../includes/ssde-md.md)]によって、操作に行またはページ ロックが使用されることがあります。 その結果、削除操作で空になったページがヒープに割り当てられたままになります。 空のページの割り当てが解除されないと、データベース内の他のオブジェクトで該当の領域を再利用できなくなります。  
  
 ヒープ内の行を削除し、ページの割り当てを解除するには、次のいずれかの方法を使用します。  
  
-   DELETE ステートメントで TABLOCK ヒントを指定します。 TABLOCK ヒントを使用すると、削除操作では、行またはページ ロックではなく、テーブルの排他的ロックが取得されます。 これにより、ページの割り当てを解除できるようになります。 TABLOCK ヒントの詳細については、次を参照してください。[テーブル ヒント & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/hints-transact-sql-table.md).  
  
-   テーブルからすべての行を削除する場合は、TRUNCATE TABLE を使用します。  
  
-   行を削除する前に、ヒープにクラスター化インデックスを作成します。 作成したクラスター化インデックスは、行を削除した後、削除できます。 この方法は前の 2 つの方法より時間がかかり、一時リソースがより多く使用されます。  
  
> [!NOTE]  
>  空のページを取り外せるヒープからいつでもを使用して、`ALTER TABLE <table_name> REBUILD`ステートメントです。  
  
## <a name="logging-behavior"></a>ログ記録の動作  
 DELETE ステートメントは、常に完全にログに記録されます。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 対象テーブルに対する DELETE 権限が必要です。 ステートメントに WHERE 句が含まれる場合は、SELECT 権限も必要です。  
  
 アクセス許可は既定のメンバーを削除、 **sysadmin**固定サーバー ロール、 **db_owner**と**db_datawriter**固定データベース ロール、およびテーブル所有者です。 メンバー、 **sysadmin**、 **db_owner**、および**db_securityadmin**ロール、およびテーブル所有者は、他のユーザーに権限を譲渡できます。  
  
## <a name="examples"></a>使用例  
  
|カテゴリ|主な構文要素|  
|--------------|------------------------------|  
|[基本構文](#BasicSyntax)|DELETE|  
|[削除する行数を制限します。](#LimitRows)|WHERE、FROM、カーソル|  
|[リモート テーブルから行を削除します。](#RemoteTables)|リンク サーバー、OPENQUERY 行セット関数、OPENDATASOURCE 行セット関数|  
|[DELETE ステートメントの結果をキャプチャ](#CaptureResults)|OUTPUT 句|  
  
###  <a name="BasicSyntax"></a>基本構文  
 このセクションの例では、最低限必要な構文を使用して DELETE ステートメントの基本機能を示します。  
  
#### <a name="a-using-delete-with-no-where-clause"></a>A. WHERE 句を指定せずに DELETE を使用する  
 次の例では、削除する行数を制限する WHERE 句が指定されていないため、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベース内の `SalesPersonQuotaHistory` テーブルからすべての行が削除されます。  
  
```  
DELETE FROM Sales.SalesPersonQuotaHistory;  
GO  
```  
  
###  <a name="LimitRows"></a>削除する行数を制限します。  
 このセクションの例では、削除する行数を制限する方法を示します。  
  
#### <a name="b-using-the-where-clause-to-delete-a-set-of-rows"></a>B. WHERE 句を使用して行セットを削除する  
 次の例のすべての行の削除、`ProductCostHistory`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]対象となるデータベース内の値、`StandardCost`列が複数の`1000.00`します。  
  
```    
DELETE FROM Production.ProductCostHistory  
WHERE StandardCost > 1000.00;  
GO  
```  
  
 次の例では、より複雑な WHERE 句を示します。 WHERE 句では、削除する行を決定するために満たす必要がある 2 つの条件を定義しています。 `StandardCost` 列の値が `12.00` から `14.00` までの範囲に含まれ、 `SellEndDate` 列の値が NULL であることが必要です。 この例もから値を出力、 **@@ROWCOUNT** 削除された行の数を返す関数。  
  
```  
DELETE Production.ProductCostHistory  
WHERE StandardCost BETWEEN 12.00 AND 14.00  
      AND EndDate IS NULL;  
PRINT 'Number of rows deleted is ' + CAST(@@ROWCOUNT as char(3));  
```  
  
#### <a name="c-using-a-cursor-to-determine-the-row-to-delete"></a>C. カーソルを使用して削除する行を決定する  
 次の例から 1 つの行の削除、`EmployeePayHistory`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]という名前のカーソルを使用してデータベース`my_cursor`です。 この操作では、カーソルから現在フェッチされている 1 行だけが削除されます。  
  
```  
DECLARE complex_cursor CURSOR FOR  
    SELECT a.BusinessEntityID  
    FROM HumanResources.EmployeePayHistory AS a  
    WHERE RateChangeDate <>   
         (SELECT MAX(RateChangeDate)  
          FROM HumanResources.EmployeePayHistory AS b  
          WHERE a.BusinessEntityID = b.BusinessEntityID) ;  
OPEN complex_cursor;  
FETCH FROM complex_cursor;  
DELETE FROM HumanResources.EmployeePayHistory  
WHERE CURRENT OF complex_cursor;  
CLOSE complex_cursor;  
DEALLOCATE complex_cursor;  
GO  
```  
  
#### <a name="d-using-joins-and-subqueries-to-data-in-one-table-to-delete-rows-in-another-table"></a>D. 1 つのテーブルへの結合およびサブクエリを使用して、別のテーブルの行を削除する  
 次の例では、1 つのテーブル内の行を、別のテーブルのデータに基づいて削除する 2 つの方法を示します。 どちらの例から行、`SalesPersonQuotaHistory`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]に格納されている今年に入ってからの売り上げ高に基づいてデータベースが削除された、`SalesPerson`テーブル。 最初の`DELETE`は ISO 互換のサブクエリ ソリューションと 2 番目のステートメントを示しています`DELETE`ステートメントの表示、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 2 つのテーブルを結合する拡張機能からです。  
  
```  
-- SQL-2003 Standard subquery  
  
DELETE FROM Sales.SalesPersonQuotaHistory   
WHERE BusinessEntityID IN   
    (SELECT BusinessEntityID   
     FROM Sales.SalesPerson   
     WHERE SalesYTD > 2500000.00);  
GO  
```  
  
```  
-- Transact-SQL extension  
  
DELETE FROM Sales.SalesPersonQuotaHistory   
FROM Sales.SalesPersonQuotaHistory AS spqh  
INNER JOIN Sales.SalesPerson AS sp  
ON spqh.BusinessEntityID = sp.BusinessEntityID  
WHERE sp.SalesYTD > 2500000.00;  
GO  
```  
  
```  
-- No need to mention target table more than once.  
  
DELETE spqh  
  FROM  
        Sales.SalesPersonQuotaHistory AS spqh  
    INNER JOIN Sales.SalesPerson AS sp  
        ON spqh.BusinessEntityID = sp.BusinessEntityID  
  WHERE  sp.SalesYTD > 2500000.00;  
```  
  
#### <a name="e-using-top-to-limit-the-number-of-rows-deleted"></a>E. TOP を使用して削除する行数を制限する  
 ときに、TOP (*n*) 句を DELETE と共に使用のランダムな選択で、削除操作が実行される *n* 行の数。 次の例削除`20`からランダムな行、`PurchaseOrderDetail`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]期限のあるデータベースは、2006 年 7 月 1 日より前の日付。  
  
```  
DELETE TOP (20)   
FROM Purchasing.PurchaseOrderDetail  
WHERE DueDate < '20020701';  
GO  
```  
  
 TOP を使用して、意味のある順序で行を削除する必要がある場合は、サブセレクト ステートメントで ORDER BY を指定して TOP を使用する必要があります。 次のクエリでは、納期が早いものから 10 行を `PurchaseOrderDetail` テーブルから削除します。 10 行だけを確実に削除するために、サブセレクト ステートメントではテーブルの主キーの列 (`PurchaseOrderID`) を指定しています。 サブセレクト ステートメントで非キー列を指定すると、指定した列に重複する値が含まれる場合、10 行以上の行が削除される可能性があります。  
  
```  
DELETE FROM Purchasing.PurchaseOrderDetail  
WHERE PurchaseOrderDetailID IN  
   (SELECT TOP 10 PurchaseOrderDetailID   
    FROM Purchasing.PurchaseOrderDetail   
    ORDER BY DueDate ASC);  
GO  
```  
  
###  <a name="RemoteTables"></a>リモート テーブルから行を削除します。  
 このセクションの例を使用してリモート テーブルから行を削除する方法をデモンストレーション、[リンク サーバー](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)または[行セット関数](../../t-sql/functions/rowset-functions-transact-sql.md)リモート テーブルを参照します。 リモート テーブルとは、別のサーバーまたは別の SQL Server インスタンスにあるテーブルのことです。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
#### <a name="f-deleting-data-from-a-remote-table-by-using-a-linked-server"></a>F. リンク サーバーを使用してリモート テーブルからデータを削除する  
 次の例では、リモート テーブルの行を削除します。 使用してリモート データ ソースへのリンクを作成した後、 [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)です。 リンク サーバー名、 `MyLinkServer`、形式で 4 部構成のオブジェクト名の一部として指定しています*server.catalog.schema.object*です。  
  
```  
USE master;  
GO  
-- Create a link to the remote data source.   
-- Specify a valid server name for @datasrc as 'server_name' or 'server_name\instance_name'.  
  
EXEC sp_addlinkedserver @server = N'MyLinkServer',  
    @srvproduct = N' ',  
    @provider = N'SQLNCLI',   
    @datasrc = N'server_name',  
    @catalog = N'AdventureWorks2012';  
GO  
```  
  
```  
-- Specify the remote data source using a four-part name   
-- in the form linked_server.catalog.schema.object.  
  
DELETE MyLinkServer.AdventureWorks2012.HumanResources.Department 
WHERE DepartmentID > 16;  
GO  
```  
  
#### <a name="g-deleting-data-from-a-remote-table-by-using-the-openquery-function"></a>G. OPENQUERY 関数を使用してリモート テーブルからデータを削除する  
 次の例では、リモート テーブルから行を削除を指定して、 [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md)行セット関数。 この例では、前の例で作成したリンク サーバー名を使用します。  
  
```  
DELETE OPENQUERY (MyLinkServer, 'SELECT Name, GroupName 
FROM AdventureWorks2012.HumanResources.Department  
WHERE DepartmentID = 18');  
GO  
```  
  
#### <a name="h-deleting-data-from-a-remote-table-by-using-the-opendatasource-function"></a>H. OPENDATASOURCE 関数を使用してリモート テーブルからデータを削除する  
 次の例では、リモート テーブルから行を削除を指定して、 [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md)行セット関数。 形式を使用して、データ ソースの有効なサーバー名を指定*server_name*または*server_name \instance_name*です。  
  
```  
DELETE FROM OPENDATASOURCE('SQLNCLI',  
    'Data Source= <server_name>; Integrated Security=SSPI')  
    .AdventureWorks2012.HumanResources.Department   
WHERE DepartmentID = 17;'  
```  
  
###  <a name="CaptureResults"></a>DELETE ステートメントの結果をキャプチャ  
  
#### <a name="i-using-delete-with-the-output-clause"></a>I. DELETE を OUTPUT 句と共に使用する  
 次の例の結果を保存する方法を示しています、`DELETE`ステートメント内のテーブル変数を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
DELETE Sales.ShoppingCartItem  
OUTPUT DELETED.*   
WHERE ShoppingCartID = 20621;  
  
--Verify the rows in the table matching the WHERE clause have been deleted.  
SELECT COUNT(*) AS [Rows in Table] 
FROM Sales.ShoppingCartItem 
WHERE ShoppingCartID = 20621;  
GO  
```  
  
#### <a name="j-using-output-with-fromtablename-in-a-delete-statement"></a>J. OUTPUT を DELETE ステートメント内で <from_table_name> と共に使用する  
 次の例は、行を削除、`ProductProductPhoto`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]で定義された検索条件に基づいて、データベース、`FROM`の句、`DELETE`ステートメントです。 `OUTPUT` 句では、削除されるテーブルの列 ( `DELETED.ProductID`、 `DELETED.ProductPhotoID`)、および `Product` テーブルの列を返します。 これは `FROM` 句で削除する行を指定するときに使用されます。  
  
```  
DECLARE @MyTableVar table (  
    ProductID int NOT NULL,   
    ProductName nvarchar(50)NOT NULL,  
    ProductModelID int NOT NULL,   
    PhotoID int NOT NULL);  
  
DELETE Production.ProductProductPhoto  
OUTPUT DELETED.ProductID,  
       p.Name,  
       p.ProductModelID,  
       DELETED.ProductPhotoID  
    INTO @MyTableVar  
FROM Production.ProductProductPhoto AS ph  
JOIN Production.Product as p   
    ON ph.ProductID = p.ProductID   
    WHERE p.ProductModelID BETWEEN 120 and 130;  
  
--Display the results of the table variable.  
SELECT ProductID, ProductName, ProductModelID, PhotoID   
FROM @MyTableVar  
ORDER BY ProductModelID;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="k-delete-all-rows-from-a-table"></a>K. テーブルからすべての行を削除します。  
 次の例では、削除する行数を制限する WHERE 句が指定されていないため、`Table1` テーブルからすべての行が削除されます。  
  
```  
DELETE FROM Table1;  
```  
  
### <a name="l-delete-a-set-of-rows-from-a-table"></a>L. テーブルから行セットを削除します。  
 次の例のすべての行の削除、`Table1`で 1000.00 より大きい値を持つテーブル、`StandardCost`列です。  
  
```  
DELETE FROM Table1  
WHERE StandardCost > 1000.00;  
```  
  
### <a name="m-using-label-with-a-delete-statement"></a>M. DELETE ステートメントとラベルを使用します。  
 次の例では、ラベルを使用して DELETE ステートメントを使用します。  
  
```  
DELETE FROM Table1  
OPTION ( LABEL = N'label1' );  
  
```  
  
### <a name="n-using-a-label-and-a-query-hint-with-the-delete-statement"></a>N. DELETE ステートメントでラベルとクエリ ヒントの使用  
 このクエリは、DELETE ステートメントと共にクエリの結合ヒントを使用するための基本構文を示しています。 結合ヒントや、OPTION 句を使用する方法の詳細については、次を参照してください。[オプション (SQL Server PDW)](http://msdn.microsoft.com/en-us/72bbce98-305b-42fa-a19f-d89620621ecc)です。  
  
```  
-- Uses AdventureWorks  
  
DELETE FROM dbo.FactInternetSales  
WHERE ProductKey IN (   
    SELECT T1.ProductKey FROM dbo.DimProduct T1   
    JOIN dbo.DimProductSubcategory T2  
    ON T1.ProductSubcategoryKey = T2.ProductSubcategoryKey  
    WHERE T2.EnglishProductSubcategoryName = 'Road Bikes' )  
OPTION ( LABEL = N'CustomJoin', HASH JOIN ) ;  
```  
  
## <a name="see-also"></a>参照  
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [TRUNCATE TABLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/truncate-table-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [で common_table_expression と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/with-common-table-expression-transact-sql.md)   
 [@@ROWCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/rowcount-transact-sql.md)  
  
  


