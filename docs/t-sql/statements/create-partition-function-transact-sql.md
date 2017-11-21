---
title: "パーティション関数 (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE PARTITION FUNCTION
- PARTITION
- PARTITION FUNCTION
- PARTITION_FUNCTION_TSQL
- PARTITION_TSQL
- CREATE_PARTITION_FUNCTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RANGE RIGHT partition functions
- RANGE LEFT partition functions
- partitioned indexes [SQL Server], functions
- functions [SQL Server], creating
- partition functions [SQL Server], creating
- partitioned tables [SQL Server], functions
- CREATE PARTITION FUNCTION statement
ms.assetid: 9dfe8b76-721e-42fd-81ae-14e22258c4f2
caps.latest.revision: 57
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a08cf71066a3713d2eb96ff11bafd951795819ff
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-partition-function-transact-sql"></a>CREATE PARTITION FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  テーブルまたはインデックスの行を指定された列の値に基づいてパーティションにマップする関数を、現在のデータベース内に作成します。 CREATE PARTITION FUNCTION の使用は、パーティション テーブルまたはパーティション インデックスを作成する最初の手順です。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、テーブルまたはインデックスは、最大 15,000 のパーティションを持つことができます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE PARTITION FUNCTION partition_function_name ( input_parameter_type )  
AS RANGE [ LEFT | RIGHT ]   
FOR VALUES ( [ boundary_value [ ,...n ] ] )   
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *partition_function_name*  
 パーティション関数の名前です。 パーティション関数の名前のデータベース内で一意であるし、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 *input_parameter_type*  
 パーティション分割に使用される列のデータ型です。 すべてのデータ型は、 **text**、 **ntext**、 **image**、 **xml**、 **timestamp**、 **varchar(max)**、 **nvarchar(max)**、 **varbinary(max)**、別名データ型、または CLR ユーザー定義データ型を除いて、列を分割して使用することができます。  
  
 パーティション分割列と呼ばれる実際の列は、CREATE TABLE ステートメントまたは CREATE INDEX ステートメントで指定します。  
  
 *boundary_value*  
 パーティション テーブルまたはを使用するインデックスの各パーティションの境界値を指定*partition_function_name*です。 場合*boundary_value*は、テーブル全体またはインデックスを使用して、空のパーティション関数にマップ*partition_function_name* 1 つのパーティションにします。 CREATE TABLE ステートメントまたは CREATE INDEX ステートメントで指定された 1 つのパーティション分割列のみが使用できます。  
  
 *boundary_value*変数を参照できる定数式です。 これには、ユーザー定義型の変数、または関数およびユーザー定義関数が含まれます。 この定数式で [!INCLUDE[tsql](../../includes/tsql-md.md)] 式を参照することはできません。 *boundary_value*一致かで指定されたデータ型に暗黙的に変換できる必要があります*input_parameter_type*サイズと値の小数点以下桁数を行うように、暗黙的な変換中に切り捨てられることはできません一致しないこと、対応する*input_parameter_type*です。  
  
> [!NOTE]  
>  場合*boundary_value*から成る**datetime**または**smalldatetime** us_english はセッション言語は、想定されるので、リテラルは、これらのリテラルが評価されます。 ただし、この動作は廃止予定となっています。 すべてのセッション言語でパーティション関数の定義が正しく認識されるようにするには、yyyymmdd 形式のようにすべての言語設定で同様に解釈される定数を使用するか、リテラルを特定の型に明示的に変換することをお勧めします。 サーバーのセッション言語を確認するには、実行`SELECT @@LANGUAGE`です。  
  
 *...n*  
 によって指定された値の数を指定*boundary_value*ではなく、14,999 します。 作成されたパーティションの数と等しい *n*  + 1 です。 値を順序どおり指定する必要はありません。 値が順番にない場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]並べ替えを実行し、関数を作成し、順序で値が指定されていないという警告を返します。 データベース エンジン エラーが返されます *n* 重複する値が含まれています。  
  
 **左**|そうです  
 各境界値間隔、左または右の辺を指定、 *boundary_value* [ **、***...n* ] が属している、間隔の値が、で並べ替えられた[!INCLUDE[ssDE](../../includes/ssde-md.md)]左から右に昇順にします。 指定しない場合は、LEFT が既定値です。  
  
## <a name="remarks"></a>解説  
 パーティション関数のスコープは、関数が作成されたデータベース内に制限されます。 データベース内では、パーティション関数は、他の関数から別の名前空間に存在します。  
  
 パーティション分割列に NULL 値がある行はすべて、左端のパーティションに配置されます。ただし、NULL が境界値として指定され、RIGHT が指定された場合は除きます。 この場合、左端のパーティションは空のパーティションになり、NULL 値は次のパーティションに配置されます。  
  
## <a name="permissions"></a>Permissions  
 次のいずれかの権限を使用すると、CREATE PARTITION FUNCTION を実行できます。  
  
-   ALTER ANY DATASPACE 権限。 この権限は、既定では **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_ddladmin** 固定データベース ロールのメンバーに与えられています。  
  
-   データベースの CONTROL 権限または ALTER 権限 (パーティション関数はこのデータベース内で作成)。  
  
-   データベースのサーバーの CONTROL SERVER 権限または ALTER ANY DATABASE 権限 (パーティション関数はこのデータベースで作成)。  
  
##  <a name="BKMK_examples"></a> 使用例  
  
### <a name="a-creating-a-range-left-partition-function-on-an-int-column"></a>A. int 型の列に RANGE LEFT パーティション関数を作成する  
 次のパーティション関数は、テーブルまたはインデックスを 4 つのパーティションに分割します。  
  
