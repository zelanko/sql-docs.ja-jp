---
title: "ASCII (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ASCII_TSQL
- ASCII
dev_langs:
- TSQL
helpviewer_keywords:
- ASCII function
- characters [SQL Server], ASCII
- code [SQL Server], ASCII
- leftmost character of expression
ms.assetid: 45c2044a-0593-4805-8bae-0fad4bde2e6b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: b933f33b8eb6b3909eaf7cb0afcd8bfe19862dee
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="ascii-transact-sql"></a>ASCII (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

文字式の左端の文字の ASCII コード値を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
ASCII ( character_expression )  
```  
  
## <a name="arguments"></a>引数  
*character_expression*  
[式](../../t-sql/language-elements/expressions-transact-sql.md)型の**char**または**varchar**です。
  
## <a name="return-types"></a>戻り値の型
 **int**  
  
## <a name="remarks"></a>解説
情報交換用米国標準コードの省略形は ASCII です。 コンピューターで使用されるエンコード文字であります。 ASCII 文字の一覧は、次を参照してください。、**印刷可能な文字**のセクション[ASCII](https://www.wikipedia.org/wiki/ASCII)です。

## <a name="examples"></a>使用例  
次の例は、ASCII 文字セットを想定しを返します、 `ASCII` 6 文字の値。
  
```sql
SELECT ASCII('A') AS A, ASCII('B') AS B,   
ASCII('a') AS a, ASCII('b') AS b,  
ASCII(1) AS [1], ASCII(2) AS [2];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
A           B           a           b           1           2  
----------- ----------- ----------- ----------- ----------- -----------  
65          66          97          98          49          50  
```  
  
## <a name="see-also"></a>参照
 [CHAR &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/char-transact-sql.md)  
 [NCHAR と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/nchar-transact-sql.md)  
 [UNICODE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/unicode-transact-sql.md)  
 [文字列関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)
  
  


