---
title: "ISNUMERIC (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ISNUMERIC
- ISNUMERIC_TSQL
dev_langs: TSQL
helpviewer_keywords:
- expressions [SQL Server], valid numeric type
- numeric data
- ISNUMERIC function
- verifying valid numeric type
- valid numeric type [SQL Server]
- checking valid numeric type
ms.assetid: 7aa816de-529a-4f6c-a99f-4d5a9ef599eb
caps.latest.revision: "44"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 15ef4648daf6489a1224536acf5ee71250afe469
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isnumeric-transact-sql"></a>ISNUMERIC (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  式が数値型として有効かどうかを調べます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ISNUMERIC ( expression )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)に評価されます。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>解説  
 ISNUMERIC は、入力式が有効な数値データ型であると判断される場合に 1 を返します。それ以外の場合は 0 を返します。 有効な数値データ型は次のとおりです。  
  
|||  
|-|-|  
|**int**|**numeric**|  
|**bigint**|**money**|  
|**smallint**|**smallmoney**|  
|**tinyint**|**float**|  
|**decimal**|**real**|  
  
> [!NOTE]  
>  ISNUMERIC は、数字以外の一部の文字に対して 1 を返します。たとえばプラス (+)、マイナス (-)、ドル記号 ($) などの通貨記号がこれに該当します。 通貨記号の一覧については、次を参照してください。 [money および smallmoney &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/money-and-smallmoney-transact-sql.md).  
  
## <a name="examples"></a>使用例  
 次の例では`ISNUMERIC`を数値の値ではないすべての郵便番号コードを返します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, PostalCode  
FROM Person.Address   
WHERE ISNUMERIC(PostalCode)<> 1;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では`ISNUMERIC`を数値の値ではないすべての郵便番号コードを返します。  
  
```  
USE master;  
GO  
SELECT name, isnumeric(name) AS IsNameANumber, database_id, isnumeric(database_id) AS IsIdANumber   
FROM sys.databases;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [式 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [システム関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  

