---
title: "DBCC PDW_SHOWSPACEUSED (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/17/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|database-console-commands
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 73f598cf-b02a-4dba-8d89-9fc0b55a12b8
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8c564a6debb9c110cb41f8fc90a7cc1c0c5a01f7
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-pdwshowspaceused-transact-sql"></a>DBCC PDW_SHOWSPACEUSED (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

行の数、ディスク領域が予約されている、特定のテーブルまたはすべてのテーブルで使用されるディスク領域が表示されます、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]データベース。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
-- Show the space used for all user tables and system tables in the current database  
DBCC PDW_SHOWSPACEUSED  
[;]  
  
-- Show the space used for a table  
DBCC PDW_SHOWSPACEUSED ( " [ database_name . [ schema_name ] . ] | [ schema_name .] table_name  " )  
[;]  
```  
  
## <a name="arguments"></a>引数  
 [ *database_name* . [ *schema_name* ] . | *schema_name* . ] *table_name*  
 1 つ、2 枚、または表示するテーブルの 3 部構成の名前。 2 つの 3 つの要素名、名前は、二重引用符で囲む必要がありますか ("")。 1 つの部分から成るテーブル名を囲む引用符を使用したはオプションです。 テーブル名が指定されていない場合は、現在のデータベースの情報が表示されます。  
  
## <a name="permissions"></a>権限  
VIEW SERVER STATE 権限が必要です。
  
## <a name="result-sets"></a>結果セット  
これは、すべてのテーブルの結果セットです。
  
|列|データ型|Description|  
|------------|---------------|-----------------|  
|reserved_space|bigint|領域の合計 (KB 単位) をデータベースに使用します。|  
|data_space|bigint|(KB 単位) のデータに使用される領域です。|  
|index_space|bigint|領域を kb 単位でのインデックスに使用します。|  
|unused_space|bigint|な領域を予約した領域の一部であり、使用しない、(KB 単位)。|  
|pdw_node_id|int|データの使用されているノードを計算します。|  
  
これは、1 つのテーブルの結果セットです。
  
|列|データ型|Description|範囲|  
|------------|---------------|-----------------|-----------|  
|rows|bigint|行の数。||  
|reserved_space|bigint|領域の合計 (KB 単位) のオブジェクト用に予約されています。||  
|data_space|bigint|領域が kb 単位で、データに使用します。||  
|index_space|bigint|領域を kb 単位でのインデックスに使用します。||  
|unused_space|bigint|な領域を予約した領域の一部であり、使用しない、(KB 単位)。||  
|pdw_node_id|int|領域の使用状況の報告に使用するためのコンピューティング ノードです。||  
|distribution_id|int|領域の使用状況をレポートに使用する配布します。|値は、レプリケートされたテーブルの場合は-1 です。|  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdwshowspaceused-basic-syntax"></a>A. DBCC PDW_SHOWSPACEUSED の基本的な構文  
次の例は、行の数を表示、ディスク領域が予約されている複数の方法を表示し、FactInternetSales テーブルで使用されるディスク領域、[!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)]データベース。
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012.dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012..FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( FactInternetSales );  
```  
  
### <a name="b-show-the-disk-space-used-by-all-tables-in-the-current-database"></a>B. 現在のデータベース内のすべてのテーブルで使用されるディスク領域を表示します。  
 次の例では、予約されており、すべてのユーザー テーブルとシステム テーブルで使用されるディスク領域、[!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)]データベース。  
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED;  
```  
 ## <a name="see-also"></a>参照
[DBCC PDW_SHOWEXECUTIONPLAN &#40;Transact-SQL&#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWPARTITIONSTATS &#40;Transact-SQL&#41;](dbcc-pdw-showpartitionstats-transact-sql.md)

  
