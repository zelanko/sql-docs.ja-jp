---
title: "+ = (加算代入) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- +=
- +=_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- += (add equals)
- compound operators, +=
ms.assetid: 9ea52519-80d1-473f-b988-0572f0e2c92f
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0d07ab123822db8f381af6fcc4f1707529bed359
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="-add-equals-transact-sql"></a>+= (加算代入) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  2 つの数値を加算し、値に演算の結果を設定します。 場合、変数など、 @x 35 にし、等しい@x+ = 2 の元の値を受け取る@x、2 とセットを追加@xにその新しい値 (37) です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
expression += expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)任意のデータ型を除く、数値カテゴリで、**ビット**データ型。  
  
## <a name="result-types"></a>戻り値の型  
 優先順位が高い引数のデータ型を返します。 詳細については、「[データ型の優先順位 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 詳細については、次を参照してください。 [+ & #40 です。追加 (& a) #41;& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/add-transact-sql.md).  
  
## <a name="see-also"></a>参照  
 [複合の演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [式 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [+ = (& a) #40 です。文字列の連結 &#41;& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/string-concatenation-equal-transact-sql.md)  
  
  
