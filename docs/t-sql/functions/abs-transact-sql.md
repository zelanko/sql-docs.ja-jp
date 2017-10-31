---
title: "ABS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ABS_TSQL
- ABS
dev_langs:
- TSQL
helpviewer_keywords:
- values [SQL Server], positive
- values [SQL Server], absolute
- ABS function
- absolute positive value
ms.assetid: e2ea7a6d-3e2f-472c-afbc-437d3b835c03
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eed45893b664e79071d1b423f5d84977e11f5a24
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="abs-transact-sql"></a>ABS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

指定した数値式の絶対値 (正値) を返す数学関数です。 (`ABS`負の値を正の値を変更します。 `ABS`0 の影響を与えませんまたは正の値です)。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
ABS ( numeric_expression )  
```  
  
## <a name="arguments"></a>引数  
*numeric_expression*  
真数型または概数型の式を指定します。
  
## <a name="return-types"></a>戻り値の型  
*numeric_expression*と同じ型を返します。
  
## <a name="examples"></a>使用例  
次の例を使用した結果、 `ABS` 3 つの異なる値に対して関数。
  
```sql
SELECT ABS(-1.0), ABS(0.0), ABS(1.0);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
---- ---- ----  
1.0  .0   1.0  
```  
  
`ABS`数値の絶対値が指定されたデータ型で表すことができる最大数より大きい場合、関数はオーバーフロー エラーを生成できます。 たとえば、`int`データ型の値のみ保持できる範囲の`-2,147,483,648`に`2,147,483,647`です。 符号付き整数の絶対値を計算`-2,147,483,648`絶対値がの正数の範囲を超えているので、オーバーフロー エラーが発生、`int`データ型。
  
```sql
DECLARE @i int;  
SET @i = -2147483648;  
SELECT ABS(@i);  
GO  
```  
  
次にエラー メッセージを示します。
  
"メッセージ 8115、レベル 16、状態 2、行 3"
  
"式をデータ型 int に変換中に演算のオーバーフロー エラーが発生しました"

  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[数学関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/mathematical-functions-transact-sql.md)  
[組み込み関数 &#40;Transact-SQL&#41;](../../t-sql/functions/functions.md)
  
  


