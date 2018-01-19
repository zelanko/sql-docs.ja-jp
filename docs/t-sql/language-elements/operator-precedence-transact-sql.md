---
title: "演算子の優先順位 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- operators [Transact-SQL], precedence
- operator precedence [Transact-SQL]
- order of operator execution [Transact-SQL]
- precedence [SQL Server], operators
ms.assetid: f04d2439-6fff-4e4c-801f-cc62faef510a
caps.latest.revision: "23"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b1208137b82bf64a6b48a7d6f2db2bc681a7d7f6
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="operator-precedence-transact-sql"></a>演算子の優先順位 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  複合式に複数の演算子がある場合は、演算子の優先順位によって、操作の実行順序が決まります。 実行される順序により、結果の値は大きく変わります。  
  
 演算子には、次の表に示す優先順位レベルが定義されています。 優先順位が高い演算子は、優先順位が低い演算子よりも前に評価されます。  
  
|レベル|演算子|  
|-----------|---------------|  
|1|~ (ビットごとの NOT)|  
|2|* (乗算)/(除算)、% (剰余)|  
|3|+ (正号)、- (負号) + (加算)、(+ 連結)、-(減算)、& (ビットごとの AND)、^ (ビットごとの排他的 OR)、(& a) #124;(ビットごとの OR)|  
|4|=、>、 \<、> =、< =、<>、! =、! >、! < (比較演算子)|  
|5|[NOT]|  
|6|[AND]|  
|7|ALL、ANY、BETWEEN、IN、LIKE、OR、SOME|  
|8|= (代入)|  
  
 式の中の 2 つの演算子が同じ優先順位レベルの場合は、式の中での位置に従って演算子は左から右へと評価されます。 たとえば、次で使用されている式で`SET`ステートメント、減算演算子が加算演算子の前に評価されます。  
  
```  
DECLARE @MyNumber int;  
SET @MyNumber = 4 - 2 + 27;  
-- Evaluates to 2 + 27 which yields an expression result of 29.  
SELECT @MyNumber;  
```  
  
 式の中で演算子の定義済みの優先順位を無効にするには、かっこを使用します。 この場合、かっこ内のすべての演算が評価され、1 つの値が作成されてから、かっこ外の演算子でこの値が使用されます。  
  
 たとえば、次で使用される式で`SET`ステートメント、乗算演算子が加算演算子より高い優先順位。 したがって、乗算演算子が先に評価され、式の結果は `13` になります。  
  
```  
DECLARE @MyNumber int;  
SET @MyNumber = 2 * 4 + 5;  
-- Evaluates to 8 + 5 which yields an expression result of 13.  
SELECT @MyNumber;  
```  
  
 次に使用される式で`SET`ステートメントでは、かっこにより、加算が先に実行されます。 式の結果は `18` になります。  
  
```  
DECLARE @MyNumber int;  
SET @MyNumber = 2 * (4 + 5);  
-- Evaluates to 2 * 9 which yields an expression result of 18.  
SELECT @MyNumber;  
```  
  
 式の中でかっこが入れ子になっている場合は、最も深い入れ子になった式が先に評価されます。 次の例には、式での入れ子になったかっこが含まれています。`5 - 3`最も深く入れ子になったかっこのセットにします。 この式の結果の値`2`です。 次に、加算演算子 (`+`) によって、この結果に `4` が加算されます。 値が生成されます。`6`です。 最後に `6` に `2` が乗算され、式の最終的な結果は `12` になります。  
  
```  
DECLARE @MyNumber int;  
SET @MyNumber = 2 * (4 + (5 - 3) );  
-- Evaluates to 2 * (4 + 2) which then evaluates to 2 * 6, and   
-- yields an expression result of 12.  
SELECT @MyNumber;  
```  
  
## <a name="see-also"></a>参照  
 [論理演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/logical-operators-transact-sql.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
  
