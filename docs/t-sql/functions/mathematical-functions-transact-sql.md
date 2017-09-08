---
title: "数学関数 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/06/2017
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
- calculations [SQL Server]
- mathematical functions [SQL Server]
- functions [SQL Server], mathematical
ms.assetid: 46495a2e-81d0-4677-9d72-9db083cd1023
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5ec4a6767acab606d6459b439683a88a0cae1caf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="mathematical-functions-transact-sql"></a>数学関数 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  以下のスカラー関数は、通常は引数として渡された入力値に基づいて計算を実行し、数値を返します。  
  
||||  
|-|-|-|  
|[ABS](../../t-sql/functions/abs-transact-sql.md)|[度](../../t-sql/functions/degrees-transact-sql.md)|[RAND 関数](../../t-sql/functions/rand-transact-sql.md)|  
|[ACOS](../../t-sql/functions/acos-transact-sql.md)|[EXP 関数](../../t-sql/functions/exp-transact-sql.md)|[ROUND](../../t-sql/functions/round-transact-sql.md)|  
|[ASIN](../../t-sql/functions/asin-transact-sql.md)|[FLOOR](../../t-sql/functions/floor-transact-sql.md)|[サインイン](../../t-sql/functions/sign-transact-sql.md)|  
|[ATAN](../../t-sql/functions/atan-transact-sql.md)|[ログ](../../t-sql/functions/log-transact-sql.md)|[SIN 関数](../../t-sql/functions/sin-transact-sql.md)|  
|[ATN2](../../t-sql/functions/atn2-transact-sql.md)|[LOG10 関数](../../t-sql/functions/log10-transact-sql.md)|[SQRT](../../t-sql/functions/sqrt-transact-sql.md)|  
|[CEILING](../../t-sql/functions/ceiling-transact-sql.md)|[PI](../../t-sql/functions/pi-transact-sql.md)|[正方形](../../t-sql/functions/square-transact-sql.md)|  
|[COS](../../t-sql/functions/cos-transact-sql.md)|[電源](../../t-sql/functions/power-transact-sql.md)|[TAN 関数](../../t-sql/functions/tan-transact-sql.md)|  
|[COT](../../t-sql/functions/cot-transact-sql.md)|[ラジアン](../../t-sql/functions/radians-transact-sql.md)||  
  
> [!NOTE]  
>  ABS、CEILING、DEGREES、FLOOR、POWER、RADIANS、SIGN などの算術関数は、入力値と同じデータ型の値を返します。 三角関数やその他の関数は、EXP、LOG、LOG10、SQUARE、および、SQRT など、入力値をキャスト**float**を返すと、 **float**値。  
  
 RAND を除くすべての数学関数は決定的です。 つまり、特定の一連の入力値を使用して呼び出されるたびに、同じ結果を返します。 RAND は、シード パラメーターが指定されている場合にのみ決定的です。 関数の決定性の詳細については、次を参照してください。[決定的関数と非決定的関数](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)です。  
  
## <a name="see-also"></a>参照  
  [算術演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/arithmetic-operators-transact-sql.md)  
  [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
  

