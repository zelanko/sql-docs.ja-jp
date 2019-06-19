---
title: 分析関数 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 60fbff84-673b-48ea-9254-6ecdad20e7fe
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ebf74ab07a424612967f1482402928fc134d9e03
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65945169"
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
  
  
