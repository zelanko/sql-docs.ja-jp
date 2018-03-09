---
title: "&amp;= (ビットごとの AND 代入) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 933555582a035d6db79c1f0676fd2befc2fd70d2
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="amp-bitwise-and-assignment-transact-sql"></a>&amp;= (ビットごとの AND 代入) (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]


  2 つの整数値の間でビットごとの論理積演算を実行し、値に演算の結果を設定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
expression &= expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)任意のデータのいずれかの型、数値カテゴリを除く、**ビット**データ型。  
  
## <a name="result-types"></a>戻り値の型  
 優先順位が高い引数のデータ型を返します。 詳細については、「[データ型の優先順位 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 詳細については、次を参照してください。 [& &#40;です。ビットごとの AND &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-and-transact-sql.md).  
  
## <a name="see-also"></a>参照  
 [複合の演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [式 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [ビット処理演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  
