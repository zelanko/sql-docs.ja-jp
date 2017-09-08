---
title: "データ型の優先順位 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- precedence [SQL Server]
- data types [SQL Server], converting
- data types [SQL Server], precedence
- converting data types [SQL Server], precedence
- precedence [SQL Server], data types
ms.assetid: f4c804ab-ed3f-43b1-a024-c9ac6944b66b
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f39337e00dfdbcd4a6bb01a00093a61f46a79fa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="data-type-precedence-transact-sql"></a>データ型の優先順位 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

演算子でデータ型が異なる 2 つの式を結合すると、データ型の優先順位の規則によって、優先順位の低いデータ型を優先順位の高いデータ型に変換することが指定されます。 暗黙的な変換がサポートされていない場合は、エラーが返されます。 両方のオペランド式が同じデータ型の場合は、演算の結果も同じデータ型になります。
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、次のデータ型の優先順位が使用されます。
  
1.  ユーザー定義データ型 (最高)  
1.  **sql_variant**  
1.  **xml**  
1.  **datetimeoffset**  
1.  **datetime2**  
1.  **datetime**  
1.  **smalldatetime**  
1.  **date**  
1. **time**  
1. **float**  
1. **real**  
1. **decimal**  
1. **money**  
1. **smallmoney**  
1. **bigint**  
1. **int**  
1. **smallint**  
1. **tinyint**  
1. **bit**  
1. **ntext**  
1. **text**  
1. **image**  
1. **timestamp**  
1. **uniqueidentifier**  
1. **nvarchar** (含む**nvarchar (max)** )  
1. **nchar**  
1. **varchar** (含む**varchar (max)** )  
1. **char**  
1. **varbinary** (含む**varbinary (max)** )  
1. **バイナリ**(最低)  
  
## <a name="see-also"></a>参照
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  

