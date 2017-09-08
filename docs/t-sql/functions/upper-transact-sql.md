---
title: "UPPER (TRANSACT-SQL) |Microsoft ドキュメント"
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
- UPPER_TSQL
- UPPER
dev_langs:
- TSQL
helpviewer_keywords:
- UPPER function
- characters [SQL Server], lowercase
- converting lowercase to uppercase
- uppercase characters [SQL Server]
- characters [SQL Server], uppercase
- lowercase characters
ms.assetid: 5ced55f7-ac89-4cf2-9465-f63f4dc480db
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7572e82178b211fba9967a88cb16c20d059c7b52
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="upper-transact-sql"></a>UPPER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  小文字データを大文字に変換して文字式を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
UPPER ( character_expression )  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)の文字データです。 *character_expression*定数、変数、または文字またはバイナリ データのいずれかの列を指定できます。  
  
 *character_expression*に暗黙的に変換できるデータ型でなければなりません**varchar**です。 それ以外の場合、使用[キャスト](../../t-sql/functions/cast-and-convert-transact-sql.md)明示的に変換する*character_expression*です。  
  
## <a name="return-types"></a>戻り値の型  
 **varchar**または**nvarchar**  
  
## <a name="examples"></a>使用例  
 次の例では、`UPPER`と`RTRIM`を内の人の姓を返す関数、`Person`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベースは大文字、ようにトリミング、および最初名を連結しました。  
  
```  
SELECT UPPER(RTRIM(LastName)) + ', ' + FirstName AS Name  
FROM Person.Person  
ORDER BY LastName;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、`UPPER`と`RTRIM`を内の人の姓を返す関数、`dbo.DimEmployee`大文字、切り捨て、名を連結した結果になるようにテーブルです。  
  
```  
-- Uses AdventureWorks  
  
SELECT UPPER(RTRIM(LastName)) + ', ' + FirstName AS Name  
FROM dbo.DimEmployee  
ORDER BY LastName;  
```  
  
 部分的な結果セットを次に示します。  
  
 `Name`  
  
 `------------------------------`  
  
 `ABBAS, Syed`  
  
 `ABERCROMBIE, Kim`  
  
 `ABOLROUS, Hazem`  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [文字列関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


