---
title: ROWCOUNT_BIG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ROWCOUNT_BIG
- ROWCOUNT_BIG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ROWCOUNT_BIG function
- number of rows affected by statement
- row affected by statements [SQL Server]
- statements [SQL Server], last statement
- counting rows
ms.assetid: 6e18a0eb-bb36-4348-90d9-8b1ecf095064
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c0bf5d49e4e9effac44fd80bfd32cc68a8107216
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="rowcountbig-transact-sql"></a>ROWCOUNT_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  直前に実行されたステートメントの影響を受けた行数を返します。 この関数は、[@@ROWCOUNT](../../t-sql/functions/rowcount-transact-sql.md) と同じように動作します。ただし、ROWCOUNT_BIG では、戻り値の型は **bigint** になります.  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ROWCOUNT_BIG ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 **bigint**  
  
## <a name="remarks"></a>Remarks  
 SELECT ステートメントの後に使用すると、この関数は、その SELECT ステートメントで返された行数を返します。  
  
 INSERT、UPDATE、または DELETE ステートメントの後に使用すると、この関数はデータ変更ステートメントの影響を受けた行数を返します。  
  
 IF ステートメントなど、行を返さないステートメントの後に使用すると、この関数は 0 を返します。  
  
## <a name="see-also"></a>参照  
 [COUNT_BIG &#40;Transact-SQL&#41;](../../t-sql/functions/count-big-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  
