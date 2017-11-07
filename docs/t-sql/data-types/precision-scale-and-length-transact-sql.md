---
title: "有効桁数、小数点以下桁数、および長さ (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 557d7a5c45e9cc5a0839dfb4a1fdb0d08c2bf83f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="precision-scale-and-length-transact-sql"></a>有効桁数、小数点以下桁数、および長さ (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

有効桁数は、数値全体の桁数です。 小数点以下桁数は、数値の中で小数点より右側の桁数です。 たとえば、123.45 という値の場合、有効桁数は 5 で、小数点以下桁数は 2 になります。
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の既定の最大有効桁数**数値**と**decimal**データ型には 38 です。 以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既定の最大値は 28 です。
  
数値型の長さは、数値の格納に使用されるバイト数です。 文字型や Unicode 型の長さは、文字数です。 長さは、**バイナリ**、 **varbinary**、および**イメージ**データ型は、バイト数。 たとえば、 **int**データ型は、10 桁を保持することができます、4 バイトに格納され、小数点が許可されません。 **Int**データ型は precision を 10、長さは 4、および小数点以下桁数は 0 です。
  
2 つ**char**、 **varchar**、**バイナリ**、または**varbinary**式を連結、結果式の長さが、2 つのソース式または 8,000 文字の長さの合計か小さい方です。
  
2 つ**nchar**または**nvarchar**式を連結、結果式の長さが 2 つのソース式または 4,000 文字の長さの合計、小さい方です。
  
同じデータ型で長さが異なる 2 つの式が、UNION、EXCEPT、または INTERSECT を使って比較される場合、結果の長さは 2 つの列の最大長になります。
  
有効桁数と小数点以下桁数の数値データ型を除く**decimal**固定されます。 同じデータ型の 2 つの式に算術演算子を使用する場合、得られる結果のデータ型は同じになり、そのデータ型に定義されている有効桁数と小数点以下桁数が適用されます。 異なるデータ型の 2 つの式に演算子を使用する場合、結果のデータ型はデータ型の優先順位規則によって決まります。 結果には、そのデータ型に定義されている有効桁数と小数点以下桁数が適用されます。
  
次の表では、操作の結果は型の場合、有効桁数と小数点の結果の計算方法を定義**decimal**です。 結果は**decimal**次のいずれかが true の場合。
-   両方の式が**decimal**です。  
-   1 つの式は**decimal**よりも優先順位が低いデータ型で、もう一方**10 進**です。  
  
オペランド式は、有効桁数 p1 および小数点以下桁数 s1 の式 e1 と、有効桁数 p2 および小数点以下桁数 s2 の式 e2 で表されます。 有効桁数と小数点以下桁数、任意の式ではない**decimal**は、有効桁数と小数点式のデータ型に対して定義されています。
  
|操作|結果の有効桁数|結果の小数点以下桁数 *|  
|---|---|---|
|e1 + e2|max(s1, s2) + max(p1-s1, p2-s2) + 1|max(s1, s2)|  
|e1 - e2|max(s1, s2) + max(p1-s1, p2-s2) + 1|max(s1, s2)|  
|e1 * e2|p1 + p2 + 1|s1 + s2|  
|e1 / e2|p1 - s1 + s2 + max(6, s1 + p2 + 1)|max(6, s1 + p2 + 1)|  
|e1 {共用体 &#124; です。除く &#124; INTERSECT} e2|max(s1, s2) + max(p1-s1, p2-s2)|max(s1, s2)|  
|e1 % e2|min(p1-s1, p2 -s2) + max( s1,s2 )|max(s1, s2)|  
  
\*結果の有効桁数と小数点以下桁数はある絶対最大値は 38 です。 結果の有効桁数が 38 より大きい場合は、38 にし、結果の整数部分が切り詰められていることを防止しようとする、対応するスケールが減ります。 乗算、除算など一部の場合、スケール ファクターが解消されない 10 進数の精度を維持するためにオーバーフロー エラーが発生することができますがします。

加算と減算操作で必要があります`max(p1 – s1, p2 – s2)`10 進数の整数部を格納する場所です。 つまりに保存する十分な領域がないか`max(p1 – s1, p2 – s2) < min(38, precision) – scale`、小数点以下桁数が十分な領域は、不可欠な部分に減少します。 結果の小数点以下桁数は`MIN(precision, 38) - max(p1 – s1, p2 – s2)`、小数部分は、結果の小数点以下桁数に収まるように丸められます可能性があります。

乗算と除算操作に必要があります`precision - scale`結果の整数部分を格納する場所です。 次の規則を使用して、スケールが低下する可能性があります。
1.  結果の小数点以下桁数に減少する`min(scale, 38 – (precision-scale))`整数部分が 32 より小さいより大きいことができないため`38 – (precision-scale)`です。 結果は、ここで丸められます可能性があります。
1. 6 未満である場合、整数部分が 32 を超える場合、小数点以下桁数は変更されません。 ここでは、decimal (38、小数点以下桁数) に収めることができない場合オーバーフロー エラーを発生する可能性があります。 
1. 6 より大きい場合に、整数部分が 32 を超える場合、小数点以下桁数は 6 に設定されます。 ここでは、整数部と小数点以下桁数の両方が低下すると、結果として得られる型 decimal(38,6) です。 結果は 6 つの小数点以下桁数に丸められます可能性があります。 または 32 桁に不可欠な部分が収まらない場合、オーバーフロー エラーがスローされます。

## <a name="examples"></a>使用例
次の式は、結果を返します`0.00000090000000000`丸め、結果に収まるのでせず`decimal(38,17)`:
```sql
select cast(0.0000009000 as decimal(30,20)) * cast(1.0000000000 as decimal(30,20)) [decimal 38,17]
```
ここで、有効桁数は 61、および小数点以下桁数は 40 です。
整数部 (- 小数点以下桁数 = 21) は、32 より小さい乗算ルールでケース (1) で、小数点以下桁数として計算`min(scale, 38 – (precision-scale)) = min(40, 38 – (61-40)) = 17`です。 結果型は`decimal(38,17)`します。

次の式は、結果を返します`0.000001`に収まるように`decimal(38,6)`:
```sql
select cast(0.0000009000 as decimal(30,10)) * cast(1.0000000000 as decimal(30,10)) [decimal(38, 6)]
```
ここで、有効桁数は 61、および小数点以下桁数は 20 です。
小数点以下桁数は 6 と整数の部分よりも大きい (`precision-scale = 41`) が 32 を超えています。 これは、乗算のルールでケース (3) と結果型は`decimal(38,6)`します。

## <a name="see-also"></a>参照
[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  

