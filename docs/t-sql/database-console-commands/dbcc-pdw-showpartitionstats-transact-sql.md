---
title: "DBCC PDW_SHOWPARTITIONSTATS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/17/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|database-console-commands
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
caps.latest.revision: "10"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fb41140783d4c334e7ee701f44d523ec68e41435
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="dbcc-pdwshowpartitionstats-transact-sql"></a>DBCC PDW_SHOWPARTITIONSTATS (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

サイズと各パーティション内のテーブルの行の数を表示、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]データベース。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
Show the partition stats for a table  
DBCC PDW_SHOWPARTITIONSTATS ( " [ database_name . [ schema_name ] . ] | [ schema_name.] table_name  ")  
[;]  
```  
  
## <a name="arguments"></a>引数  
 [ *database_name*です。 [ *schema_name* ] です。 | *schema_name*です。 *table_name*  
 1 つ、2 枚、または表示するテーブルの 3 部構成の名前。  2 つの 3 つの要素名、名前は、二重引用符で囲む必要がありますか ("")。 1 つの部分から成るテーブル名を囲む引用符を使用したはオプションです。  
  
## <a name="permissions"></a>Permissions
必要があります**VIEW SERVER STATE**権限です。
  
## <a name="result-sets"></a>結果セット  
これは、DBCC PDW_SHOWPARTITIONSTATS コマンドの結果です。
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|partition_number|int|パーティション番号。|  
|used_page_count|bigint|データの使用ページ数です。|  
|reserved_page_count|bigint|パーティションに割り当てられたページの数。|  
|row_count|bigint|パーティション内の行の数。|  
|pdw_node_id|int|データのノードを計算します。|  
|distribution_id|int|データの配布の id です。|  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdwshowpartitionstats-basic-syntax-examples"></a>A. DBCC PDW_SHOWPARTITIONSTATS の基本的な構文の例  
次の例では、FactInternetSales テーブルのパーティションによって使用される領域と行の数を表示、[!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)]データベース。
  
```sql
DBCC PDW_SHOWPARTITIONSTATS ("ssawPDW.dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS ("dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS (FactInternetSales);  
```  
## <a name="see-also"></a>参照
[DBCC PDW_SHOWEXECUTIONPLAN &#40;です。TRANSACT-SQL と #41 です。](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED &#40;です。TRANSACT-SQL と #41 です。](dbcc-pdw-showspaceused-transact-sql.md)  
  
