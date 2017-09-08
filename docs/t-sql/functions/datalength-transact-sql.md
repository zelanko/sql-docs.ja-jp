---
title: "DATALENGTH (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATALENGTH_TSQL
- DATALENGTH
dev_langs:
- TSQL
helpviewer_keywords:
- number of bytes representing expression
- data types [SQL Server], length
- DATALENGTH function
- expressions [SQL Server], length
- lengths [SQL Server], data
ms.assetid: 00f377f1-cc3e-4eac-be47-b3e3f80267c9
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 49889c4b29de0d86859c1363ce13b9656645848d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="datalength-transact-sql"></a>DATALENGTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

式を表すために必要なバイト数を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
DATALENGTH ( expression )   
```  
  
## <a name="arguments"></a>引数  
*式 (expression)*  
[式](../../t-sql/language-elements/expressions-transact-sql.md)任意のデータ型。
  
## <a name="return-types"></a>戻り値の型
**bigint**場合*式*は、 **varchar (max)**、 **nvarchar (max)**または**varbinary (max)**データ型です。それ以外の場合**int**です。
  
## <a name="remarks"></a>解説  
DATALENGTH は特に効果的**varchar**、 **varbinary**、**テキスト**、**イメージ**、 **nvarchar**、および**ntext**データ型をこれらのデータ型は可変長のデータを格納できるためです。
  
NULL の DATALENGTH は NULL です。
  
> [!NOTE]  
>  戻り値は、互換性レベルによって変わることがあります。 互換性レベルの詳細については、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
次の例の長さの検索、`Name`内の列、`Product`テーブル。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT length = DATALENGTH(Name), Name  
FROM Production.Product  
ORDER BY Name;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
次の例の長さの検索、`Name`内の列、`Product`テーブル。
  
```sql
-- Uses AdventureWorks  
  
SELECT length = DATALENGTH(EnglishProductName), EnglishProductName  
FROM dbo.DimProduct  
ORDER BY EnglishProductName;  
GO  
```  
  
## <a name="see-also"></a>参照
[Len 関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/len-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[システム関数 & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/system-functions-for-transact-sql.md)
  
  


