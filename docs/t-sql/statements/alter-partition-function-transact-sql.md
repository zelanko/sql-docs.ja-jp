---
title: "ALTER PARTITION FUNCTION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER PARTITION FUNCTION
- ALTER_PARTITION_FUNCTION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- splitting partitions [SQL Server]
- partitioned tables [SQL Server], splitting
- ALTER PARTITION FUNCTION statement
- merging partitions [SQL Server]
- partitioned indexes [SQL Server], merging
- partitioned indexes [SQL Server], splitting
- modifying partition functions
- partition functions [SQL Server], modifying
- partitioned tables [SQL Server], merging
ms.assetid: 70866dac-0a8f-4235-8108-51547949ada4
caps.latest.revision: "43"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 66b921eb3bd6378d20de11a0197a20c957d14ac6
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="alter-partition-function-transact-sql"></a>ALTER PARTITION FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  境界値の分割または結合によって、パーティション関数を変更します。 ALTER PARTITION FUNCTION を実行すると、任意のテーブルまたはインデックスで、そのパーティション関数を使用する 1 つのパーティションを 2 つに分割したり、2 つのパーティションを 1 つにマージしたりできます。  
  
> [!CAUTION]  
>  複数のテーブルやインデックスで同じパーティション関数を使用できます。 ALTER PARTITION FUNCTION は、1 回のトランザクションでこれらすべてを操作できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER PARTITION FUNCTION partition_function_name()  
{   
    SPLIT RANGE ( boundary_value )  
  | MERGE RANGE ( boundary_value )   
} [ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *partition_function_name*  
 変更するパーティション関数の名前です。  
  
 SPLIT RANGE ( *boundary_value* )  
 1 つのパーティションをパーティション関数に追加します。 *boundary_value*新しいパーティションの範囲を決定し、パーティション関数の既存の境界範囲と異なる必要があります。 基づく*boundary_value*、[!INCLUDE[ssDE](../../includes/ssde-md.md)]を 2 つに分割します。 既存の範囲のいずれか。 これらの 2 つの 1 つの場所、新しい*boundary_value*が存在する、新しいパーティションと見なされます。  
  
 新しいパーティションを保持するには、ファイル グループがオンラインに存在し、このパーティション関数を使用するパーティション構成によって NEXT USED とマークされている必要があります。 ファイル グループは、CREATE PARTITION SCHEME ステートメントでパーティションに割り当てられます。 CREATE PARTITION SCHEME ステートメントで必要以上のファイル グループを割り当てた (CREATE PARTITION FUNCTION ステートメントで、パーティションを含めるファイル グループよりも少ないパーティションを作成した) 場合、割り当てられていないファイル グループができ、そのうちの 1 つがパーティション構成によって NEXT USED とマークされます。 このファイル グループに、新しいパーティションが保持されます。 パーティション構成によって NEXT USED とマークされたファイル グループがない場合、新しいパーティションを保持するには、ALTER PARTITION SCHEME を使用して、ファイル グループを追加するか、既存のファイル グループを指定する必要があります。 既にパーティションを保持するファイル グループは、追加のパーティションを保持するように指定できます。 1 つのパーティション関数を複数のパーティション構成に関連付けできるので、パーティションを追加するパーティション関数を使用するには、すべてのパーティション構成に NEXT USED ファイル グループが必要です。 NEXT USED ファイル グループがない場合、パーティション構成に NEXT USED ファイル グループが存在しないというエラーが表示され、ALTER PARTITION FUNCTION が失敗します。  
  
 すべてのパーティションを同じファイル グループ内に作成した場合、最初に、そのグループが自動的に NEXT USED ファイル グループに割り当てられます。 ただし、分割操作が実行されると、指定された NEXT USED ファイル グループがなくなります。 このファイル グループは、ALTER PARITION SCHEME を使用して NEXT USED ファイル グループになるように明示的に割り当てる必要があります。そうしないと、その後の分割操作は失敗します。  
  
> [!NOTE]  
>  列ストア インデックスでの制限: 空のパーティション分割できるは、テーブルに列ストア インデックスが存在する場合。 削除するか、この操作を実行する前に、列ストア インデックスを無効にする必要があります。  
  
 マージ [範囲 ( *boundary_value*)]  
 パーティションを削除し、そのパーティションに存在する任意の値を残りのパーティションのうちの 1 つにマージします。 範囲 (*boundary_value*) を削除したパーティションの値がマージされた既存の境界値にする必要があります。 最初に保持されているファイル グループ*boundary_value*や、NEXT USED プロパティでマークされている残りのパーティションによって使用されていない限りは、パーティション構成から削除します。 マージされたパーティションは、ファイル グループに最初に保持されていなかった*boundary_value*です。 *boundary_value*変数 (ユーザー定義型の変数を含む) または関数 (ユーザー定義関数を含む) を参照できる定数式です。 [!INCLUDE[tsql](../../includes/tsql-md.md)] 式を参照することはできません。 *boundary_value*必要があります一致または、対応するパーティション分割列のデータ型に暗黙的に変換できるように、暗黙的な変換中に切り捨てられることはできませんとサイズと値の小数点以下桁数が一致しないことの対応する*input_parameter_type*です。  
  
> [!NOTE]  
>  列ストア インデックスでの制限: 列ストア インデックスを含む 2 つの空でないパーティションをマージすることはできません。 削除するか、この操作を実行する前に、列ストア インデックスを無効にする必要があります。  
  
## <a name="best-practices"></a>ベスト プラクティス  
 常にパーティション範囲の両端に空のパーティションを残しておき、パーティションの分割 (新しいデータを読み込む前) およびパーティションのマージ (古いデータをアンロードした後) によってデータの移動が発生しないようにします。 設定されたパーティションが分割またはマージされないようにします。 これが発生すると、ログの生成が最大で 4 倍になり、大量のロックが発生する場合もあるので、きわめて非効率的になる可能性があります。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 ALTER PARTITION FUNCTION は、1 回のアトミックな操作で、その関数を使用するすべてのテーブルおよびインデックスのパーティションを分割し直します。 しかし、この操作はオフラインで実行され、分割し直すエクステントによってはリソースを大きく消費します。  
  
 ALTER PARTITION FUNCTION を使用すると、1 つのパーティションを 2 つに分割する、または 2 つのパーティションを 1 つにマージすることができます。 他のパーティション分割方法でテーブルを変更する (たとえば、10 のパーティションを 5 つにする) には、次のいずれかを実行します。 システムの構成に応じて、これらの方法のリソース消費量は異なります。  
  
-   適切なパーティション関数でパーティション テーブルを新規作成し、次に INSERT INTO...SELECT FROM ステートメントを使用して、古いテーブルのデータを新しいテーブルに挿入します。  
  
-   パーティション分割されたクラスター化インデックスを、ヒープ上に作成します。  
  
    > [!NOTE]  
    >  パーティション分割されたクラスター化インデックスを削除すると、パーティション分割されたヒープが生成されます。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] の CREATE INDEX ステートメントと DROP EXISTING = ON 句を使用して、既存のパーティション インデックスを削除および再構築します。  
  
