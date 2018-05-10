---
title: DATALENGTH (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 346b5aada1a16e84aa3e74019e83dd7a74d9914a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="datalength-transact-sql"></a>DATALENGTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

式を表すために必要なバイト数を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DATALENGTH ( expression )   
```  
  
## <a name="arguments"></a>引数  
*式 (expression)*  
任意の型の[式](../../t-sql/language-elements/expressions-transact-sql.md)を指定します。
  
## <a name="return-types"></a>戻り値の型
*式*が **varchar(max)**、**nvarchar(max)**、または **varbinary(max)** データ型の場合は **bigint**。それ以外の場合は **int**。
  
## <a name="remarks"></a>Remarks  
DATALENGTH は、可変長データを保存できる **varchar**、**varbinary**、**text**、**image**、**nvarchar**、および **ntext** などのデータ型にとって特に効果的です。
  
NULL の DATALENGTH は NULL です。
  
> [!NOTE]  
>  戻り値は、互換性レベルによって変わることがあります。 互換性レベルの詳細については、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
次の例は、`Name` テーブルの `Product` 列の長さを返します。
  
```sql
-- Uses AdventureWorks  
  
SELECT length = DATALENGTH(EnglishProductName), EnglishProductName  
FROM dbo.DimProduct  
ORDER BY EnglishProductName;  
GO  
```  
  
## <a name="see-also"></a>参照
[LEN &#40;Transact-SQL&#41;](../../t-sql/functions/len-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[システム関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)
  
  

