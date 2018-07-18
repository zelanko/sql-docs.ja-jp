---
title: 分析関数 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 60fbff84-673b-48ea-9254-6ecdad20e7fe
caps.latest.revision: 5
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a850e153a2c64fb3de4828d2698d16cad97d7d17
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37781163"
---
# <a name="analytic-functions-transact-sql"></a>分析関数 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

SQL Server は、これらの分析関数をサポートします。
  
|||  
|-|-|  
|[CUME_DIST (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cume-dist-transact-sql.md)|[潜在顧客と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/lead-transact-sql.md)|  
|[FIRST_VALUE と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/first-value-transact-sql.md)|[PERCENTILE_CONT と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/percentile-cont-transact-sql.md)|  
|[間隔 (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/lag-transact-sql.md)|[PERCENTILE_DISC (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/percentile-disc-transact-sql.md)|  
|[LAST_VALUE (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/last-value-transact-sql.md)|[PERCENT_RANK (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/percent-rank-transact-sql.md)|  
  
分析関数によって、行のグループに基づいた集計値が計算されます。 ただし集計関数とは異なり、分析関数は各グループについて複数の行を返すことがあります。 グループ内の移動平均、集計途中経過、パーセンテージまたは上位 N 位の結果を計算するには、分析関数を使用します。
 
## <a name="see-also"></a>参照
[OVER 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
