---
title: "ROWCOUNT_BIG (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 38c430082532904b230e7a4a594e82e5c14e670e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="rowcountbig-transact-sql"></a>ROWCOUNT_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  直前に実行されたステートメントの影響を受けた行数を返します。 この関数のように動作する[@@ROWCOUNT](../../t-sql/functions/rowcount-transact-sql.md)ROWCOUNT_BIG の戻り値の型は点を除いて、 **bigint**です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ROWCOUNT_BIG ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 **bigint**  
  
## <a name="remarks"></a>解説  
 SELECT ステートメントの後に使用すると、この関数は、その SELECT ステートメントで返された行数を返します。  
  
 INSERT、UPDATE、または DELETE ステートメントの後に使用すると、この関数はデータ変更ステートメントの影響を受けた行数を返します。  
  
 IF ステートメントなど、行を返さないステートメントの後に使用すると、この関数は 0 を返します。  
  
## <a name="see-also"></a>参照  
 [COUNT_BIG & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/count-big-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  

