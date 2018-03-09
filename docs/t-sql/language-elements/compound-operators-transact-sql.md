---
title: "複合演算子 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators
- compound operators, described
ms.assetid: 5072fe91-02d3-42a7-831f-756eff714a17
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 38aa65b196288c120dea5766fe29c64d58af0216
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="compound-operators-transact-sql"></a>複合演算子 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  複合演算子では、いくつかの演算を実行し、元の値に演算の結果を設定します。 場合、変数など、 @x 35 にし、等しい@x+ = 2 の元の値を受け取る@x、2 とセットを追加@xにその新しい値 (37) です。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]次の複合演算子を提供します。  
  
|演算子|詳細情報へのリンク|操作|  
|--------------|------------------------------|------------|  
|+=|[+ = (& a) #40 です。追加の割り当て &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/add-equals-transact-sql.md)|いくつかの数値を元の値に加算し、元の値に結果を設定します。|  
|-=|[-= (& a) #40 です。減算代入 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/subtract-equals-transact-sql.md)|いくつかの数値を元の値から減算し、元の値に結果を設定します。|  
|*=|[&#42; = (& a) #40 です。乗算代入 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/multiply-equals-transact-sql.md)|1 つの数値で乗算し、元の値に結果を設定します。|  
|/=|[& # #40; 除算代入 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/divide-equals-transact-sql.md)|1 つの数値で除算し、元の値に結果を設定します。|  
|%=|[剰余代入 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/modulo-equals-transact-sql.md)|1 つの数値で除算し、元の値に剰余を設定します。|  
|&=|[& = (& a) #40 です。ビットごとの AND 代入 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)|ビットごとの AND 演算を実行し、元の値に結果を設定します。|  
|^=|[^ = (& a) #40 です。ビットごとの排他的 OR 代入 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)|ビットごとの排他的 OR 演算を実行し、元の値に結果を設定します。|  
|&#124;=|[&#124; = (& a) #40 です。ビットごとの OR 代入 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)|ビットごとの OR 演算を実行し、元の値に結果を設定します。|  
  
## <a name="syntax"></a>構文  
  
```  
  
expression operator expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)任意の数値のカテゴリのデータのいずれかの型します。  
  
## <a name="result-types"></a>戻り値の型  
 優先順位が高い引数のデータ型を返します。 詳細については、「[データ型の優先順位 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 詳細については、それぞれの演算子に関するトピックを参照してください。  
  
## <a name="examples"></a>使用例  
 複合演算の例を次に示します。  
  
```  
DECLARE @x1 int = 27;  
SET @x1 += 2 ;  
SELECT @x1 AS Added_2;  
  
DECLARE @x2 int = 27;  
SET @x2 -= 2 ;  
SELECT @x2 AS Subtracted_2;  
  
DECLARE @x3 int = 27;  
SET @x3 *= 2 ;  
SELECT @x3 AS Multiplied_by_2;  
  
DECLARE @x4 int = 27;  
SET @x4 /= 2 ;  
SELECT @x4 AS Divided_by_2;  
  
DECLARE @x5 int = 27;  
SET @x5 %= 2 ;  
SELECT @x5 AS Modulo_of_27_divided_by_2;  
  
DECLARE @x6 int = 9;  
SET @x6 &= 13 ;  
SELECT @x6 AS Bitwise_AND;  
  
DECLARE @x7 int = 27;  
SET @x7 ^= 2 ;  
SELECT @x7 AS Bitwise_Exclusive_OR;  
  
DECLARE @x8 int = 27;  
SET @x8 |= 2 ;  
SELECT @x8 AS Bitwise_OR;  
  
```  
  
## <a name="see-also"></a>参照  
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [ビット処理演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  
