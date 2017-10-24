---
title: "LTRIM (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LTRIM
- LTRIM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- leading blanks
- deleting blank spaces
- characters [SQL Server], blanks
- removing blank spaces
- LTRIM function
- blank characters [SQL Server]
ms.assetid: 369ed340-1a09-4597-a9eb-6720156cd39a
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ad63999f685b31848ea505fd5a671d1e163ddc91
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="ltrim-transact-sql"></a>LTRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  先頭の空白を削除した後の文字式を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
LTRIM ( character_expression )  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)の文字またはバイナリ データ。 *character_expression*定数、変数、または列を指定できます。 *character_expression*を除くデータ型である必要があります**テキスト**、 **ntext**、および**イメージ**、つまりに暗黙的に変換**varchar**. それ以外の場合、使用[キャスト](../../t-sql/functions/cast-and-convert-transact-sql.md)明示的に変換する*character_expression*です。  
  
## <a name="return-type"></a>戻り値の型  
 **varchar**または**nvarchar**  
  
## <a name="examples"></a>使用例  

### <a name="a-simple-example"></a>A. 簡単な例   

 次の例では、LTRIM を使用して、文字式から先頭のスペースを削除します。  
  
```tsql  
SELECT LTRIM('     Five spaces are at the beginning of this string.') FROM sys.databases;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ---------------------------------------------------------------  
  Five spaces are at the beginning of this string.
  ```  

### <a name="b-example-using-a-variable"></a>B: 例の変数を使用します。   
  
 次の例では、`LTRIM` を使用して文字変数から先頭の空白を削除します。  
  
```  
DECLARE @string_to_trim varchar(60);  
SET @string_to_trim = '     5 spaces are at the beginning of this string.';  
SELECT 
    @string_to_trim AS 'Original string',
    LTRIM(@string_to_trim) AS 'Without spaces';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Original string Without spaces
--------------------------------------------------- ---------------------------------------------
     5 spaces are at the beginning of this string.  5 spaces are at the beginning of this string.
```  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [文字列関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  
  
  



