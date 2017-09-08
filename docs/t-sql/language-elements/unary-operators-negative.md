---
title: "- (負)(TRANSACT-SQL) |Microsoft ドキュメント"
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
- negative
dev_langs:
- TSQL
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
- negative values
ms.assetid: d6c14d14-d379-403b-82db-c197ad58c896
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 47a9eb729127e53dc3ee72fe5353ad536c56d922
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="unary-operators---negative"></a>単項演算子 - 負の値
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  数値式について負の値を返します (単項演算子)。 単項演算子は、数値型に分類されるデータ型の 1 つの式に対してだけ操作を実行します。   
  
|演算子|意味|  
|--------------|-------------|  
|[+ (正号)](../../t-sql/language-elements/unary-operators-positive.md)|数値は正の値です。|  
|[- (負号)](../../t-sql/language-elements/unary-operators-negative.md)|数値は負の値です。|  
|[~ (ビット演算子 NOT)](../../t-sql/language-elements/bitwise-not-transact-sql.md)|値の 1 の補数を返します。|  
  
 + (正) 演算子と - (負) 演算子は、数値型に分類されるデータ型の式で使用します。 ~ (ビットごとの NOT) 演算子を使用できるのは、整数型に分類されるデータ型の式だけです。 
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
- numeric_expression  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)日付以外の数値データ型カテゴリと時間のカテゴリのデータ型のいずれか。  
  
## <a name="result-types"></a>戻り値の型  
 データ型を返す*numeric_expression*する点を除いて、符号なし**tinyint**式の昇格を符号付き**smallint**結果。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-setting-a-variable-to-a-negative-value"></a>A. 変数に負の値を設定する  
 次の例では、変数に負の値を設定します。  
  
```  
USE tempdb;  
GO  
DECLARE @MyNumber decimal(10,2);  
SET @MyNumber = -123.45;  
SELECT @MyNumber AS NegativeValue;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
NegativeValue  
---------------------------------------  
-123.45  
  
(1 row(s) affected)  
  
```  
  
### <a name="b-changing-a-variable-to-a-negative-value"></a>B. 変数を負の値に変更する  
 次の例では、変数を負の値に変更します。  
  
```  
USE tempdb;  
GO  
DECLARE @Num1 int;  
SET @Num1 = 5;  
SELECT @Num1 AS VariableValue, -@Num1 AS NegativeValue;  
GO  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
VariableValue NegativeValue  
------------- -------------  
5             -5  
  
(1 row(s) affected)  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-the-negative-of-a-positive-constant"></a>C. 正の定数の負の値を返す  
 次の例では、正の定数の負の値を返します。  
  
```  
USE ssawPDW;  
  
SELECT TOP (1) - 17 FROM DimEmployee;  
```  
  
 返します。  
  
```  
-17  
```  
  
### <a name="d-returning-the-positive-of-a-negative-constant"></a>D. 負の定数の正の値を返す  
 次の例では、負の定数の正の値を返します。  
  
```  
USE ssawPDW;  
  
SELECT TOP (1) – ( - 17) FROM DimEmployee;  
```  
  
 返します。  
  
```  
17  
```  
  
### <a name="e-returning-the-negative-of-a-column"></a>E. 列の負の値を返す  
 次の例の負の値を返します、`BaseRate`内の各従業員の値、`dimEmployee`テーブル。  
  
```  
USE ssawPDW;  
  
SELECT - BaseRate FROM DimEmployee;  
```  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [式 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)  
  
  


