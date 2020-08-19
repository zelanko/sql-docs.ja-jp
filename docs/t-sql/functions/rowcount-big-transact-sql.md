---
description: ROWCOUNT_BIG (Transact-SQL)
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
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 2523d69bbab745f9cc8dfc206a4949f8c15c0f9b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88459584"
---
# <a name="rowcount_big-transact-sql"></a>ROWCOUNT_BIG (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  最後に実行されたステートメントの影響を受けた行数を返します。 この関数は、[@@ROWCOUNT](../../t-sql/functions/rowcount-transact-sql.md) と同じように動作します。ただし、ROWCOUNT_BIG では、戻り値の型は **bigint** になります.  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ROWCOUNT_BIG ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>戻り値の型
 **bigint**  
  
## <a name="remarks"></a>解説  
 この関数は、SELECT ステートメントの後に置かれると、SELECT ステートメントによって返される行数を返します。  
  
 この関数は、INSERT ステートメント、UPDATE ステートメント、および DELETE ステートメントの後に置かれると、データ変更ステートメントによって影響を受ける行数を返します。  
  
 この関数は、IF ステートメントなどの行を返さないステートメントの後に置かれると、0 を返します。  
  
## <a name="see-also"></a>参照  
 [COUNT_BIG &#40;Transact-SQL&#41;](../../t-sql/functions/count-big-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  
