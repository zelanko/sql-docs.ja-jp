---
title: '&amp;= (ビットごとの AND 代入) (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 01/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|language-elements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '&='
- '&=_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators, &=
- assignment operators, &=
- augmented operators, &=
- '&= (bitwise AND equals)'
ms.assetid: f374c885-3fee-434a-93fb-dfe6e0bcd100
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0f769e6b8d1499c5636e3756ec01d94e070267c6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="amp-bitwise-and-assignment-transact-sql"></a>&amp;= (ビットごとの AND 代入) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]


  2 つの整数値の間でビットごとの論理積演算を実行し、値に演算の結果を設定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
expression &= expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 数値型に分類される任意のデータ型を持つ有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)です。ただし、**bit** データ型は除きます。  
  
## <a name="result-types"></a>戻り値の型  
 優先順位が高い引数のデータ型を返します。 詳細については、「[データ型の優先順位 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 詳細については、「[& &#40;ビット演算 AND&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/bitwise-and-transact-sql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [複合演算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [演算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [ビットごとの演算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  