```tsql  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
```  
  
 次の表にパーティション分割列でこのパーティション関数を使用するテーブルをどのように**col1**に分割されます。  
  
|パーティション|1|2|3|4|  
|---------------|-------|-------|-------|-------|  
|**値**|**col1** <= `1`|**col1**  >  `1` AND **col1** <= `100`|**col1**  >  `100` AND **col1** <=`1000`|**col1** > `1000`|  
  
### <a name="b-creating-a-range-right-partition-function-on-an-int-column"></a>B. int 型の列に RANGE RIGHT パーティション関数を作成する  
 次のパーティション関数と同じ値を使用して*boundary_value* [ **、***...n* ] RANGE RIGHT を示す点を除いて、前の例とします。  
  
```tsql  
CREATE PARTITION FUNCTION myRangePF2 (int)  
AS RANGE RIGHT FOR VALUES (1, 100, 1000);  
```  
  
 次の表にパーティション分割列でこのパーティション関数を使用するテーブルをどのように**col1**に分割されます。  
  
|パーティション|1|2|3|4|  
|---------------|-------|-------|-------|-------|  
|**値**|**col1** \<`1`|**col1**  >=  `1` AND **col1** \<`100`|**col1**  >=  `100` AND **col1** \<`1000`|**col1** >= `1000`| 
  
### <a name="c-creating-a-range-right-partition-function-on-a-datetime-column"></a>C. datetime 型の列に RANGE RIGHT パーティション関数を作成する  
 次のパーティション関数が 12 のパーティションがあり、それぞれの月の値の 1 年分の 1 つをテーブルまたはインデックスをパーティション分割、 **datetime**列です。  
  
```tsql  
CREATE PARTITION FUNCTION [myDateRangePF1] (datetime)  
AS RANGE RIGHT FOR VALUES ('20030201', '20030301', '20030401',  
               '20030501', '20030601', '20030701', '20030801',   
               '20030901', '20031001', '20031101', '20031201');  
```  
  
 次の表に、テーブルまたはインデックス パーティション分割列でこのパーティション関数を使用する方法**datecol**に分割されます。  
  
|パーティション|1|2|[...]|11|12|  
|---------------|-------|-------|---------|--------|--------|  
|**値**|**datecol** \<`February 1, 2003`|**datecol**  >=  `February 1, 2003` AND **datecol** \<`March 1, 2003`||**datecol**  >=  `November 1, 2003` AND **col1** \<`December 1, 2003`|**datecol** >= `December 1, 2003`| 
  
### <a name="d-creating-a-partition-function-on-a-char-column"></a>D. char 型の列にパーティション関数を作成する  
 次のパーティション関数では、4 つのパーティションをテーブルまたはインデックスがパーティション分割します。  
  
```tsql  
CREATE PARTITION FUNCTION myRangePF3 (char(20))  
AS RANGE RIGHT FOR VALUES ('EX', 'RXE', 'XR');  
```  
  
 次の表にパーティション分割列でこのパーティション関数を使用するテーブルをどのように**col1**に分割されます。  
  
|パーティション|1|2|3|4|  
|---------------|-------|-------|-------|-------|  
|**値**|**col1** \< `EX`しています.|**col1**  >=  `EX` AND **col1** \< `RXE`しています.|**col1**  >=  `RXE` AND **col1** \< `XR`しています.|**col1** >= `XR`| 
  
### <a name="e-creating-15000-partitions"></a>E. 15,000 のパーティションを作成する  
 次のパーティション関数は、テーブルまたはインデックスを 15,000 のパーティションに分割します。  
  
```tsql  
--Create integer partition function for 15,000 partitions.  
DECLARE @IntegerPartitionFunction nvarchar(max) = 
    N'CREATE PARTITION FUNCTION IntegerPartitionFunction (int) 
    AS RANGE RIGHT FOR VALUES (';  
DECLARE @i int = 1;  
WHILE @i < 14999  
BEGIN  
SET @IntegerPartitionFunction += CAST(@i as nvarchar(10)) + N', ';  
SET @i += 1;  
END  
SET @IntegerPartitionFunction += CAST(@i as nvarchar(10)) + N');';  
EXEC sp_executesql @IntegerPartitionFunction;  
GO  
```  
  
### <a name="f-creating-partitions-for-multiple-years"></a>F. 複数年のパーティションを作成する  
 次のパーティション関数パーティション テーブルまたはインデックスを 50 のパーティションで、 **datetime2**列です。 2007 年 1 月から 2011 年 1 月までの各月に対して 1 つのパーティションがあります。  
  
```tsql  
--Create date partition function with increment by month.  
DECLARE @DatePartitionFunction nvarchar(max) = 
    N'CREATE PARTITION FUNCTION DatePartitionFunction (datetime2) 
    AS RANGE RIGHT FOR VALUES (';  
DECLARE @i datetime2 = '20070101';  
WHILE @i < '20110101'  
BEGIN  
SET @DatePartitionFunction += '''' + CAST(@i as nvarchar(10)) + '''' + N', ';  
SET @i = DATEADD(MM, 1, @i);  
END  
SET @DatePartitionFunction += '''' + CAST(@i as nvarchar(10))+ '''' + N');';  
EXEC sp_executesql @DatePartitionFunction;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [パーティション テーブルとインデックス](../../relational-databases/partitions/partitioned-tables-and-indexes.md)   
 [$PARTITION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/partition-transact-sql.md)   
 [ALTER PARTITION FUNCTION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-partition-function-transact-sql.md)   
 [DROP PARTITION FUNCTION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.partition_functions & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [sys.partition_parameters & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)   
 [sys.partition_range_values & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)   
 [sys.partitions および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  


