---
title: ROWCOUNT_BIG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f485d550a122ede18b3faea9d1d490a449ab8d54
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65942787"
---
# <a name="rowcountbig-transact-sql"></a>ROWCOUNT_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  最後に実行されたステートメントの影響を受けた行数を返します。 この関数は、[@@ROWCOUNT](../../t-sql/functions/rowcount-transact-sql.md) と同じように動作します。ただし、ROWCOUNT_BIG では、戻り値の型は **bigint** になります.  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ROWCOUNT_BIG ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 **bigint**  
  
## <a name="remarks"></a>Remarks  
 この関数は、SELECT ステートメントの後に置かれると、SELECT ステートメントによって返される行数を返します。  
  
 この関数は、INSERT ステートメント、UPDATE ステートメント、および DELETE ステートメントの後に置かれると、データ変更ステートメントによって影響を受ける行数を返します。  
  
 この関数は、IF ステートメントなどの行を返さないステートメントの後に置かれると、0 を返します。  
  
## <a name="see-also"></a>参照  
 [COUNT_BIG &#40;Transact-SQL&#41;](../../t-sql/functions/count-big-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  
