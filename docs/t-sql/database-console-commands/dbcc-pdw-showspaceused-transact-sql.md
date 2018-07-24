---
title: DBCC PDW_SHOWSPACEUSED (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.suite: sql
ms.component: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 73f598cf-b02a-4dba-8d89-9fc0b55a12b8
author: uc-msft
ms.author: umajay
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 24a2eb0a69a6fcbedf1d5323caa97cdccd180fd5
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38039777"
---
# <a name="dbcc-pdwshowspaceused-transact-sql"></a>DBCC PDW_SHOWSPACEUSED (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] または [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] データベースの特定のテーブルまたはすべてのテーブルの行数、予約済みのディスク領域、使用済みのディスク領域を表示します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
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
  
## <a name="permissions"></a>アクセス許可  
VIEW SERVER STATE 権限が必要です。
  
## <a name="result-sets"></a>結果セット  
これは、すべてのテーブルの結果セットです。
  
|[列]|データ型|[説明]|  
|------------|---------------|-----------------|  
|reserved_space|BIGINT|領域の合計 (KB 単位) をデータベースに使用します。|  
|data_space|BIGINT|(KB 単位) のデータに使用される領域です。|  
|index_space|BIGINT|領域を kb 単位でのインデックスに使用します。|  
|unused_space|BIGINT|な領域を予約した領域の一部であり、使用しない、(KB 単位)。|  
|pdw_node_id|ssNoversion|データの使用されているノードを計算します。|  
  
これは、1 つのテーブルの結果セットです。
  
|[列]|データ型|[説明]|範囲|  
|------------|---------------|-----------------|-----------|  
|rows|BIGINT|行の数。||  
|reserved_space|BIGINT|領域の合計 (KB 単位) のオブジェクト用に予約されています。||  
|data_space|BIGINT|領域が kb 単位で、データに使用します。||  
|index_space|BIGINT|領域を kb 単位でのインデックスに使用します。||  
|unused_space|BIGINT|な領域を予約した領域の一部であり、使用しない、(KB 単位)。||  
|pdw_node_id|ssNoversion|領域の使用状況の報告に使用するためのコンピューティング ノードです。||  
|distribution_id|ssNoversion|領域の使用状況をレポートに使用する配布します。|値は、レプリケートされたテーブルの場合は-1 です。|  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdwshowspaceused-basic-syntax"></a>A. DBCC PDW_SHOWSPACEUSED の基本的な構文  
次の例では、[!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] データベースの FactInternetSales テーブルの行数、予約済みのディスク領域、使用済みのディスク領域を表示する複数の方法を示します。
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012.dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "AdventureWorksPDW2012..FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( "dbo.FactInternetSales" );  
DBCC PDW_SHOWSPACEUSED ( FactInternetSales );  
```  
  
### <a name="b-show-the-disk-space-used-by-all-tables-in-the-current-database"></a>B. 現在のデータベース内のすべてのテーブルで使用されるディスク領域を表示します。  
 次の例では、[!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] のすべてのユーザー テーブルとシステム テーブルで使用される予約済みのディスク領域を示します。  
  
```sql
-- Uses AdventureWorks  
  
DBCC PDW_SHOWSPACEUSED;  
```  
 ## <a name="see-also"></a>参照
[DBCC PDW_SHOWEXECUTIONPLAN &#40;Transact-SQL&#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWPARTITIONSTATS &#40;Transact-SQL&#41;](dbcc-pdw-showpartitionstats-transact-sql.md)

  
