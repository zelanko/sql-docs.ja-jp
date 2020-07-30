---
title: RAND (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- RAND
- RAND_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RAND function
- values [SQL Server], random float
- random float value
ms.assetid: 363c84d6-b9fa-49ba-9a75-e44f27535ff6
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6eaffe69fa7ce886b358f5b4adbd41d56796bbeb
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396269"
---
# <a name="rand-transact-sql"></a>RAND (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  擬似乱数を返します **float** 0 ～ 1 の排他値。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
RAND ( [ seed ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>引数
 *seed*  
 シード値を指定する整数の[式](../../t-sql/language-elements/expressions-transact-sql.md) (**tinyint**、**smallint**、または **int**)。 場合 *シード* が指定されていない、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] シード値をランダムに割り当てられます。 指定されたシード値に対し、返される結果は常に同じです。  
  
## <a name="return-types"></a>戻り値の型  
 **float**  
  
## <a name="remarks"></a>解説  
 同じシード値を使用して RAND() を繰り返し呼び出しても、同じ結果が返されます。  
  
 1 つの接続について、指定したシード値で RAND() を呼び出すと、以降のすべての RAND() の呼び出しで、シード値を指定した RAND() の呼び出しに基づいた結果が生成されます。 たとえば、次のクエリでは、同じ数値のシーケンスが常に返されます。  
  
```sql  
SELECT RAND(100), RAND(), RAND()   
```  
  
## <a name="examples"></a>例  
 次の例では、RAND 関数によって 4 つの異なる乱数が生成されます。  
  
```sql  
DECLARE @counter SMALLINT;  
SET @counter = 1;  
WHILE @counter < 5  
   BEGIN  
      SELECT RAND() Random_Number  
      SET @counter = @counter + 1  
   END;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [数学関数 &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  
