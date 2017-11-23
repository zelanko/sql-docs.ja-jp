---
title: "DROP TABLE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/12/2017
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
- DROP_TABLE_TSQL
- DROP TABLE
dev_langs: TSQL
helpviewer_keywords:
- removing indexes
- table removal [SQL Server]
- deleting indexes
- dropping data
- deleting tables
- dropping indexes
- removing constraints
- removing permissions
- DROP TABLE statement
- removing tables
- deleting triggers
- removing data
- dropping tables
- deleting permissions
- dropping triggers
- deleting constraints
- removing triggers
- deleting data
- dropping constraints
- dropping permissions
ms.assetid: 0b6f2b6f-3aa3-4767-943f-43df3c3c5cfd
caps.latest.revision: "61"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: df9843e4b72c6a8092756725d1d4b3f96eefec74
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="drop-table-transact-sql"></a>DROP TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  1 つ以上のテーブルの定義、およびそれらのテーブルのすべてのデータ、インデックス、トリガー、制約、権限の仕様を削除します。 すべてのビューと削除するテーブルを参照するストアド プロシージャを使用して明示的に削除する必要があります[DROP VIEW](../../t-sql/statements/drop-view-transact-sql.md)または[DROP PROCEDURE](../../t-sql/statements/drop-procedure-transact-sql.md)です。 テーブルの依存関係をレポートする使用[sys.dm_sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP TABLE [ IF EXISTS ] [ database_name . [ schema_name ] . | schema_name . ]  
table_name [ ,...n ]  
[ ; ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP TABLE [ database_name . [ schema_name ] . | schema_name . ] table_name   
[;]  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 テーブルが作成されたデータベースの名前です。  
  
 Windows Azure SQL データベースでは、database_name が現在のデータベースの場合、または database_name が tempdb で、object_name が # で始まる場合に、3 つの要素で構成された名前形式 database_name.[schema_name].object_name をサポートします。 Windows Azure SQL データベースでは、4 つの要素で構成された名前はサポートされません。  
  
 *場合に存在します。*  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
 条件付きでは既に存在する場合にのみ、テーブルを削除します。  
  
 *schema_name*  
 テーブルが所属するスキーマの名前を指定します。  
  
 *table_name*  
 削除するテーブル名を指定します。  
  
## <a name="remarks"></a>解説  
 DROP TABLE を使用して、FOREIGN KEY 制約によって参照されているテーブルを削除することはできません。 まず、参照している FOREIGN KEY 制約または参照テーブルを削除する必要があります。 参照しているテーブルと、主キーを格納しているテーブルの両方を同じ DROP TABLE ステートメントで削除する場合には、参照しているテーブルを先に指定する必要があります。  
  
 任意のデータベースから、複数のテーブルを削除することができます。 削除するテーブルが、同時に削除される別のテーブルの主キーを参照している場合には、外部キーを持つ参照元のテーブルを、参照されている主キーを持つテーブルよりも前に指定する必要があります。  
  
 テーブルを削除すると、そのテーブルのルールや既定値はバインドを失い、そのテーブルに関係付けられている制約やトリガーも自動的に削除されます。 テーブルを再作成する場合は、適切なルールや既定値を再バインドし、トリガーを再作成し、必要なすべての制約を追加する必要があります。  
  
 DELETE を使用してテーブル内のすべての行を削除するかどうかは*tablename*または TRUNCATE TABLE ステートメントを使用して、削除されるまで、テーブルが存在します。  
  
 128 個を超えるエクステントを使用する大きなテーブルやインデックスは、論理フェーズと物理フェーズの 2 段階で削除します。 論理フェーズでは、そのテーブルが使用している既存のアロケーション ユニットに割り当て解除のマークが付き、トランザクションがコミットするまでロックされます。 物理フェーズでは、割り当て解除のマークが付いた IAM ページが、バッチによって物理的に削除されます。  
  
 FILESTREAM 属性が指定されている VARBINARY(MAX) 列を含むテーブルを削除しても、ファイル システムに保存されているデータは削除されません。  
  
> [!IMPORTANT]  
>  DROP TABLE と CREATE TABLE を同じバッチ内の同じテーブルに対して実行しないでください。 実行した場合、予期しないエラーが発生する可能性があります。  
  
## <a name="permissions"></a>Permissions  
 テーブルが属するスキーマに対する ALTER 権限、テーブルに対する CONTROL 権限、または **db_ddladmin** 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-a-table-in-the-current-database"></a>A. 現在のデータベース内のテーブルを削除する  
 次の例では、削除、`ProductVendor1`テーブル、データ、および現在のデータベースからのインデックス。  
  
```  
DROP TABLE ProductVendor1 ;  
```  
  
### <a name="b-dropping-a-table-in-another-database"></a>B. 他のデータベースのテーブルを削除する  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースにある `SalesPerson2` テーブルを削除します。 この例は、サーバー インスタンス上にあるどのデータベースからでも実行できます。  
  
```  
DROP TABLE AdventureWorks2012.dbo.SalesPerson2 ;  
```  
  
### <a name="c-dropping-a-temporary-table"></a>C. 一時テーブルを削除する  
 次の例では、一時テーブルを作成して、その存在テストを行います。さらに、このテーブルを削除して、再度存在テストを行います。 この例では使用できません、 **IF EXISTS**以降で使用される構文[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。  
  
```  
CREATE TABLE #temptable (col1 int);  
GO  
INSERT INTO #temptable  
VALUES (10);  
GO  
SELECT * FROM #temptable;  
GO  
IF OBJECT_ID(N'tempdb..#temptable', N'U') IS NOT NULL   
DROP TABLE #temptable;  
GO  
--Test the drop.  
SELECT * FROM #temptable;  
  
```  
  
### <a name="d-dropping-a-table-using-if-exists"></a>D. IF EXISTS を使用してテーブルを削除します。  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
 次の例では、T1 のという名前のテーブルを作成します。 2 番目のステートメントは、テーブルを削除します。 3 番目のステートメントでは、操作は一切実行、テーブルが既に削除されるためが、エラーは発生しません。  
  
```  
CREATE TABLE T1 (Col1 int);  
GO  
DROP TABLE IF EXISTS T1;  
GO  
DROP TABLE IF EXISTS T1;  
```  
  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [TRUNCATE TABLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/truncate-table-transact-sql.md)   
 [DROP VIEW &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-view-transact-sql.md)   
 [DROP PROCEDURE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-procedure-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  
