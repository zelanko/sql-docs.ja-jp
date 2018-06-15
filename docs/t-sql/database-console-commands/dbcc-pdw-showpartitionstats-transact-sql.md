---
title: DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
caps.latest.revision: 10
author: edmacauley
ms.author: umajay
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 40f8af57d1caff81e7738fabfab0788154f90772
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33702025"
---
# <a name="dbcc-pdwshowpartitionstats-transact-sql"></a>DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] または [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] データベースに含まれるテーブルの各パーティションについて、サイズと行数を表示します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
Show the partition stats for a table  
DBCC PDW_SHOWPARTITIONSTATS ( " [ database_name . [ schema_name ] . ] | [ schema_name.] table_name  ")  
[;]  
```  
  
## <a name="arguments"></a>引数  
 [ *database_name* . [ *schema_name* ] . | *schema_name* . ] *table_name*  
 1 つ、2 枚、または表示するテーブルの 3 部構成の名前。  2 つの 3 つの要素名、名前は、二重引用符で囲む必要がありますか ("")。 1 つの部分から成るテーブル名を囲む引用符を使用したはオプションです。  
  
## <a name="permissions"></a>アクセス許可
**VIEW SERVER STATE** アクセス許可が必要です。
  
## <a name="result-sets"></a>結果セット  
これは、DBCC PDW_SHOWPARTITIONSTATS コマンドの結果です。
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|partition_number|ssNoversion|パーティション番号。|  
|used_page_count|BIGINT|データの使用ページ数です。|  
|reserved_page_count|BIGINT|パーティションに割り当てられたページの数。|  
|row_count|BIGINT|パーティション内の行の数。|  
|pdw_node_id|ssNoversion|データのノードを計算します。|  
|distribution_id|ssNoversion|データの配布の id です。|  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdwshowpartitionstats-basic-syntax-examples"></a>A. DBCC PDW_SHOWPARTITIONSTATS の基本的な構文の例  
次の例では、[!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] データベースの FactInternetSales テーブルについて、パーティションごとに使用されている領域と行数を表示しています。
  
```sql
DBCC PDW_SHOWPARTITIONSTATS ("ssawPDW.dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS ("dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS (FactInternetSales);  
```  
## <a name="see-also"></a>参照
[DBCC PDW_SHOWEXECUTIONPLAN &#40;Transact-SQL&#41;](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED &#40;Transact-SQL&#41;](dbcc-pdw-showspaceused-transact-sql.md)  
  
