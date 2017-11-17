---
title: "+ = (文字列連結) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/07/2016
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
dev_langs:
- TSQL
helpviewer_keywords:
- concatenate strings
- string concatenation
- += (concatenate operator)
ms.assetid: 4aaeaab7-9b2b-48e0-8487-04ed672ebcb1
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7c557bcc1d3c2f314ce57e93701b11833f5a6fc6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="string-concatenation---equal-transact-sql"></a>文字列の連結 - 等しい (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  2 つの文字列を連結し、その結果の文字列を演算の結果に設定します。 たとえば、変数@x'Adventure' を等しい@x+ = 'Works' の元の値を受け取る@xを文字列に 'Works' を追加し、設定@xにその新しい値 'AdventureWorks'。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
expression += expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)文字データ型のいずれか。  
  
## <a name="result-types"></a>戻り値の型  
 変数に対して定義されているデータ型を返します。  
  
## <a name="remarks"></a>解説  
 設定@v1+ = 'expression' はセットに相当@v1= @v1 + ('expression')。 また、設定@v1= @v2 + @v3 +@v4はセットに相当@v1= (@v2 + @v3) +@v4です。  
  
 += 演算子を変数なしで使用することはできません。 たとえば、次のコードはエラーになります。  
  
```  
SELECT 'Adventure' += 'Works'  
```  
  
## <a name="examples"></a>使用例  
### <a name="a-concatenation-using--operator"></a>A. + = 演算子を使用して連結
 次の例では、`+=` 演算子を使用して文字列を連結しています。  
  
```  
DECLARE @v1 varchar(40);  
SET @v1 = 'This is the original.';  
SET @v1 += ' More text.';  
PRINT @v1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `This is the original. More text.`  
  
### <a name="b-order-of-evaluation-while-concatenating-using--operator"></a>B. + = 演算子を使用して連結するときに評価の順序
次の例では、1 つの長い文字列を形成する複数の文字列を連結し、最終的な文字列の長さの計算を試みます。 この例では、連結演算子を使用しているときに、評価順序と切り捨てルールを示します。 

```
DECLARE @x varchar(4000) = replicate('x', 4000)
DECLARE @z varchar(8000) = replicate('z',8000)
DECLARE @y varchar(max);
 
SET @y = '';
SET @y += @x + @z;
SELECT LEN(@y) AS Y; -- 8000
 
SET @y = '';
SET @y = @y + @x + @z;
SELECT LEN(@y) AS Y; -- 12000
 
SET @y = '';
SET @y = @y +(@x + @z);
SELECT LEN(@y) AS Y; -- 8000
-- or
SET @y = '';
SET @y = @x + @z + @y;
SELECT LEN(@y) AS Y; -- 8000
GO
```
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Y       
 ------- 
 8000 
  
 (1 row(s) affected) 
  
    
 Y       
 ------- 
 12000 
  
 (1 row(s) affected) 

 Y       
 ------- 
 8000 
  
 (1 row(s) affected) 
  
 Y       
 ------- 
 8000 
  
 (1 row(s) affected)
  ```   
   
## <a name="see-also"></a>参照  
 [演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [+ = (& a) #40 です。追加等しい &#41;& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/add-equals-transact-sql.md)   
 [+ (& a) #40 です。文字列の連結 &#41;& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
  
  