-   一連の ALTER PARTITION FUNCTION ステートメントを実行します。  
  
 ALTER PARITITION FUNCTION の影響を受けるすべてのファイル グループは、オンラインである必要があります。  
  
 そのパーティション関数を使用するテーブル上に、無効化されたクラスター化インデックスがあると、ALTER PARTITION FUNCTION は失敗します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、パーティション関数の変更に関するレプリケーションはサポートされていません。 パブリケーション データベース内のパーティション関数への変更は、手動でサブスクリプション データベースに適用させる必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 次の権限のいずれかを使用すると、ALTER PARTITION FUNCTION を実行できます。  
  
-   ALTER ANY DATASPACE 権限。 この権限は、既定では **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_ddladmin** 固定データベース ロールのメンバーに与えられています。  
  
-   パーティション関数が作成されたデータベースでの CONTROL または ALTER 権限。  
  
-   パーティション関数が作成されたデータベースのサーバーでの CONTROL SERVER または ALTER ANY DATABASE 権限。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-splitting-a-partition-of-a-partitioned-table-or-index-into-two-partitions"></a>A. パーティション テーブルまたはパーティション インデックスの 1 つのパーティションを 2 つのパーティションに分割する  
 次の例では、テーブルまたはインデックスを 4 つのパーティションに分割するパーティション関数を作成します。 `ALTER PARTITION FUNCTION`5 つのパーティションの集計を作成するのには、2 には、1 つのパーティションを分割します。  
  
```sql  
IF EXISTS (SELECT * FROM sys.partition_functions  
    WHERE name = 'myRangePF1')  
DROP PARTITION FUNCTION myRangePF1;  
GO  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
GO  
--Split the partition between boundary_values 100 and 1000  
--to create two partitions between boundary_values 100 and 500  
--and between boundary_values 500 and 1000.  
ALTER PARTITION FUNCTION myRangePF1 ()  
SPLIT RANGE (500);  
```  
  
### <a name="b-merging-two-partitions-of-a-partitioned-table-into-one-partition"></a>B. パーティション テーブルの 2 つのパーティションを 1 つのパーティションにマージする  
 次の例では、上記と同じパーティション関数を作成し、次にこれらのパーティションのうちの 2 つを 1 つにマージして、合計 3 つのパーティションにします。  
  
```sql  
IF EXISTS (SELECT * FROM sys.partition_functions  
    WHERE name = 'myRangePF1')  
DROP PARTITION FUNCTION myRangePF1;  
GO  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
GO  
--Merge the partitions between boundary_values 1 and 100  
--and between boundary_values 100 and 1000 to create one partition  
--between boundary_values 1 and 1000.  
ALTER PARTITION FUNCTION myRangePF1 ()  
MERGE RANGE (100);  
```  
  
## <a name="see-also"></a>参照  
 [パーティション テーブルとインデックス](../../relational-databases/partitions/partitioned-tables-and-indexes.md)   
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [DROP PARTITION FUNCTION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [ALTER PARTITION SCHEME &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-partition-scheme-transact-sql.md)   
 [DROP PARTITION SCHEME &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-partition-scheme-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [sys.partition_functions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [sys.partition_parameters &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)   
 [sys.partition_range_values &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)   
 [sys.partitions および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
