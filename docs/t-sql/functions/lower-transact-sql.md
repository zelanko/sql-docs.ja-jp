---
title: "下位 (TRANSACT-SQL) |Microsoft ドキュメント"
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
- LOWER
- LOWER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- characters [SQL Server], lowercase
- LOWER function
- uppercase characters [SQL Server]
- characters [SQL Server], uppercase
- lowercase characters
- converting uppercase to lowercase characters
ms.assetid: 1783352b-6852-4658-9d94-51963c59b9bf
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 545d3b5a0635c80f55aeb5b0a7a4e1804098e19c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lower-transact-sql"></a>LOWER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  大文字の文字データを小文字に変換した後の文字式を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
LOWER ( character_expression )  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)の文字またはバイナリ データ。 *character_expression*定数、変数、または列を指定できます。 *character_expression*に暗黙的に変換できるデータ型でなければなりません**varchar**です。 それ以外の場合、使用[キャスト](../../t-sql/functions/cast-and-convert-transact-sql.md)明示的に変換する*character_expression*です。  
  
## <a name="return-types"></a>戻り値の型  
 **varchar**または**nvarchar**  
  
## <a name="examples"></a>使用例  
 次の例では、$11 ～ $20 の価格の製品名を選択する際に、`LOWER` 関数、`UPPER` 関数、`UPPER` 関数を入れ子にしている `LOWER` 関数を使用しています。 この例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
SELECT LOWER(SUBSTRING(Name, 1, 20)) AS Lower,   
   UPPER(SUBSTRING(Name, 1, 20)) AS Upper,   
   LOWER(UPPER(SUBSTRING(Name, 1, 20))) As LowerUpper  
FROM Production.Product  
WHERE ListPrice between 11.00 and 20.00;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Lower                    Upper                    LowerUpper  
---------------------    ---------------------    --------------------  
minipump                 MINIPUMP                 minipump 
taillights - battery     TAILLIGHTS - BATTERY     taillights - battery  
  
(2 row(s) affected)
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、$11 ～ $20 の価格の製品名を選択する際に、`LOWER` 関数、`UPPER` 関数、`UPPER` 関数を入れ子にしている `LOWER` 関数を使用しています。  
  
```  
-- Uses AdventureWorks  
  
SELECT LOWER(SUBSTRING(EnglishProductName, 1, 20)) AS Lower,   
       UPPER(SUBSTRING(EnglishProductName, 1, 20)) AS Upper,   
       LOWER(UPPER(SUBSTRING(EnglishProductName, 1, 20))) As LowerUpper  
FROM dbo.DimProduct  
WHERE ListPrice between 11.00 and 20.00;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Lower                 Upper                  LowerUpper  
--------------------  ---------------------  --------------------  
minipump              MINIPUMP               minipump  
taillights – battery  TAILLIGHTS – BATTERY   taillights - battery
```  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [文字列関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


