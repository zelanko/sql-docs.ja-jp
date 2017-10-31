---
title: "相違点 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DIFFERENCE
- DIFFERENCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DIFFERENCE function
- comparing SOUNDEX values
- SOUNDEX values
ms.assetid: c58ca25d-d6ea-48fa-93bb-c9374b0b2a2b
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 1868f902cf41eba9637138d7333ac908c72cb76e
ms.contentlocale: ja-jp
ms.lasthandoff: 10/17/2017

---
# <a name="difference-transact-sql"></a>DIFFERENCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  2 つの文字式の SOUNDEX 値の差を示す整数値を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DIFFERENCE ( character_expression , character_expression )  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 英数字で構成[式](../../t-sql/language-elements/expressions-transact-sql.md)の文字データです。 *character_expression*定数、変数、または列を指定できます。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>解説  
 返される整数は、2 つ式の SOUNDEX 値に、どの程度同じ文字が含まれているかを表します。 戻り値の範囲は 0 ～ 4 で、0 は類似性が低いか類似性がないことを示し、4 は類似性が高いか同じ値であることを示します。  
  
 DIFFERENCE と SOUNDEX は照合順序に依存します。  
  
## <a name="examples"></a>使用例  
 次の例の最初の部分では、よく似た 2 つの文字列の `SOUNDEX` 値が比較されます。 Latin1_General の照合順序`DIFFERENCE`の値を返します`4`です。 次の例の 2 番目の部分で、`SOUNDEX`値どうしを比較する 2 つの大きく異なる文字列と Latin1_General の照合順序`DIFFERENCE`の値を返します`0`です。  
  
```  
-- Returns a DIFFERENCE value of 4, the least possible difference.  
SELECT SOUNDEX('Green'), SOUNDEX('Greene'), DIFFERENCE('Green','Greene');  
GO  
-- Returns a DIFFERENCE value of 0, the highest possible difference.  
SELECT SOUNDEX('Blotchet-Halls'), SOUNDEX('Greene'), DIFFERENCE('Blotchet-Halls', 'Greene');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----- ----- -----------   
G650  G650  4             
  
(1 row(s) affected)  
  
----- ----- -----------   
B432  G650  0             
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [SOUNDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/soundex-transact-sql.md)   
 [文字列関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


