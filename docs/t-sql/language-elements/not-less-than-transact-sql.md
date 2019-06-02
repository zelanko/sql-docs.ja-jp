---
title: '!&lt;(より小さくない) (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '!<'
- Not Less
- '!<_TSQL'
- Not Less Than
- Less Than
dev_langs:
- TSQL
helpviewer_keywords:
- '!< (not less than)'
- not less than operator (!<)
ms.assetid: ecbb598e-58a2-4b6c-90b4-3ad5bdfcae39
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8bc9a49f65c6c6d3b85444efd55665321c9bbc89
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65981901"
---
# <a name="lt-not-less-than-transact-sql"></a>!&lt;(より小さくない) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  2 つの式を比較します (比較演算子)。 NULL でない式を比較したときに、左側のオペランドが右側のオペランドよりも小さい値ではない場合、結果は TRUE です。それ以外の場合、結果は FALSE です。 どちらか一方、または両方のオペランドが NULL の場合は、トピック「[SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
expression !< expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 任意の有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)を指定します。 両方の式とも、暗黙的に変換可能なデータ型でなければなりません。 変換は、[データ型の優先順位](../../t-sql/data-types/data-type-precedence-transact-sql.md)のルールに依存します。  
  
## <a name="result-types"></a>戻り値の型  
 **ブール値**  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [演算子 (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
