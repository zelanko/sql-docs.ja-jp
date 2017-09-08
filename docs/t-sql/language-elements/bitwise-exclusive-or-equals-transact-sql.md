---
title: "^ = (ビットごとの排他的 OR 代入) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ^=
- ^=_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ^= (bitwise exclusive OR equals)
- compound operators, ^=
ms.assetid: ce524b0f-a24d-44e7-bd5b-b6943793cd48
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5f7c69571c760fe828a6a731b348a12168b095cb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="-bitwise-exclusive-or-equals-transact-sql"></a>^= (ビットごとの排他的 OR 代入) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  2 つの整数値の間でビットごとの排他的 OR 演算を実行し、値に演算の結果を設定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
expression ^= expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)任意のデータのいずれかの型、数値カテゴリを除く、**ビット**データ型。  
  
## <a name="result-types"></a>戻り値の型  
 優先順位が高い引数のデータ型を返します。 詳細については、「[データ型の優先順位 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 詳細については、次を参照してください。 [^ & #40 です。ビットごとの排他的 OR &#41;& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-exclusive-or-transact-sql.md).  
  
## <a name="see-also"></a>参照  
 [複合の演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [式 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [ビット処理演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  

