---
title: 有効桁数、小数点以下桁数、および長さ (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], length
- data types [SQL Server], scale
- precision [SQL Server], data types
- lengths [SQL Server], data types
- number of digits
- scale [SQL Server]
- scale [SQL Server], data types
- data types [SQL Server], precision
ms.assetid: fbc9ad2c-0d3b-4e98-8fdd-4d912328e40a
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: dc12ae4429ab39c1eb20059f17473e67cdbf60ca
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="precision-scale-and-length-transact-sql"></a>有効桁数、小数点以下桁数、および長さ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

有効桁数は、数値全体の桁数です。 小数点以下桁数は、数値の中で小数点より右側の桁数です。 たとえば、123.45 という値の場合、有効桁数は 5 で、小数点以下桁数は 2 になります。
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], の既定の最大有効桁数 **数値** と **decimal** データ型には 38 です。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、既定の最大値は 28 桁です。
  
数値型の長さは、数値の格納に使用されるバイト数です。 文字型や Unicode 型の長さは、文字数です。 長さは **バイナリ**, 、**varbinary**, 、および **イメージ** データ型には、バイト数。 たとえば、 **int** データ型の 10 桁を保持することができます、4 バイトに格納されている場合は、および小数点が許可されません。 **Int** データ型には precision を 10、長さは 4、および小数点以下桁数は 0 です。
  
2 つ **char**, 、**varchar**, 、**バイナリ**, 、または **varbinary** 式を連結するには、結果として得られる式の長さが 2 つのソース式または 8,000 文字の長さの合計は、小さい方です。
  
2 つ **nchar** または **nvarchar** 式を連結するには、結果として得られる式の長さが 2 つのソース式または 4,000 文字の長さの合計は、小さい方です。
  
同じデータ型で長さが異なる 2 つの式が、UNION、EXCEPT、または INTERSECT を使って比較される場合、結果の長さは 2 つの列の最大長になります。
  
有効桁数と小数点数値データ型を除くの **decimal** は固定です。 同じデータ型の 2 つの式に算術演算子を使用する場合、得られる結果のデータ型は同じになり、そのデータ型に定義されている有効桁数と小数点以下桁数が適用されます。 異なるデータ型の 2 つの式に演算子を使用する場合、結果のデータ型はデータ型の優先順位規則によって決まります。 結果には、そのデータ型に定義されている有効桁数と小数点以下桁数が適用されます。
  
次の表では、操作の結果を型の場合、有効桁数と小数点を結果の計算方法を定義 **decimal**です。 結果は **decima**l 、次のいずれかが true の場合。
-   両方の式が **decimal**です。  
-   一方の式が **decimal** よりも優先順位の低いデータ型をもう一方は **10 進**です。  
  
オペランド式は、有効桁数 p1 および小数点以下桁数 s1 の式 e1 と、有効桁数 p2 および小数点以下桁数 s2 の式 e2 で表されます。 有効桁数とは、任意の式の小数点以下桁数 **decimal** は、有効桁数と小数点以下桁数が、式のデータ型に対して定義されています。
  
|操作|結果の有効桁数|結果の小数点以下桁数 *|  
|---|---|---|
|e1 + e2|max(s1, s2) + max(p1-s1, p2-s2) + 1|max(s1, s2)|  
|e1 - e2|max(s1, s2) + max(p1-s1, p2-s2) + 1|max(s1, s2)|  
|e1 * e2|p1 + p2 + 1|s1 + s2|  
|e1 / e2|p1 - s1 + s2 + max(6, s1 + p2 + 1)|max(6, s1 + p2 + 1)|  
|e1 { UNION &#124; EXCEPT &#124; INTERSECT } e2|max(s1, s2) + max(p1-s1, p2-s2)|max(s1, s2)|  
|e1 % e2|min(p1-s1, p2 -s2) + max( s1,s2 )|max(s1, s2)|  
  
\*(& a) #42 です。結果の有効桁数と小数点以下桁数はある絶対最大値は 38 です。 結果の有効桁数が 38 桁を超える場合は 38 桁に減らされます。この際、結果の整数部分が切り捨てられることを防ぐために、小数点以下の桁数が減らされます。 乗算や除算などの演算では、10 進数の精度を維持するために、小数点以下の桁数が減らされることはありません。これは、オーバーフロー エラーが発生する可能性がある場合でも同じです。

加算と減算では、10 進数の整数部を格納するには、`max(p1 – s1, p2 – s2)` 桁必要です。 それらを格納できる十分な領域がない (つまり `max(p1 – s1, p2 – s2) < min(38, precision) – scale`) の場合は、整数部の領域を提供するために、小数点以下の桁数が減らされます。 結果の小数点以下の桁数は `MIN(precision, 38) - max(p1 – s1, p2 – s2)` になるため、この桁数に収まるように小数部が丸められます。

乗算と除算では、結果の整数部を格納するには、`precision - scale` 桁必要です。 次のルールを使用して、小数点以下の桁数が減らされることがあります。
1.  整数部が 32 桁よりも少ない場合、結果の小数点以下の桁数は `38 – (precision-scale)` を超えることはできないため、`min(scale, 38 – (precision-scale))` に減らされます。 これに該当する場合、結果は丸められる可能性があります。
1. 小数点以下の桁数が 6 桁未満であり、整数部が 32 を超える場合、小数点以下の桁数が変更されることはありません。 これに該当する場合、decimal(38, scale) に収まらなければ、オーバーフロー エラーが発生することがあります。 
1. 小数点以下の桁数が 6 桁以上であり、整数部が 32 を超える場合、小数点以下の桁数は 6 に設定されます。 これに該当する場合、整数部の桁数と小数部の桁数の両方が減らされ、結果の型は decimal(38,6) になります。 結果は、小数点以下の桁数が 6 桁に丸められるか、整数部を 32 桁に収めることができない場合はオーバーフロー エラーがスローされます。

## <a name="examples"></a>使用例
次の式は、丸めなしの結果 `0.00000090000000000` を返します。これは、結果が `decimal(38,17)` に収まるためです。
```sql
select cast(0.0000009000 as decimal(30,20)) * cast(1.0000000000 as decimal(30,20)) [decimal 38,17]
```
ここでは、有効桁数は 61 であり、小数点以下の桁数は 40 です。
整数部 (precision-scale = 21) が 32 未満であり、乗算ルールの (1) に該当するため、小数点以下の桁数は `min(scale, 38 – (precision-scale)) = min(40, 38 – (61-40)) = 17` で計算されます。 結果のデータ型は `decimal(38,17)` です。

次の式は、`decimal(38,6)` に収めた結果 `0.000001` を返します。
```sql
select cast(0.0000009000 as decimal(30,10)) * cast(1.0000000000 as decimal(30,10)) [decimal(38, 6)]
```
ここでは、有効桁数は 61 であり、小数数点以下の桁数は 20 です。
小数点以下の桁数が 6 桁を越えており、整数部 (`precision-scale = 41`) が 32 を超えています。 これは乗算ルールの (3) に該当するため、結果の型は `decimal(38,6)` になります。

## <a name="see-also"></a>参照
[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  
